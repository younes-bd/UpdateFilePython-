<p align="center">
<h1> Update a file through a Python algorithm </h1> 

<h2>Description:</h2>
At my organization, access to restricted content is controlled with an allow list of IP addresses. The "allow_list.txt" file identifies these IP addresses. A separate remove list identifies IP addresses that should no longer have access to this content. I created an algorithm to automate updating the "allow_list.txt" file and remove these IP addresses that should no longer have access. 
<br />

<h2> Open the file that contains the allow list:</h2>
For the first part of the algorithm, I opened the "allow_list.txt" file. First, I assigned this file name as a string to the import_file variable:
<br/><br/>
 <img src="https://i.imgur.com/HfNgfc9.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
Then, I used a with statement to open the file:
<br/><br/>
 <img src="https://i.imgur.com/87MWrnT.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
In my algorithm, the with statement is used with the .open() function in read mode to open the allow list file for the purpose of reading it. The purpose of opening the file is to allow me to access the IP addresses stored in the allow list file. The with keyword will help manage the resources by closing the file after exiting the with statement. In the code with open(import_file, "r") as file:, the open() function has two parameters. The first identifies the file to import, and then the second indicates what I want to do with the file. In this case, "r" indicates that I want to read it. The code also uses the as keyword to assign a variable named file; file stores the output of the .open() function while I work within the with statement.
 
<h2> Read the file contents: </h2>
 In order to read the file contents, I used the .read() method to convert it into the string.
<br/>
<br/>
<img src="https://i.imgur.com/PWtsHT0.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
When using an .open() function that includes the argument "r" for “read,” I can call the .read() function in the body of the with statement. The .read() method converts the file into a string and allows me to read it. I applied the .read() method to the file variable identified in the with statement. Then, I assigned the string output of this method to the variable ip_addresses. <br/>
In summary, this code reads the contents of the "allow_list.txt" file into a string format that allows me to later use the string to organize and extract data in my Python program.

 <h2> Convert the string into a list: </h2>
In order to remove individual IP addresses from the allow list, I needed it to be in list format. Therefore, I next used the .split() method to convert the ip_addresses string into a list:
<br/>
<br/>
<img src="https://i.imgur.com/NKlvscK.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
The .split() function is called by appending it to a string variable. It works by converting the contents of a string to a list. The purpose of splitting ip_addresses into a list is to make it easier to remove IP addresses from the allow list. By default, the .split() function splits the text by whitespace into list elements. In this algorithm, the .split() function takes the data stored in the variable ip_addresses, which is a string of IP addresses that are each separated by a whitespace, and it converts this string into a list of IP addresses. To store this list, I reassigned it back to the variable ip_addresses. 

<h2> Iterate through the remove list: </h2>
 A key part of my algorithm involves iterating through the IP addresses that are elements in the remove_list. To do this, I incorporated a for loop:
<br/><br/>
<img src="https://i.imgur.com/Fm96YLP.png" height="20%" width="40%" alt="Disk Sanitization Steps"/> 
The for loop in Python repeats code for a specified sequence. The overall purpose of the for loop in a Python algorithm like this is to apply specific code statements to all elements in a sequence. The for keyword starts the for loop. It is followed by the loop variable element and the keyword in. The keyword in indicates to iterate through the sequence ip_addresses and assign each value to the loop variable element. 
 
<h2> Remove IP addresses that are on the remove list: </h2>
My algorithm requires removing any IP address from the allow list, ip_addresses, that is also contained in remove_list.  Because there were not any duplicates in ip_addresses, I was able to use the following code to do this:
<br/><br/>
 <img src="https://i.imgur.com/dcXfoLY.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
First, within my for loop, I created a conditional that evaluated whether or not the loop variable element was found in the ip_addresses list. I did this because applying .remove() to elements that were not found in ip_addresses would result in an error.  <br/>
Then, within that conditional, I applied .remove() to ip_addresses. I passed in the loop variable element as the argument so that each IP address that was in the remove_list would be removed from ip_addresses.

<h2> Update the file with the revised list of IP addresses:  </h2>
As a final step in my algorithm, I needed to update the allow list file with the revised list of IP addresses. To do so, I first needed to convert the list back into a string. I used the .join() method for this: <br/>
<br/>
 <img src="https://i.imgur.com/sYKdskQ.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
The .join() method combines all items in an iterable into a string. The .join() method is applied to a string containing characters that will separate the elements in the iterable once joined into a string. In this algorithm, I used the .join() method to create a string from the list ip_addresses so that I could pass it in as an argument to the .write() method when writing to the file "allow_list.txt". I used the string ("\n") as the separator to instruct Python to place each element on a new line.  <br/>
Then, I used another with statement and the .write() method to update the file:
<br/><br/>
<img src="https://i.imgur.com/sISvJ07.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
This time, I used a second argument of "w" with the open() function in my with statement. This argument indicates that I want to open a file to write over its contents. When using this argument "w", I can call the .write() function in the body of the with statement. The .write() function writes string data to a specified file and replaces any existing file content. 
In this case I wanted to write the updated allow list as a string to the file "allow_list.txt". This way, the restricted content will no longer be accessible to any IP addresses that were removed from the allow list. To rewrite the file, I appended the .write() function to the file object file that I identified in the with statement. I passed in the ip_addresses variable as the argument to specify that the contents of the file specified in the with statement should be replaced with the data in this variable.

<h2> Summary: </h2>
 I created an algorithm that removes IP addresses identified in a remove_list variable from the "allow_list.txt" file of approved IP addresses. This algorithm involved opening the file, converting it to a string to be read, and then converting this string to a list stored in the variable ip_addresses. I then iterated through the IP addresses in remove_list. With each iteration, I evaluated if the element was part of the ip_addresses list. If it was, I applied the .remove() method to it to remove the element from ip_addresses.. After this, I used the .join() method to convert the ip_addresses back into a string so that I could write over the contents of the "allow_list.txt" file with the revised list of IP addresses.
<br/>
<br/>

Certainly, here are more examples of automation Python scripts for system administrators:

<h1> 1. Automate Log Cleanup </h1>

<h2> Description: </h2>
Automate log file cleanup by removing log files older than a specified number of days.

```
import os
import datetime

# Log cleanup script

log_dir = "/var/log"
max_age_days = 7

now = datetime.datetime.now()

for filename in os.listdir(log_dir):
    file_path = os.path.join(log_dir, filename)
    if os.path.isfile(file_path):
        creation_time = datetime.datetime.fromtimestamp(os.path.getctime(file_path))
        if (now - creation_time).days > max_age_days:
            os.remove(file_path)
```
<h2> Summary: </h2>
This Python script automatically removes log files older than a specified number of days from the log directory.

<h1> 2. Monitor Disk Space </h1>

<h2> Description: </h2>
Automate disk space monitoring and alerting when free disk space falls below a threshold.

```
import psutil

# Disk space monitoring script

threshold = 10  # Set the disk space threshold in gigabytes

partition = '/'
disk = psutil.disk_usage(partition)
free_space_gb = disk.free / (2**30)

if free_space_gb < threshold:
    print(f"Warning: Low disk space on {partition}. Free space is {free_space_gb:.2f} GB.")
```
<h2> Summary: </h2>
This Python script automatically monitors disk space and alerts when free space falls below a specified threshold.

<h1> 3. Backup Script </h1>

<h2> Description:</h2> 
 Automate system backups with date-based directories.

```
import shutil
import datetime

# Backup script

backup_source = "/var/www"
backup_destination = "/backups"
current_date = datetime.datetime.now().strftime("%Y%m%d")

backup_directory = os.path.join(backup_destination, current_date)

shutil.make_archive(backup_directory, 'zip', backup_source)
```
<h2> Summary: </h2> 
This Python script automates backups of a specified source directory, creating backups with date-based directories.

<h1> 4. Automate Firewall Rule Updates </h1>

<h2> Description: </h2>
Automate the addition of firewall rules to enhance network security.

```
import subprocess

# Firewall rule automation script

new_rule = "iptables -A INPUT -p tcp --dport 80 -j ACCEPT"
subprocess.run(new_rule, shell=True)
```
<h2> Summary: </h2>
This Python script automates the addition of a new firewall rule to allow incoming traffic on port 80.


<h1> 5. Automate Server Reboot </h1>

<h2> Description: </h2>
 Automate server reboots on a schedule.

```
import subprocess
import time

# Server reboot script

reboot_time = "03:00"  # Set the desired reboot time

while True:
    current_time = time.strftime("%H:%M")
    if current_time == reboot_time:
        subprocess.run(["reboot"])
    time.sleep(60)
```
<h2> Summary: </h2>
This Python script continuously checks the current time and reboots the server at a specified time.

These Python scripts provide system administrators with tools to automate various tasks, including log cleanup, disk space monitoring, backups, firewall rule updates, and scheduled server reboots, enhancing system management and efficiency.

Certainly, here are more examples of Python scripts for automating routine tasks as a system administrator:

<h1> 6. Automate User Account Management </h1>

<h2> Description: </h2>
Automate user account creation and deletion on a Linux system.

```
import subprocess

# User account automation script

new_user = "john"
user_password = "secretpassword"

# Create a new user
subprocess.run(["useradd", new_user])

# Set the user's password
subprocess.run(["echo", f"{new_user}:{user_password}" "|", "chpasswd"])

# Delete a user
# subprocess.run(["userdel", new_user])
```
<h2> Summary: </h2>
This Python script automates user account management tasks, including user creation and password setting.

<h1> 7. Automate Software Updates </h1>

<h2> Description: </h2>
Automate the process of checking for and applying software updates.

```
import subprocess

# Software update automation script

# Check for updates
subprocess.run(["apt", "update"])

# Upgrade installed packages
subprocess.run(["apt", "upgrade", "-y"])
```
<h2> Summary: </h2>
This Python script automates the process of checking for and applying software updates on a Debian-based Linux system.

<h1> 8. Automate Log File Analysis </h1>

<h2> Description: </h2>
Automate log file analysis to identify and report specific patterns or issues.

```
import re

# Log file analysis script

log_file = "/var/log/syslog"
pattern = "error"

with open(log_file, "r") as file:
    for line in file:
        if re.search(pattern, line, re.I):
            print(line.strip())
```
<h2> Summary: </h2>
This Python script automates log file analysis to identify and report log entries containing specific patterns like "error."

<h1> 9. Monitor Service Status </h1>

<h2> Description: </h2>
Automate service status monitoring and restart services if they are down.

``` 
import subprocess

# Service monitoring and automation script

service_name = "apache2"

# Check service status
status = subprocess.run(["systemctl", "is-active", service_name])

# Restart the service if it's inactive
if status.returncode != 0:
    subprocess.run(["systemctl", "restart", service_name])
```
<h2> Summary: </h2>
This Python script automates the monitoring and restart of a specific service if it's inactive.

<h1> 10. Automate System Health Checks </h1>

<h2> Description: </h2>
Automate system health checks, such as checking CPU and memory usage.

```
import psutil

# System health check automation script

# Check CPU usage
cpu_percent = psutil.cpu_percent(interval=1)
print(f"CPU Usage: {cpu_percent}%")

# Check available memory
memory = psutil.virtual_memory()
print(f"Available Memory: {memory.available / (1024 ** 3):.2f} GB")
```
<h2> Summary: </h2>
This Python script automates system health checks, providing information about CPU and memory usage.

These Python scripts assist system administrators in automating common tasks, such as user account management, software updates, log analysis, service monitoring, and system health checks, thereby improving efficiency and system management.
Certainly, here are more examples of Python scripts for automating routine tasks as a system administrator:


<h1> 11. Automated Backup Script </h1>

<h2> Description: </h2>
Automate the process of backing up critical system files to a specified location.

```
import shutil
import os
import time

# Backup script

backup_source = "/etc/"
backup_destination = "/backup/"

# Create a timestamp for the backup folder
timestamp = time.strftime("%Y-%m-%d-%H-%M-%S")
backup_folder = os.path.join(backup_destination, f"backup_{timestamp}")

# Copy the files to the backup folder
shutil.copytree(backup_source, backup_folder)
```
<h2> Summary: </h2>
This script automates the process of creating a timestamped backup of system files, making it easy to recover configuration files if needed.

<h1> 12. Log Rotation Script </h1>

<h2> Description: </h2>
Automate log file rotation and compression to manage log file sizes.

```
import subprocess

# Log rotation and compression script

log_file = "/var/log/myapp.log"
compressed_log_file = f"{log_file}.gz"

# Rotate and compress log files
subprocess.run(["logrotate", "-f", "/etc/logrotate.conf"])
subprocess.run(["gzip", log_file])
```
<h2> Summary: </h2>
This script automates log rotation and compression to keep log files from consuming excessive disk space.

<h1> 13. Automated Filesystem Checks </h1>

<h2> Description: </h2>
Automate filesystem checks to ensure the integrity of filesystems and repair issues if necessary.

```
import subprocess

# Automated filesystem check script

filesystem = "/dev/sda1"

# Check and repair the filesystem
subprocess.run(["fsck", "-p", filesystem])
```
<h2> Summary: </h2>
This script automates the filesystem check process to maintain the integrity of filesystems.

<h1> 14. Automated Email Notifications </h1>

<h2> Description: </h2>
Automate email notifications for system events or alerts.

```
import smtplib
from email.mime.text import MIMEText

# Automated email notification script

def send_email(subject, message, to_email):
    from_email = "your_email@example.com"
    password = "your_password"

    msg = MIMEText(message)
    msg["Subject"] = subject
    msg["From"] = from_email
    msg["To"] = to_email

    server = smtplib.SMTP("smtp.example.com", 587)
    server.starttls()
    server.login(from_email, password)
    server.sendmail(from_email, to_email, msg.as_string())
    server.quit()

# Usage
send_email("System Alert", "High CPU usage detected.", "admin@example.com")
```
<h2> Summary: </h2>
This script automates the process of sending email notifications for system events or alerts.

<h1> 15. System Cleanup Script </h1>

<h2> Description: </h2>
Automate system cleanup tasks, such as removing temporary files and logs.

```
import subprocess

# System cleanup script

# Remove temporary files
subprocess.run(["rm", "-rf", "/tmp/*"])

# Clear log files
subprocess.run(["rm", "/var/log/*.log"])
```
<h2> Summary: </h2>
This script automates routine system cleanup tasks to free up disk space and maintain system performance.

These Python scripts are valuable tools for system administrators, helping to streamline various tasks, including backups, log management, filesystem checks, email notifications, and system cleanup.
Certainly, here are more examples of Python scripts for automating tasks as a system administrator:

<h1> 16. User Account Management Script </h1>

<h2> Description: </h2>
Automate the creation and management of user accounts on a Linux system.

```
import subprocess

# User account management script

def create_user(username, password):
    subprocess.run(["useradd", username])
    subprocess.run(["passwd", f"--stdin {username}"], input=password, shell=True)

# Usage
create_user("newuser", "securepassword")
```
<h2> Summary: </h2>
This script simplifies the process of creating user accounts on a Linux system.

<h1> 17. Firewall Rule Management Script </h1>

<h2> Description: </h2>
Automate the management of firewall rules to control network traffic.

```
import subprocess

# Firewall rule management script

def allow_port(port):
    subprocess.run(["firewall-cmd", f"--zone=public --add-port={port}/tcp --permanent"])
    subprocess.run(["firewall-cmd", "--reload"])

# Usage
allow_port("80")
```
<h2> Summary: </h2>
This script automates the process of adding and removing firewall rules, enhancing network security.

<h1> 18. Log File Monitoring Script </h1>

<h2> Description: </h2>
Automate log file monitoring for specific events or errors.

```
import subprocess

# Log file monitoring script

log_file = "/var/log/myapp.log"

def monitor_log_file():
    subprocess.run(["tail", "-f", log_file])

# Usage
monitor_log_file()
```
<h2> Summary: </h2>
This script simplifies log file monitoring for system administrators, making it easy to track important events.

<h1> 19. System Health Check Script </h1>

<h2> Description: </h2>
Automate system health checks, including checking CPU, memory, and disk usage.

```
import psutil

# System health check script

def check_system_health():
    cpu_usage = psutil.cpu_percent()
    memory_usage = psutil.virtual_memory().percent
    disk_usage = psutil.disk_usage('/').percent

    return f"CPU Usage: {cpu_usage}%, Memory Usage: {memory_usage}%, Disk Usage: {disk_usage}%"

# Usage
health_status = check_system_health()
print(health_status)
```
<h2> Summary: </h2>
This script automates system health checks, providing real-time information on CPU, memory, and disk usage.

<h1> 20. Automated Patch Management Script </h1>

<h2> Description: </h2>
Automate the process of checking for and applying system updates.

```
import subprocess

# Automated patch management script

def apply_system_updates():
    subprocess.run(["yum", "update", "-y"])

# Usage
apply_system_updates()
```
<h2> Summary: </h2>
This script automates the application of system updates, enhancing system security and stability.

These Python scripts are useful for system administrators to automate various tasks, such as user account management, firewall rule management, log file monitoring, system health checks, and automated patch management.
Certainly, here are more examples of Python scripts for automating tasks as a system administrator:


<h1> 21. Backup Script </h1>

<h2> Description: </h2>
Automate regular backups of important files and directories.

```
import shutil
import time

# Backup script

def create_backup(source, destination):
    timestamp = time.strftime("%Y%m%d%H%M%S")
    backup_dir = f"{destination}/backup_{timestamp}"
    shutil.copytree(source, backup_dir)

# Usage
source_directory = "/path/to/source"
backup_location = "/path/to/backup"
create_backup(source_directory, backup_location)
```
<h2> Summary: </h2>
This script automates the backup of specified files or directories, creating a timestamped backup copy.

<h2> 22. Log Rotation Script </h2>

<h2> Description: </h2>
Automate log file rotation to prevent log files from consuming excessive disk space.

```
import logging.handlers

# Log rotation script

log_file = "/var/log/myapp.log"

def rotate_log_file():
    max_log_size = 1024 * 1024  # 1 MB
    backup_count = 3
    handler = logging.handlers.RotatingFileHandler(log_file, maxBytes=max_log_size, backupCount=backup_count)
    log = logging.getLogger("myapp")
    log.setLevel(logging.INFO)
    log.addHandler(handler)

# Usage
rotate_log_file()
```
<h2> Summary: </h2>
This script automates log file rotation to manage log files efficiently.

<h1> 23. Service Monitoring Script </h1>

<h2> Description: </h2>
Automate the monitoring of services and restart them if they go down.

```
import subprocess

# Service monitoring script

def monitor_service(service_name):
    try:
        subprocess.run(["systemctl", "status", service_name], check=True)
    except subprocess.CalledProcessError:
        # Service is not running; restart it
        subprocess.run(["systemctl", "restart", service_name])

# Usage
service_name = "httpd"
monitor_service(service_name)
```
<h2> Summary: </h2>
This script automates the monitoring of services and restarts them if they are not running.

