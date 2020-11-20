#!/bin/bash

#Change "cloudflared-linux-armv6" with the arch of your system. These can be found at https://github.com/cloudflare/cloudflared/releases/
curl -L "https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-armv6" -O /var/tmp/cloudflared

chmod +x /var/tmp/cloudflared
oldVer="$(/usr/local/bin/cloudflared -v | grep -oP "\s\d*\.\d*\.\d*\s" | xargs)"
newVer="$(/var/tmp/./cloudflared -v | grep -oP "\s\d*\.\d*\.\d*\s" | xargs)"

if [ "$oldVer" = "$newVer" ] && [ $? = 0 ]; then
    echo "Version up-to-date"
    rm /var/tmp/cloudflared
    echo "[$(date +"%d/%m %Y %H:%M:%S")] Version already up-to-date: $newVer" >> /var/log/cloudflared-updater.log
else
    echo "Updating version $newVer over $oldVer"
    systemctl stop cloudflared
    mv /var/tmp/cloudflared /usr/local/bin/cloudflared
    echo "[$(date +"%d/%m %Y %H:%M:%S")] Updated $newVer over $oldVer" >> /var/log/cloudflared-updater.log
    systemctl start cloudflared
fi
