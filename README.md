# cloudflared-updater

A simple bash script to update the cloudflared binary in conjunction to the guide used at https://docs.pi-hole.net/guides/dns-over-https/#if-you-configured-cloudflared-with-your-own-service-files. 

## Prerequisites
This requires you to have cloudflared manually installed under `/usr/local/bin/cloudflared` and a systemd service for it called `cloudflared`.
<br>

## Installation

Download the script and modify the link in the script to fit your arch (links further down):

```
curl -L https://github.com/chippey5/cloudflared-updater/releases/latest/download/cloudflared-updater -o ./cloudflared-updater
```

Add the script to `crontab` as root. Logs will show up at `/var/log/cloudflared-updater.log`


#### Links for architectures

* ##### AMD64: https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64

* ##### i386: https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-386

* ##### ARMv8 64-bit: https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm64

* ##### ARMv8/ARMv7/ARMv6 32-bit: https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-armv6


###### All the links are available at https://github.com/cloudflare/cloudflared/releases/

## Examples 

##### Testing the script

`sudo bash /path/to/cloudflared-updater`

##### Run the updater on Sunday every week

`sudo crontab -e`

Add the following to the bottom of the list and modify the path:
```
0 0 * * 0 bash /path/to/cloudflared-updater.sh
```
