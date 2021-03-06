## Week 5 Homework Submission File: Archiving and Logging Data

Please edit this file by adding the solution commands on the line below the prompt.

Save and submit the completed file for your homework submission.

---

### Step 1: Create, Extract, Compress, and Manage tar Backup Archives

1. Command to **extract** the `TarDocs.tar` archive to the current directory: tar -xvf TarDocs.tar

2. Command to **create** the `Javaless_Doc.tar` archive from the `TarDocs/` directory, while excluding the `TarDocs/Documents/Java` directory: 

tar -cvf Javaless_Docs.tar --exclude TarDocs/Documents/Java TarDocs

3. Command to ensure `Java/` is not in the new `Javaless_Docs.tar` archive:

tar -tvf Javaless_Docs.tar | grep "Java"

**Bonus** 
- Command to create an incremental archive called `logs_backup_tar.gz` with only changed files to `snapshot.file` for the `/var/log` directory:

#### Critical Analysis Question

- Why wouldn't you use the options `-x` and `-c` at the same with `tar`?
The -x is to untar the file the -c is to create a tar
---

### Step 2: Create, Manage, and Automate Cron Jobs

1. Cron job for backing up the `/var/log/auth.log` file:
0 6 * * 3 tar -czf /auth_backup.tgz /var/log/auth.log
---

### Step 3: Write Basic Bash Scripts

1. Brace expansion command to create the four subdirectories:

2. Paste your `system.sh` script edits below:

    ```bash
    #!/bin/bash
    mkdir ~/backups/{freemem,diskuse,openlist,freedisk}
    ```

3. Command to make the `system.sh` script executable:
     sudo chmod +x system.sh
**Optional**
- Commands to test the script and confirm its execution:

**Bonus**
- Command to copy `system` to system-wide cron directory:

---

### Step 4: Perform Various Log Filtering Techniques

1. Command to return `journalctl` messages with priorities from emergency to error:
journalctl -p err
2. Command to check the disk usage of the system journal unit since the most recent boot:
journalctl --disk-usage
3. Comand to remove all archived journal files except the most recent two:
sudo journalctl --vacuum-files=2
**Bonus** 
- Command to filter all log messages with priority levels between zero and two, and save output to `/home/sysadmin/Priority_High.txt`:

- Command to automate the last command in a daily cronjob:


- Add the edits made to the crontab file below:

    ```bash
    [Your solution cron edits here]
    ```

---

### Step 5. Create Priority-Based Log Files

1. Command to record all mail log messages, except for debug, to `/var/log/mail.log`:


mail.info                       /var/log/mail.log
mail.warn                       /var/log/mail.log
mail.err                        /var/log/mail.log
mail.crit                       /var/log/mail.log
mail.alert                      /var/log/mail.log
mail.emerg                      /var/log/mail.log



### Step 6. Manage Log File Sizes
 
1. Run `sudo nano /etc/logrotate.conf` to edit the `logrotate` configuration file. 

    Configure a log rotation scheme that backs up authentication messages to the `/var/log/auth.log`.

    - /var/log/auth.log {
        missingok
        weekly
        rotate 7
        notifempty
        delaycompress
}

    ```

---
