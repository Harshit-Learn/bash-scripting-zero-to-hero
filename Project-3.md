
# 🚀 Project 2 - Auto Backup Script with Cron

## 📌 Overview
This script automatically takes backup of a directory and stores it in compressed format with date. It can be scheduled using cron for daily backups.

---

## 🐧 Script

```bash
#!/bin/bash

SOURCE="/home/ubuntu/data"
DEST="/backup"
DATE=$(date +%F)

mkdir -p $DEST

tar -czf $DEST/backup-$DATE.tar.gz $SOURCE

echo "Backup completed on $DATE"
````

---

## ⚙️ How to Use

1. Create script file:

```bash id="b2s1"
nano backup.sh
```

2. Paste the script and save.

3. Make it executable:

```bash id="b2s2"
chmod +x backup.sh
```

4. Run manually:

```bash id="b2s3"
./backup.sh
```

---

## ⏰ Cron Setup (Automation)

Open crontab:

```bash id="b2s4"
crontab -e
```

Add this line:

```bash id="b2s5"
0 2 * * * /home/ubuntu/backup.sh
```

👉 This will run backup daily at **2 AM**

---

## 💡 Explanation

* `date +%F` → current date (YYYY-MM-DD)
* `mkdir -p` → creates backup directory if not exists
* `tar -czf` → compress and archive files
* Cron → automates execution

---

## 🧠 Real Use Case

👉 Production servers me daily backup lena mandatory hota hai
👉 Data loss se bachne ke liye automated backup use hota hai
👉 Cron ke through fully automated system

---

## 🎯 Interview Questions

1. How do you take backup in Linux?
2. What is `tar` command used for?
3. What is cron and how does it work?
4. How do you automate backups?

---

## 🚀 Future Improvements

* Store backup on remote server (SCP/S3) ☁️
* Add backup retention policy
* Add logging system

