# Linux Automation Bash Scripts Collection

This collection contains beginner-friendly Bash scripts for automating common Linux administration tasks. Each script is simple, readable, and includes a sample cron job entry to schedule it every Sunday at 12:00 AM.

---

# 1. System Updates and Package Upgrades

```bash
#!/bin/bash

echo "Starting system update..."

sudo apt update && sudo apt upgrade -y

echo "System update completed successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/system_update.sh
```

---

# 2. Log Rotation and Old Log Cleanup

```bash
#!/bin/bash

LOG_DIR="/var/log"

find $LOG_DIR -type f -name "*.log" -mtime +7 -exec rm -f {} \;

echo "Old log files cleaned successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/log_cleanup.sh
```

---

# 3. User Account Creation

```bash
#!/bin/bash

read -p "Enter new username: " username

sudo useradd -m $username
sudo passwd $username

echo "User account created successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/user_management.sh
```

---

# 4. Backup Scheduling and Restoration

```bash
#!/bin/bash

SOURCE_DIR="/home"
BACKUP_DIR="/backup"
DATE=$(date +%F)

mkdir -p $BACKUP_DIR

tar -czf $BACKUP_DIR/home_backup_$DATE.tar.gz $SOURCE_DIR

echo "Backup completed successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/backup.sh
```

---

# 5. Disk Space and Filesystem Monitoring

```bash
#!/bin/bash

echo "Checking disk usage..."

df -h
```

Cron Job:

```bash
0 0 * * 0 /path/to/disk_monitor.sh
```

---

# 6. CPU, RAM, and Server Health Monitoring

```bash
#!/bin/bash

echo "CPU Usage:"
top -bn1 | grep "Cpu(s)"

echo "Memory Usage:"
free -h
```

Cron Job:

```bash
0 0 * * 0 /path/to/server_health.sh
```

---

# 7. Service Monitoring and Automatic Restart

```bash
#!/bin/bash

SERVICE="apache2"

if systemctl is-active --quiet $SERVICE
then
    echo "$SERVICE is running."
else
    echo "$SERVICE is down. Restarting service..."
    sudo systemctl restart $SERVICE
fi
```

Cron Job:

```bash
0 0 * * 0 /path/to/service_monitor.sh
```

---

# 8. File Cleanup and Temporary Data Removal

```bash
#!/bin/bash

TEMP_DIR="/tmp"

rm -rf $TEMP_DIR/*

echo "Temporary files cleaned successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/temp_cleanup.sh
```

---

# 9. Automated Report Generation

```bash
#!/bin/bash

REPORT="system_report.txt"

{
    echo "System Report"
    echo "=============="
    date
    uptime
    free -h
    df -h
} > $REPORT

echo "System report generated: $REPORT"
```

Cron Job:

```bash
0 0 * * 0 /path/to/report_generation.sh
```

---

# 10. Security Patch Deployment

```bash
#!/bin/bash

echo "Installing security updates..."

sudo apt update
sudo unattended-upgrade -d

echo "Security patches installed successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/security_patch.sh
```

---

# 11. SSH Key Management

```bash
#!/bin/bash

ssh-keygen -t rsa -b 4096

echo "SSH key generated successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/ssh_key_management.sh
```

---

# 12. Firewall Rule Updates

```bash
#!/bin/bash

sudo ufw allow 22
sudo ufw enable

echo "Firewall rules updated successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/firewall_update.sh
```

---

# 13. Network Connectivity Checks

```bash
#!/bin/bash

ping -c 4 google.com

if [ $? -eq 0 ]
then
    echo "Network connection is active."
else
    echo "Network issue detected."
fi
```

Cron Job:

```bash
0 0 * * 0 /path/to/network_check.sh
```

---

# 14. SSL Certificate Renewal

```bash
#!/bin/bash

sudo certbot renew

echo "SSL certificates renewed successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/ssl_renewal.sh
```

---

# 15. Scheduled Server Reboot and Maintenance

```bash
#!/bin/bash

echo "Server reboot scheduled now."

sudo reboot
```

Cron Job:

```bash
0 0 * * 0 /path/to/server_reboot.sh
```

---

# 16. Database Backup Automation

```bash
#!/bin/bash

DB_NAME="testdb"
DB_USER="root"
BACKUP_DIR="/backup"
DATE=$(date +%F)

mkdir -p $BACKUP_DIR

mysqldump -u $DB_USER -p $DB_NAME > $BACKUP_DIR/db_backup_$DATE.sql

echo "Database backup completed successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/database_backup.sh
```

---

# 17. File Synchronization Using rsync

```bash
#!/bin/bash

SOURCE="/home"
DESTINATION="/backup/home_backup"

rsync -avz $SOURCE $DESTINATION

echo "Files synchronized successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/file_sync.sh
```

---

# 18. Permission and Ownership Management

```bash
#!/bin/bash

TARGET_DIR="/home/shared"

sudo chown -R user:user $TARGET_DIR
sudo chmod -R 755 $TARGET_DIR

echo "Permissions updated successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/permission_management.sh
```

---

# 19. Cron-Based Scheduled Maintenance Tasks

```bash
#!/bin/bash

echo "Running scheduled maintenance tasks..."

sudo apt autoremove -y
sudo apt autoclean

echo "Maintenance completed successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/maintenance.sh
```

---

# 20. Automated Deployment and Startup Scripts

