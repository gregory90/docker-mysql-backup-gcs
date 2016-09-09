### How to backup?
Backup continuously to GCS. Database should be running.

```
docker run -v DIRECTORY_TO_BACKUP:/data -e GCLOUD_KEYFILE_BASE64= -e GCLOUD_PROJECT= -e BUCKET=gs:// -e DBHOST= -e DBPORT=3306 -e DBUSER= -e DBPASS= gregory90/file-backup-gcs /app/run
```


##### Environment variables
GCLOUD_KEYFILE_BASE64 - service account json key,  
GCLOUD_PROJECT - project id,  
BUCKET - GCS bucket for backup.  
DBHOST - MySQL host,  
DBPORT - MySQL port,  
DBUSER - MySQL user,  
DBPASS - MySQL password.  

### Restore backup
Restore database from GCS. Database should be shutdown.

```
docker run -v DIRECTORY_TO_RESTORE_TO:/data -e GCLOUD_KEYFILE_BASE64= -e GCLOUD_PROJECT= -e BUCKET=gs:// -e FILE= gregory90/mysql-backup-gcs /app/restore
```

##### Environment variables
GCLOUD_KEYFILE_BASE64 - service account json key,  
GCLOUD_PROJECT - project id,  
BUCKET - GCS bucket for backup.  
FILE - file to restore,  
