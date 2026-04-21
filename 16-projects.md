

# 🚀 1. Disk Alert Script (80% Alert)

```bash
#!/bin/bash

THRESHOLD=80

df -h | grep -vE '^Filesystem|tmpfs|cdrom' | while read line
do
  usage=$(echo $line | awk '{print $5}' | sed 's/%//g')
  partition=$(echo $line | awk '{print $1}')

  if [ $usage -ge $THRESHOLD ]; then
    echo "⚠️ Disk usage on $partition is ${usage}% (Above ${THRESHOLD}%)"
  fi
done
```

---

## 💡 Explanation:

* `df -h` → disk usage nikalta hai
* `awk '{print $5}'` → usage column (like 85%)
* `sed 's/%//g'` → % remove
* `if usage >= 80` → alert trigger

---

## 🧠 Real Use:

👉 Production server me disk full hone se service down ho sakti hai
👉 Ye script **early alert deta hai**

---

# 🚀 2. Auto Backup Script (with Cron)

```bash
#!/bin/bash

SOURCE="/home/ubuntu/data"
DEST="/backup"
DATE=$(date +%F)

mkdir -p $DEST

tar -czf $DEST/backup-$DATE.tar.gz $SOURCE

echo "Backup completed on $DATE"
```

---

## 💡 Explanation:

* `date +%F` → current date (YYYY-MM-DD)
* `tar -czf` → compress backup
* `mkdir -p` → folder create if not exist

---

## ⏰ Cron Setup

```bash
crontab -e
```

```bash
0 2 * * * /home/ubuntu/backup.sh
```

👉 Daily 2 AM backup run hoga

---

## 🧠 Real Use:

👉 Data loss avoid
👉 Daily automated backup (production must)

---

# 🚀 3. Service Monitor Script (Auto Restart)

```bash
#!/bin/bash

SERVICE="nginx"

status=$(systemctl is-active $SERVICE)

if [ "$status" != "active" ]; then
  echo "⚠️ $SERVICE is down. Restarting..."
  systemctl start $SERVICE
  echo "✅ $SERVICE restarted"
else
  echo "✅ $SERVICE is running"
fi
```

---

## 💡 Explanation:

* `systemctl is-active` → service status check
* If not active → restart
* Auto recovery system

---

## 🧠 Real Use:

👉 Agar service crash ho jaye → auto fix
👉 No manual intervention

---

# 🚀 4. Log Cleaner Script (Advanced)

```bash
#!/bin/bash

LOG_DIR="/var/log"
DAYS=7

echo "Cleaning logs older than $DAYS days..."

find $LOG_DIR -type f -name "*.log" -mtime +$DAYS -exec rm -f {} \;

echo "Log cleanup completed!"
```

---

## 💡 Explanation:

* `find` → files search
* `-mtime +7` → 7 din purane logs
* `-exec rm` → delete

---

## ⚡ Advanced Version (Safer)

```bash
#!/bin/bash

LOG_DIR="/var/log"
DAYS=7
BACKUP_DIR="/backup/logs"

mkdir -p $BACKUP_DIR

find $LOG_DIR -type f -name "*.log" -mtime +$DAYS | while read file
do
  cp $file $BACKUP_DIR
  > $file
done

echo "Logs backed up & cleaned!"
```

---

## 💡 Advanced Logic:

* Delete nahi → backup + clear
* `> file` → file empty karta hai (safe method)

---

# 🔥 Interview Ready Answers

👉 **Q: Disk full ho jaye to kya karoge?**
✔️ Check: `df -h` → cleanup logs → extend disk

👉 **Q: Backup kaise loge?**
✔️ `tar + cron` automation

👉 **Q: Service down ho jaye to?**
✔️ `systemctl status` → restart → automate script

👉 **Q: Logs kaise manage karte ho?**
✔️ Rotate / cleanup / backup

---