```bash
#!/bin/bash

echo "Starting application deployment..."

cd /var/www/html/myapp

git pull
sudo systemctl restart apache2

echo "Deployment completed successfully."
```

Cron Job:

```bash
0 0 * * 0 /path/to/deployment.sh
```

---

# Combined Linux Automation Script

```bash
#!/bin/bash

# ==========================================
# Linux Automation Master Script
# ==========================================
# Author: Logeshkanna TV
# Purpose: Automate common Linux administration tasks
# ==========================================

DATE=$(date +%F)
BACKUP_DIR="/backup"
REPORT_FILE="/var/log/system_report_$DATE.txt"
TEMP_DIR="/tmp"
LOG_DIR="/var/log"
SERVICE="apache2"
SOURCE_DIR="/home"
SYNC_DESTINATION="/backup/home_sync"
TARGET_DIR="/home/shared"

mkdir -p $BACKUP_DIR
mkdir -p $SYNC_DESTINATION


echo "=========================================="
echo "Linux Automation Script Started"
echo "Date: $(date)"
echo "=========================================="

# ------------------------------------------
# 1. System Updates and Package Upgrades
# ------------------------------------------

echo "Updating system packages..."
sudo apt update && sudo apt upgrade -y

# ------------------------------------------
# 2. Log Rotation and Cleanup
# ------------------------------------------

echo "Cleaning old log files..."
find $LOG_DIR -type f -name "*.log" -mtime +7 -exec rm -f {} \;

# ------------------------------------------
# 3. Backup Scheduling
# ------------------------------------------

echo "Creating system backup..."
tar -czf $BACKUP_DIR/home_backup_$DATE.tar.gz $SOURCE_DIR

# ------------------------------------------
# 4. Disk Space Monitoring
# ------------------------------------------

echo "Checking disk space..."
df -h

# ------------------------------------------
# 5. CPU and RAM Monitoring
# ------------------------------------------

echo "Checking CPU and Memory Usage..."
free -h
top -bn1 | grep "Cpu(s)"

# ------------------------------------------
# 6. Service Monitoring
# ------------------------------------------

echo "Checking Apache service status..."
if systemctl is-active --quiet $SERVICE
then
    echo "$SERVICE service is running."
else
    echo "$SERVICE service is down. Restarting..."
    sudo systemctl restart $SERVICE
fi

# ------------------------------------------
# 7. Temporary File Cleanup
# ------------------------------------------

echo "Cleaning temporary files..."
rm -rf $TEMP_DIR/*

# ------------------------------------------
# 8. Generate System Report
# ------------------------------------------

echo "Generating system report..."
{
    echo "========== SYSTEM REPORT =========="
    date
    echo ""
    echo "System Uptime"
    uptime
    echo ""
    echo "Memory Usage"
    free -h
    echo ""
    echo "Disk Usage"
    df -h
} > $REPORT_FILE

# ------------------------------------------
# 9. Security Patch Deployment
# ------------------------------------------

echo "Installing security updates..."
sudo unattended-upgrade -d

# ------------------------------------------
# 10. Network Connectivity Check
# ------------------------------------------

echo "Checking internet connectivity..."
ping -c 4 google.com

# ------------------------------------------
# 11. SSL Certificate Renewal
# ------------------------------------------

echo "Renewing SSL certificates..."
sudo certbot renew

# ------------------------------------------
# 12. Database Backup
# ------------------------------------------

echo "Creating database backup..."
mysqldump -u root -p testdb > $BACKUP_DIR/db_backup_$DATE.sql

# ------------------------------------------
# 13. File Synchronization
# ------------------------------------------

echo "Synchronizing files using rsync..."
rsync -avz $SOURCE_DIR $SYNC_DESTINATION

# ------------------------------------------
# 14. Permission Management
# ------------------------------------------

echo "Updating file permissions..."
sudo chown -R user:user $TARGET_DIR
sudo chmod -R 755 $TARGET_DIR

# ------------------------------------------
# 15. Maintenance Cleanup
# ------------------------------------------

echo "Performing maintenance cleanup..."
sudo apt autoremove -y
sudo apt autoclean

# ------------------------------------------
# 16. Deployment Automation
# ------------------------------------------

echo "Deploying application updates..."
cd /var/www/html/myapp || exit

git pull
sudo systemctl restart apache2

# ------------------------------------------
# Completion Message
# ------------------------------------------

echo "=========================================="
echo "Linux Automation Tasks Completed Successfully"
echo "=========================================="
```

# Weekly Cron Job Scheduling

Open crontab editor:

```bash
crontab -e
```

Add this line to execute the script every Sunday at 12:00 AM:

```bash
0 0 * * 0 /path/to/linux_automation_master.sh
```

# How to Enable Cron Jobs

Open crontab editor:

```bash
crontab -e
```

Add the required cron job line:

```bash
0 0 * * 0 /path/to/script.sh
```

Meaning:

* 0 Minute
* 0 Hour
* * Every Day of Month
* * Every Month
* 0 Sunday

This executes the script every Sunday at 12:00 AM.


These files can be easily executed by the linux commands in the terminal


Command:
$  ./<filename>



Example:
$  ./logrotation.sh


ALL OTHER TASKS ARE ALSO IN THE DESCRIPTION [AUTOMATED +40% TASKS IN LINUX] 

!Try it and feel free to comment if any error occurs.


_____ If you are a leyman , use chatgpt for the assist _____