<h1> 24. Disk Space Monitoring Script </h1>

<h2> Description: </h2>
Automate disk space monitoring and send alerts if free space falls below a certain threshold.

```
import psutil
import smtplib

# Disk space monitoring script

def monitor_disk_space(threshold):
    disk = psutil.disk_usage('/')
    if disk.percent > threshold:
        send_alert_email(f"Low disk space: {disk.percent}% used")

def send_alert_email(message):
    # Implement email sending here
    pass

# Usage
threshold = 90
monitor_disk_space(threshold)
```
<h2> Summary: </h2>
This script automates the monitoring of disk space and sends alerts when it falls below a specified threshold.

<h1> 25. Active Directory User Management Script </h1>

<h2> Description:</h2>
Automate user management tasks in Active Directory, like adding, disabling, or enabling user accounts.

```
import pyad.adquery
from pyad import *

# Active Directory User Management Script

def add_user(username, password):
    with PyAD("your_domain.com") as pyad:
        pyad.set_defaults(username="admin_username", password="admin_password")
        user = pyad.aduser.ADUser.create(username)
        user.set_password(password)

# Usage
add_user("newuser", "securepassword")
```
<h2> Summary: </h2>
This script automates user management tasks in an Active Directory environment.

These Python scripts provide further examples of automation for system administrators, including backup, log rotation, service monitoring, disk space monitoring, and Active Directory user management.
Of course, here are more examples of Python scripts for automating tasks as a system administrator:

<h1> 26. Network Port Scanner Script </h1>

<h2> Description: </h2>
Automate the scanning of network ports on a target machine.

```
import socket

# Network Port Scanner Script

def scan_ports(target, port_range):
    open_ports = []
    for port in range(port_range[0], port_range[1] + 1):
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        result = sock.connect_ex((target, port))
        if result == 0:
            open_ports.append(port)
        sock.close()
    return open_ports

# Usage
target_host = "example.com"
port_range_to_scan = (1, 1024)
open_ports = scan_ports(target_host, port_range_to_scan)
print(f"Open ports: {open_ports}")
```
<h2> Summary: </h2>
This script automates network port scanning to identify open ports on a target machine.

<h1> 27. File System Cleanup Script </h1>

<h2> Description: </h2>
Automate the cleanup of files or directories based on certain criteria like age or size.

```
import os
import time

# File System Cleanup Script

def cleanup_directory(directory, max_age_in_seconds):
    current_time = time.time()
    for root, dirs, files in os.walk(directory):
        for file in files:
            file_path = os.path.join(root, file)
            if os.stat(file_path).st_mtime < current_time - max_age_in_seconds:
                os.remove(file_path)

# Usage
directory_to_clean = "/path/to/cleanup"
max_age_seconds = 30 * 24 * 60 * 60  # 30 days
cleanup_directory(directory_to_clean, max_age_seconds)
```
<h2> Summary: </h2>
This script automates the cleanup of files or directories older than a specified age.

<h1> 28. SSL Certificate Expiry Checker Script </h1>

<h2> Description: </h2> 
 Automate the checking of SSL certificate expiry dates.

```
import ssl
import socket
import datetime

# SSL Certificate Expiry Checker Script

def check_ssl_expiry(domain, port):
    context = ssl.create_default_context()
    conn = context.wrap_socket(socket.create_connection((domain, port)), server_hostname=domain)
    cert = conn.getpeercert()
    expires = datetime.datetime.strptime(cert['notAfter'], "%b %d %H:%M:%S %Y %Z")
    remaining_days = (expires - datetime.datetime.now()).days
    return remaining_days

# Usage
domain_to_check = "example.com"
port_to_check = 443
remaining_days = check_ssl_expiry(domain_to_check, port_to_check)
print(f"Days until SSL certificate expires: {remaining_days}")
```
<h2> Summary: </h2>
This script automates the checking of SSL certificate expiry dates for a specified domain.

<h1> 29. Security Patch Checker Script </h1>

<h2> Description: </h2>
Automate the checking of available security patches for the system.

```
import os
import subprocess

# Security Patch Checker Script

def check_security_patches():
    update_command = "yum check-update"  # Replace with the appropriate package manager's command
    result = subprocess.run(update_command, shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
    available_patches = result.stdout.decode('utf-8')
    return available_patches

# Usage
available_security_patches = check_security_patches()
print("Available security patches:")
print(available_security_patches)
```
<h2> Summary: </h2>
This script automates the checking of available security patches for the system.

<h1> 30. Centralized Log Aggregator Script </h1>

<h2> Description: </h2>
Automate the aggregation of logs from multiple servers to a central location.

```
import socketserver
import logging

# Centralized Log Aggregator Script

class LogHandler(socketserver.BaseRequestHandler):
    def handle(self):
        data = self.request.recv(1024)
        log_entry = data.decode('utf-8')
        logger.info(log_entry)

if __name__ == '__main__':
    logging.basicConfig(filename='/var/log/aggregated.log', level=logging.INFO)
    logger = logging.getLogger()
    server = socketserver.TCPServer(('0.0.0.0', 514), LogHandler)
    server.serve_forever()

# Usage
# Forward logs from other servers to this script (usually via syslog)
```
<h2> Summary: </h2>
This script automates the aggregation of logs from multiple servers to a central log file.

These Python scripts extend the automation capabilities for system administrators and cover tasks such as network port scanning, file system cleanup, SSL certificate expiry checks, security patch checks, and centralized log aggregation.
Here are more examples of Python scripts for automating tasks as a system administrator:

<h1> 31. User Account Management Script </h1>

<h2> Description: </h2>
Automate user account management tasks, such as creating, updating, and deleting user accounts on a Linux system.

```
import subprocess

# User Account Management Script

def create_user(username, password):
    subprocess.run(['useradd', '-m', username])
    subprocess.run(['passwd', username], input=password.encode('utf-8'))

def delete_user(username):
    subprocess.run(['userdel', '-r', username])

# Usage
new_user = 'john_doe'
new_password = 'secure_password'
create_user(new_user, new_password)
delete_user(new_user)
```
<h2> Summary: </h2>
This script automates the creation and deletion of user accounts on a Linux system.

<h1> 32. Remote System Information Retrieval Script </h1>

<h2> Description: </h2>
Automate the retrieval of system information from remote servers, such as OS version, available RAM, and disk space.

```
import paramiko

# Remote System Information Retrieval Script

def get_system_info(hostname, username, private_key_path):
    client = paramiko.SSHClient()
    client.load_system_host_keys()
    client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    
    client.connect(hostname, username=username, key_filename=private_key_path)
    
    # Execute system information commands
    stdin, stdout, stderr = client.exec_command('uname -a')
    os_info = stdout.read().decode('utf-8').strip()
    
    stdin, stdout, stderr = client.exec_command('free -m')
    ram_info = stdout.read().decode('utf-8').strip()
    
    stdin, stdout, stderr = client.exec_command('df -h')
    disk_info = stdout.read().decode('utf-8').strip()
    
    client.close()
    
    return os_info, ram_info, disk_info

# Usage
remote_host = 'example.com'
remote_username = 'your_username'
private_key_path = '/path/to/your/private/key'
os_info, ram_info, disk_info = get_system_info(remote_host, remote_username, private_key_path)
print("Operating System Info:", os_info)
print("RAM Info:", ram_info)
print("Disk Info:", disk_info)
```
<h2> Summary: </h2>
This script automates the retrieval of system information from a remote server.

<h1> 33. Automated Backup Script </h1>

<h2> Description: </h2>
 Automate the process of creating backups for specific directories.

```
import shutil
import tarfile
import datetime

# Automated Backup Script

def create_backup(source_directory, backup_directory):
    now = datetime.datetime.now()
    backup_filename = f'backup_{now.strftime("%Y%m%d%H%M%S")}.tar.gz'
    backup_path = os.path.join(backup_directory, backup_filename)
    
    with tarfile.open(backup_path, 'w:gz') as tar:
        tar.add(source_directory, arcname=os.path.basename(source_directory))
    
    return backup_path

# Usage
source_dir = '/path/to/source_directory'
backup_dir = '/path/to/backup_directory'
backup_file = create_backup(source_dir, backup_dir)
print("Backup created:", backup_file)
```
<h2> Summary: </h2>
This script automates the creation of backups for a specified directory.

<h1> 34. Configuration File Management Script </h1>

<h2> Description: </h2>
Automate the management of configuration files, such as editing, backup, and restoration.

```
import shutil

# Configuration File Management Script

def edit_and_backup_config_file(config_file, new_settings):
    # Backup the original config file
    backup_file = config_file + '.bak'
    shutil.copy(config_file, backup_file)
    
    # Update the config file with new settings
    with open(config_file, 'w') as file:
        for key, value in new_settings.items():
            file.write(f'{key} = {value}\n')

# Usage
config_file_path = '/path/to/config.conf'
new_settings = {'setting_1': 'new_value_1', 'setting_2': 'new_value_2'}
edit_and_backup_config_file(config_file_path, new_settings)
Summary: This script automates the editing and backup of configuration files.

35. Service Status Checker Script

Description: Automate checking the status of services on a remote server.

python
Copy code
import paramiko

# Service Status Checker Script

def check_service_status(hostname, username, private_key_path, service_name):
    client = paramiko.SSHClient()
    client.load_system_host_keys()
    client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    
    client.connect(hostname, username=username, key_filename=private_key_path)
    
    # Check if the service is running
    stdin, stdout, stderr = client.exec_command(f'systemctl is-active {service_name}')
    status = stdout.read().decode('utf-8').strip()
    
    client.close()
    
    return status

# Usage
remote_host = 'example.com'
remote_username = 'your_username'
private_key_path = '/path/to/your/private/key'
service_name_to_check = 'apache2'  # Change to the desired service name
service_status = check_service_status(remote_host, remote_username, private_key_path, service_name_to_check)
print(f"Service {service_name_to_check} is {service_status}")
```
<h2> Summary: </h2>
This script automates checking the status of a service on a remote server.

These Python scripts can help system administrators streamline various tasks, from user account management and remote system information retrieval to automated backups, configuration file management, and service status checks.
Certainly, here are more examples of Python scripts for automating tasks as a system administrator:

<h1> 36. Log File Analysis Script </h1>

<h2> Description: </h2>
 Automate the analysis of log files, such as identifying critical events, errors, or unusual patterns in the log data.

```
# Log File Analysis Script

def analyze_log_file(log_file_path):
    critical_events = []
    
    with open(log_file_path, 'r') as log_file:
        for line in log_file:
            if "ERROR" in line:
                critical_events.append(line)
    
    return critical_events

# Usage
log_path = '/var/log/system.log'
critical_events = analyze_log_file(log_path)
for event in critical_events:
    print("Critical Event:", event)
```
<h2> Summary: </h2>
This script automates the analysis of log files to identify critical events or errors.

<h1> 37. Package Update Script </h1>

<h2> Description: </h2>
Automate the process of checking for and updating installed packages or software.

```
import subprocess

# Package Update Script

def update_packages():
    subprocess.run(['apt', 'update'])
    subprocess.run(['apt', 'upgrade', '-y'])

# Usage
update_packages()
Summary: This script automates the update of installed packages on a Debian-based system.

38. Disk Space Monitoring Script

Description: Automate the monitoring of disk space usage on a server and receive alerts when usage exceeds a certain threshold.

python
Copy code
import shutil

# Disk Space Monitoring Script

def check_disk_space(path, threshold):
    total, used, free = shutil.disk_usage(path)
    usage_percentage = (used / total) * 100
    if usage_percentage > threshold:
        return f"Disk space is running low ({usage_percentage:.2f}% used)."
    return "Disk space is within acceptable limits."

# Usage
disk_path = '/'
threshold_percentage = 90  # Adjust as needed
result = check_disk_space(disk_path, threshold_percentage)
print(result)
```
<h2> Summary: </h2>
This script automates disk space monitoring and alerts when usage exceeds a specified threshold.

<h1> 39. Scheduled Backup Script </h1>

<h2> Description: </h2>
Automate the creation of scheduled backups for specific directories and databases.

```
import subprocess
import datetime

# Scheduled Backup Script

def create_backup(source_directory, backup_directory):
    now = datetime.datetime.now()
    backup_filename = f'backup_{now.strftime("%Y%m%d%H%M%S")}.tar.gz'
    backup_path = os.path.join(backup_directory, backup_filename)
    
    with tarfile.open(backup_path, 'w:gz') as tar:
        tar.add(source_directory, arcname=os.path.basename(source_directory))
    
    return backup_path

# Usage (schedule this script with a cron job)
source_dir = '/path/to/source_directory'
backup_dir = '/path/to/backup_directory'
backup_file = create_backup(source_dir, backup_dir)
print("Scheduled backup created:", backup_file)
```
<h2> Summary: </h2>
This script automates the creation of scheduled backups for a specified directory.

<h1> 40. SSH Key Rotation Script </h1>

<h2> Description:</h2> 
Automate the rotation of SSH keys for user accounts, providing enhanced security.

```
import os
import paramiko

# SSH Key Rotation Script

def rotate_ssh_key(username, private_key_path, new_public_key_path):
    client = paramiko.SSHClient()
    client.load_system_host_keys()
    client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    
    try:
        # Connect to the remote server
        client.connect('example.com', username=username, key_filename=private_key_path)
        
        # Upload the new public key
        with open(new_public_key_path, 'r') as key_file:
            public_key_data = key_file.read()
            client.exec_command(f"echo '{public_key_data}' >> ~/.ssh/authorized_keys")
        
        # Remove the old public key
        client.exec_command(f"sed -i '/old_public_key_string/d' ~/.ssh/authorized_keys")
    finally:
        client.close()

# Usage
user_to_rotate = 'your_username'
private_key_path = '/path/to/your/private/key'
new_public_key_path = '/path/to/your/new/public/key'
rotate_ssh_key(user_to_rotate, private_key_path, new_public_key_path)
```
<h2> Summary: </h2>
This script automates the rotation of SSH keys for enhanced security.

<h1> 41. Resource Cleanup Script </h1>

<h2> Description: </h2>
Automate the cleanup of temporary files, log files, and other resources to free up disk space.

```
import os

# Resource Cleanup Script

def cleanup_resources(directory_path, file_extension, days_to_keep):
    for root, dirs, files in os.walk(directory_path):
        for file in files:
            if file.endswith(file_extension):
                file_path = os.path.join(root, file)
                file_stat = os.stat(file_path)
                file_age = (time.time() - file_stat.st_mtime) / (60 * 60 * 24)  # in days
                if file_age >= days_to_keep:
                    os.remove(file_path)

# Usage
cleanup_directory = '/path/to/cleanup'
file_extension_to_delete = '.log'
days_to_keep = 7  # Adjust as needed
cleanup_resources(cleanup_directory, file_extension_to_delete, days_to_keep)
```
<h2> Summary: </h2> 
This script automates the cleanup of specific file types that are older than a certain number of days.

These Python scripts cover various automation tasks commonly performed by system administrators, such as log analysis, package updates, disk space monitoring, scheduled backups, SSH key rotation, and resource cleanup.
Certainly, here are more examples of Python scripts for automating tasks as a system administrator:

<h1> 42. User Account Management Script </h1>

<h2> Description: </h2>
Automate the creation, modification, or deletion of user accounts on a Linux system.

```
import subprocess

# User Account Management Script

def create_user(username, password):
    subprocess.run(['useradd', username])
    subprocess.run(['echo', f'{username}:{password}', '|', 'chpasswd'])

def modify_user(username, new_password):
    subprocess.run(['echo', f'{username}:{new_password}', '|', 'chpasswd'])

def delete_user(username):
    subprocess.run(['userdel', '-r', username])

# Usage
create_user('newuser', 'newpassword')
modify_user('existinguser', 'newpassword')
delete_user('obsoleteuser')
Summary: This script automates user account management tasks, including account creation, modification, and deletion.

43. SSL Certificate Renewal Script

Description: Automate the renewal of SSL certificates to ensure secure connections.

python
Copy code
import subprocess
import datetime

# SSL Certificate Renewal Script

def renew_ssl_certificate(domain, cert_path, key_path, output_path):
    now = datetime.datetime.now()
    expiration_date = subprocess.check_output(['openssl', 'x509', '-noout', '-enddate', '-in', cert_path]).decode()
    expiration_date = datetime.datetime.strptime(expiration_date[9:], '%b %d %H:%M:%S %Y %Z')
    
    if expiration_date < now:
        subprocess.run(['certbot', 'certonly', '--webroot', '-d', domain, '--cert-path', cert_path, '--key-path', key_path, '--fullchain-path', output_path])
    else:
        print("Certificate is still valid.")

# Usage
renew_ssl_certificate('example.com', '/etc/ssl/certs/cert.pem', '/etc/ssl/private/key.pem', '/etc/ssl/fullchain.pem')
```
<h2> Summary: </h2>
This script automates the renewal of SSL certificates when they are close to expiration.

<h1> 44. Firewall Rule Management Script </h1>

<h2> Description: </h2>
Automate the management of firewall rules, including adding, modifying, or deleting rules.

```
import subprocess

# Firewall Rule Management Script

def add_firewall_rule(protocol, port):
    subprocess.run(['ufw', 'allow', f'{port}/{protocol}'])

def delete_firewall_rule(protocol, port):
    subprocess.run(['ufw', 'delete', f'allow {port}/{protocol}'])

# Usage
add_firewall_rule('tcp', 80)
delete_firewall_rule('tcp', 8080)
```
<h2> Summary: </h2>
This script automates firewall rule management tasks, including adding and deleting rules.

<h1> 45. Automated Server Monitoring Script </h1>

<h2> Description: </h2>
Automate server monitoring and receive alerts when predefined conditions are met.

```
import subprocess
import smtplib
from email.mime.text import MIMEText

# Automated Server Monitoring Script

def monitor_server():
    # Perform server monitoring tasks
    if server_conditions_met():
        send_alert_email()

def server_conditions_met():
    # Define server monitoring conditions
    # For example, check CPU load, available disk space, etc.
    return False

def send_alert_email():
    # Send alert email when conditions are met
    from_address = 'youremail@gmail.com'
    to_address = 'admin@example.com'
    msg = MIMEText('Server alert: predefined conditions have been met.')
    msg['Subject'] = 'Server Alert'
    msg['From'] = from_address
    msg['To'] = to_address
    
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.starttls()
    server.login(from_address, 'yourpassword')
    server.sendmail(from_address, to_address, msg.as_string())
    server.quit()

# Usage
monitor_server()
```
<h2> Summary: </h2>
This script automates server monitoring and sends alert emails when predefined conditions are met.

