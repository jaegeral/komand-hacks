# Description


If you want to post stuff to Mattermost you can do that by making use of the REST plugin.

# Installation
## Webhooks
To enable Webhooks in Mattermost, see: https://docs.mattermost.com/developer/webhooks-incoming.html

## Install Workflow to Komand

- Download the workflow
- Import Workflow as Full workflow to Komand instance
- install all needed Plugins
- Provide and set up needed Connections
- Adjust the Endpoint of your Webhook in the REST Calls
- Activate the Workflow

# Usage

You can call it by using the KOMAND Plugin:

Run Asynchronously: Run a workflow without waiting for results

Connection --> your Komand Connection

Values:
<pre>
Workflow Name: Post_Text_to_Mattermost
</pre>

Input:
```json
{"text_post":"{{[$job].[$name]}} started https://$YouKomandURL/jobs/details/{{[$job].[$id]}} {{[$job].[$URL]}}"}
```

That will Post the text to the pre-defined channel using the web hook.

The text to be posted can of course being adjusted.
