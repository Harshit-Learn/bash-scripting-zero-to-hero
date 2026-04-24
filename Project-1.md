
# 🚀 Project 1 - Service Monitor & Auto Restart Script

## 📌 Overview
This script monitors a service (e.g., nginx) and automatically restarts it if it is found to be down.

---

## 🐧 Script

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
````

---

## ⚙️ How to Use

1. Create script file:

```bash id="s3_1"
nano service-monitor.sh
```

2. Paste the script and save.

3. Make it executable:

```bash id="s3_2"
chmod +x service-monitor.sh
```

4. Run manually:

```bash id="s3_3"
./service-monitor.sh
```

---

## ⏰ Automation with Cron

Open crontab:

```bash id="s3_4"
crontab -e
```

Add this line:

```bash id="s3_5"
*/5 * * * * /home/ubuntu/service-monitor.sh
```

👉 This will check service every **5 minutes**

---

## 💡 Explanation

* `systemctl is-active` → checks service status
* If not active → restart service
* `systemctl start` → starts the service
* Cron → automates monitoring

---

## 🧠 Real Use Case

👉 Production me service crash ho sakti hai
👉 Manual monitoring possible nahi hota
👉 Ye script auto-recovery provide karta hai

---

## 🎯 Interview Questions

1. How do you check service status in Linux?
2. What is `systemctl` used for?
3. How do you restart a service automatically?
4. What will you do if a service goes down?

---

## 🚀 Future Improvements

* Send alert (Email/Slack) 📧
* Monitor multiple services
* Add logging system