<h1> 46. Automated Backup Verification Script </h1>

<h2> Description: </h2>
Automate the verification of backups to ensure data integrity.

```
import subprocess

# Automated Backup Verification Script

def verify_backup(backup_file, original_file):
    subprocess.run(['diff', backup_file, original_file])

# Usage
backup_path = '/path/to/backup/file'
original_path = '/path/to/original/file'
verify_backup(backup_path, original_path)
```
<h2> Summary: </h2>
This script automates the verification of backup files against their original counterparts.

These Python scripts cover a wide range of automation tasks relevant to system administrators, including user account management, SSL certificate renewal, firewall rule management, server monitoring, and backup verification.
Certainly, here are more examples of Python scripts for automating tasks as a system administrator:

<h1> 47. System Information Script </h1>

<h2> Description: </h2>
Gather and display essential system information, such as OS version, CPU, RAM, and disk space.

```
import platform
import os

# System Information Script

def get_system_info():
    system_info = {
        "OS": platform.system(),
        "OS Version": platform.version(),
        "CPU": platform.processor(),
        "RAM (GB)": round(os.sysconf('SC_PAGE_SIZE') * os.sysconf('SC_PHYS_PAGES') / (1024. ** 3)),
        "Disk Space (GB)": round(os.statvfs('/').f_frsize * os.statvfs('/').f_blocks / (1024. ** 3)),
    }
    return system_info

def display_system_info(info):
    for key, value in info.items():
        print(f"{key}: {value}")

# Usage
system_info = get_system_info()
display_system_info(system_info)
```
<h2> Summary: </h2>
This script gathers and displays essential system information, making it useful for system administrators.

<h1> 48. Log Rotation Script </h1>

<h2> Description: </h2>
Automate log rotation to manage log files efficiently.

```
import subprocess

# Log Rotation Script

def rotate_logs(log_directory, max_log_count):
    subprocess.run(['logrotate', '-s', '/var/logrotate.status', '-f', log_directory])
    cleanup_old_logs(log_directory, max_log_count)

def cleanup_old_logs(log_directory, max_log_count):
    log_files = sorted(os.listdir(log_directory), key=lambda x: os.path.getctime(os.path.join(log_directory, x)), reverse=True)
    if len(log_files) > max_log_count:
        for log_file in log_files[max_log_count:]:
            os.remove(os.path.join(log_directory, log_file))

# Usage
rotate_logs('/var/log/myapp/', 5)
```
<h2> Summary:</h2> 
This script automates log rotation and cleanup, ensuring that log files do not consume excessive disk space.

<h1> 49. Disk Space Monitoring Script </h1>

<h2> Description: </h2>
Continuously monitor disk space usage and receive alerts when it reaches a critical level.

```
import subprocess
import smtplib
from email.mime.text import MIMEText

# Disk Space Monitoring Script

def monitor_disk_space():
    if disk_space_usage() > 90:
        send_alert_email()

def disk_space_usage():
    df_output = subprocess.check_output(['df', '/']).decode()
    disk_usage = df_output.split('\n')[1].split()[4][:-1]
    return int(disk_usage)

def send_alert_email():
    # Send alert email when disk space usage is high
    from_address = 'youremail@gmail.com'
    to_address = 'admin@example.com'
    msg = MIMEText('Disk space alert: Disk space usage is above 90%.')
    msg['Subject'] = 'Disk Space Alert'
    msg['From'] = from_address
    msg['To'] = to_address

    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.starttls()
    server.login(from_address, 'yourpassword')
    server.sendmail(from_address, to_address, msg.as_string())
    server.quit()

# Usage
monitor_disk_space()
```
<h2> Summary: </h2>
This script continuously monitors disk space usage and sends alert emails when it reaches a critical level.

<h1> 50. SSH Key Deployment Script </h1>

<h2> Description: </h2>
 Automate the deployment of SSH keys to multiple servers.

```
import subprocess

# SSH Key Deployment Script

def deploy_ssh_key(username, server, ssh_key_path):
    subprocess.run(['ssh-copy-id', f'{username}@{server}', '-i', ssh_key_path])

# Usage
deploy_ssh_key('user', 'server.example.com', '/path/to/ssh/key')
```
<h2> Summary: </h2>
This script automates the deployment of SSH keys to multiple servers, simplifying the process of SSH key management.

<h1> 51. Network Service Monitoring Script </h1>

<h2> Description: </h2>
Continuously monitor network services (e.g., HTTP, SSH) and send alerts if they become unavailable.

```
import socket
import smtplib
from email.mime.text import MIMEText

# Network Service Monitoring Script

def monitor_service(service, host, port):
    if not is_service_available(host, port):
        send_alert_email(service, host, port)

def is_service_available(host, port):
    try:
        socket.create_connection((host, port), timeout=10)
        return True
    except (socket.timeout, ConnectionRefusedError):
        return False

def send_alert_email(service, host, port):
    # Send alert email when a service is unavailable
    from_address = 'youremail@gmail.com'
    to_address = 'admin@example.com'
    msg = MIMEText(f'Service alert: {service} on {host}:{port} is unavailable.')
    msg['Subject'] = 'Service Alert'
    msg['From'] = from_address
    msg['To'] = to_address

    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.starttls()
    server.login(from_address, 'yourpassword')
    server.sendmail(from_address, to_address, msg.as_string())
    server.quit()

# Usage
monitor_service('SSH', 'server.example.com', 22)
```
<h2> Summary: </h2>
This script continuously monitors network services and sends alert emails if they become unavailable.

These Python scripts cover a wide range of automation tasks relevant to system administrators, including system information retrieval, log rotation, disk space monitoring, SSH key deployment, and network service monitoring.

Certainly, here are more examples of Python scripts for automation tasks relevant to system administrators:

<h1> 52. Scheduled Backup Script </h1>

<h2> Description: </h2>
Create a script to automate scheduled backups of critical files and directories.

```
import shutil
import datetime

# Scheduled Backup Script

def backup_files(source_dir, backup_dir):
    today = datetime.date.today()
    backup_folder = f"backup_{today}"
    backup_path = os.path.join(backup_dir, backup_folder)

    try:
        shutil.copytree(source_dir, backup_path)
        print(f"Backup completed successfully to {backup_path}")
    except Exception as e:
        print(f"Backup failed: {e}")

# Usage
backup_files('/path/to/source', '/path/to/backup')
```
<h2> Summary: </h2>
This script automates the backup of files and directories to a specified backup location, creating a new backup folder for each backup.

<h1> 53. User Account Management Script </h1>

<h2> Description: </h2>
Automate user account management tasks, such as creating, modifying, or deleting user accounts.

```
import subprocess

# User Account Management Script

def create_user(username):
    subprocess.run(['useradd', username])
    print(f"User {username} created.")

def change_password(username, new_password):
    subprocess.run(['passwd', username], input=new_password.encode())
    print(f"Password changed for user {username}.")

def delete_user(username):
    subprocess.run(['userdel', username])
    print(f"User {username} deleted.")

# Usage
create_user('newuser')
change_password('existinguser', 'newpassword')
delete_user('olduser')
```
<h2> Summary: </h2>
This script simplifies user account management tasks, such as user creation, password changes, and user deletion.

<h1> 54. Monitoring Script with Alerts </h1>

<h2> Description: </h2>
Create a script to monitor server health and send alerts if critical conditions are met.

```
import psutil
import smtplib
from email.mime.text import MIMEText

# Server Monitoring Script with Alerts

def monitor_server():
    cpu_usage = psutil.cpu_percent()
    memory_usage = psutil.virtual_memory().percent
    if cpu_usage > 90 or memory_usage > 90:
        send_alert(cpu_usage, memory_usage)

def send_alert(cpu_usage, memory_usage):
    # Send an alert email if CPU or memory usage is high
    from_address = 'youremail@gmail.com'
    to_address = 'admin@example.com'
    subject = 'Server Health Alert'
    message = f'CPU Usage: {cpu_usage}%\nMemory Usage: {memory_usage}%'
    
    msg = MIMEText(message)
    msg['Subject'] = subject
    msg['From'] = from_address
    msg['To'] = to_address

    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.starttls()
    server.login(from_address, 'yourpassword')
    server.sendmail(from_address, to_address, msg.as_string())
    server.quit()

# Usage
monitor_server()
```
<h2> Summary: </h2>
This script monitors server health, specifically CPU and memory usage, and sends an alert email if usage exceeds a certain threshold.

<h1> 55. Configuration Management Script </h1>

<h2> Description: </h2>
Automate configuration management tasks, such as deploying and maintaining configuration files across multiple servers.

```
import paramiko

# Configuration Management Script

def deploy_config(server, username, password, local_file, remote_file):
    ssh_client = paramiko.SSHClient()
    ssh_client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    
    try:
        ssh_client.connect(server, username=username, password=password)
        sftp = ssh_client.open_sftp()
        sftp.put(local_file, remote_file)
        print(f"Configuration file deployed to {server}.")
    except Exception as e:
        print(f"Configuration deployment failed: {e}")
    finally:
        ssh_client.close()

# Usage
deploy_config('server.example.com', 'user', 'password', 'local.conf', 'remote.conf')
```
<h2> Summary: </h2>
This script uses SSH to deploy a local configuration file to a remote server, simplifying configuration management tasks.

<h1> 56. Centralized Log Collection Script </h1>

<h2> Description: </h2>
Create a script to collect and centralize logs from multiple servers to a central log server.

```
import socket
import syslog

# Centralized Log Collection Script

def collect_and_forward_logs(log_server, log_port, logs):
    syslog_server = (log_server, log_port)

    for log in logs:
        try:
            syslog.syslog(syslog.LOG_INFO, f'{log}: Log message')
            print(f'{log} logs forwarded to {log_server}')
        except Exception as e:
            print(f'Error forwarding logs to {log_server}: {e}')

# Usage
log_servers = ['logserver1.example.com', 'logserver2.example.com']
log_port = 514
log_sources = ['appserver1.example.com', 'appserver2.example.com']
collect_and_forward_logs(log_servers[0], log_port, log_sources)
```
<h2> Summary: </h2>
This script collects and forwards logs from various sources to a central log server, simplifying centralized log collection.

These Python scripts address a variety of automation needs for system administrators, including scheduled backups, user account management, server monitoring with alerts, configuration management, and centralized log collection.
Of course, here are more examples of Python scripts for automating common system administrator tasks:

<h1> 57. Disk Space Monitoring and Alerting Script </h1>

<h2> Description: </h2>
Create a script to monitor disk space usage and send alerts when it exceeds a specified threshold.

```
import psutil
import smtplib
from email.mime.text import MIMEText

# Disk Space Monitoring and Alerting Script

def monitor_disk_space(path, threshold_gb):
    disk = psutil.disk_usage(path)
    free_gb = disk.free / (2**30)  # Convert bytes to GB
    if free_gb < threshold_gb:
        send_alert(path, free_gb, threshold_gb)

def send_alert(path, free_gb, threshold_gb):
    subject = 'Disk Space Alert'
    message = f'Disk space on {path} is running low.\nFree space: {free_gb} GB\nThreshold: {threshold_gb} GB'

    from_address = 'your_email@gmail.com'
    to_address = 'admin@example.com'

    msg = MIMEText(message)
    msg['Subject'] = subject
    msg['From'] = from_address
    msg['To'] = to_address

    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.starttls()
    server.login(from_address, 'your_password')
    server.sendmail(from_address, to_address, msg.as_string())
    server.quit()

# Usage
monitor_disk_space('/', 5)  # Monitor the root directory and send an alert if free space is less than 5 GB
```
<h2> Summary: </h2>
This script monitors the free disk space of a specified directory and sends an email alert if it falls below a given threshold.

<h1> 58. Network Configuration Backup Script </h1>

<h2> Description: </h2>
Automate the backup of network device configurations using the Paramiko library.

```
import paramiko
import os

# Network Configuration Backup Script

def backup_network_device_config(host, username, password, enable_password, save_path):
    try:
        ssh = paramiko.SSHClient()
        ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
        ssh.connect(host, username=username, password=password, allow_agent=False, look_for_keys=False)
        
        remote_conn = ssh.invoke_shell()
        remote_conn.send("enable\n")
        remote_conn.send(enable_password + "\n")
        remote_conn.send("terminal length 0\n")
        remote_conn.send("show run\n")
        
        output = remote_conn.recv(65535)
        save_backup(output, save_path)

        ssh.close()
        print(f"Configuration saved to {save_path}")
    except Exception as e:
        print(f"Backup failed: {e}")

def save_backup(output, save_path):
    with open(save_path, 'wb') as f:
        f.write(output)

# Usage
backup_network_device_config('192.168.1.1', 'admin', 'admin_password', 'enable_password', 'router_backup.txt')
```
<h2> Summary: </h2>
This script connects to a network device via SSH, retrieves its configuration, and saves it to a specified file.

<h1> 59. Remote Server Reboot Script </h1>

<h2> Description: </h2>
Create a script to reboot a remote server using SSH.

```
import paramiko

# Remote Server Reboot Script

def reboot_remote_server(host, username, password):
    try:
        ssh = paramiko.SSHClient()
        ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
        ssh.connect(host, username=username, password=password)
        ssh.exec_command('sudo reboot')
        print(f"Reboot command sent to {host}")
    except Exception as e:
        print(f"Reboot failed: {e}")

# Usage
reboot_remote_server('remote_server.example.com', 'admin', 'password')
```
<h2> Summary: </h2>
This script uses SSH to connect to a remote server and initiates a reboot.

<h1> 60. Log Analysis Script </h1>

<h2> Description: </h2>
Create a script to parse and analyze log files for specific patterns or issues.

```
# Log Analysis Script

def analyze_log_file(log_file, keyword):
    try:
        with open(log_file, 'r') as file:
            for line in file:
                if keyword in line:
                    print(f"Found '{keyword}' in log: {line.strip()}")
    except Exception as e:
        print(f"Log analysis failed: {e}")

# Usage
analyze_log_file('/var/log/syslog', 'error')
```
<h2> Summary: </h2>
This script reads a log file and searches for a specific keyword, helping identify potential issues.

These Python scripts demonstrate automating tasks such as disk space monitoring and alerting, network configuration backups, remote server reboots, and log analysis.

Certainly, here are more examples of Python scripts for automating various system administrator tasks:

<h1> 61. Service Status Monitoring Script </h1>

<h2> Description: </h2>
Create a script to check the status of a service (e.g., a web server) and restart it if it's not running.

```
import subprocess

# Service Status Monitoring Script

def monitor_and_restart_service(service_name):
    try:
        result = subprocess.run(['systemctl', 'is-active', service_name], stdout=subprocess.PIPE)
        if result.stdout.decode().strip() != 'active':
            subprocess.run(['systemctl', 'restart', service_name])
            print(f"Service '{service_name}' was not running, but has been restarted.")
    except Exception as e:
        print(f"Service monitoring and restart failed: {e}")

# Usage
monitor_and_restart_service('apache2')  # Monitor and restart Apache web server if not active
```
<h2> Summary: </h2>
This script checks the status of a service and restarts it if it's not active.

<h1> 62. User Account Management Script </h1>

<h2> Description: </h2>
Create a script to automate user account management tasks, such as creating or deleting user accounts.

```
import subprocess

# User Account Management Script

def create_user(username, password):
    try:
        subprocess.run(['useradd', '-m', username])
        subprocess.run(['echo', f'{username}:{password}', '|', 'chpasswd'])
        print(f"User '{username}' has been created.")
    except Exception as e:
        print(f"User creation failed: {e}")

def delete_user(username):
    try:
        subprocess.run(['userdel', '-r', username])
        print(f"User '{username}' has been deleted.")
    except Exception as e:
        print(f"User deletion failed: {e}")

# Usage
create_user('newuser', 'password123')  # Create a new user
delete_user('olduser')  # Delete an existing user
```
<h2> Summary: </h2>
This script allows for creating or deleting user accounts.

<h1> 63. Firewall Rule Management Script </h1>

<h2> Description: </h2>
Create a script to manage firewall rules, such as adding or removing rules.

```
import subprocess

# Firewall Rule Management Script

def add_firewall_rule(port):
    try:
        subprocess.run(['ufw', 'allow', str(port)])
        print(f"Firewall rule for port {port} has been added.")
    except Exception as e:
        print(f"Firewall rule addition failed: {e}")

def remove_firewall_rule(port):
    try:
        subprocess.run(['ufw', 'delete', 'allow', str(port)])
        print(f"Firewall rule for port {port} has been removed.")
    except Exception as e:
        print(f"Firewall rule removal failed: {e}")

# Usage
add_firewall_rule(8080)  # Add a firewall rule to allow traffic on port 8080
remove_firewall_rule(22)  # Remove the rule allowing SSH traffic on port 22
```
<h2> Summary: </h2>
This script can add or remove firewall rules to control incoming and outgoing network traffic.

64. System Updates and Patch Management Script

Description: Create a script to automate system updates and patch management.

python
Copy code
import subprocess

# System Updates and Patch Management Script

def update_system():
    try:
        subprocess.run(['apt', 'update', '-y'])
        subprocess.run(['apt', 'upgrade', '-y'])
        print("System updates and patches applied.")
    except Exception as e:
        print(f"System update and patch application failed: {e}")

# Usage
update_system()  # Update and patch the system
Summary: This script updates the system and applies patches.

These Python scripts cover a range of system administration tasks, including service monitoring, user account management, firewall rule management, and system updates.




User
give me examples
ChatGPT
Of course, here are more examples of Python scripts for automating various system administrator tasks:

65. Backup Script

Description: Create a script to automatically backup specified files or directories to a backup location.

python
Copy code
import shutil
import time

# Backup Script

def backup_files(source, destination):
    try:
        timestamp = time.strftime("%Y-%m-%d-%H-%M-%S")
        backup_folder = f"{destination}/backup-{timestamp}"
        shutil.copytree(source, backup_folder)
        print(f"Backup of '{source}' created at '{backup_folder}'")
    except Exception as e:
        print(f"Backup failed: {e}")

# Usage
backup_files('/var/www/html', '/backup')  # Backup the web server files to a specified location
Summary: This script creates backups of files or directories, including a timestamp in the backup folder name.

66. Log Rotation Script

Description: Create a script for log file management that compresses and archives log files when they reach a certain size.

python
Copy code
import os
import gzip

# Log Rotation Script

def rotate_log(log_file, max_size):
    try:
        if os.path.getsize(log_file) > max_size:
            with open(log_file, 'rb') as f_in:
                with gzip.open(log_file + '.gz', 'wb') as f_out:
                    shutil.copyfileobj(f_in, f_out)
            open(log_file, 'w').close()
            print(f"Rotated log file '{log_file}'")
    except Exception as e:
        print(f"Log rotation failed: {e}")

