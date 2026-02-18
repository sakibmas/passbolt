# Prerequisites  
*   A minimal Ubuntu 24.04 server.  
*   A domain / host name pointing to your server.
*   A working SMTP server for email notifications.
*   A working NTP service to avoid GPG authentication issues.  

The recommended server requirements are:  
*   2 cores  
*   2GB of RAM      
*   20GB of free disk space  

# Health check
```
 sudo -u www-data /usr/share/php/passbolt/bin/cake passbolt healthcheck
```
