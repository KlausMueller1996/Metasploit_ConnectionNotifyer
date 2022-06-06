# Metasploit Slack Notifier
This Metasploit plugin was created to monitor sessions, new ones and those closing. The idea is to provide a way for consultants to see new sessions coming in when they might not have access to their listener(s). 

SlackNotifier uses session subscriptions to monitor activity and then sends an alert to Slack using Slack's Incoming WebHooks. The alert is sent using the WebHook URL and a POST request and will tag a specified username (you could also use @channel or @here) and provide the computer name of the server with the session (if set).

## Setup
Place the SlackNotifier.rb file inside "/usr/share/metasploit-framework/plugins/" or a folder you have linked to this primary plugins folder.

Then create a new Incoming WebHook for Slack. You may also want to create a new channel for the alerts, like #shell-alerts.

## Sample Usage
The SlackNotifier plugin can be used like any other Metasploit plugin. Begin by loading ShellHerder and setting your options. Then you will need to run notify_start to subscribe to session events. See the following example:

  msf exploit(handler) > load SlackNotifier

  [\*] Successfully loaded plugin: notify

  msf exploit(handler) > notify_set_user @<your user name>

  [\*] Setting the Slack handle to @<your user name>

  msf exploit(handler) > notify_set_webhook <Your hooks.slack.com URL>

  [\*] Setting the Webhook URL to <Your hooks.slack.com URL>

  msf exploit(handler) > notify_set_source Test_VM

  [\*] Setting the Source to Test_VM

  msf exploit(handler) > notify_test

  [\*] Sending tests message
