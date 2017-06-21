---
layout: post
title:  "Backup remoto com Attic"
date:   2017-06-21 08:00:00
author: stevelacerda
categories: blog
---

Backup remoto é algo extremamente importante e cada vez mais necessário, principalmente com o ransomware à solta. Neste post, apresento um passo-a-passo para configurar um sistema de backup remoto incremental utilizando o Attic. Vamos lá?

Sou cliente da [Hetzner](http://hetzner.de) há quase 04 anos e, desde então, trabalhei com cerca de 15 servidores diferentes. Em todo esse tempo, foram raras as vezes em que o datacenter me deixou na mão. Para completar, a empresa lançou há poucos meses o serviço de storage box, um disco virtual que pode ser acessado via FTP ou CIFS, por exemplo.

Atualmente tenho servidores com discos que somam 12 TB e, por isso, preciso de um sistema de backup seguro e eficiente. Por indicação do [Flaudísio](https://github.com/flaudisio), comecei a usar o Attic e, desde então, as tarefas de backup se tornaram muito mais simples. Para começar, o Attic utiliza o conceito de deduplicação de arquivos e busca otimizar o espaço utilizado para armazenamento, o que se torna muito útil quando o volume de dados é grande. Juntando o Attic e o storage box, consegui criar um sistema de backup que tem superado as minhas expectativas, tanto de desempenho quanto de facilidade de uso.

O primeiro passo é a contratação do storage box da Hetzner, que pode ser feito diretamente pelo site. Após a sua ativação, podemos acessá-lo via compartilhamento do Windows (CIFS) ou FTP. Nesse caso, será utilizado o CIFS em um servidor Linux. Para tal, basta utilizar o comando mount.cifs, da seguinte maneira:

        mount.cifs //<id>.your-storagebox.de/backup \
                   <diretorio-de-destino> \
                   -o user=<id>,pass=<senha>

Pronto! O storage box está disponível no diretório escolhido e já pode ser utilizado. O id e a senha são fornecidos pelo datacenter, bastando apenas configurar uma senha forte para evitar ataques de força bruta.

O próximo passo é configurar o Attic, o que é extremamente simples. Após a instalação, é necessário apenas iniciar o repositório e criar o primeiro backup:

        attic init <diretoriodebackup/repositorio.attic>
        attic create <diretoriodebackup/repositorio.attic>::<nome-do-backup> \
                     <arquivos-e-diretorios-para-backup>

Vale ressaltar que o nome do backup pode ser escolhido no momento da criação, mas recomenda-se utilizar algo que seja representativo, como a data e o horário do backup.

Embora seja possível, a criação do backup diretamente no storage box não é recomendado para grandes volumes de dados, especialmente devido ao tempo necessário para verificação dos arquivos. Em vez disso, será utilizado um diretório local, posteriormente sincronizado com o repositório remoto. Como o storage box já está montado, a sincronização pode ser feita via RSync para minimizar o tráfego de dados.

Para simplificar e automatizar todo o processo, um simples shell script pode ajudar:

        #!/bin/sh
        BACKUPFILES="$@"
        BACKUPDIR="/backup/backup.attic"
        CIFSMOUNT="<DIRETORIO-DE-DESTINO>"
        STORAGEBOXADDRESS="//<ID>.your-storagebox.de/backup"
        STORAGEBOXADDRESSOPTIONS="user=<ID>,pass=<SENHA>"
        DAILY=15
        WEEKLY=4
        MONTHLY=12
        
        checkmount () {
            if mount | grep $CIFSMOUNT > /dev/null; then
                return 1
            else
                return 0
            fi
        }
        
        if checkmount; then
            mount.cifs $STORAGEBOXADDRESS $CIFSMOUNT \
                       -o $STORAGEBOXADDRESSOPTIONS
            if checkmount; then
                echo "ERROR: CIFS not mounted"
                exit 1
            fi
        fi
        
        attic create --stats $BACKUPDIR::$(date +%Y-%m-%d) ${BACKUPFILES}
        attic prune -v $BACKUPDIR \
                    --keep-daily=$DAILY \
                    --keep-weekly=$WEEKLY \
                    --keep-monthly=$MONTHLY
        rsync -rlptDv --del $BACKUPDIR/ \
              $CIFSMOUNT/backup/backup.attic/
        umount -v $CIFSMOUNT

Além de criar os backups, o script acima faz a sincronização com o storage box e apaga os backups antigos. Ao final da execução, ele ainda desmonta o storage box, para evitar algum acesso indevido aos arquivos.

Agora é só jogar o script no CRON e ser feliz!
