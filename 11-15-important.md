
# 🐧 Day 11 - Arguments & Positional Parameters

````md id="d11"
# 🐚 Day 11 - Arguments & Positional Parameters

## What are Arguments?

Arguments are values passed to a script during execution.

---

## Example

```bash
#!/bin/bash

echo "First argument: $1"
echo "Second argument: $2"
````

Run:

```bash
./script.sh Hello World
```

---

## Special Variables

* `$#` → Number of arguments
* `$@` → All arguments
* `$?` → Last command status

---

## Interview Questions

1. What are positional parameters?
2. What does `$#` represent?
3. Difference between `$@` and `$*`?



---

# 🐧 Day 12 - Exit Status & Error Handling

```md id="d12"
# 🐚 Day 12 - Exit Status & Error Handling

## What is Exit Status?

Every command returns a status:
- `0` → Success  
- Non-zero → Failure  

---

## Check Exit Status

```bash
echo $?
````

---

## Example

```bash id="3qnyhn"
mkdir test
echo $?
```

---

## Exit Command

```bash id="mb0g2t"
exit 1
```

---

## set -e

```bash id="p4n7xz"
set -e
```

Stops script if any command fails.

---

## Interview Questions

1. What is exit status?
2. What does `set -e` do?
3. How do you handle errors in scripts?



---

# 🐧 Day 13 - Debugging Scripts

```md id="d13"
# 🐚 Day 13 - Debugging Scripts

## Debugging a Script

```bash
bash -x script.sh
````

---

## Enable Debug Mode

```bash id="h2k9lp"
set -x
```

---

## Disable Debug Mode

```bash id="z7p3xr"
set +x
```

---

## Interview Questions

1. How do you debug a shell script?
2. What does `set -x` do?



---

# 🐧 Day 14 - Cron Jobs

```md id="d14"
# 🐚 Day 14 - Cron Jobs

## What is Cron?

Cron is used to schedule tasks automatically.

---

## Edit Cron Jobs

```bash
crontab -e
````

---

## Example

```bash id="k3l9op"
0 2 * * * /home/user/backup.sh
```

Runs daily at 2 AM.

---

## View Cron Jobs

```bash id="n8v2zm"
crontab -l
```

---

## Interview Questions

1. What is cron?
2. How do you schedule a job?
3. Explain cron timing format?



---

# 🐧 Day 15 - Logging in Scripts

```md id="d15"
# 🐚 Day 15 - Logging in Scripts

## Output Redirection

```bash
echo "Hello" > file.txt
echo "World" >> file.txt
````

---

## Error Logging

```bash id="x8k3qp"
command 2> error.log
```

---

## Standard Output + Error

```bash id="c7n4yr"
command > output.log 2>&1
```

---

## Example

```bash id="v9m2ld"
#!/bin/bash

echo "Script started" >> log.txt
date >> log.txt
```

---

## Interview Questions

1. What is logging in shell scripting?
2. Difference between `>` and `>>`?
3. What is `2>&1`?