# Usage
rotate_log('/var/log/myapp.log', 1048576)  # Rotate log file if it exceeds 1 MB
Summary: This script rotates log files by compressing and archiving them when they reach a specified size.

67. Directory Cleanup Script

Description: Create a script to clean up a directory by removing files that are older than a specified number of days.

python
Copy code
import os
import time

# Directory Cleanup Script

def cleanup_directory(directory, days_to_keep):
    try:
        current_time = time.time()
        for item in os.listdir(directory):
            item_path = os.path.join(directory, item)
            if os.path.isfile(item_path):
                item_time = os.path.getctime(item_path)
                if current_time - item_time > days_to_keep * 86400:
                    os.remove(item_path)
                    print(f"Removed '{item_path}'")
    except Exception as e:
        print(f"Directory cleanup failed: {e}")

# Usage
cleanup_directory('/var/log', 7)  # Remove log files older than 7 days
Summary: This script cleans up a directory by removing files older than a specified number of days.

68. Server Monitoring Script

Description: Create a script that monitors server resource usage (CPU, memory, disk space) and sends alerts if certain thresholds are exceeded.

python
Copy code
import psutil
import smtplib

# Server Monitoring Script

def monitor_server_resources():
    try:
        cpu_usage = psutil.cpu_percent()
        memory_usage = psutil.virtual_memory().percent
        disk_usage = psutil.disk_usage('/').percent
        if cpu_usage > 90 or memory_usage > 90 or disk_usage > 90:
            send_alert_email()
    except Exception as e:
        print(f"Server monitoring failed: {e}")

def send_alert_email():
    try:
        server = "your_smtp_server.com"
        port = 587
        sender_email = "your_email@gmail.com"
        password = "your_password"
        recipient_email = "admin@example.com"
        subject = "Server Resource Alert"
        body = "CPU, memory, or disk usage is above 90%."
        message = f"Subject: {subject}\n\n{body}"
        with smtplib.SMTP(server, port) as server:
            server.starttls()
            server.login(sender_email, password)
            server.sendmail(sender_email, recipient_email, message)
            print("Alert email sent.")
    except Exception as e:
        print(f"Email alert failed: {e}")

# Usage
monitor_server_resources()  # Monitor server resources and send alerts if thresholds are exceeded
Summary: This script monitors server resource usage and sends email alerts if CPU, memory, or disk usage exceeds a specified threshold.

These Python scripts cover a range of system administration tasks, including backups, log rotation, directory cleanup, and server resource monitoring.




User
give me examples
ChatGPT
Certainly, here are more examples of Python scripts for automating tasks as a system administrator:

69. User Account Management Script

Description: Create a script to manage user accounts, including adding, deleting, and listing user accounts.

python
Copy code
import subprocess

# User Account Management Script

def add_user(username, password):
    try:
        subprocess.run(["useradd", username, "-m", "-p", password])
        print(f"User '{username}' added.")
    except Exception as e:
        print(f"User creation failed: {e}")

def delete_user(username):
    try:
        subprocess.run(["userdel", "-r", username])
        print(f"User '{username}' deleted.")
    except Exception as e:
        print(f"User deletion failed: {e}")

def list_users():
    try:
        users = subprocess.check_output(["cut", "-d:", "-f1", "/etc/passwd"])
        print("User List:")
        print(users.decode())
    except Exception as e:
        print(f"User listing failed: {e}")

# Usage
add_user("newuser", "password123")  # Add a new user
delete_user("olduser")  # Delete an existing user
list_users()  # List all user accounts
Summary: This script allows you to add, delete, and list user accounts on a Linux system.

70. Software Package Updates Script

Description: Create a script to automate software package updates on a Linux system.

python
Copy code
import subprocess

# Software Package Updates Script

def update_packages():
    try:
        subprocess.run(["apt", "update"])
        subprocess.run(["apt", "upgrade", "-y"])
        print("Software packages updated.")
    except Exception as e:
        print(f"Package update failed: {e}")

# Usage
update_packages()  # Update software packages
Summary: This script automates the process of updating software packages on a Debian-based Linux system using the apt package manager.

71. Server Backup Script

Description: Create a script to automate the backup of critical server configuration files.

python
Copy code
import shutil
import time

# Server Backup Script

def backup_server_config():
    try:
        timestamp = time.strftime("%Y%m%d%H%M%S")
        backup_folder = f"/backups/server-config-{timestamp}"
        config_files = ["/etc/nginx/nginx.conf", "/etc/ssh/sshd_config", "/etc/apache2/httpd.conf"]
        for file in config_files:
            shutil.copy2(file, backup_folder)
        print("Server configuration files backed up.")
    except Exception as e:
        print(f"Server backup failed: {e}")

# Usage
backup_server_config()  # Backup server configuration files
Summary: This script automates the backup of critical server configuration files, such as web server and SSH configuration files.

72. Automated Monitoring Alerts Script

Description: Create a script to monitor server logs for specific events and send alerts when those events occur.

python
Copy code
import subprocess
import smtplib

# Automated Monitoring Alerts Script

def monitor_logs():
    try:
        log_file = "/var/log/syslog"
        keyword = "error"
        if check_logs(log_file, keyword):
            send_alert_email(log_file, keyword)
    except Exception as e:
        print(f"Log monitoring failed: {e}")

def check_logs(log_file, keyword):
    log_content = subprocess.check_output(["grep", keyword, log_file])
    return len(log_content) > 0

def send_alert_email(log_file, keyword):
    server = "your_smtp_server.com"
    port = 587
    sender_email = "your_email@gmail.com"
    password = "your_password"
    recipient_email = "admin@example.com"
    subject = "Error Alert"
    body = f"Error keyword '{keyword}' found in log file '{log_file}'."
    message = f"Subject: {subject}\n\n{body}"
    with smtplib.SMTP(server, port) as server:
        server.starttls()
        server.login(sender_email, password)
        server.sendmail(sender_email, recipient_email, message)
        print("Error alert email sent.")

# Usage
monitor_logs()  # Monitor logs for errors and send alerts if found
Summary: This script monitors server logs for specific events and sends email alerts if the defined keyword is found.

These Python scripts can help automate various system administration tasks, including user account management, software updates, server configuration backups, and log monitoring.




User
give me more examples like this as cybersecurity analyst.
ChatGPT
Certainly, here are more examples of Python scripts for automating tasks as a cybersecurity analyst:

73. Network Port Scanner Script

Description: Create a script to scan and list open network ports on a target system.

python
Copy code
import socket

# Network Port Scanner Script

def scan_ports(target, port_range):
    open_ports = []
    for port in range(port_range[0], port_range[1] + 1):
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        result = sock.connect_ex((target, port))
        if result == 0:
            open_ports.append(port)
        sock.close()
    return open_ports

# Usage
target_host = "example.com"
port_range_to_scan = (1, 100)
open_ports = scan_ports(target_host, port_range_to_scan)
print(f"Open ports on {target_host}: {open_ports}")
Summary: This script allows you to scan a range of network ports on a target system and list the open ports.

74. Log Analysis Script

Description: Create a script to analyze log files for security-related events and generate reports.

python
Copy code
# Log Analysis Script

def analyze_logs(log_file):
    try:
        with open(log_file, "r") as file:
            log_data = file.readlines()
        security_events = [line for line in log_data if "security" in line]
        report_file = "security_report.txt"
        with open(report_file, "w") as report:
            report.write("Security Log Analysis Report:\n")
            for event in security_events:
                report.write(event)
        print(f"Log analysis report generated: {report_file}")
    except Exception as e:
        print(f"Log analysis failed: {e}")

# Usage
log_file_to_analyze = "/var/log/auth.log"
analyze_logs(log_file_to_analyze)
Summary: This script reads a log file, extracts security-related events, and generates a report with those events.

75. Automated Vulnerability Scanner Script

Description: Create a script to run a vulnerability scanner on a target system and produce a vulnerability report.

python
Copy code
import subprocess

# Automated Vulnerability Scanner Script

def run_vulnerability_scan(target):
    try:
        report_file = "vulnerability_report.txt"
        with open(report_file, "w") as report:
            subprocess.run(["nmap", "-Pn", "-p-", "-sV", target], stdout=report, stderr=subprocess.DEVNULL)
        print(f"Vulnerability scan completed. Report saved to {report_file}")
    except Exception as e:
        print(f"Vulnerability scan failed: {e}")

# Usage
target_to_scan = "example.com"
run_vulnerability_scan(target_to_scan)
Summary: This script uses the nmap tool to run a vulnerability scan on a target system and saves the results in a report.

76. Password Strength Checker Script

Description: Create a script to check the strength of user passwords and enforce password policies.

python
Copy code
# Password Strength Checker Script

def check_password_strength(password):
    if len(password) < 8:
        return "Weak"
    elif any(char.islower() for char in password) and any(char.isupper() for char in password) and any(char.isdigit() for char in password):
        return "Strong"
    else:
        return "Moderate"

# Usage
user_password = "SecureP@ssw0rd"
strength = check_password_strength(user_password)
print(f"Password strength: {strength}")
Summary: This script checks the strength of a user's password based on length, complexity, and enforces password policies.

These Python scripts can assist cybersecurity analysts in automating tasks related to network port scanning, log analysis, vulnerability scanning, and password strength checking.




User
give me examples
ChatGPT
Certainly, here are more examples of Python scripts for automating tasks as a cybersecurity analyst:

77. Intrusion Detection Script

Description: Create a script to monitor log files for suspicious activity and trigger alerts.

python
Copy code
import time

# Intrusion Detection Script

def monitor_logs(log_file):
    while True:
        with open(log_file, "r") as file:
            log_data = file.readlines()
        for line in log_data:
            if "suspicious_pattern" in line:
                alert_security_team(line)
        time.sleep(60)

def alert_security_team(event):
    # Replace this with your alerting mechanism (e.g., email, SMS)
    print(f"Suspicious event detected: {event}")

# Usage
log_file_to_monitor = "security.log"
monitor_logs(log_file_to_monitor)
Summary: This script continuously monitors log files for specific patterns indicating suspicious activity and alerts the security team.

78. SSL Certificate Expiry Checker Script

Description: Create a script to check the expiration dates of SSL certificates on web servers.

python
Copy code
import ssl
import socket

# SSL Certificate Expiry Checker Script

def check_ssl_certificate_expiry(domain, port):
    context = ssl.create_default_context()
    with socket.create_connection((domain, port)) as sock:
        with context.wrap_socket(sock, server_hostname=domain) as ssock:
            cert = ssock.getpeercert()
            expiry_date = cert['notAfter']
    return expiry_date

# Usage
web_domain = "example.com"
web_port = 443
expiry_date = check_ssl_certificate_expiry(web_domain, web_port)
print(f"SSL certificate for {web_domain} expires on {expiry_date}.")
Summary: This script checks the expiration date of an SSL certificate for a specified web domain.

79. Security Policy Compliance Checker Script

Description: Create a script to verify system configurations against security policies.

python
Copy code
import subprocess

# Security Policy Compliance Checker Script

def check_security_policy_compliance():
    try:
        compliance_report = "compliance_report.txt"
        with open(compliance_report, "w") as report:
            subprocess.run(["auditctl", "-l"], stdout=report, stderr=subprocess.DEVNULL)
        print(f"Security policy compliance report generated: {compliance_report}")
    except Exception as e:
        print(f"Compliance check failed: {e}")

# Usage
check_security_policy_compliance()
Summary: This script checks system configurations against security policies using the auditctl tool and generates a compliance report.

80. Patch Management Script

Description: Create a script to automate the process of applying security patches to servers.

python
Copy code
import subprocess

# Patch Management Script

def apply_security_patches():
    try:
        subprocess.run(["apt", "update"], stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)
        subprocess.run(["apt", "upgrade", "-y"], stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)
        print("Security patches applied successfully.")
    except Exception as e:
        print(f"Patch application failed: {e}")

# Usage
apply_security_patches()
Summary: This script updates the package lists and applies security patches to the system using the apt package manager.

These Python scripts can assist cybersecurity analysts in automating tasks related to intrusion detection, SSL certificate monitoring, security policy compliance checks, and patch management.




User
give me examples
ChatGPT
Certainly, here are more examples of Python scripts for automating tasks as a cybersecurity analyst:

81. Network Scanning Script

Description: Create a script to perform network scanning using the Python nmap library.

python
Copy code
import nmap

# Network Scanning Script

def scan_target(target):
    nm = nmap.PortScanner()
    nm.scan(target, arguments="-p 1-1024 -T4 -F")
    
    for host in nm.all_hosts():
        print(f"Scanning host: {host}")
        for port in nm[host]["tcp"]:
            print(f"Port {port} is {nm[host]['tcp'][port]['state']}")

# Usage
target_ip = "192.168.1.1"
scan_target(target_ip)
Summary: This script performs a fast network scan on a specified target IP address using the nmap library in Python.

82. Log Analysis Script

Description: Create a script to analyze log files for unusual patterns or security events.

python
Copy code
# Log Analysis Script

def analyze_logs(log_file):
    with open(log_file, "r") as file:
        logs = file.readlines()
    for line in logs:
        if "unusual_pattern" in line:
            alert_security(line)

def alert_security(event):
    # Replace this with your alerting mechanism (e.g., email, SMS)
    print(f"Potential security event: {event}")

# Usage
log_file_to_analyze = "security.log"
analyze_logs(log_file_to_analyze)
Summary: This script reads log files, checks for unusual patterns, and triggers security alerts.

83. Vulnerability Scanning Script

Description: Create a script to scan a server for vulnerabilities using the nmap library.

python
Copy code
import nmap

# Vulnerability Scanning Script

def scan_vulnerabilities(target):
    nm = nmap.PortScanner()
    nm.scan(target, arguments="-T4 -F --script vuln")
    
    for host in nm.all_hosts():
        print(f"Scanning host: {host}")
        if 'script' in nm[host]:
            for script_name, script_output in nm[host]['script'].items():
                print(f"Script: {script_name}\n{script_output}")

# Usage
target_ip = "192.168.1.1"
scan_vulnerabilities(target_ip)
Summary: This script uses the nmap library to scan a target for vulnerabilities and lists the scripts and their outputs.

84. Security Policy Checker Script

Description: Create a script to validate system configurations against predefined security policies.

python
Copy code
import subprocess

# Security Policy Checker Script

def check_security_policy_compliance(policy_file):
    try:
        compliance_report = "compliance_report.txt"
        with open(compliance_report, "w") as report:
            subprocess.run(["auditctl", "-l"], stdout=report, stderr=subprocess.DEVNULL)
        print(f"Security policy compliance report generated: {compliance_report}")
    except Exception as e:
        print(f"Compliance check failed: {e}")

# Usage
security_policy = "policy.rules"
check_security_policy_compliance(security_policy)
Summary: This script checks the system's configuration against a predefined security policy and generates a compliance report.

These Python scripts can assist cybersecurity analysts in automating tasks related to network scanning, log analysis, vulnerability scanning, and security policy compliance checks.




User
give me examples
ChatGPT
Certainly, here are more examples of Python scripts for automating tasks as a cybersecurity analyst:

85. Incident Response Automation Script

Description: Create a script to automate incident response tasks, such as isolating a compromised host from the network and collecting forensic data.

python
Copy code
import subprocess

# Incident Response Automation Script

def isolate_host(host_ip):
    try:
        subprocess.run(["iptables", "-A", "INPUT", "-s", host_ip, "-j", "DROP"])
        print(f"Isolated host {host_ip} from the network.")
    except Exception as e:
        print(f"Failed to isolate host: {e}")

def collect_forensic_data(host_ip):
    try:
        subprocess.run(["tcpdump", "-i", "eth0", "-w", f"forensics_{host_ip}.pcap", f"host {host_ip}"])
        print(f"Collecting forensic data for host {host_ip}.")
    except Exception as e:
        print(f"Failed to collect forensic data: {e}")

# Usage
compromised_host = "192.168.1.10"
isolate_host(compromised_host)
collect_forensic_data(compromised_host)
Summary: This script automates incident response actions by isolating a compromised host from the network and capturing forensic data.

86. File Integrity Monitoring Script

Description: Create a script to monitor file integrity by calculating and comparing hashes of critical files.

python
Copy code
import hashlib

# File Integrity Monitoring Script

def calculate_file_hash(file_path):
    sha256 = hashlib.sha256()
    with open(file_path, 'rb') as file:
        while True:
            data = file.read(65536)
            if not data:
                break
            sha256.update(data)
    return sha256.hexdigest()

def check_file_integrity(file_path, expected_hash):
    current_hash = calculate_file_hash(file_path)
    if current_hash == expected_hash:
        print(f"File {file_path} has not been tampered with.")
    else:
        print(f"File {file_path} has been modified!")

# Usage
critical_file = "important.doc"
expected_hash = "2a81071d6a00d2b505ee111a7a243db2cd91f42c26a1705b063db6a1d34310232"
check_file_integrity(critical_file, expected_hash)
Summary: This script calculates the hash of a critical file and compares it to an expected hash to monitor file integrity.

87. Threat Intelligence Feed Script

Description: Create a script to fetch and process threat intelligence feeds for IP addresses and domains.

python
Copy code
import requests

# Threat Intelligence Feed Script

def fetch_threat_feed(feed_url):
    try:
        response = requests.get(feed_url)
        if response.status_code == 200:
            data = response.text
            return data.split('\n')
        else:
            print(f"Failed to fetch feed: HTTP {response.status_code}")
            return []
    except Exception as e:
        print(f"Failed to fetch feed: {e}")
        return []

def process_threat_feed(feed_data):
    for entry in feed_data:
        if entry:
            ip_or_domain = entry.strip()
            analyze_threat(ip_or_domain)

def analyze_threat(ip_or_domain):
    # Add your threat analysis logic here
    print(f"Analyzing threat: {ip_or_domain}")

# Usage
threat_feed_url = "https://example.com/threat_feed.txt"
threat_data = fetch_threat_feed(threat_feed_url)
process_threat_feed(threat_data)
Summary: This script fetches threat intelligence feeds, processes the data, and analyzes potential threats based on IP addresses and domains.

These Python scripts can help automate tasks related to incident response, file integrity monitoring, and threat intelligence feed processing, making the work of a cybersecurity analyst more efficient.




User
give me examples
ChatGPT
Of course, here are more examples of Python scripts for a cybersecurity analyst:

88. Vulnerability Scanner Script

Description: Create a script to automate vulnerability scanning of a target system using a tool like Nessus.

python
Copy code
import os

# Vulnerability Scanner Script

def run_vulnerability_scan(target_ip, output_file):
    try:
        scan_command = f"nessuscli scan --hosts {target_ip} --output {output_file}"
        os.system(scan_command)
        print(f"Vulnerability scan completed. Results saved to {output_file}.")
    except Exception as e:
        print(f"Failed to run vulnerability scan: {e}")

