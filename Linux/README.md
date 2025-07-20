
---

## 🐧 Linux Interview Notes

### 1. **What is Linux?**

* Open-source Unix-like OS kernel created by Linus Torvalds.
* Foundation of most server infrastructure (cloud, containers, embedded).
* Distributions (distros) = Linux kernel + GNU tools + package manager + desktop (optional).

---

### 2. **Linux History**

* Based on UNIX concepts (developed in 1970s at Bell Labs).
* Linux kernel released in 1991.
* Common distros: Ubuntu, Debian, CentOS, Fedora, Arch, Alpine.

---

### 3. **Linux File System Hierarchy**

| Directory | Purpose                    |
| --------- | -------------------------- |
| `/`       | Root directory             |
| `/bin`    | Essential binaries         |
| `/sbin`   | System binaries            |
| `/etc`    | Configuration files        |
| `/var`    | Logs, variable data        |
| `/opt`    | Optional software          |
| `/usr`    | User-level apps, libraries |
| `/home`   | User directories           |
| `/tmp`    | Temporary files            |
| `/dev`    | Device files               |
| `/proc`   | Kernel info (virtual FS)   |
| `/mnt`    | Mount points               |

---

### 4. **Important Concepts**

* **Init Systems**:

  * `init`, `upstart`, `systemd` (most common now)
  * Manage service startup and logs

* **Processes**:

  * `ps`, `top`, `htop`, `kill`, `nice`

* **Permissions**:

  * `rwx` (read, write, execute)
  * `chmod`, `chown`, `umask`

---

### 5. **Bash Shell & Scripting**

* Common commands:

  ```bash
  ls, cd, pwd, cp, mv, rm, cat, less, head, tail
  grep, awk, sed, sort, uniq, cut
  tar, gzip, zip, unzip
  ```

* Scripting basics:

  ```bash
  #!/bin/bash
  for file in *.txt; do
    echo "$file"
  done
  ```

* Conditional statements:

  ```bash
  if [ -f "myfile.txt" ]; then
    echo "File exists"
  fi
  ```

* Schedule tasks:

  ```bash
  crontab -e
  * * * * * /home/user/script.sh
  ```

---

### 6. **Linux Kernel**

* Heart of the OS: manages hardware, memory, processes.
* Monolithic design (vs microkernel).
* Can be configured, patched, or compiled.
* Interact via `/proc`, `uname`, `sysctl`.

---

### 7. **Distros vs GNU/Linux**

* **Distro** = Linux kernel + GNU tools + package manager
* Examples:

  * Ubuntu (Debian-based, user-friendly)
  * CentOS/RHEL (enterprise)
  * Alpine (minimal, good for Docker)
  * Arch (customizable, rolling release)

---

### 8. **Nginx: Concept & Setup**

* Web server and reverse proxy.
* Can serve static files, proxy requests, load balance.

**Basic config:**

```nginx
server {
  listen 80;
  server_name example.com;
  location / {
    proxy_pass http://localhost:5000;
  }
}
```

```bash
# Install & manage
sudo apt install nginx
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

### 9. **DNS Basics**

* Resolves domain names to IP addresses.

* Key record types:

  * `A`: maps domain to IPv4
  * `AAAA`: maps domain to IPv6
  * `CNAME`: alias to another domain
  * `MX`: mail server
  * `PTR`: reverse DNS

* Check DNS:

  ```bash
  nslookup google.com
  dig example.com
  ```

---

### 10. **Useful Commands**

```bash
df -h           # Disk usage
du -sh *        # Folder sizes
top / htop      # Live processes
free -h         # RAM usage
uptime          # System load
whoami, id      # User info
lsof -i         # List open ports
netstat -tulnp  # Listening ports
```

---

### 11. **Interview Questions**

* Explain Linux file permissions.
* How does systemd work?
* Difference between hard link and soft link?
* What is the purpose of `/proc` and `/dev`?
* How do you debug a Linux server issue?
* What’s the difference between a process and a thread?
* How to schedule cron jobs?

---
