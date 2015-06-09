# innobackupex-s3

Utility scripts for encrypted incremental backups to amazon s3 based on [Streaming MariaDB backups in the cloud](https://mariadb.com/blog/streaming-mariadb-backups-cloud).
 
The xbstream format is used for easy to manage backups.
 
## Scripts

### innobackupex-s3-backup

Handles the incremental backups to amazon s3, 1 week of backups is also kept locally on the server.

Required environment variables:

- **S3_BUCKET**: amazon s3 bucket backups will be uploaded
- **AWS_ACCESS_KEY_ID**: amazon s3 access key 
- **AWS_SECRET_ACCESS_KEY**: amazon s3 access key secret 

Optional environment variables:

- **BACKUPS_DIR**: full path where mysql backups will be stored on the server. 
- **KEY_FILE**: key file used for encrypted backups. use `innobackupex-s3-genkey` to generate key.  

### innobackupex-s3-restore-prepare

prepares a directory containing encrypted xbstream backups for restore. expects the first xbstream file in the directory to be a full backup.

Optional environment variables:

- **KEY_FILE**: key file used for encrypted backups. use `innobackupex-s3-genkey` to generate key.  

### innobackupex-s3-genkey

Generates a key file for use with encrypted backups.

Optional environment variables:

- **KEY_FILE**: override the default output file location. 