# Usage
target_system = "192.168.1.100"
output_report = "vulnerability_report.pdf"
run_vulnerability_scan(target_system, output_report)
Summary: This script automates the execution of a vulnerability scan on a target system using Nessus.

89. Log Analysis Script

Description: Create a script to parse and analyze log files for suspicious activities.

python
Copy code
# Log Analysis Script

def analyze_logs(log_file):
    try:
        with open(log_file, 'r') as file:
            for line in file:
                if "ERROR" in line:
                    print(f"Found an error in the log: {line}")
                # Add more log analysis logic here
    except Exception as e:
        print(f"Failed to analyze logs: {e}")

# Usage
log_file_path = "/var/log/app.log"
analyze_logs(log_file_path)
Summary: This script parses log files and identifies errors or other suspicious activities.

90. Password Policy Checker Script

Description: Create a script to check the compliance of user passwords with security policies.

python
Copy code
# Password Policy Checker Script

def check_password_policy(password):
    # Add password policy checks here
    if len(password) < 8:
        return "Password is too short"
    if not any(char.isupper() for char in password):
        return "Password must contain at least one uppercase letter"
    if not any(char.islower() for char in password):
        return "Password must contain at least one lowercase letter"
    if not any(char.isdigit() for char in password):
        return "Password must contain at least one digit"
    return "Password meets policy requirements"

# Usage
user_password = "SecureP@ssw0rd"
policy_result = check_password_policy(user_password)
print(policy_result)
Summary: This script checks if a user's password complies with security policy requirements.

91. Certificate Expiry Checker Script

Description: Create a script to check the expiration dates of SSL certificates.

python
Copy code
import ssl
import datetime

# Certificate Expiry Checker Script

def check_certificate_expiry(hostname, port):
    try:
        cert = ssl.get_server_certificate((hostname, port))
        x509 = ssl.PEM_cert_to_DER_cert(cert)
        cert = ssl.DER_cert_to_PEM_cert(x509)
        x509 = ssl.PEM_cert_to_DER_cert(cert)
        x509 = ssl.DER_cert_to_PEM_cert(x509)
        cert = ssl.DER_cert_to_PEM_cert(x509)
        cert_info = ssl.cert_time_to_seconds(cert)
        expiry_date = datetime.datetime.utcfromtimestamp(cert_info)
        return expiry_date
    except Exception as e:
        print(f"Failed to check certificate expiry: {e}")
        return None

# Usage
target_host = "example.com"
port = 443
expiry_date = check_certificate_expiry(target_host, port)
if expiry_date:
    print(f"The SSL certificate expires on: {expiry_date}")
Summary: This script checks the expiration date of an SSL certificate for a given hostname and port.

These Python scripts can assist cybersecurity analysts in automating tasks such as vulnerability scanning, log analysis, password policy checking, and certificate expiry checks, streamlining their work.




User
give me examples
ChatGPT
Certainly, here are more examples of Python scripts for a cybersecurity analyst:

92. Network Port Scanner Script

Description: Create a script to scan open ports on a target system using the socket library.

python
Copy code
import socket

# Network Port Scanner Script

def scan_ports(target_ip, ports):
    open_ports = []
    for port in ports:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        result = sock.connect_ex((target_ip, port))
        if result == 0:
            open_ports.append(port)
        sock.close()
    return open_ports

# Usage
target_system = "192.168.1.100"
common_ports = [20, 21, 22, 80, 443, 8080]
open_ports = scan_ports(target_system, common_ports)
print(f"Open ports on {target_system}: {open_ports}")
Summary: This script scans a range of ports on a target system to identify open ports.

93. Threat Feed Integration Script

Description: Create a script that integrates with threat intelligence feeds to check if a given IP address or domain is associated with known threats.

python
Copy code
import requests

# Threat Feed Integration Script

def check_threat_feed(ip_or_domain):
    threat_feed_url = f"https://api.threatintel.com/check?target={ip_or_domain}"
    try:
        response = requests.get(threat_feed_url)
        if response.status_code == 200:
            threat_data = response.json()
            if threat_data['is_threat']:
                return f"{ip_or_domain} is associated with known threats."
            else:
                return f"{ip_or_domain} is not associated with known threats."
    except Exception as e:
        print(f"Failed to check threat feed: {e}")
    return "Threat feed check failed."

# Usage
target_ip_or_domain = "example.com"
threat_status = check_threat_feed(target_ip_or_domain)
print(threat_status)
Summary: This script queries a threat feed API to check if a given IP address or domain is associated with known threats.

94. Network Traffic Capture Script

Description: Create a script to capture network traffic using a tool like tcpdump and analyze it.

python
Copy code
import os

# Network Traffic Capture Script

def capture_network_traffic(interface, output_file, duration):
    try:
        capture_command = f"tcpdump -i {interface} -w {output_file} -G {duration}"
        os.system(capture_command)
        print(f"Captured network traffic saved to {output_file}.")
    except Exception as e:
        print(f"Failed to capture network traffic: {e}")

# Usage
network_interface = "eth0"
output_capture_file = "captured_traffic.pcap"
capture_duration = 60  # Captures traffic for 60 seconds
capture_network_traffic(network_interface, output_capture_file, capture_duration)
Summary: This script captures network traffic on a specified interface for a duration and saves it to a capture file.

95. Digital Certificate Checker Script

Description: Create a script to check the validity and details of SSL certificates.

python
Copy code
import ssl
import OpenSSL.crypto

# Digital Certificate Checker Script

def check_ssl_certificate(hostname, port):
    try:
        context = ssl.create_default_context()
        with socket.create_connection((hostname, port)) as sock:
            with context.wrap_socket(sock, server_hostname=hostname) as ssock:
                cert = ssock.getpeercert(binary_form=True)
                x509 = OpenSSL.crypto.load_certificate(OpenSSL.crypto.FILETYPE_ASN1, cert)
                subject = x509.get_subject()
                issuer = x509.get_issuer()
                valid_from = x509.get_notBefore()
                valid_to = x509.get_notAfter()
                return {
                    "subject": dict(subject.get_components()),
                    "issuer": dict(issuer.get_components()),
                    "valid_from": valid_from,
                    "valid_to": valid_to,
                }
    except Exception as e:
        print(f"Failed to check SSL certificate: {e}")
    return None

# Usage
target_host = "example.com"
port = 443
certificate_details = check_ssl_certificate(target_host, port)
print(f"Certificate Details:\n{certificate_details}")
Summary: This script checks the validity and details of SSL certificates for a given hostname and port.

These Python scripts can be valuable tools for cybersecurity analysts to perform tasks such as network port scanning, threat feed integration, network traffic capture, and SSL certificate checking, enhancing their efficiency and capabilities.




User
give me examples
ChatGPT
Certainly, here are more examples of Python scripts for a cybersecurity analyst:

96. Log Analysis Script

Description: Create a script that analyzes log files, such as Apache or Nginx access logs, to identify suspicious or malicious activities.

python
Copy code
# Log Analysis Script

def analyze_access_logs(log_file):
    suspicious_ips = set()
    with open(log_file, 'r') as file:
        for line in file:
            parts = line.split()
            ip_address = parts[0]
            request = parts[6]

            if "wp-login" in request:
                suspicious_ips.add(ip_address)

    return suspicious_ips

# Usage
log_file_path = "/var/log/apache/access.log"
suspicious_ip_addresses = analyze_access_logs(log_file_path)
print(f"Suspicious IP addresses: {suspicious_ip_addresses}")
Summary: This script parses access logs to identify IP addresses associated with suspicious activities, like probing for WordPress login pages.

97. Password Strength Checker Script

Description: Create a script to check the strength of user passwords against common password policies.

python
Copy code
# Password Strength Checker Script

import re

def check_password_strength(password):
    # Define password policy rules
    min_length = 8
    has_lowercase = bool(re.search(r'[a-z]', password))
    has_uppercase = bool(re.search(r'[A-Z]', password))
    has_digit = bool(re.search(r'[0-9]', password))
    has_special_char = bool(re.search(r'[!@#$%^&*]', password))

    # Check against policy rules
    if (
        len(password) >= min_length and
        has_lowercase and
        has_uppercase and
        has_digit and
        has_special_char
    ):
        return "Password meets policy requirements."
    else:
        return "Password does not meet policy requirements."

# Usage
user_password = "SecureP@ssw0rd123"
password_strength = check_password_strength(user_password)
print(password_strength)
Summary: This script checks if a user's password meets specific policy requirements, such as length, character types, and special characters.

98. Web Application Vulnerability Scanner Script

Description: Create a script to scan a web application for common vulnerabilities, such as cross-site scripting (XSS) or SQL injection.

python
Copy code
# Web Application Vulnerability Scanner Script

import requests
from bs4 import BeautifulSoup

def scan_web_application(url):
    vulnerabilities = []

    # Retrieve web page content
    response = requests.get(url)
    if response.status_code == 200:
        page_content = response.text
        soup = BeautifulSoup(page_content, 'html.parser')

        # Check for potential vulnerabilities (e.g., XSS)
        if "alert(document.cookie)" in page_content:
            vulnerabilities.append("XSS vulnerability detected.")
        # Add checks for other vulnerabilities as needed

    return vulnerabilities

# Usage
web_app_url = "https://example.com"
vulnerabilities_found = scan_web_application(web_app_url)
print(f"Vulnerabilities found: {vulnerabilities_found}")
Summary: This script scans a web application for common vulnerabilities by analyzing its HTML content for potential issues.

99. Hash Cracker Script

Description: Create a script to crack hashed passwords using common password dictionaries.

python
Copy code
# Hash Cracker Script

import hashlib

def crack_password_hash(hash_to_crack, password_list):
    for password in password_list:
        if hashlib.md5(password.encode()).hexdigest() == hash_to_crack:
            return f"Password cracked: {password}"
    return "Password not found in the list."

# Usage
hashed_password = "5f4dcc3b5aa765d61d8327deb882cf99"  # Hash of "password"
password_dictionary = ["password", "letmein", "admin", "123456"]
cracked_password = crack_password_hash(hashed_password, password_dictionary)
print(cracked_password)
Summary: This script attempts to crack a hashed password using a list of common passwords.

100. Security Information and Event Management (SIEM) Log Aggregator Script

Description: Create a script to aggregate log data from various sources into a SIEM system for centralized monitoring and analysis.

python
Copy code
# SIEM Log Aggregator Script

def aggregate_logs(log_sources, siem_system):
    for source in log_sources:
        log_data = fetch_logs_from_source(source)
        siem_system.send_logs(log_data)
    
    return "Logs successfully aggregated."

# Usage
log_sources = ["firewall_logs", "server_logs", "network_logs"]
siem_instance = SIEM("siem.example.com")
result = aggregate_logs(log_sources, siem_instance)
print(result)
Summary: This script collects logs from various sources, such as firewalls, servers, and network devices, and sends them to a SIEM system for analysis.

These Python scripts are valuable tools for a cybersecurity analyst to perform tasks like log analysis, password strength checking, web application vulnerability scanning, password hash cracking, and log aggregation, which can enhance their capabilities in enhancing security.




User
give me more examples like this as SOC Analyst
ChatGPT
Certainly, here are more examples of Python scripts for a Security Operations Center (SOC) Analyst:

101. Incident Ticketing Automation Script

Description: Create a script to automate the generation of incident tickets for security events that require investigation.

python
Copy code
# Incident Ticketing Automation Script

import requests

def create_incident_ticket(event_details, ticketing_system_url, auth_token):
    # Format incident details
    incident_summary = event_details['summary']
    incident_description = event_details['description']

    # Create an incident ticket
    ticket_data = {
        'summary': incident_summary,
        'description': incident_description,
        'status': 'Open',
        'priority': 'High',
    }

    headers = {
        'Authorization': f'Bearer {auth_token}',
        'Content-Type': 'application/json',
    }

    response = requests.post(ticketing_system_url, json=ticket_data, headers=headers)

    if response.status_code == 201:
        return "Incident ticket created successfully."
    else:
        return f"Error creating incident ticket: {response.status_code}"

# Usage
event_info = {
    'summary': 'Security Event - Unauthorized Access',
    'description': 'A user attempted unauthorized access to a critical server.'
}
ticketing_url = 'https://ticketing.example.com/api/incidents'
api_token = 'your-api-token'
result = create_incident_ticket(event_info, ticketing_url, api_token)
print(result)
Summary: This script automates the creation of incident tickets in a ticketing system for security events requiring investigation.

102. Threat Intelligence Feed Integration Script

Description: Create a script that integrates with threat intelligence feeds to fetch and analyze the latest threat data.

python
Copy code
# Threat Intelligence Feed Integration Script

import requests

def fetch_threat_intelligence_feed(feed_url):
    response = requests.get(feed_url)

    if response.status_code == 200:
        threat_data = response.json()
        # Analyze threat data and take appropriate actions
        return "Threat feed data fetched and analyzed."
    else:
        return f"Failed to fetch threat feed: {response.status_code}"

# Usage
threat_feed_url = 'https://threatintel.example.com/feed'
result = fetch_threat_intelligence_feed(threat_feed_url)
print(result)
Summary: This script fetches and analyzes threat intelligence data from a feed source to stay updated on the latest threats.

103. Endpoint Security Health Checker Script

Description: Create a script that checks the health and compliance of endpoints by querying their security status.

python
Copy code
# Endpoint Security Health Checker Script

import requests

def check_endpoint_health(endpoint_url, auth_token):
    headers = {
        'Authorization': f'Bearer {auth_token}',
    }

    response = requests.get(endpoint_url, headers=headers)

    if response.status_code == 200:
        endpoint_status = response.json()
        # Analyze endpoint status and trigger alerts if necessary
        return "Endpoint security health checked."
    else:
        return f"Failed to check endpoint health: {response.status_code}"

# Usage
endpoint_url = 'https://endpoint.example.com/health'
api_token = 'your-api-token'
result = check_endpoint_health(endpoint_url, api_token)
print(result)
Summary: This script queries the security status of endpoints, enabling the SOC analyst to monitor and maintain endpoint security.

104. Network Traffic Analyzer Script

Description: Create a script that captures and analyzes network traffic to detect suspicious or unauthorized activity.

python
Copy code
# Network Traffic Analyzer Script

import scapy

def analyze_network_traffic(interface, pcap_filename):
    packets = scapy.sniff(iface=interface, count=100)
    scapy.sniff(prn=analyze_packet, store=0, count=100)

def analyze_packet(packet):
    # Analyze packet content and trigger alerts if necessary
    print(f"Analyzing packet: {packet.summary()}")

# Usage
network_interface = 'eth0'
pcap_file = 'capture.pcap'
analyze_network_traffic(network_interface, pcap_file)
Summary: This script captures and analyzes network traffic using Scapy, helping the SOC analyst identify suspicious activities.

105. Vulnerability Scanner Integration Script

Description: Create a script to integrate with a vulnerability scanner to initiate scans and retrieve scan results.

python
Copy code
# Vulnerability Scanner Integration Script

import requests

def initiate_vulnerability_scan(target_url, scanner_api_key):
    headers = {
        'X-Api-Key': scanner_api_key,
    }

    scan_data = {
        'target': target_url,
        'scan_profile': 'full-scan',
    }

    response = requests.post('https://vulnscanner.example.com/api/scans', json=scan_data, headers=headers)

    if response.status_code == 201:
        scan_id = response.json()['scan_id']
        return f"Vulnerability scan initiated. Scan ID: {scan_id}"
    else:
        return f"Failed to initiate vulnerability scan: {response.status_code}"

# Usage
target_url = 'https://example.com'
api_key = 'your-scanner-api-key'
result = initiate_vulnerability_scan(target_url, api_key)
print(result)
Summary: This script integrates with a vulnerability scanner to initiate scans on target systems and retrieves scan results for analysis.

These Python scripts are useful for SOC analysts in automating incident ticketing, integrating threat intelligence feeds, checking endpoint security health, analyzing network traffic, and interacting with vulnerability scanners, thereby enhancing their incident response and threat analysis capabilities.




User
give me more examples
ChatGPT
Certainly, here are more examples of Python scripts for a Security Operations Center (SOC) Analyst:

106. Log Analysis Script

Description: Create a script to parse and analyze log files from various sources, searching for signs of security incidents.

python
Copy code
# Log Analysis Script

import re

def analyze_logs(log_file):
    with open(log_file, 'r') as file:
        logs = file.readlines()

    security_incidents = []
    for log in logs:
        # Perform regex matching or keyword searches to identify incidents
        if re.search(r'Security incident', log) or 'Unauthorized access' in log:
            security_incidents.append(log)

    return security_incidents

# Usage
log_file_path = 'security.log'
incidents = analyze_logs(log_file_path)
for incident in incidents:
    print(incident)
Summary: This script parses log files, searching for predefined security incident patterns or keywords and then reports any findings.

107. Suspicious File Detector Script

Description: Create a script to scan and detect suspicious files on endpoints by comparing file hashes to known malware signatures.

python
Copy code
# Suspicious File Detector Script

import hashlib

def detect_suspicious_files(directory_path, signature_database):
    suspicious_files = []
    for root, dirs, files in os.walk(directory_path):
        for file in files:
            file_path = os.path.join(root, file)
            file_hash = hash_file(file_path)
            if file_hash in signature_database:
                suspicious_files.append(file_path)

    return suspicious_files

def hash_file(file_path):
    sha256 = hashlib.sha256()
    with open(file_path, 'rb') as f:
        while True:
            data = f.read(65536)
            if not data:
                break
            sha256.update(data)
    return sha256.hexdigest()

# Usage
endpoint_directory = '/path/to/endpoint'
known_malware_signatures = ['hash1', 'hash2', 'hash3']
suspicious = detect_suspicious_files(endpoint_directory, known_malware_signatures)
for file in suspicious:
    print(f"Suspicious file found: {file}")
Summary: This script scans an endpoint directory for files that match known malware signatures and reports any suspicious files found.

108. User Account Lock Script

Description: Create a script to monitor user account login attempts and lock accounts after a specified number of failed attempts.

python
Copy code
# User Account Lock Script

import time

failed_login_attempts = {}

def monitor_login_attempts(username, max_attempts, lock_duration):
    if username not in failed_login_attempts:
        failed_login_attempts[username] = {'attempts': 0, 'locked_until': 0}

    if failed_login_attempts[username]['locked_until'] > time.time():
        return f"Account locked. Try again after {failed_login_attempts[username]['locked_until']}"

    failed_login_attempts[username]['attempts'] += 1
    if failed_login_attempts[username]['attempts'] >= max_attempts:
        failed_login_attempts[username]['locked_until'] = time.time() + lock_duration
        return f"Account locked for {lock_duration} seconds due to too many failed login attempts."

    return "Login successful."

