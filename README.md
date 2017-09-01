[![](https://scdn.rapidapi.com/RapidAPI_banner.png)](https://rapidapi.com/package/GroupMe/functions?utm_source=RapidAPIGitHub_GroupMeFunctions&utm_medium=button&utm_content=RapidAPI_GitHub)

# GroupMe Package
GroupMe is a free group messaging app. A free and simple way to stay in touch with friends and family, quickly and easily.
* Domain: [GroupMe](http://http://groupme.com/)
* Credentials: accessToken

## How to get credentials: 
0. Browse to [GroupMe](http://http://groupme.com/)
1. Register or Log In
2. Create new application at [Developers page](https://dev.groupme.com/applications/new) to get your accessToken



## Custom datatypes: 
 |Datatype|Description|Example
 |--------|-----------|----------
 |Datepicker|String which includes date and time|```2016-05-28 00:00:00```
 |Map|String which includes latitude and longitude coma separated|```50.37, 26.56```
 |List|Simple array|```["123", "sample"]``` 
 |Select|String with predefined values|```sample```
 |Array|Array of objects|```[{"Second name":"123","Age":"12","Photo":"sdf","Draft":"sdfsdf"},{"name":"adi","Second name":"bla","Age":"4","Photo":"asfserwe","Draft":"sdfsdf"}] ```
 

## GroupMe.listGroups
List the authenticated user`s active groups.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| page       | Number     | Fetch a particular page of results. Defaults to 1.
| perPage    | Number     | Define page size. Defaults to 10.

## GroupMe.listFormerGroups
List they groups you have left but can rejoin.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| page       | Number     | Fetch a particular page of results. Defaults to 1.
| perPage    | Number     | Define page size. Defaults to 10.

## GroupMe.getSingleGroup
Load a specific group.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | Id of the group

## GroupMe.createGroup
Create a new group

| Field           | Type       | Description
|-----------------|------------|----------
| accessToken     | credentials| Access token provided by GroupMe
| groupName       | String     | Primary name of the group. Maximum 140 characters
| groupDescription| String     | A subheading for the group. Maximum 255 characters
| groupImage      | String     |  GroupMe Image Service URL
| shareGroup      | Select     | If you pass a true value for share, we`ll generate a share URL. Anybody with this URL can join the group.

## GroupMe.updateGroup
Update existing group

| Field           | Type       | Description
|-----------------|------------|----------
| accessToken     | credentials| Access token provided by GroupMe
| groupId         | String     | Id of the group
| groupName       | String     | Primary name of the group. Maximum 140 characters
| groupDescription| String     | A subheading for the group. Maximum 255 characters
| groupImage      | String     |  GroupMe Image Service URL
| shareGroup      | Select     | If you pass a true value for share, we`ll generate a share URL. Anybody with this URL can join the group.
| officeMode      | Select     | Office mode of the group

## GroupMe.deleteGroup
Delete a specific group.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | Id of the group

## GroupMe.joinSharedGroup
Join a shared group

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | Id of the group
| shareToken | String     | Share token of the group

## GroupMe.rejoinSharedGroup
Rejoin a group. Only works if you previously removed yourself.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | Id of the group

## GroupMe.changeGroupOwners
Change owner of requested groups.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| requests   | List       | One request is object where user_id is the new owner who must be active member of a group specified by group_id.

## GroupMe.addMembers
Add members to a group.  The response includes a results_id that`s used in the results request.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | ID of the group
| members    | List       | nickname is required. You must use one of the following identifiers: user_id, phone_number, or email.

```
sample of single member object
{
      "nickname": "Mom",
      "user_id": "1234567890",
      "guid": "GUID-1"
    }
```

## GroupMe.getAddResults
Get the membership results from an add call.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | ID of the group
| resultId   | String     | ID of the result

## GroupMe.removeMember
Remove a member (or yourself) from a group.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | ID of the group
| memberId   | String     | ID of the member

## GroupMe.updateNickname
Update your nickname in a group. The nickname must be between 1 and 50 characters.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | ID of the group
| nickname   | String     | New nickname

## GroupMe.listGroupMessages
Retrieve messages for a group.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | ID of the group
| beforeId   | String     | Returns messages created before the given message ID
| sinceId    | String     | Returns most recent messages created after the given message ID
| afterId    | String     | Returns messages created immediately after the given message ID
| limit      | Number     | Number of messages returned. Default is 20. Max is 100.

## GroupMe.sendTextMessage
Send a text message to a group

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | ID of the group
| sourceGuid | String     |  Client-side IDs for messages. This can be used by clients to set their own identifiers on messages, but the server also scans these for de-duplication. That is, if two messages are sent with the same source_guid within one minute of each other, the second message will fail with a 409 Conflict response.
| text       | String     | The maximum length is 1,000 characters.
| attachments| List       | A polymorphic list of attachments (locations, images, etc). You may have more than one of any type of attachment, provided clients can display it.

```
sample of attachment objects
{
        "type": "image",
        "url": "https://i.groupme.com/123456789"
      },
      {
        "type": "image",
        "url": "https://i.groupme.com/123456789"
      },
      {
        "type": "location",
        "lat": "40.738206",
        "lng": "-73.993285",
        "name": "GroupMe HQ"
      }
```

## GroupMe.sendAttachmentMessage
Send a message with attachment and optional text to a group

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | ID of the group
| sourceGuid | String     |  Client-side IDs for messages. This can be used by clients to set their own identifiers on messages, but the server also scans these for de-duplication. That is, if two messages are sent with the same source_guid within one minute of each other, the second message will fail with a 409 Conflict response.
| text       | String     | The maximum length is 1,000 characters.
| attachments| List       | A polymorphic list of attachments (locations, images, etc). You may have more than one of any type of attachment, provided clients can display it.

```
sample of attachment objects
{
        "type": "image",
        "url": "https://i.groupme.com/123456789"
      },
      {
        "type": "image",
        "url": "https://i.groupme.com/123456789"
      },
      {
        "type": "location",
        "lat": "40.738206",
        "lng": "-73.993285",
        "name": "GroupMe HQ"
      }
```

## GroupMe.listChats
Returns a paginated list of direct message chats, or conversations, sorted by updated_at descending.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| page       | Number     | Fetch a particular page of results. Defaults to 1.
| perPage    | Number     | Define page size. Defaults to 10.

## GroupMe.listDirectMessages
Fetch direct messages between two users.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| otherUserId| String     | The other participant in the conversation.
| beforeId   | String     | Returns messages created before the given message ID
| sinceId    | String     | Returns most recent messages created after the given message ID

## GroupMe.sendDirectTextMessage
Send a text DM to another user

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| recipientId| String     | The other participant in the conversation.
| sourceGuid | String     |  Client-side IDs for messages. This can be used by clients to set their own identifiers on messages, but the server also scans these for de-duplication. That is, if two messages are sent with the same source_guid within one minute of each other, the second message will fail with a 409 Conflict response.
| text       | String     | The maximum length is 1,000 characters.
| attachments| List       | A polymorphic list of attachments (locations, images, etc). You may have more than one of any type of attachment, provided clients can display it.

```
sample of attachment objects
{
        "type": "image",
        "url": "https://i.groupme.com/123456789"
      },
      {
        "type": "image",
        "url": "https://i.groupme.com/123456789"
      },
      {
        "type": "location",
        "lat": "40.738206",
        "lng": "-73.993285",
        "name": "GroupMe HQ"
      }
```

## GroupMe.sendDirectAttachmentMessage
Send a DM to another user with attachment and options text

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| recipientId| String     | The other participant in the conversation.
| sourceGuid | String     |  Client-side IDs for messages. This can be used by clients to set their own identifiers on messages, but the server also scans these for de-duplication. That is, if two messages are sent with the same source_guid within one minute of each other, the second message will fail with a 409 Conflict response.
| text       | String     | The maximum length is 1,000 characters.
| attachments| List       | A polymorphic list of attachments (locations, images, etc). You may have more than one of any type of attachment, provided clients can display it.

```
sample of attachment objects
{
        "type": "image",
        "url": "https://i.groupme.com/123456789"
      },
      {
        "type": "image",
        "url": "https://i.groupme.com/123456789"
      },
      {
        "type": "location",
        "lat": "40.738206",
        "lng": "-73.993285",
        "name": "GroupMe HQ"
      }
```

## GroupMe.likeMessage
Like a message.

| Field         | Type       | Description
|---------------|------------|----------
| accessToken   | credentials| Access token provided by GroupMe
| conversationId| String     | ID of the group
| messageId     | String     | ID of the message

## GroupMe.unlikeMessage
Unlike a message.

| Field         | Type       | Description
|---------------|------------|----------
| accessToken   | credentials| Access token provided by GroupMe
| conversationId| String     | ID of the group
| messageId     | String     | ID of the message

## GroupMe.listLikedMessages
A list of the liked messages in the group for a given period of time. Messages are ranked in order of number of likes.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | Id of the group
| period     | Select     | One of: `day`, `week`, or `month`

## GroupMe.listMyLikes
A list of messages you have liked. Messages are returned in reverse chrono-order. Note that the payload includes a liked_at timestamp in ISO-8601 format.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | Id of the group

## GroupMe.listLikesForMe
A list of messages others have liked.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| groupId    | String     | Id of the group

## GroupMe.createBot
Create a bot. 

| Field         | Type       | Description
|---------------|------------|----------
| accessToken   | credentials| Access token provided by GroupMe
| groupId       | String     | Id of the group
| name          | String     | Bot name
| avatar        | String     | Bot avatar. Note that the url must be for an image hosted by our image service.
| callbackUrl   | String     | Bot callback url
| dmNotification| Select     | Enable DM notifications

## GroupMe.sendBotMessage
Post a message from a bot

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| botId      | String     | Id of the bot
| text       | String     | Message text
| picture    | String     | Image must be processed through image service.

## GroupMe.listBots
List bots that you have created

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe

## GroupMe.deleteBot
Remove a bot that you have created

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| botId      | String     | Id of the bot

## GroupMe.getMyInfo
Get details about the authenticated user

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe

## GroupMe.updateMyInfo
Update attributes about your own account

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| avatarUrl  | String     | URL to valid JPG/PNG/GIF image. URL will be converted into an image service link (https://i.groupme.com/....)
| name       | String     | Name must be of the form FirstName LastName
| email      | String     | Email address. Must be in name@domain.com form.
| zipCode    | String     | Zip code.

## GroupMe.enableSMSMode
Enables SMS mode for N hours, where N is at most 48. After N hours have elapsed, user will receive push notfications.

| Field         | Type       | Description
|---------------|------------|----------
| accessToken   | credentials| Access token provided by GroupMe
| duration      | Number     | Maximum sms mode duration
| registrationId| String     | The push notification ID/token that should be suppressed during SMS mode. If this is omitted, both SMS and push notifications will be delivered to the device.

## GroupMe.disableSMSMode
Disables SMS mode

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe

## GroupMe.listBlockedUsers
A list of contacts you have blocked. These people cannot DM you.

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| user       | String     | Your user Id

## GroupMe.checkIfBlocked
Asks if a block exists between you and another user id

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| user       | String     | Your user Id
| otherUser  | String     | Other user Id

## GroupMe.createBlock
Creates a block between you and the contact

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| user       | String     | Your user Id
| otherUser  | String     | Other user Id

## GroupMe.deleteBlock
Removes block between you and other user

| Field      | Type       | Description
|------------|------------|----------
| accessToken| credentials| Access token provided by GroupMe
| user       | String     | Your user Id
| otherUser  | String     | Other user Id

