# Check_mk notification script for Slack

## Introduction

This is a script designed to bounce Check_MK/OMD notifications 
into a Slack Channel, using Slacks Incoming Webhooks API.

## HOW TO USE:

1) Create an incoming webhook integration in your slack and note down the URL.

2) Put into /usr/(local/)share/check_mk/notifications (or 
~/share/check_mk/notifications on OMD installs) directory and 
edit configuration variables in the 'slack' script, and make 
sure that the script is executable (chmod +x slack)

3) Create a user for slack in WATO, use flexible custom notifications and select 'CMK-Slack Websocket integration' as the notifier.

Select option "Call with the following parameters" and set your channel without "#". If you leave the parameter box in blank the channel takes "#monitoring" value.

4) Wait for something to send an alert or generate a test 
alert.

## Good to know

I haven't tested this with Notification Bulking (In newer cmk 
releases), I assume it doesn't work. Where it has been used 
bulk notification setups, bulking for the slack script has 
been explicitly disabled.


### Test it

if you want to test if you have configured the slack script correcty you can try:
```
export NOTIFY_PARAMETER_1=dennis-test
export NOTIFY_HOSTNAME=TestHost
export NOTIFY_WHAT=""
export NOTIFY_HOSTACKCOMMENT=false
export NOTIFY_NOTIFICATIONAUTHOR=""
export NOTIFY_HOSTSTATE=DOWN
```
### Mattermost

To use it with the opensource alternative mattermost run those settings:

your api key url
`slack_path = "/hooks/kderbmy7yjrr9p9qfwzto374sr"`

your mattermost domain
`slack_domain = "mattermost.example.com"`
