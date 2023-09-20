Delete all images
>sudo docker rmi -f $(sudo docker images | awk -F' ' '{print $3}' | grep -v 'IMAGE')

/opt/greenbook/CTARepo
When you see `greenbook-api exited with code 139` do
>sudo docker-compose restart api

Import store procedure
```
docker exec greenbook-db /usr/bin/mysqldump -u root --password=test@123! ctadb < stored-procedure-may-03.sql
```

```
docker exec greenbook-db /usr/bin/mysqldump -u root --password=test@123! ctadb > ctadb_backup2022_Oct_10.sql
```
