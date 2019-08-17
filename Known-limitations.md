## Message throttling

Unless your bot is whitelisted for higher limits, the bot's attempt at sending a message will get throttled at 8,000 messages every 30 minutes (rolling window). If you exceed this limit, you will see messages in the throttled state. Please raise a request [here](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UN0RWNTNNVTkwQlRIQVpRWVEyTTU3TkJDVC4u) if your app is getting throttled, we can whitelist apps which will bump up the thresholds.

## No retries

If your message is throttled, there is no retry. There is also no way for the creator to explicitly retry sending a failed message.

We intend to add the ability to retry failed messages in the next version of the template.

## App installation is required

The app can only send messages to users and teams who have the app installed. To mitigate this limitation and reach a wider audience, install the app in personal scope for all the intended recipients in the tenant, as well as in the teams to allow a targeted message to be delivered. This is to be done outside the app manually. 
