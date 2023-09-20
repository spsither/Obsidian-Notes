Get the `museum.sql` file from Image DB
`scp tibetmuseum@172.28.13.135:~/backup/museum.sql ~`

Get the Images from Image DB
`scp tibetmuseum@172.28.13.135:~/backup/imageBackup.tar.xz ~`

Unzip Images and put `upload_museum` in `museum-backend/public/` in your local computer's `museum-backend` Laravel repo

Take the `museum.sql` to a server with `phpmyadmin`
`mysql -u root -p museum < museum.sql`

Change the character set to `utf8mb4_general_ci`  for the following columns in the `list` table
- title
- keywords
- remarks

Export the `museum.sql` file with updated character set in server with `phpmyadmin`
`mysqldump -u root -p museum > museum.sql`

Drop all the tables and seed the database `newmuseum` database
`php artisan migrate:fresh --seed`

Bring back the `museum.sql` from server with `phpmyadmin` to local computer and import it in `newmuseum` database
`mysql -u root -p newmuseum < museum.sql`

Update `category`, `subject` and `sub_subject` table in the `newmuseum`
`art move:subject`

Gives `color_id` based on average image colour in `list` table. This script is in `museum-data-cleanup` repository
`./enterColorFromImage.py`

Delete all the Objects in `S3` `thetibetmuseum`

Migrate on your local machine
`art move:all`
(will take several hours)

Export the `newmuseum.sql` file out of local 
`mysqldump -u root -p newmuseum > newmuseum.sql`

Copy the `newmsuem.sql` file to The Museum `EC2` server
`scp -i "first key pair.pem" ~/newmuseum.sql ubuntu@ec2-3-109-172-97.ap-south-1.compute.amazonaws.com:~`

Import the `newmsueum.sql` file in The Museum `EC2` server
`mysql -u root -p newmuseum < ~/newmuseum.sql`

To upload `3D` Objects static sites to `S3` `museumobject` bucket
`aws s3 cp objects s3://museumobject --recursive`

To run the `Next.js` app on the server
`npm run deploy:prod`

## To Increment
Get the `museum.sql` file from Image DB
`scp tibetmuseum@172.28.13.135:~/backup/museum.sql ~`

Get the Images from Image DB
`scp tibetmuseum@172.28.13.135:~/backup/imageBackup.tar.xz ~`

Unzip Images and put `upload_museum` in `museum-backend/public/` in your local computer's `museum-backend` Laravel repo

Take the `museum.sql` to a server with `phpmyadmin`
`mysql -u root -p museum < museum.sql`

Change the character set to `utf8mb4_general_ci`  for the following columns in the `list` table
- title
- keywords
- remarks

Export the `museum.sql` file with updated character set in server with `phpmyadmin`
`mysqldump -u root -p museum > museum.sql`

Bring back the `museum.sql` from server with `phpmyadmin` to local computer and import it in `newmuseum` database
`mysql -u root -p newmuseum < museum.sql`

Update `category`, `subject` and `sub_subject` table in the `newmuseum`
`art move:subject`

Gives color_id based on average image color in `list` table. This script is in `museum-data-cleanup` repository
`./enterColorFromImage.py`

Update `MoveIncrement.php` to select which alert range to incrementally update
```php
$logs = DB::table('alert')
->where('id', '>', 33177)
->where('id', '<=', 33859)
->get();
```
And then run
`art move:increment`

To upload 3D Objects static sites to S3 `museumobject` bucket
`aws s3 cp objects s3://museumobject --recursive`

To run the Next.js app on the server
```bash

cd /var/www/interactive.tibetmuseum.org/react-tibet-museum

npm run deploy:prod

```


## Tables in `Laravel` Back-end
audits
categories
colors
departments
failed_jobs
image_tag
images
media
migrations
password_resets
personal_access_tokens
questions
sub_subjects
subjects
tags
users
virtual_tours

## Tables in Image DB Core PHP
alert
category
colors
comment
department
download
list
login
sub_subject
subject