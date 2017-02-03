# Backup

This is a script for making automatic backups of specified directories. It can backup to both a local directory or a remote server. It tries to read three configuration files, each of which defines the backup type:
* `/etc/backup-local.conf` or `.backup-local.conf` in the user's home directory. This will create a backup using rsync to a local directory with 7 days history.
* `/etc/backup-remote-duplicity.conf` or `.backup-remote-duplicity.conf` in the user's home directory. This will use duplicity to backup to a remote server with history and encryption.
* `/etc/backup-remote-rsync.conf` or `.backup-remote-rsync.conf` in the user's home directory. This will use rsync to backup to a remote server without history or encryption.

These configuration files should set the following variables:

* `LOCATION`: The path where the backup is to be stored.
* `MOUNT`: If set to "yes" the backup location should be mounted before making the backup and unmounted afterwards. Only used for local backups.
* `SERVER`: The name of the remote backup server. Not used for local backups.
* `USER`: The name to use when logging in on the remote server. Not used for local backups.
* `PASSPHRASE`: The GPG passphrase for duplicity. Not used for local backups.
* `FOLDERS`: An array with the absolute paths of the folders to backup.
* `DELETEDFILESFOLDER`: The location where files that are removed from the backup will be backupped. This path is relative to the LOCATION settings. Only used for rsync backups. Not used for local backups.

