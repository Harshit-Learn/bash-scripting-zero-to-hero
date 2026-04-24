
#  Project 1 - Disk Alert Script (80% Alert)

## 📌 Overview
This script monitors disk usage and alerts when any partition exceeds the defined threshold (80%).

---

## 🐧 Script

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
````

---

## ⚙️ How to Use

1. Create script file:

```bash
nano disk-alert.sh
```

2. Paste the script and save.

3. Make it executable:

```bash
chmod +x disk-alert.sh
```

4. Run the script:

```bash
./disk-alert.sh
```

---

## 💡 Explanation

* `df -h` → disk usage nikalta hai
* `awk '{print $5}'` → usage column (like 85%)
* `sed 's/%//g'` → % remove
* `if usage >= 80` → alert trigger

---

## 🧠 Real Use Case

👉 Production server me disk full hone se service down ho sakti hai
👉 Ye script early alert deta hai

---

## 🎯 Interview Questions

1. How do you check disk usage in Linux?
2. What command is used to monitor disk space?
3. How do you automate disk monitoring?
4. What will you do if disk usage crosses 80%?

---

## 🚀 Future Improvements

* Send email alert 📧
* Integrate with monitoring tools
* Add logging system



