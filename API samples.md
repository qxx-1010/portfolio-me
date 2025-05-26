# Zoom Chatbot API

Chatbot APIs allow developers to interface with chatbot features programmatically. These APIs allow chatbots to send and
receive messages, respond to user requests, and execute actions in Zoom Team Chat. They can be useful for automating
tasks, pushing notifications, or integrating third-party services with Zoom.

This documentation includes cURL code samples for POST, PUT, and DELETE Chatbot message operations.

Base URL: https://api.zoom.us/v2 Endpoints:

-   POST /im/chat/messages
-   PUT /im/chat/messages/{message_id}
-   DELETE /im/chat/messages/{message_id}

## Send Chatbot messages

#### Use this API to send messages from your Chatbot app. 

Follow the [client credentials flow](https://developers.zoom.us/docs/team-chat/installation-and-authentication/) to enable the authorization.

To authorize your chatbot, make a POST request to the endpoint:
https://api.zoom.us/oauth/token?grant_type=client_credentials

For more information about authorizing Chatbots, read the
[Chatbot Installation and Authentication documentation](https://developers.zoom.us/docs/team-chat/installation-and-authentication/).

[Scopes](https://developers.zoom.us/docs/integrations/oauth-scopes-overview/): imchat:bot

[Rate Limit Label](https://marketplace.zoom.us/docs/api-reference/rate-limits?_gl=1*butfld*_gcl_au*MTQ3MzMxNzY5LjE3NDM1ODczNTY.*_ga*MjA4MzAwMDA4MC4xNzM0NjA0MDAz*_ga_L8TBF28DDX*czE3NDgyMjQ4MTgkbzYkZzEkdDE3NDgyMjc5OTgkajAkbDAkaDA.#rate-limits):
MEDIUM

### Body parameters
| Name                | Type    | Description                                                                                                                                                                                 | Required | Notes                                                                                                                                                             |
| ------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| robot_jid           | string  | The bot JID. <br>You can find this value in the Feature tab's Chat Subscription section of your Marketplace Chatbot app.                                                                    | Required |                                                                                                                                                                   |
| to_jid              | string  | The JID of the group channel or user to whom the message was sent.                                                                                                                          | Required |                                                                                                                                                                   |
| account_id          | string  | The authorized account's account ID.                                                                                                                                                        | Required |                                                                                                                                                                   |
| content             | object  | A JSON-format template that describes how the edited message should be displayed for the user.                                                                                              | Required | For more information, read our [Chatbot Send, Edit, and Delete Messages documentation](https://developers.zoom.us/docs/team-chat/send-edit-and-delete-messages/). |
| visible_to_user     | string  | The user ID of the user who will receive Chatbot messages in the group channel. Only this user will see the Chatbot's messages.                                                             |          |                                                                                                                                                                   |
| user_jid            | string  | The JID of the user on whose behalf the message is being sent. This is used to prevent members of a channel from getting notifications that were set up by a user who has left the channel. | Required |                                                                                                                                                                   |
| reply_to            | string  | The unique identifier of the parent message to which you want to send the chatbot's reply.                                                                                                  |          |                                                                                                                                                                   |
| is_markdown_support | boolean | Whether to apply the [Markdown parser to your Chatbot message](https://developers.zoom.us/docs/team-chat/customizing-messages/).                                                            |          |                                                                                                                                                                   |

### Sample request
POST    /im/chat/messages

```
curl --request POST \
  --url https://api.zoom.us/v2/im/chat/messages \
  --header 'Authorization: Bearer YOUR_SECRET_TOKEN' \
  --header 'Content-Type: application/json' \
  --data '{
  "robot_jid": "v1pky3tyBBB5pl8q@xmpp.zoom.us",
  "to_jid": "xghfd@shj.zoom.us",
  "account_id": "ABCDE12345",
  "content": {},
  "visible_to_user": "FGHIJ67890@xmpp.zoom.us",
  "user_jid": "jnrgfjp6w@xmpp.zoom.us",
  "reply_to": "5AF2A82E-9220-4600-AFB2-A028852E377C",
  "is_markdown_support": true
}'
```

### Sample response

If your POST request is successful, you’ll get a response. HTTP status code is 201. 

```
{
  "robot_jid": "v1pky3tyBBB5pl8q@xmpp.zoom.us",
  "to_jid": "xghfd@shj.zoom.us",
  "sent_time": "2019-10-17 01:40:24",
  "message_id": "DWQ2A82E-9220-4600-AFB2-A028852E377C",
  "user_jid": "jnrgfjp6w@xmpp.zoom.us"
}
```

## Edit a Chatbot message

#### Use this API to edit a message sent by your Chatbot app.

After sending a message via the Send Chatbot message API, store the messageId value returned in the API response. You
will need this value edit the associated message using this API.

Follow the [client credentials flow](https://developers.zoom.us/docs/team-chat/installation-and-authentication/) to
enable the authorization.

To authorize your chatbot, make a POST request to the endpoint:
https://api.zoom.us/oauth/token?grant_type=client_credentials

For more information about authorizing Chatbots, read the
[Chatbot Installation and Authentication documentation](https://developers.zoom.us/docs/team-chat/installation-and-authentication/).

[Scopes](https://developers.zoom.us/docs/integrations/oauth-scopes-overview/): imchat:bot

[Rate Limit Label](https://marketplace.zoom.us/docs/api-reference/rate-limits?_gl=1*butfld*_gcl_au*MTQ3MzMxNzY5LjE3NDM1ODczNTY.*_ga*MjA4MzAwMDA4MC4xNzM0NjA0MDAz*_ga_L8TBF28DDX*czE3NDgyMjQ4MTgkbzYkZzEkdDE3NDgyMjc5OTgkajAkbDAkaDA.#rate-limits):
MEDIUM

### Body parameters
| Name                | Type    | Description                                                                                                                                                                                 | Required | Notes                                                                                                                                                             |
| ------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| message_id          | string  | The message ID. <br>You can get this value from the [Send Chatbot message API](https://developers.zoom.us/docs/api/rest/reference/chatbot/methods/#operation/sendChatbot).                  | Required |                                                                                                                                                                   |
| robot_jid           | string  | The bot JID. <br>You can find this value in the Feature tab's Chat Subscription section of your Marketplace Chatbot app.                                                                    | Required |                                                                                                                                                                   |
| account_id          | string  | The authorized account's account ID.                                                                                                                                                        | Required |                                                                                                                                                                   |
| content             | object  | A JSON-format template that describes how the edited message should be displayed for the user.                                                                                              | Required | For more information, read our [Chatbot Send, Edit, and Delete Messages documentation](https://developers.zoom.us/docs/team-chat/send-edit-and-delete-messages/). |
| user_jid            | string  | The JID of the user on whose behalf the message is being sent. This is used to prevent members of a channel from getting notifications that were set up by a user who has left the channel. |          |                                                                                                                                                                   |
| is_markdown_support | boolean | Whether to apply the [Markdown parser to your Chatbot message](https://developers.zoom.us/docs/team-chat/customizing-messages/).                                                            |          |                                                                                                                                                                   |

### Sample request
PUT /im/chat/messages/{message_id}

```
curl --request PUT \
  --url https://api.zoom.us/v2/im/chat/messages/201910tryyRFjM_main \
  --header 'Authorization: Bearer YOUR_SECRET_TOKEN' \
  --header 'Content-Type: application/json' \
  --data '{
  "robot_jid": "v1pky3tyBBB5pl8q@xmpp.zoom.us",
  "account_id": "ABCDE12345",
  "content": {},
  "user_jid": "jnrgfjp6w@xmpp.zoom.us",
  "is_markdown_support": true
}'
```

### Sample response

If your PUT request is successful, you’ll get a response. HTTP status code is 200 (Message updated.). 

```
{
  "message_id": "201910tryyRFjM_main",
  "robot_jid": "v1pky3tyBBB5pl8q@xmpp.zoom.us",
  "sent_time": "2019-10-17 01:40:24 +0000",
  "to_jid": "xghfd@shj.zoom.us",
  "user_jid": "jnrgfjp6w@xmpp.zoom.us"
}
```

## Delete a Chatbot message

#### Use this API to delete a message sent by your Chatbot app.

Follow the [client credentials flow](https://developers.zoom.us/docs/team-chat/installation-and-authentication/) to enable the authorization.

To authorize your chatbot, make a POST request to the endpoint:
https://api.zoom.us/oauth/token?grant_type=client_credentials

For more information about authorizing Chatbots, read the
[Chatbot Installation and Authentication documentation](https://developers.zoom.us/docs/team-chat/installation-and-authentication/).

[Scopes](https://developers.zoom.us/docs/integrations/oauth-scopes-overview/): imchat:bot

[Rate Limit Label](https://marketplace.zoom.us/docs/api-reference/rate-limits?_gl=1*butfld*_gcl_au*MTQ3MzMxNzY5LjE3NDM1ODczNTY.*_ga*MjA4MzAwMDA4MC4xNzM0NjA0MDAz*_ga_L8TBF28DDX*czE3NDgyMjQ4MTgkbzYkZzEkdDE3NDgyMjc5OTgkajAkbDAkaDA.#rate-limits):
MEDIUM

### Body parameters
| Name       | Type   | Description                                                                                                                                                                                                  | Required | Notes |
| ---------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- | ----- |
| message_id | string | The message ID. <br>You can get this value from the [Send Chatbot message API](https://developers.zoom.us/docs/api/rest/reference/chatbot/methods/#operation/sendChatbot).                                   | Required |       |
| robot_jid  | string | The bot JID. <br>You can find this value in the Feature tab's Chat Subscription section of your Marketplace Chatbot app.                                                                                     | Required |       |
| account_id | string | The authorized account's account ID. <br>You can get this value from the [Chatbot request sent to your server](https://developers.zoom.us/docs/team-chat-apps/send-edit-and-delete-messages/#send-messages). | Required |       |
| user_jid   | string | The JID of the user on whose behalf the message is being sent. This is used to prevent members of a channel from getting notifications that were set up by a user who has left the channel.                  |          |       |

### Sample request
DELETE  /im/chat/messages/{message_id}

```
curl --request DELETE \
  --url 'https://api.zoom.us/v2/im/chat/messages/201910tryyRFjM_main?account_id=ABCDE12345&robot_jid=v1pky3tyBBB5pl8q%40xmpp.zoom.us' \
  --header 'Authorization: Bearer YOUR_SECRET_TOKEN'
```
  
### Sample response

If your DELETE request is successful, you’ll get a response. HTTP status code is 200 (Message deleted.).

```
{
  "message_id": "201910tryyRFjM_main",
  "robot_jid": "v1pky3tyBBB5pl8q@xmpp.zoom.us",
  "sent_time": "2019-10-17 01:40:24 +0000",
  "to_jid": "xghfd@shj.zoom.us",
  "user_jid": "jnrgfjp6w@xmpp.zoom.us"
}
```

If you want to use the APIs of other Zoom products or features, check the [Zoom API References page](https://developers.zoom.us/docs/api/).
