# Prerequisites  
*   A minimal Ubuntu 24.04 server.  
*   A domain / host name pointing to your server.
*   A working SMTP server for email notifications.
*   A working NTP service to avoid GPG authentication issues.  

The recommended server requirements are:  
*   2 cores  
*   2GB of RAM      
*   20GB of free disk space

# Package repository setup  
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
sha512sum -c passbolt-ce-SHA512SUM.txt && sudo bash ./passbolt-repo-setup.ce.sh || echo "Bad checksum. Aborting" && rm -f passbolt-repo-setup.ce.sh
```

# Install Passbolt official Linux package
```
apt install passbolt-ce-server
```

# Troubleshooting
 - 
 ```
   sudo -u www-data /usr/share/php/passbolt/bin/cake passbolt healthcheck
```
 -
```
sudo -u www-data /usr/share/php/passbolt/bin/cake cache clear_all
```

