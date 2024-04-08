# Shell Script
## What do we need?
- A script that creates a file where to save our backups
- To have weekly updates on a weekend to not create any issues on weekdays
- to automate the process

## Script

With the following requirements we can start writing our scripts and then use cron jobs to do th weekly back up on sunday midnight. First here is how our script will look:

```bash
#!/bin/bash

# Define the backup directory
backup_dir="/backup"

# Create the backup directory if it doesn't exist
mkdir -p "$backup_dir"

# Backup DHCP configuration
cp /etc/dhcp/dhcpd.conf "$backup_dir/dhcpd.conf"

# Backup DNS configuration
cp /etc/bind/named.conf.options "$backup_dir/named.conf.o>
cp /etc/bind/named.conf.local "$backup_dir/named.conf.loc>
cp /etc/bind/db.* "$backup_dir/"

# Backup HTTP configuration
cp /etc/apache2/sites-available/glpi.conf "$backup_dir/"
```
Now that we have our script, we have to make it executable by running:

```bash
$ chmod +x backup.sh
```
Then run the script to make sure it works:

```bash
$ ./backup.sh
```
## Cron Job

Now we can set up our cron job:

```bash
$ crontab -e
```
Inside the cron interface we can now set our script to run every week of every month on sunday midnight:

```bash
0 0 * * 0 /path/to/backup.sh
```
Just make sure to replace the path with the actual directory where the backup.sh file is. 

Congrats! You not only backed up your server but automated it!!! Now we can continue to the next and final step for the server, [ssh](./SSH.md).