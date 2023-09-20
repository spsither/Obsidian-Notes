## check the size
>du -h /var

## to zip
>tar -zcvf test.tar.gz ./getting-started

## to unzip
>tar -xvzf test.tar.gz

## to zip only specific files
>tar -cJ -T /home/tibetmuseum/backup/to_zip.txt -f /home/tibetmuseum/backup/imageBackup.tar.xz

## zip .tar.xz
>tar -cJvf /home/tcrc/backup/media.tar.xz /var/www/psc/upload_psc

## to unzip .tar.xz
>tar -xJvf media.tar.xz  upload_museum_thumb