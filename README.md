# cloudflared-updater

A simple bash script to update the cloudflared binary in conjunction to the guide used at https://docs.pi-hole.net/guides/dns/cloudflared/ (manual installation steps). 

## Prerequisites
This requires you to have cloudflared manually installed under `/usr/local/bin/cloudflared` and a systemd service for it called `cloudflared`.
<br>

## Installation

Modify the link to fit your arch and download the script (link sources further down):

```
curl -L -o ./cloudflared-updater https://github.com/chippey5/cloudflared-updater/releases/latest/download/cloudflared-updater_{ARCH}
```

Make the file executable
```
chmod +x cloudflared-updater
```

Add the script to `crontab` as root. Logs will show up at `/var/log/cloudflared-updater.log`


#### Link sources for architectures

* ##### AMD64: https://github.com/chippey5/cloudflared-updater/releases/latest/download/cloudflared-updater_amd64

* ##### i386: https://github.com/chippey5/cloudflared-updater/releases/latest/download/cloudflared-updater_i386

* ##### ARMv8 (64-bit): https://github.com/chippey5/cloudflared-updater/releases/latest/download/cloudflared-updater_arm64

* ##### ARMv6/ARMv7/ARMv8 (32-bit): https://github.com/chippey5/cloudflared-updater/releases/latest/download/cloudflared-updater_armv6


###### All the _cloudflared_ releases are available at https://github.com/cloudflare/cloudflared/releases/

## Examples 

##### Testing the script

`sudo bash /path/to/cloudflared-updater`

##### Run the updater on Sunday every week

`sudo crontab -e`

Add the following to the bottom of the list and modify the path:
```
0 0 * * 0 /bin/bash /path/to/cloudflared-updater
```
