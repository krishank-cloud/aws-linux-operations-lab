# Commands Used

This file documents the Linux and AWS-related commands used during the AWS Linux Operations Lab project.

---

## 1. Check current user and system information

```bash
whoami
pwd
cat /etc/os-release
uname -a
```

### What these commands do

```text
whoami              Shows the current Linux user
pwd                 Shows the current working directory
cat /etc/os-release Shows the Linux distribution and version
uname -a            Shows kernel, system, and architecture information
```

---

## 2. Update Amazon Linux packages

```bash
sudo dnf update -y
```

### What this command does

```text
sudo   Runs the command with administrator permissions
dnf    Package manager used by Amazon Linux 2023
update Updates installed packages
-y     Automatically answers yes to confirmation prompts
```

---

## 3. Install Nginx web server

```bash
sudo dnf install nginx -y
```

### What this command does

```text
Installs the Nginx web server package on Amazon Linux 2023.
```

---

## 4. Start and enable Nginx

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

### What these commands do

```text
systemctl start nginx   Starts the Nginx service immediately
systemctl enable nginx  Enables Nginx to start automatically after reboot
```

---

## 5. Check Nginx service status

```bash
sudo systemctl status nginx
sudo systemctl status nginx --no-pager
```

### What these commands do

```text
Shows whether the Nginx service is running, stopped, failed, or disabled.

The --no-pager option displays the output directly in the terminal without opening the less viewer.
```

Expected result:

```text
Active: active (running)
```

---

## 6. Test the web server locally

```bash
curl -I http://localhost
```

### What this command does

```text
curl -I checks the HTTP response headers from the local web server.
```

Expected result:

```text
HTTP/1.1 200 OK
```

---

## 7. View the Nginx website directory

```bash
ls -l /usr/share/nginx/html/
```

### What this command does

```text
Lists the files inside the Nginx default website folder.
```

---

## 8. Backup the default Nginx homepage

```bash
sudo cp /usr/share/nginx/html/index.html /usr/share/nginx/html/index.html.backup
```

### What this command does

```text
Creates a backup copy of the original Nginx homepage before editing it.
```

---

## 9. Edit the Nginx homepage

```bash
sudo nano /usr/share/nginx/html/index.html
```

### What this command does

```text
Opens the Nginx homepage file using the nano text editor with administrator permissions.
```

Nano save commands:

```text
CTRL + O  Save file
Enter     Confirm file name
CTRL + X  Exit nano
```

---

## 10. Restart Nginx after editing the website

```bash
sudo systemctl restart nginx
```

### What this command does

```text
Restarts Nginx so the updated website file is served.
```

---

## 11. Check Nginx again after changes

```bash
sudo systemctl status nginx --no-pager
curl -I http://localhost
```

Expected results:

```text
Active: active (running)
HTTP/1.1 200 OK
```

---

## 12. View Nginx access logs

```bash
sudo tail -20 /var/log/nginx/access.log
```

### What this command does

```text
Shows the last 20 lines of the Nginx access log.
This log records web requests made to the server.
```

---

## 13. View Nginx error logs

```bash
sudo tail -20 /var/log/nginx/error.log
```

### What this command does

```text
Shows the last 20 lines of the Nginx error log.
This log helps troubleshoot web server errors.
```

---

## 14. View Nginx systemd logs

```bash
sudo journalctl -u nginx --no-pager | tail -30
```

### What this command does

```text
journalctl       Views logs managed by systemd
-u nginx         Filters logs for the Nginx service only
--no-pager       Prints output directly in the terminal
tail -30         Shows only the last 30 lines
```

---

## 15. Useful command learned during the project

```bash
q
```

### What this does

```text
Exits the pager view when systemctl status opens in the less viewer.
```

---

## Project learning summary

During this stage of the project, I learned how to:

```text
Connect to an EC2 Linux instance using AWS Systems Manager Session Manager
Check Linux system information
Update Amazon Linux 2023 packages
Install Nginx
Start, enable, restart, and check a Linux service using systemctl
Test a local web server using curl
Edit website files using nano
Backup files before making changes
View Nginx access logs, error logs, and systemd service logs
```
