# discordtee
discordtee is a bash script that works like tee command. Instead of writing the standard input to files, discordtee posts it to Discord.

## Description
I was looking for a script to use on my server(s) that could send output from various scripts, like log analyzing stuff to Discord. I already was using [slacktee](https://github.com/coursehero/slacktee) but I wanted a Discord version as well.
Because I'm not really a programmer and previous attempts to create something and searching for existing solutions (like: [discord.sh](https://github.com/fieu/discord.sh) didn't give the results I wanted, I decided to give it a try using [Claude.ai](https://claude.ai). So this script was written with the help of AI and whoever is going to use it, should keep that in mind. I can't guarantee the code quality. So If you find bugs or bigger issues, please let me know! Also requests for improvements are welcome, because more eyes on the project can only help!

## Requirements
- This was tested on an AlmaLinux server.
- The script is written in bash and uses the jq to be installed
  `sudo dnf install jq`

## Installation
1. Save the script discordtee to `/usr/local/bin/discordtee` and make it executable
`chmod +x /usr/local/bin/discordtee`
2. Create webhook in Discord:
  - Go to your Discord channel settings
  - Click "Integrations" → "Webhooks" → "Create Webhook"
  - Copy the webhook URL
3. Create the config file in `/etc/discordtee.conf` and make sure to fill in your actual webhook URL.

## Usage
```
Usage: discordtee [OPTIONS]

Send stdin to Discord via webhook.

OPTIONS:
    -t, --title TEXT     Set message title
    -u, --username TEXT  Set username (default: discordtee)
    -c, --config FILE    Use alternative config file (default: /etc/discordtee.conf)
    -v, --verbose        Show success messages (default is quiet)
    -h, --help          Show this help
    --version           Show version

EXAMPLE:
echo "Hello World" | discordtee -t "Test Message"
grep "error" /var/log/messages | discordtee -t "System Errors"
```