# Usage
username = 'user123'
max_login_attempts = 3
lock_duration_seconds = 300
for _ in range(5):
    result = monitor_login_attempts(username, max_login_attempts, lock_duration_seconds)
    print(result)
    time.sleep(60)
Summary: This script monitors user login attempts and locks accounts temporarily after a defined number of failed attempts.

109. Phishing Email Analyzer Script

Description: Create a script to analyze email headers and content to identify potential phishing emails.

python
Copy code
# Phishing Email Analyzer Script

import email
import re

def analyze_phishing_email(email_message):
    sender = email_message['From']
    subject = email_message['Subject']
    content = email_message.get_payload()

    if re.search(r'paypal\.com', sender, re.I) and 'Your account has been compromised' in subject:
        return "Potential phishing email from PayPal detected."

    if 'Urgent: Verify your account' in subject and 'Click the link below to verify' in content:
        return "Suspicious email with a verification link detected."

    return "No phishing indicators found."

# Usage
raw_email = """From: paypal@example.com
Subject: Your account has been compromised
Date: Thu, 01 Jan 2023 12:00:00 +0000

Dear Customer,

Your PayPal account has been compromised. Click the link to reset your password.

Regards,
PayPal Team
"""

email_message = email.message_from_string(raw_email)
result = analyze_phishing_email(email_message)
print(result)
Summary: This script examines email headers and content to identify potential phishing emails based on predefined patterns.

110. Patch Management Script

Description: Create a script to automate the process of applying security patches to software and operating systems on endpoints.

python
Copy code
# Patch Management Script

import subprocess

def apply_security_patches():
    # Use a package manager (e.g., apt, yum, or Windows Update) to update software
    subprocess.run(['apt', 'update'])
    subprocess.run(['apt', 'upgrade', '-y'])

# Usage
apply_security_patches()
Summary: This script automates the process of updating and applying security patches to software and operating systems on endpoints.

These Python scripts are designed to assist SOC analysts in log analysis, detecting suspicious files, monitoring login attempts, analyzing phishing emails, managing patches, and improving security incident response.




User
give me more examples
ChatGPT
Certainly, here are more examples of Python scripts for a Security Operations Center (SOC) Analyst:

111. Network Traffic Analysis Script

Description: Create a script to capture and analyze network traffic to detect and report anomalies.

python
Copy code
# Network Traffic Analysis Script

import pyshark

def analyze_network_traffic(interface, filter, duration):
    capture = pyshark.LiveCapture(interface=interface, display_filter=filter, duration=duration)
    for packet in capture.sniff_continuously():
        # Analyze network traffic here
        if 'suspicious_pattern' in packet:
            print("Suspicious network traffic detected:")
            print(packet)
            
# Usage
interface = 'eth0'
filter = 'tcp port 80'
duration = 60
analyze_network_traffic(interface, filter, duration)
Summary: This script uses the PyShark library to capture and analyze network traffic, helping detect suspicious patterns.

112. Security Alert Notification Script

Description: Create a script to monitor security alerts and send notifications via email or other channels.

python
Copy code
# Security Alert Notification Script

import smtplib
from email.mime.text import MIMEText

def send_alert_email(receiver, subject, message):
    sender_email = 'your_email@example.com'
    sender_password = 'your_password'
    smtp_server = 'smtp.example.com'
    smtp_port = 587

    msg = MIMEText(message)
    msg['Subject'] = subject
    msg['From'] = sender_email
    msg['To'] = receiver

    with smtplib.SMTP(smtp_server, smtp_port) as server:
        server.starttls()
        server.login(sender_email, sender_password)
        server.sendmail(sender_email, receiver, msg.as_string())

# Usage
receiver = 'admin@example.com'
subject = 'Security Alert'
message = 'A potential security incident has been detected. Please investigate.'
send_alert_email(receiver, subject, message)
Summary: This script sends email notifications for security alerts to specified recipients.

113. Threat Intelligence Integration Script

Description: Create a script to integrate threat intelligence feeds and enrich indicators of compromise (IoCs).

python
Copy code
# Threat Intelligence Integration Script

import requests

def get_threat_intelligence_data(ioc):
    threat_intel_api = 'https://api.threatintel.com'
    api_key = 'your_api_key'

    headers = {
        'Authorization': f'Bearer {api_key}'
    }

    response = requests.get(f'{threat_intel_api}/ioc/{ioc}', headers=headers)

    if response.status_code == 200:
        return response.json()
    else:
        return None

# Usage
ioc = 'example_ip_address'
threat_data = get_threat_intelligence_data(ioc)
if threat_data:
    print(f"Threat Intelligence Data for {ioc}: {threat_data}")
else:
    print("No threat intelligence data found.")
Summary: This script queries a threat intelligence API to enrich IoCs with additional information.

114. Network Port Scanner Script

Description: Create a script to scan network hosts for open ports and services.

python
Copy code
# Network Port Scanner Script

import socket

def scan_ports(host, ports):
    open_ports = []

    for port in ports:
        try:
            with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
                s.settimeout(2)
                s.connect((host, port))
                open_ports.append(port)
        except:
            pass

    return open_ports

# Usage
target_host = 'example.com'
target_ports = range(1, 1025)
open_ports = scan_ports(target_host, target_ports)
print(f"Open ports on {target_host}: {open_ports}")
Summary: This script scans network hosts to identify open ports, which can help identify potential security risks.

115. Endpoint Detection and Response (EDR) Data Collector Script

Description: Create a script to collect endpoint data, such as process information, from multiple systems and centralize it for analysis.

python
Copy code
# EDR Data Collector Script

import os
import shutil

def collect_endpoint_data(agents, destination):
    for agent in agents:
        data_path = f'/path/to/agent_data/{agent}'
        if os.path.exists(data_path):
            shutil.copytree(data_path, os.path.join(destination, agent))

# Usage
agent_list = ['agent1', 'agent2', 'agent3']
collection_destination = '/central_data_storage'
collect_endpoint_data(agent_list, collection_destination)
Summary: This script collects data from multiple endpoint agents and centralizes it for analysis.

These Python scripts are designed to assist SOC analysts in network traffic analysis, security alert notifications, threat intelligence integration, network port scanning, and EDR data collection, helping improve incident detection and response capabilities.




User
give me more examples
ChatGPT
Of course! Here are more examples of Python scripts for a Security Operations Center (SOC) Analyst:

116. Log Analysis Script

Description: Create a script to parse and analyze log files from various sources like firewalls, servers, and applications.

python
Copy code
# Log Analysis Script

import re

def analyze_logs(log_file):
    with open(log_file, 'r') as file:
        for line in file:
            # Analyze log data
            if re.search('suspicious_pattern', line):
                print("Suspicious activity detected:")
                print(line)

# Usage
log_file_path = '/var/log/app.log'
analyze_logs(log_file_path)
Summary: This script helps SOC analysts parse and analyze log files for security incidents.

117. Network Enumeration Script

Description: Create a script to enumerate network resources, such as hosts, services, and shares.

python
Copy code
# Network Enumeration Script

import nmap

def enumerate_network(hosts, ports):
    scanner = nmap.PortScanner()
    scanner.scan(hosts, ports)

    for host in scanner.all_hosts():
        print(f"Host: {host}")
        for proto in scanner[host].all_protocols():
            ports = scanner[host][proto].keys()
            for port in ports:
                state = scanner[host][proto][port]['state']
                print(f"Port: {port} - {state}")

# Usage
target_hosts = '192.168.0.1-20'
target_ports = '22,80,443'
enumerate_network(target_hosts, target_ports)
Summary: This script uses the Nmap library to scan and enumerate network resources.

118. Threat Hunting Script

Description: Create a script to proactively search for signs of compromise or threats within the network.

python
Copy code
# Threat Hunting Script

import elasticsearch
from elasticsearch_dsl import Search

def hunt_for_threats(indicator):
    es = elasticsearch.Elasticsearch(['https://elasticsearch-server:9200'])
    search = Search(using=es, index='logs-*') \
        .filter('term', indicator=indicator) \
        .filter('range', timestamp={'gte': 'now-7d'})

    response = search.execute()
    for hit in response:
        print(f"Potential threat found: {hit.to_dict()}")

# Usage
ioc_to_hunt = 'suspicious_domain.com'
hunt_for_threats(ioc_to_hunt)
Summary: This script queries Elasticsearch for logs containing indicators of compromise (IoCs) to proactively hunt for threats.

119. Incident Reporting Script

Description: Create a script to generate and send incident reports to stakeholders.

python
Copy code
# Incident Reporting Script

import os
from jinja2 import Environment, FileSystemLoader
import smtplib
from email.mime.text import MIMEText

def generate_report(incident_details, template_path, output_path):
    env = Environment(loader=FileSystemLoader(template_path))
    template = env.get_template('incident_report_template.html')
    report = template.render(incident=incident_details)

    with open(output_path, 'w') as file:
        file.write(report)

def send_report(report_path, recipient, subject):
    sender_email = 'your_email@example.com'
    sender_password = 'your_password'
    smtp_server = 'smtp.example.com'
    smtp_port = 587

    msg = MIMEText("Please find the attached incident report.")
    msg['Subject'] = subject
    msg['From'] = sender_email
    msg['To'] = recipient

    with smtplib.SMTP(smtp_server, smtp_port) as server:
        server.starttls()
        server.login(sender_email, sender_password)
        server.sendmail(sender_email, recipient, msg.as_string())

# Usage
incident_details = {
    'incident_type': 'Data Breach',
    'incident_date': '2023-10-01',
    'description': 'Sensitive data was exposed due to a misconfiguration.',
    'actions_taken': 'Isolated affected systems, patched the vulnerability, notified affected users.'
}
template_path = '/path/to/templates'
output_path = '/path/to/output/report.html'
recipient = 'stakeholder@example.com'
email_subject = 'Incident Report - Data Breach'
generate_report(incident_details, template_path, output_path)
send_report(output_path, recipient, email_subject)
Summary: This script generates an incident report from a template and sends it to the specified recipient.

120. Data Loss Prevention (DLP) Script

Description: Create a script to monitor and enforce data loss prevention policies by scanning files and network traffic for sensitive information.

python
Copy code
# Data Loss Prevention Script

import os
import re

def scan_files_for_sensitive_data(directory, pattern):
    sensitive_files = []

    for root, dirs, files in os.walk(directory):
        for file in files:
            file_path = os.path.join(root, file)
            with open(file_path, 'r') as f:
                data = f.read()
                if re.search(pattern, data):
                    sensitive_files.append(file_path)

    return sensitive_files

# Usage
directory_to_scan = '/path/to/data'
sensitive_data_pattern = 'credit_card_number: \d{4}-\d{4}-\d{4}-\d{4}'
found_sensitive_files = scan_files_for_sensitive_data(directory_to_scan, sensitive_data_pattern)
print("Sensitive data found in these files:")
for file in found_sensitive_files:
    print(file)
Summary: This script scans files for sensitive data using regular expressions.

These Python scripts are designed to assist SOC analysts with log analysis, network enumeration, threat hunting, incident reporting, and data loss prevention, enhancing security monitoring and incident response capabilities.




User
give me more examples
ChatGPT
Certainly! Here are more examples of Python scripts for a Security Operations Center (SOC) Analyst:

121. Security Incident Ticketing Script

Description: Create a script that generates and tracks security incident tickets.

python
Copy code
# Security Incident Ticketing Script

import requests
import json

def create_security_ticket(title, description, severity):
    ticket = {
        'title': title,
        'description': description,
        'severity': severity
    }

    headers = {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer your_api_token'
    }

    response = requests.post('https://ticketing-system.example.com/api/incidents', data=json.dumps(ticket), headers=headers)
    if response.status_code == 201:
        return "Incident ticket created successfully."
    else:
        return "Failed to create incident ticket."

# Usage
incident_title = "Unauthorized Access Attempt"
incident_description = "A user attempted unauthorized access to a critical server."
incident_severity = "High"
result = create_security_ticket(incident_title, incident_description, incident_severity)
print(result)
Summary: This script automates the creation of security incident tickets in a ticketing system.

122. IOC (Indicators of Compromise) Validation Script

Description: Create a script to validate known IOCs against network traffic or log data.

python
Copy code
# IOC Validation Script

import re

def validate_iocs(log_file, ioc_patterns):
    results = []

    with open(log_file, 'r') as file:
        for line in file:
            for pattern in ioc_patterns:
                if re.search(pattern, line):
                    results.append(f"IOC Match: {pattern}\nLog Line: {line}")

    return results

# Usage
log_file_path = '/var/log/app.log'
ioc_patterns = ['malicious_domain.com', 'md5:0123456789abcdef']
validation_results = validate_iocs(log_file_path, ioc_patterns)
print("IOC Validation Results:")
for result in validation_results:
    print(result)
Summary: This script checks log data for matches with known IOC patterns.

123. Certificate Expiry Checker Script

Description: Create a script that checks SSL/TLS certificate expiration dates for web servers.

python
Copy code
# Certificate Expiry Checker Script

import ssl
import socket
import datetime

def check_certificate_expiry(hostname, port):
    context = ssl.create_default_context()
    with socket.create_connection((hostname, port)) as sock:
        with context.wrap_socket(sock, server_hostname=hostname) as ssock:
            cert = ssock.getpeercert()
            cert_expiry_date = datetime.datetime.strptime(cert['notAfter'], '%b %d %H:%M:%S %Y %Z')
            days_until_expiry = (cert_expiry_date - datetime.datetime.now()).days

            if days_until_expiry <= 30:
                return f"Certificate for {hostname} will expire in {days_until_expiry} days."
            else:
                return f"Certificate for {hostname} is valid."

# Usage
web_server = 'example.com'
web_server_port = 443
result = check_certificate_expiry(web_server, web_server_port)
print(result)
Summary: This script checks SSL/TLS certificate expiration for web servers and notifies if certificates are about to expire.

124. DNS Query Monitor Script

Description: Create a script to monitor DNS queries on the network and identify suspicious domains.

python
Copy code
# DNS Query Monitor Script

from scapy.all import sniff, DNSQR

def dns_query_monitor(pkt):
    if pkt.haslayer(DNSQR):
        domain = pkt[DNSQR].qname.decode('utf-8')
        if 'suspicious' in domain:
            print(f"Suspicious DNS query detected: {domain}")

# Usage
sniff(filter="udp port 53", prn=dns_query_monitor)
Summary: This script uses Scapy to monitor DNS queries and raises alerts for suspicious domains.

125. Firewall Rule Review Script

Description: Create a script to review and validate firewall rules against a security policy.

python
Copy code
# Firewall Rule Review Script

import csv

def review_firewall_rules(firewall_rules_csv, security_policy_csv):
    firewall_rules = []
    security_policy = []

    with open(firewall_rules_csv, 'r') as file:
        firewall_rules = list(csv.DictReader(file))

    with open(security_policy_csv, 'r') as file:
        security_policy = list(csv.DictReader(file))

    # Compare firewall rules with security policy
    for rule in firewall_rules:
        if rule not in security_policy:
            print(f"Firewall rule not found in security policy: {rule}")

# Usage
firewall_rules_csv = 'firewall_rules.csv'
security_policy_csv = 'security_policy.csv'
review_firewall_rules(firewall_rules_csv, security_policy_csv)
Summary: This script helps SOC analysts compare firewall rules against an established security policy.

These Python scripts are designed to assist SOC analysts with tasks like incident ticketing, IOC validation, certificate expiry checks, DNS query monitoring, and firewall rule reviews, enhancing security operations and incident response capabilities.




User
give me more examples
ChatGPT
Certainly! Here are more examples of Python scripts for a Security Operations Center (SOC) Analyst:

126. Malware Signature Scanner

Description: Create a script that scans files for known malware signatures.

python
Copy code
# Malware Signature Scanner

import hashlib

def scan_file_for_malware(file_path):
    known_signatures = {
        '4a99a9bfc2d16e23c5b8782d796c0553': 'Trojan.Win32.Generic',
        '16d60efb6f4ac38b02e6f7e1a61052df': 'Worm.Mydoom',
        # Add more known malware signatures here
    }

    with open(file_path, 'rb') as file:
        content = file.read()
        file_hash = hashlib.md5(content).hexdigest()

        if file_hash in known_signatures:
            return f"Malware Detected: {known_signatures[file_hash]}"
        else:
            return "No malware detected."

# Usage
file_to_scan = 'suspicious_file.exe'
result = scan_file_for_malware(file_to_scan)
print(result)
Summary: This script scans files for known malware signatures using MD5 hashes.

127. Network Flow Analyzer

Description: Create a script that analyzes network flows to detect anomalies.

python
Copy code
# Network Flow Analyzer

from scapy.all import sniff

def analyze_network_flows(pkt):
    # Add logic to analyze network flows
    pass

# Usage
sniff(filter="tcp and port 80", prn=analyze_network_flows)
Summary: This script uses Scapy to capture and analyze network flows for anomalies.

128. Log File Anomaly Detector

Description: Create a script that analyzes log files and detects anomalies in log entries.

python
Copy code
# Log File Anomaly Detector

import re

def detect_log_anomalies(log_file):
    pattern = r'ERROR|WARNING'
    anomalies = []

    with open(log_file, 'r') as file:
        for line in file:
            if re.search(pattern, line):
                anomalies.append(line)

    return anomalies

# Usage
log_file_path = 'app.log'
anomalies = detect_log_anomalies(log_file_path)
print("Log Anomalies:")
for anomaly in anomalies:
    print(anomaly)
Summary: This script scans log files for error and warning messages to detect anomalies.

129. SIEM Integration Script

Description: Create a script to integrate with a Security Information and Event Management (SIEM) system to send alerts.

python
Copy code
# SIEM Integration Script

import requests
import json

def send_alert_to_siem(event_data):
    headers = {'Content-Type': 'application/json'}
    siem_url = 'https://siem.example.com/api/alerts'
    response = requests.post(siem_url, data=json.dumps(event_data), headers=headers)

    if response.status_code == 201:
        return "Alert sent to SIEM."
    else:
        return "Failed to send alert."

# Usage
event_data = {
    'timestamp': '2023-10-10T12:00:00',
    'event_type': 'SecurityAlert',
    'description': 'Potential intrusion detected.',
    'source_ip': '192.168.1.100',
}
result = send_alert_to_siem(event_data)
print(result)
Summary: This script sends security alerts to a SIEM system for further analysis.

130. Password Policy Checker

Description: Create a script that checks user passwords against a defined password policy.

python
Copy code
# Password Policy Checker

import re

def check_password_policy(password):
    policy = re.compile(r'^(?=.*[A-Z])(?=.*[a-z])(?=.*\d)(?=.*[@#$%^&+=])(?!.*\s).{8,16}$')

    if policy.match(password):
        return "Password complies with the policy."
    else:
        return "Password does not meet the policy requirements."

