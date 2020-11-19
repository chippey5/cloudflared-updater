# cloudflared-updater

A simple bash script to update the cloudflared binary in conjunction to the guide used at https://docs.pi-hole.net/guides/dns-over-https/#if-you-configured-cloudflared-with-your-own-service-files. 

## Prerequisites
This requires you to have cloudflared manually installed under `/usr/local/bin/cloudflared` and a systemd service for it called `cloudflared`.

## Installation

Download the script and modify the link in the script to fit your arch:

```
curl -L https://github.com/chippey5/cloudflared-updater/releases/latest/download/cloudflared-updater.sh -o ./cloudflared-updater.sh
```

Add the script to `crontab` as root. Logs will show up at `/var/log/cloudflared-updater.log`


### Example: Run the updater on Sunday every week

`sudo crontab -e`

Add the following to the bottom of the list and modify the path:
```
0 0 * * 0 bash /path/to/cloudflared-updater.sh
```
