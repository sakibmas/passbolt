# Prerequisites  
*   A minimal Ubuntu 24.04 server.  
*   A domain / host name pointing to your server.
*   A working SMTP server for email notifications.
*   A working NTP service to avoid GPG authentication issues.  

The recommended server requirements are:  
*   2 cores  
*   2GB of RAM      
*   20GB of free disk space

# Repository setup  
For easier installation and update tasks, Passbolt provides a package repository that you need to set up before you download Passbolt CE and install it.

**Step 1.** Download our dependencies installation script:  
```
curl -LO https://download.passbolt.com/ce/installer/passbolt-repo-setup.ce.sh
```

**Step 2.** Download our SHA512SUM for the installation script:  
```
curl -LO https://github.com/passbolt/passbolt-dep-scripts/releases/latest/download/passbolt-ce-SHA512SUM.txt
```

**Step 3.** Ensure that the script is valid and execute it:  
```
sha512sum -c passbolt-ce-SHA512SUM.txt && bash ./passbolt-repo-setup.ce.sh || rm -f passbolt-repo-setup.ce.sh
```

# Install
```
apt install passbolt-ce-server
```

# Upgrade
```
apt update
```
```
systemctl stop nginx
```
```
apt --only-upgrade install passbolt-ce-server
```
```
apt upgrade -y
```
```
apt autoremove -y
```
```
reboot
```

# Troubleshooting
* Run the healthcheck command:
  ```
  sudo -u www-data /usr/share/php/passbolt/bin/cake passbolt healthcheck
  ```
* For database migration:
  ```
  sudo -u www-data /usr/share/php/passbolt/bin/cake passbolt migrate
  ```
  ```
  sudo -u www-data /usr/share/php/passbolt/bin/cake cache clear_all
  ```
* Reset filesystem permissions:
  ```
  chown -R www-data:www-data /var/lib/passbolt/tmp/
  chmod -R 775 $(find /var/lib/passbolt/tmp/ -type d)
  chmod -R 664 $(find /var/lib/passbolt/tmp/ -type f)
  ```