# Usage
user_password = 'SecureP@ss1'
result = check_password_policy(user_password)
print(result)
Summary: This script checks user passwords for compliance with a defined password policy.

These Python scripts can assist SOC analysts in various tasks, including malware signature scanning, network flow analysis, log file anomaly detection, SIEM integration, and password policy checking, to enhance security monitoring and incident detection capabilities.




User
give me more examples
ChatGPT
Certainly! Here are more Python script examples for a Security Operations Center (SOC) Analyst:

131. Vulnerability Scanner Integration

Description: Create a script to integrate with a vulnerability scanner to automate vulnerability assessments.

python
Copy code
# Vulnerability Scanner Integration

import requests
import json

def run_vulnerability_scan(target):
    scanner_url = 'https://vuln-scanner.example.com/api/scan'
    scan_data = {
        'target': target,
        'scan_type': 'Full',
    }
    headers = {'Content-Type': 'application/json'}

    response = requests.post(scanner_url, data=json.dumps(scan_data), headers=headers)

    if response.status_code == 202:
        return "Vulnerability scan initiated."
    else:
        return "Failed to start the scan."

# Usage
target_host = 'example.com'
result = run_vulnerability_scan(target_host)
print(result)
Summary: This script integrates with a vulnerability scanner to initiate scans on target hosts.

132. Threat Intelligence Feed Parser

Description: Create a script that parses threat intelligence feeds and extracts indicators of compromise (IoCs).

python
Copy code
# Threat Intelligence Feed Parser

import requests

def parse_threat_intel_feed(feed_url):
    response = requests.get(feed_url)

    if response.status_code == 200:
        feed_data = response.json()
        indicators = feed_data.get('indicators', [])
        return indicators
    else:
        return "Failed to fetch the threat feed."

# Usage
threat_feed_url = 'https://threat-intel.example.com/feed.json'
indicators = parse_threat_intel_feed(threat_feed_url)
print("Indicators of Compromise:")
for indicator in indicators:
    print(indicator)
Summary: This script fetches and parses threat intelligence feeds for indicators of compromise.

133. Security Incident Ticket Generator

Description: Create a script to generate incident tickets for security incidents.

python
Copy code
# Security Incident Ticket Generator

import random
import string

def generate_incident_ticket():
    ticket_id = ''.join(random.choice(string.ascii_uppercase + string.digits) for _ in range(8))
    return f"Incident Ticket ID: {ticket_id}"

# Usage
ticket = generate_incident_ticket()
print(ticket)
Summary: This script generates unique incident ticket IDs for tracking security incidents.

134. Disk Space Monitor

Description: Create a script to monitor disk space on critical servers and send alerts when space is low.

python
Copy code
# Disk Space Monitor

import psutil
import smtplib

def check_disk_space(server, threshold):
    usage = psutil.disk_usage(server)
    if usage.percent > threshold:
        send_alert(f"Low disk space on {server}: {usage.percent}% used")

def send_alert(message):
    server = 'smtp.example.com'
    port = 587
    sender = 'alerts@example.com'
    receiver = 'admin@example.com'
    password = 'your_password'
    
    subject = 'Disk Space Alert'
    body = message

    headers = f"From: {sender}\r\nTo: {receiver}\r\nSubject: {subject}\r\n"
    server = smtplib.SMTP(server, port)
    server.starttls()
    server.login(sender, password)
    server.sendmail(sender, receiver, headers + body)
    server.quit()

# Usage
server_to_monitor = '/'
threshold_percent = 90
check_disk_space(server_to_monitor, threshold_percent)
Summary: This script monitors disk space on a server and sends email alerts when disk usage exceeds a defined threshold.

135. Security Dashboard Data Fetcher

Description: Create a script to fetch security data for a dashboard, such as incident statistics and threat alerts.

python
Copy code
# Security Dashboard Data Fetcher

import requests

def fetch_security_data(api_url):
    response = requests.get(api_url)

    if response.status_code == 200:
        security_data = response.json()
        return security_data
    else:
        return "Failed to fetch security data."

# Usage
dashboard_api_url = 'https://security-dashboard.example.com/api/data'
security_data = fetch_security_data(dashboard_api_url)
print("Security Dashboard Data:")
print(security_data)
Summary: This script fetches security data from an API to populate a security dashboard.

These Python scripts can assist SOC analysts in tasks such as vulnerability scanning, threat feed parsing, incident ticket generation, disk space monitoring, and security dashboard data fetching, streamlining security operations and incident response.




User
give me more examples
ChatGPT
Certainly! Here are more Python script examples for a Security Operations Center (SOC) Analyst:

136. SIEM Log Enrichment

Description: Create a script to enrich Security Information and Event Management (SIEM) logs with additional contextual information.

python
Copy code
# SIEM Log Enrichment

import requests
import json

def enrich_siem_log(log_entry):
    ip_address = log_entry['source_ip']
    geo_info = get_geolocation(ip_address)
    log_entry['geolocation'] = geo_info
    return log_entry

def get_geolocation(ip):
    api_url = f'https://geoip.example.com/api/{ip}'
    response = requests.get(api_url)

    if response.status_code == 200:
        geo_data = response.json()
        return geo_data
    else:
        return "Failed to retrieve geolocation data."

# Usage
siem_log_entry = {
    'timestamp': '2023-05-15 14:30:00',
    'source_ip': '192.168.1.100',
    'event_type': 'Login Failure',
}

enriched_log = enrich_siem_log(siem_log_entry)
print("Enriched SIEM Log:")
print(json.dumps(enriched_log, indent=4))
Summary: This script enriches SIEM log entries with geolocation information based on the source IP address.

137. Phishing Email Analysis

Description: Create a script to analyze phishing emails, extract URLs, and check them against threat intelligence feeds.

python
Copy code
# Phishing Email Analysis

import re
import requests

def analyze_phishing_email(email_content, threat_feeds):
    urls = re.findall('https?://(?:[-\w.]|(?:%[\da-fA-F]{2}))+', email_content)
    suspicious_urls = []

    for url in urls:
        if is_url_malicious(url, threat_feeds):
            suspicious_urls.append(url)

    return suspicious_urls

def is_url_malicious(url, threat_feeds):
    for feed in threat_feeds:
        if url in feed:
            return True
    return False

# Usage
phishing_email = "Suspicious email with a malicious link: https://evil-site.com"
threat_intel_feeds = ["https://threatfeed1.example.com", "https://threatfeed2.example.com"]

suspicious_urls = analyze_phishing_email(phishing_email, threat_intel_feeds)
print("Suspicious URLs:")
print(suspicious_urls)
Summary: This script analyzes a phishing email, extracts URLs, and checks them against known threat intelligence feeds for malicious links.

138. User Account Activity Monitor

Description: Create a script to monitor user account activities and detect unusual login patterns.

python
Copy code
# User Account Activity Monitor

import time

def monitor_user_activity(user_id, activity_threshold):
    activity_log = []
    while True:
        user_activity = get_user_activity(user_id)
        activity_log.append(user_activity)

        if len(activity_log) >= activity_threshold:
            if has_unusual_activity(activity_log):
                alert_security_team(user_id)
            activity_log.clear()

        time.sleep(60)  # Check every minute

def get_user_activity(user_id):
    # Implement code to retrieve user activity from logs or APIs
    pass

def has_unusual_activity(activity_log):
    # Implement logic to detect unusual activity
    pass

def alert_security_team(user_id):
    # Implement code to alert the security team
    pass

# Usage
user_to_monitor = 'user123'
activity_threshold = 5  # Check every 5 minutes
monitor_user_activity(user_to_monitor, activity_threshold)
Summary: This script continuously monitors user account activity and alerts the security team if unusual patterns are detected.

139. Firewall Rule Management

Description: Create a script to manage firewall rules, allowing SOC analysts to add or remove rules easily.

python
Copy code
# Firewall Rule Management

import subprocess

def add_firewall_rule(rule):
    command = f"firewall-cmd --add-rule='{rule}'"
    return run_firewall_command(command)

def remove_firewall_rule(rule):
    command = f"firewall-cmd --remove-rule='{rule}'"
    return run_firewall_command(command)

def run_firewall_command(command):
    try:
        subprocess.run(command, shell=True, check=True)
        return "Firewall rule updated successfully."
    except subprocess.CalledProcessError as e:
        return f"Failed to update firewall rule: {e}"

# Usage
new_firewall_rule = "port=8080/tcp"
result = add_firewall_rule(new_firewall_rule)
print(result)

rule_to_remove = "port=8080/tcp"
result = remove_firewall_rule(rule_to_remove)
print(result)
Summary: This script allows SOC analysts to add and remove firewall rules easily using firewall-cmd commands.

140. Incident Response Workflow Tracker

Description: Create a script to track and manage the incident response workflow, including task assignments and progress.

python
Copy code
# Incident Response Workflow Tracker

class Incident:
    def __init__(self, title, description, status):
        self.title = title
        self.description = description
        self.status = status

class IncidentTracker:
    def __init__(self):
        self.incidents = []

    def add_incident(self, title, description):
        incident = Incident(title, description, "Open")
        self.incidents.append(incident)

    def assign_task(self, incident_title, task_description, assignee):
        for incident in self.incidents:
            if incident.title == incident_title:
                incident.status = "In Progress"
                incident.task = task_description
                incident.assignee = assignee

    def resolve_incident(self, incident_title):
        for incident in self.incidents:
            if incident.title == incident_title:
                incident.status = "Resolved"

    def list_incidents(self):
        return [(incident.title, incident.status) for incident in self.incidents]

# Usage
tracker = IncidentTracker()
tracker.add_incident("Data Breach", "Unauthorized access to sensitive data.")
tracker.assign_task("Data Breach", "Investigate the access logs.", "Analyst123")
tracker.resolve_incident("Data Breach")

incidents = tracker.list_incidents()
print("Current Incidents:")
for incident in incidents:
    print(f"Title: {incident[0]}, Status: {incident[1]}")
Summary: This script tracks and manages the incident response workflow, allowing SOC analysts to add, assign tasks, and resolve incidents.

These Python scripts are designed to help SOC analysts streamline various tasks, from SIEM log enrichment and phishing email analysis to user account activity monitoring, firewall rule management, and incident response workflow tracking.




User
give me more examples
ChatGPT
Of course! Here are additional Python script examples for a Security Operations Center (SOC) Analyst:

141. Log Aggregation and Analysis

Description: Create a script to aggregate and analyze logs from multiple sources, allowing SOC analysts to quickly identify security incidents.

python
Copy code
# Log Aggregation and Analysis

import time

def aggregate_logs(log_sources):
    aggregated_logs = []

    while True:
        for source in log_sources:
            log_entry = get_log_entry(source)
            if log_entry:
                aggregated_logs.append(log_entry)

        if len(aggregated_logs) > 10:  # Analyze when there are sufficient logs
            analyze_logs(aggregated_logs)
            aggregated_logs.clear()

        time.sleep(60)  # Check every minute

def get_log_entry(log_source):
    # Implement code to retrieve log entries from various sources
    pass

def analyze_logs(log_entries):
    # Implement security analysis on aggregated logs
    pass

# Usage
log_sources = ['source1.log', 'source2.log', 'source3.log']
aggregate_logs(log_sources)
Summary: This script aggregates logs from various sources and triggers log analysis when a sufficient number of logs are available.

142. File Integrity Monitoring

Description: Create a script to monitor critical system files for any unauthorized changes, helping detect potential intrusions.

python
Copy code
# File Integrity Monitoring

import os
import hashlib
import time

def monitor_files(directory, file_extensions):
    monitored_files = discover_monitored_files(directory, file_extensions)
    file_hashes = {}

    while True:
        for file_path in monitored_files:
            file_hash = calculate_file_hash(file_path)

            if file_path in file_hashes and file_hash != file_hashes[file_path]:
                alert_security_team(file_path)

            file_hashes[file_path] = file_hash

        time.sleep(600)  # Check every 10 minutes

def discover_monitored_files(directory, file_extensions):
    monitored_files = []
    for root, dirs, files in os.walk(directory):
        for file in files:
            if file.endswith(tuple(file_extensions)):
                monitored_files.append(os.path.join(root, file))
    return monitored_files

def calculate_file_hash(file_path):
    hasher = hashlib.sha256()
    with open(file_path, 'rb') as f:
        while True:
            data = f.read(65536)
            if not data:
                break
            hasher.update(data)
    return hasher.hexdigest()

def alert_security_team(file_path):
    # Implement code to alert the security team about file changes
    pass

# Usage
directory_to_monitor = '/var/www/html'
file_extensions_to_monitor = ('.php', '.html')
monitor_files(directory_to_monitor, file_extensions_to_monitor)
Summary: This script continuously monitors critical system files for changes and alerts the security team if unauthorized modifications are detected.

143. Threat Intelligence Feed Integration

Description: Create a script to fetch threat intelligence feeds, parse the data, and check if any indicators of compromise (IOCs) match the organization's systems.

python
Copy code
# Threat Intelligence Feed Integration

import requests

def fetch_threat_intelligence(feed_url):
    response = requests.get(feed_url)

    if response.status_code == 200:
        threat_data = response.json()
        return threat_data
    else:
        return None

def check_iocs(threat_data, organization_systems):
    matched_iocs = []

    for ioc in threat_data['indicators']:
        if ioc['value'] in organization_systems:
            matched_iocs.append(ioc)

    return matched_iocs

# Usage
threat_feed_url = 'https://threatfeed.example.com/feed.json'
organization_systems = ['192.168.1.10', 'example.com', 'file.exe']

threat_data = fetch_threat_intelligence(threat_feed_url)

if threat_data:
    matched_iocs = check_iocs(threat_data, organization_systems)
    print("Matched IOCs:")
    for ioc in matched_iocs:
        print(f"Indicator: {ioc['value']}, Type: {ioc['type']}")
else:
    print("Failed to fetch threat intelligence feed.")
Summary: This script fetches a threat intelligence feed, checks if any IOCs match the organization's systems, and reports the matched IOCs.

144. DNS Query Analyzer

Description: Create a script to analyze DNS query logs for unusual patterns or potentially malicious domain names.

python
Copy code
# DNS Query Analyzer

import re

def analyze_dns_queries(log_file):
    suspicious_domains = []
    with open(log_file, 'r') as f:
        for line in f:
            if is_suspicious_dns_query(line):
                domain = extract_domain_name(line)
                suspicious_domains.append(domain)
    return suspicious_domains

def is_suspicious_dns_query(log_line):
    # Implement logic to detect suspicious DNS queries
    pass

def extract_domain_name(log_line):
    # Extract domain name from the log line
    pass

# Usage
dns_log_file = 'dns_queries.log'

suspicious_domains = analyze_dns_queries(dns_log_file)
print("Suspicious Domains:")
for domain in suspicious_domains:
    print(domain)
Summary: This script analyzes DNS query logs, detects suspicious queries, and extracts potentially malicious domain names.

These Python scripts provide SOC analysts with tools for log aggregation and analysis, file integrity monitoring, threat intelligence feed integration, and DNS query analysis. They help improve the security monitoring and incident detection capabilities of a Security Operations Center.




User
give me more examples
ChatGPT
Certainly! Here are more Python script examples for a Security Operations Center (SOC) Analyst:

145. User Account Monitoring

Description: Create a script to monitor user account activities, such as login attempts and privilege changes, and notify the SOC team of suspicious activities.

python
Copy code
# User Account Monitoring

import subprocess
import smtplib

def monitor_user_accounts():
    command = "cat /var/log/auth.log | grep 'Failed password'"
    output = subprocess.check_output(command, shell=True).decode()

    if "Failed password" in output:
        send_alert_email("Suspicious login attempt detected")

def send_alert_email(message):
    # Implement code to send an alert email to the SOC team
    pass

# Usage
monitor_user_accounts()
Summary: This script monitors the system logs for failed login attempts and sends an email alert to the SOC team when a suspicious activity is detected.

146. Network Traffic Analysis

Description: Create a script to capture and analyze network traffic, helping to detect unusual patterns or traffic from blacklisted IP addresses.

python
Copy code
# Network Traffic Analysis

import scapy.all as scapy

def capture_and_analyze_traffic(interface):
    packets = scapy.sniff(iface=interface, count=100)
    analyze_network_traffic(packets)

def analyze_network_traffic(packets):
    for packet in packets:
        if "ARP" in packet:
            analyze_arp_packet(packet)
        elif "TCP" in packet or "UDP" in packet:
            analyze_tcp_or_udp_packet(packet)

def analyze_arp_packet(packet):
    # Implement logic to analyze ARP packets
    pass

def analyze_tcp_or_udp_packet(packet):
    # Implement logic to analyze TCP or UDP packets
    pass

# Usage
capture_and_analyze_traffic("eth0")
Summary: This script captures network traffic on a specified interface and analyzes it for suspicious patterns or potentially malicious IP addresses.

147. Email Header Analyzer

Description: Create a script to extract and analyze email headers, checking for signs of phishing or spoofed emails.

python
Copy code
# Email Header Analyzer

import email
import quopri

def analyze_email_header(email_file):
    with open(email_file, 'r') as f:
        email_data = f.read()
        parsed_email = email.message_from_string(quopri.decodestring(email_data).decode('utf-8'))

        sender = parsed_email["From"]
        subject = parsed_email["Subject"]
        received = parsed_email.get_all("Received")

        if not is_legitimate(sender, received):
            send_alert_email(f"Suspicious email detected: {subject} from {sender}")

def is_legitimate(sender, received_headers):
    # Implement logic to verify email legitimacy
    pass

def send_alert_email(message):
    # Implement code to send an alert email to the SOC team
    pass

# Usage
analyze_email_header("suspicious_email.eml")
Summary: This script extracts and analyzes email headers for signs of phishing or spoofed emails and sends an alert to the SOC team when suspicious activity is detected.

148. Firewall Rule Change Detection

Description: Create a script to monitor and detect changes in firewall rules, alerting the SOC team when unauthorized changes are made.

python
Copy code
# Firewall Rule Change Detection

import os
import difflib

def detect_firewall_rule_changes(old_rules_file, new_rules_file):
    if not os.path.exists(old_rules_file):
        return  # No previous rules to compare

    with open(old_rules_file, 'r') as old_file, open(new_rules_file, 'r') as new_file:
        old_rules = old_file.readlines()
        new_rules = new_file.readlines()

        differ = difflib.Differ()
        diff = list(differ.compare(old_rules, new_rules))

    for line in diff:
        if line.startswith('- ') or line.startswith('+ '):
            send_alert_email("Firewall rule change detected")

def send_alert_email(message):
    # Implement code to send an alert email to the SOC team
    pass

