# ⏰ cron — Schedule Tasks Automatically on Linux

**cron** is a built-in Linux utility used to schedule commands or scripts to run periodically at fixed times, dates, or intervals. It's perfect for automating system maintenance, backups, updates, and more.

---

## ✅ Features

- Schedule scripts and commands to run automatically
- Supports per-user cron jobs
- Flexible time-based scheduling
- Lightweight and reliable
- Works in the background as `cron` or `crond` service

---

## 🔧 Installation

### Debian/Ubuntu
```bash
sudo apt install cron
sudo systemctl enable cron
sudo systemctl start cron
```

### Arch Linux
```bash
sudo pacman -S cronie
sudo systemctl enable cronie
sudo systemctl start cronie
```

---

## 🚀 Basic Usage

### Open the crontab editor
```bash
crontab -e
```

### View current user's cron jobs
```bash
crontab -l
```

### Remove current user's cron jobs
```bash
crontab -r
```

---

## 📅 Cron Time Format

A cron job follows this format:

```
*  *  *  *  *  command-to-execute
│  │  │  │  │
│  │  │  │  └─ day of week (0-7) (Sunday is 0 or 7)
│  │  │  └──── month (1-12)
│  │  └─────── day of month (1-31)
│  └────────── hour (0-23)
└───────────── minute (0-59)
```

---

## 🔁 Examples

| Schedule              | Cron Format           | Description                          |
|-----------------------|------------------------|--------------------------------------|
| Every minute          | `* * * * *`            | Run every minute                     |
| Every 5 minutes       | `*/5 * * * *`          | Run every 5 minutes                  |
| Every day at 2am      | `0 2 * * *`            | Run daily at 2:00 AM                 |
| Every Monday at 8am   | `0 8 * * 1`            | Run every Monday at 8:00 AM          |
| First of month at 12h | `0 12 1 * *`           | Run at noon on the first of the month |

---

## 📂 Cron Job File Locations

- `crontab -e` → Edits user-specific cron jobs
- `/etc/crontab` → System-wide cron jobs
- `/etc/cron.*` → Hourly, daily, weekly, monthly job folders:
  - `/etc/cron.hourly/`
  - `/etc/cron.daily/`
  - `/etc/cron.weekly/`
  - `/etc/cron.monthly/`

---

## 🧩 Tips

- Redirect output to log file:
  ```bash
  * * * * * /path/script.sh >> /var/log/myscript.log 2>&1
  ```
- Use absolute paths in your scripts or cron jobs.
- Use `crontab -u <user> -e` to edit another user’s cron jobs (as root).
- Restart cron if you edit `/etc/crontab` directly.

---

## 📚 More Info

- Run `man 5 crontab` or `man cron` in terminal
- [https://man7.org/linux/man-pages/man5/crontab.5.html](https://man7.org/linux/man-pages/man5/crontab.5.html)
