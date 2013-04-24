Selectel S3QL Backup
====================

S3QL allows you to use **rsync** or other weapon of choice to push backup files to the cloud.

Selectel S3QL Backup is invoked, it mounts the cloud container, copies your backups into it and unmounts. Keeping the container mounted is not recommended as S3QL is prone to filesystem corruption on unexpected reboot.

Note that you'll be unable to browse your cloud container via Selectel web interface. To access the container, you'll have to use `mount` and `umount` scripts that come with Selectel S3QL Backup.


Installation, configuration and usage
-------------------------------------

1) Install S3QL. On Ubuntu you can do that with:

    aptitude install s3ql python-pkg-resources

2) Clone this to a permanent location:

    sudo mkdir /opt/selectel-s3ql-backup
    sudo git clone https://github.com/lolmaus/selectel-s3ql-backup.git /opt/selectel-s3ql-backup

3) Edit `authfile` and `vars` to match your Selectel properties. Edit `backup` to store the files you need.

4) Create a mount point:

    sudo mkdir /mnt/selectel
    sudo touch /mnt/selectel/s3ql-is-not-mounted

5) Test by running `backup`:

    sudo /opt/selectel-s3ql-backup/backup

6) Add `backup` to cron. On Ubuntu you can do that with:

    sudo ln -s /opt/selectel-s3ql-backup/backup /etc/cron.daily/selectel-backup


Credit and License
------------------

Created by Andrey 'lolmaus' Mikhaylov, covered by the [MIT licence][1].

You are encouraged to use the [issue queue][2] to report problems and suggest ideas.

  [1]: http://opensource.org/licenses/MIT
  [2]: https://github.com/lolmaus/selectel-s3ql-backup/issues
