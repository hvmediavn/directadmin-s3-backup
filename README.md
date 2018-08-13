# directadmin-s3-backup
DirectAdmin S3 Backup

Features
--------
- Auto backup upload to AWS S3
- Auto Create S3 Bucket
- Auto delete old backups after X day(s)

Installation
------------

Download the [.zip](https://github.com/powerkernel/directadmin-s3-backup/archive/master.zip) file, and then extract it into your DirectAdmin at a location you choose. Then update `config.php` with your AWS access keys.

We assume that the .zip is extracted at `/home/admin/tools/directadmin-s3-backup`, run `composer update` to download the AWS PHP-SDK.

Create `ftp_upload.php` file in `/usr/local/directadmin/scripts/custom` with the following content:
```
#!/bin/sh
RET=0;
/usr/local/bin/php /home/admin/tools/directadmin-s3-backup/ftp_upload_aws.php $ftp_local_file $ftp_remote_file 2>&1
RET=$?
exit $RET
```

Finally, go to `DirectAdmin \ Admin Backup/Transfer` to create Cron Schedule backup, select FTP for the backup location.