# Usage
detect_firewall_rule_changes("firewall_rules_old.txt", "firewall_rules_new.txt")
Summary: This script detects changes in firewall rules by comparing old and new rule sets and sends an alert to the SOC team when unauthorized changes are found.

These Python scripts provide additional tools for SOC analysts, including user account monitoring, network traffic analysis, email header analysis, and firewall rule change detection, to enhance security monitoring and incident detection in a Security Operations Center.




User
give me more examples
ChatGPT
Certainly! Here are more Python script examples for a Security Operations Center (SOC) Analyst:

149. Log File Analysis

Description: Create a script to parse and analyze various log files from servers and devices in your network, looking for signs of security incidents.

python
Copy code
# Log File Analysis

import os
import re

def analyze_logs(log_directory):
    for log_file in os.listdir(log_directory):
        if log_file.endswith(".log"):
            with open(os.path.join(log_directory, log_file), 'r') as log:
                analyze_log_file(log.read())

def analyze_log_file(log_data):
    # Implement custom logic to analyze log data
    # Example: Look for patterns indicative of unauthorized access
    unauthorized_access_pattern = re.compile(r'Unauthorized access attempt: (.+)')
    matches = unauthorized_access_pattern.findall(log_data)
    if matches:
        for match in matches:
            send_alert_email(f"Suspicious activity detected: {match}")

def send_alert_email(message):
    # Implement code to send an alert email to the SOC team
    pass

# Usage
analyze_logs("/var/log")
Summary: This script analyzes log files in a specified directory for signs of security incidents, such as unauthorized access attempts.

150. SIEM Integration

Description: Develop a script to integrate with a Security Information and Event Management (SIEM) system to automate event handling and alerting.

python
Copy code
# SIEM Integration

import requests

def send_alert_to_siem(severity, description):
    siem_url = "https://siem.example.com/alerts"
    payload = {
        "severity": severity,
        "description": description,
    }

    headers = {"Authorization": "Bearer YOUR_API_KEY"}
    response = requests.post(siem_url, json=payload, headers=headers)

    if response.status_code == 200:
        print("Alert sent to SIEM successfully")
    else:
        print("Failed to send alert to SIEM")

# Usage
send_alert_to_siem("High", "Security breach detected in database server")
Summary: This script sends security alerts to a SIEM system, allowing for automated event handling and alerting.

151. Threat Feed Integration

Description: Create a script that integrates with threat intelligence feeds to automatically update threat information and apply it to your security systems.

python
Copy code
# Threat Feed Integration

import requests

def fetch_threat_feed():
    threat_feed_url = "https://threatfeed.example.com/indicators"
    response = requests.get(threat_feed_url)

    if response.status_code == 200:
        threat_data = response.json()
        process_threat_feed(threat_data)
    else:
        print("Failed to fetch threat feed")

def process_threat_feed(threat_data):
    # Implement logic to apply threat indicators to security systems
    for indicator in threat_data:
        update_firewall_blacklist(indicator)

def update_firewall_blacklist(indicator):
    # Implement logic to update the firewall blacklist with the new indicator
    pass

# Usage
fetch_threat_feed()
Summary: This script fetches threat intelligence data from a threat feed, processes the data, and applies threat indicators to security systems like firewalls.

152. Security Awareness Training Reminder

Description: Create a script to automate security awareness training reminders for employees, ensuring they complete required training modules.

python
Copy code
# Security Awareness Training Reminder

import smtplib
from datetime import datetime, timedelta

def send_training_reminder():
    today = datetime.now()
    training_due_date = today + timedelta(days=7)  # Set the due date for training

    if today == training_due_date:
        send_training_email()

def send_training_email():
    sender_email = "training@example.com"
    receiver_email = "employee@example.com"
    subject = "Security Awareness Training Reminder"
    message = "This is a reminder to complete your security awareness training."

    try:
        server = smtplib.SMTP('smtp.example.com')
        server.sendmail(sender_email, receiver_email, f"Subject: {subject}\n\n{message}")
        print("Reminder email sent successfully.")
    except Exception as e:
        print(f"An error occurred: {e}")

# Usage
send_training_reminder()
Summary: This script sends automated security awareness training reminders to employees, helping ensure they complete their training on time.

These Python scripts offer additional automation capabilities for SOC analysts, including log file analysis, SIEM integration, threat feed integration, and security awareness training reminders, to enhance security monitoring and incident response in a Security Operations Center.




User
give me more examples
ChatGPT
Certainly! Here are more Python script examples for a Security Operations Center (SOC) Analyst:

153. Network Traffic Analysis

Description: Create a script to capture and analyze network traffic to identify anomalies or potential security threats.

python
Copy code
# Network Traffic Analysis

import scapy.all as scapy

def analyze_network_traffic():
    # Sniff packets on the network interface
    packets = scapy.sniff(iface="eth0", count=100)  # Capture 100 packets on eth0 interface

    for packet in packets:
        # Implement custom logic to analyze packets
        if "HTTP" in packet:
            print("Potential HTTP traffic detected")

# Usage
analyze_network_traffic()
Summary: This script uses the Scapy library to capture and analyze network traffic, making it easier to identify suspicious or potentially malicious network activities.

154. Password Policy Checker

Description: Develop a script to check if user passwords meet the organization's password policy.

python
Copy code
# Password Policy Checker

import re

def check_password_policy(password):
    # Define the organization's password policy
    length_check = len(password) >= 8
    uppercase_check = re.search(r'[A-Z]', password)
    lowercase_check = re.search(r'[a-z]', password)
    digit_check = re.search(r'[0-9]', password)

    if length_check and uppercase_check and lowercase_check and digit_check:
        print("Password meets the organization's policy")
    else:
        print("Password does not meet the organization's policy")

# Usage
password = "SecureP@ssw0rd"
check_password_policy(password)
Summary: This script checks if a given password adheres to the organization's password policy, which includes length, uppercase, lowercase, and digit requirements.

155. Security Incident Reporting

Description: Create a script that allows employees to report security incidents by providing necessary information.

python
Copy code
# Security Incident Reporting

def report_security_incident():
    print("Please provide details of the security incident:")
    incident_type = input("Incident Type: ")
    description = input("Description: ")
    timestamp = get_current_time()

    # Save the incident report to a file or database
    save_incident_report(incident_type, description, timestamp)

    print("Incident report submitted successfully.")

def get_current_time():
    # Implement code to get the current timestamp
    return "2023-08-10 14:30:00"

def save_incident_report(incident_type, description, timestamp):
    # Implement code to save the incident report
    pass

# Usage
report_security_incident()
Summary: This script allows employees to report security incidents by providing details such as incident type, description, and a timestamp.

156. Security Patch Management

Description: Develop a script to automate the process of checking for and applying security patches to servers and devices.

python
Copy code
# Security Patch Management

import os

def check_and_apply_patches():
    # Define a list of servers and devices
    servers = ["server1.example.com", "server2.example.com"]
    devices = ["firewall.example.com", "router.example.com"]

    for server in servers:
        check_server_patches(server)

    for device in devices:
        check_device_patches(device)

def check_server_patches(server):
    print(f"Checking patches for {server}")
    # Implement code to check and apply patches for servers

def check_device_patches(device):
    print(f"Checking patches for {device}")
    # Implement code to check and apply patches for devices

# Usage
check_and_apply_patches()
Summary: This script automates the process of checking for and applying security patches on servers and devices, helping to keep the environment secure.

157. Threat Intel Feeds Monitoring

Description: Create a script to monitor threat intelligence feeds for the latest threats and alert the SOC team when relevant information is found.

python
Copy code
# Threat Intel Feeds Monitoring

import requests

def monitor_threat_intel_feeds():
    threat_feed_url = "https://threatfeeds.example.com/latest"
    response = requests.get(threat_feed_url)

    if response.status_code == 200:
        threat_data = response.json()
        process_threat_data(threat_data)
    else:
        print("Failed to fetch threat intelligence feeds")

def process_threat_data(threat_data):
    # Implement logic to analyze threat data
    for entry in threat_data:
        if entry["severity"] == "High":
            send_alert_to_soc(entry)

def send_alert_to_soc(threat_entry):
    # Implement code to send an alert to the SOC team
    pass

# Usage
monitor_threat_intel_feeds()
Summary: This script monitors threat intelligence feeds for the latest threats, alerts the SOC team when high-severity information is found, and allows further analysis.

These Python scripts provide additional automation capabilities for SOC analysts, including network traffic analysis, password policy checking, security incident reporting, security patch management, and threat intelligence feeds monitoring, all aimed at improving security and incident response in a Security Operations Center.




User
give me more examples
ChatGPT
Certainly, here are more examples of Python scripts for a Security Operations Center (SOC) Analyst:

158. Log Analysis for Anomaly Detection

Description: Create a script to analyze system logs for anomalies or suspicious activities, which can help in early threat detection.

python
Copy code
# Log Analysis for Anomaly Detection

def analyze_system_logs(log_file):
    with open(log_file, 'r') as log:
        for line in log:
            if "suspicious_activity" in line:
                send_alert("Suspicious activity detected", line)

def send_alert(alert_message, log_entry):
    # Implement code to send an alert to the SOC team
    print(alert_message)
    print(log_entry)

# Usage
log_file = "system.log"
analyze_system_logs(log_file)
Summary: This script analyzes system logs for suspicious activity and sends alerts to the SOC team when anomalies are detected.

159. Threat Hunting Automation

Description: Develop a script to automate threat hunting by querying logs, network data, and endpoint data for patterns that may indicate threats.

python
Copy code
# Threat Hunting Automation

import elasticsearch

def hunt_for_threats(query):
    es = elasticsearch.Elasticsearch('https://elasticsearch.example.com')
    results = es.search(index='logs', body=query)

    for hit in results['hits']['hits']:
        send_alert("Potential threat detected", hit)

def send_alert(alert_message, threat_data):
    # Implement code to send an alert to the SOC team
    print(alert_message)
    print(threat_data)

# Usage
query = {
    "query": {
        "match": {
            "threat_level": "High"
        }
    }
}
hunt_for_threats(query)
Summary: This script automates the process of threat hunting by querying logs stored in Elasticsearch and sending alerts when high-level threats are found.

160. User Account Activity Monitoring

Description: Create a script to monitor user account activities, including login attempts and privilege changes, and notify the SOC team of any suspicious events.

python
Copy code
# User Account Activity Monitoring

import subprocess

def monitor_user_activity():
    user_accounts = ["user1", "user2"]
    for user in user_accounts:
        get_account_activity(user)

def get_account_activity(user):
    command = f"last | grep {user}"
    result = subprocess.check_output(command, shell=True)
    if "suspicious_activity" in result:
        send_alert("Suspicious account activity detected", result)

def send_alert(alert_message, account_activity):
    # Implement code to send an alert to the SOC team
    print(alert_message)
    print(account_activity)

# Usage
monitor_user_activity()
Summary: This script monitors user account activity, such as login attempts, by analyzing system logs and sends alerts when suspicious activity is detected.

161. Security Dashboard Generator

Description: Develop a script to generate a security dashboard summarizing key security metrics and incidents.

python
Copy code
# Security Dashboard Generator

import matplotlib.pyplot as plt

def generate_security_dashboard():
    security_metrics = {"Incidents": 15, "Vulnerabilities": 8, "Threat Alerts": 25}
    plot_security_metrics(security_metrics)

def plot_security_metrics(metrics):
    plt.figure(figsize=(8, 4))
    plt.bar(metrics.keys(), metrics.values())
    plt.xlabel("Security Metrics")
    plt.ylabel("Counts")
    plt.title("Security Dashboard")
    plt.show()

# Usage
generate_security_dashboard()
Summary: This script generates a simple security dashboard displaying key security metrics using a bar chart.

These Python scripts cover various aspects of SOC tasks, including log analysis for anomaly detection, threat hunting automation, user account activity monitoring, and security dashboard generation. They help automate and streamline SOC activities for improved security monitoring and response.




User
give me more examples
ChatGPT
Certainly, here are more examples of Python scripts for a Security Operations Center (SOC) Analyst:

162. Real-time Log Monitoring and Alerting

Description: Create a script that monitors log files in real-time and sends alerts when specific events are detected.

python
Copy code
# Real-time Log Monitoring and Alerting

import time
import tailer

def real_time_log_monitor(log_file, keyword):
    for line in tailer.follow(open(log_file)):
        if keyword in line:
            send_alert("Keyword detected in log", line)

def send_alert(alert_message, log_entry):
    # Implement code to send an alert to the SOC team
    print(alert_message)
    print(log_entry)

# Usage
log_file = "system.log"
keyword = "suspicious_activity"
real_time_log_monitor(log_file, keyword)
Summary: This script monitors log files in real-time and sends alerts when a specified keyword (e.g., "suspicious_activity") is detected.

163. Automated Malware Analysis

Description: Develop a script that automates the analysis of suspicious files for malware characteristics.

python
Copy code
# Automated Malware Analysis

import hashlib
import requests
import json

def analyze_malware(file_path):
    sha256_hash = hash_file(file_path)
    report = submit_to_malware_analysis(sha256_hash)
    analyze_report(report)

def hash_file(file_path):
    sha256 = hashlib.sha256()
    with open(file_path, "rb") as f:
        while chunk := f.read(8192):
            sha256.update(chunk)
    return sha256.hexdigest()

def submit_to_malware_analysis(sha256_hash):
    api_key = "your_api_key"
    url = f"https://malware-analysis.example.com/api/analyze/{sha256_hash}"
    headers = {"x-api-key": api_key}
    response = requests.get(url, headers=headers)
    return response.json()

def analyze_report(report):
    if "malicious" in report["result"]:
        send_alert("Malicious file detected", report)

def send_alert(alert_message, report):
    # Implement code to send an alert to the SOC team
    print(alert_message)
    print(report)

# Usage
file_path = "suspicious_file.exe"
analyze_malware(file_path)
Summary: This script automates the analysis of suspicious files for malware characteristics and sends alerts when malicious files are detected.

164. Security Incident Handling Workflow

Description: Create a script that automates the workflow for handling security incidents, including documentation and response actions.

python
Copy code
# Security Incident Handling Workflow

import time

def handle_security_incident(incident_details):
    log_incident(incident_details)
    assess_risk(incident_details)
    take_response_actions(incident_details)
    recover_systems(incident_details)
    close_incident(incident_details)

def log_incident(incident_details):
    # Implement code to log incident details
    print(f"Incident logged: {incident_details['description']}")

def assess_risk(incident_details):
    # Implement code to assess the risk of the incident
    print("Incident risk assessed")

def take_response_actions(incident_details):
    # Implement code to take response actions
    print("Response actions taken")

def recover_systems(incident_details):
    # Implement code to recover affected systems
    print("Systems recovered")

def close_incident(incident_details):
    # Implement code to close the incident
    print("Incident closed")

# Usage
incident_details = {
    "description": "Data breach",
    "timestamp": time.strftime("%Y-%m-%d %H:%M:%S")
}
handle_security_incident(incident_details)
Summary: This script automates the workflow for handling security incidents, including documenting the incident, assessing risk, taking response actions, recovering systems, and closing the incident.

These Python scripts cover various SOC tasks, including real-time log monitoring and alerting, automated malware analysis, and security incident handling. They help SOC analysts streamline their work and enhance their ability to detect and respond to security threats.




User
give me more examples
ChatGPT
Certainly, here are more examples of Python scripts for a Security Operations Center (SOC) Analyst:

165. Network Port Scanner

Description: Create a Python script that scans a range of IP addresses for open network ports.

python
Copy code
# Network Port Scanner

import socket

def port_scanner(target, port_range):
    open_ports = []
    for port in range(port_range[0], port_range[1] + 1):
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        result = sock.connect_ex((target, port))
        if result == 0:
            open_ports.append(port)
        sock.close()
    return open_ports

# Usage
target = "192.168.1.1"
port_range = (1, 1024)
open_ports = port_scanner(target, port_range)
print(f"Open ports on {target}: {open_ports}")
Summary: This script scans a range of network ports on a specified IP address and returns a list of open ports.

166. Log Analysis for Anomalies

Description: Develop a script that analyzes log files for anomalies and triggers alerts for unusual patterns.

python
Copy code
# Log Analysis for Anomalies

import re

def analyze_logs(log_file):
    with open(log_file, "r") as file:
        logs = file.readlines()
    
    for log in logs:
        if re.search(r"Unauthorized access", log):
            send_alert("Unauthorized access detected", log)

def send_alert(alert_message, log_entry):
    # Implement code to send an alert to the SOC team
    print(alert_message)
    print(log_entry)

# Usage
log_file = "system.log"
analyze_logs(log_file)
Summary: This script analyzes log files for anomalies and sends alerts when patterns like "Unauthorized access" are detected.

167. Network Traffic Analysis

Description: Create a script that captures and analyzes network traffic to detect suspicious patterns.

python
Copy code
# Network Traffic Analysis

import scapy.all as scapy

def analyze_network_traffic():
    packets = scapy.sniff(count=100)
    for packet in packets:
        if packet.haslayer(scapy.HTTPRequest):
            url = packet[scapy.HTTPRequest].Host + packet[scapy.HTTPRequest].Path
            if "malicious" in url:
                send_alert("Malicious URL detected", url)

def send_alert(alert_message, url):
    # Implement code to send an alert to the SOC team
    print(alert_message)
    print(url)

# Usage
analyze_network_traffic()
Summary: This script uses the Scapy library to capture and analyze network traffic, sending alerts when suspicious URLs are detected.

168. Security Policy Compliance Checker

Description: Develop a script that checks systems for compliance with security policies and generates reports.

python
Copy code
# Security Policy Compliance Checker

def check_security_policy_compliance(systems):
    non_compliant_systems = []
    for system in systems:
        if not is_compliant(system):
            non_compliant_systems.append(system)
    generate_compliance_report(non_compliant_systems)

def is_compliant(system):
    # Implement code to check system compliance
    return True  # Replace with compliance checks

def generate_compliance_report(non_compliant_systems):
    # Implement code to generate compliance report
    if non_compliant_systems:
        send_alert("Non-compliant systems detected", non_compliant_systems)

def send_alert(alert_message, non_compliant_systems):
    # Implement code to send an alert to the SOC team
    print(alert_message)
    print("Non-compliant systems:", non_compliant_systems)

# Usage
systems = ["Server1", "Server2", "Workstation1"]
check_security_policy_compliance(systems)
Summary: This script checks systems for compliance with security policies, generates a report of non-compliant systems, and sends alerts to the SOC team.

These Python scripts cover a range of SOC tasks, including network port scanning, log analysis for anomalies, network traffic analysis, and security policy compliance checking. They assist SOC analysts in identifying vulnerabilities, monitoring logs, analyzing network traffic, and ensuring compliance with security policies.

 
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
