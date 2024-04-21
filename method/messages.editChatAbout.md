# messages.editChatAbout
Edit the description of a group/supergroup/channel.

```
boolFalse#bc799737 = Bool;
boolTrue#997275b5 = Bool;
---functions---
messages.editChatAbout#def60797 peer:InputPeer about:string = Bool;
```

## Parameters
| Name | Type | Description |
| ---- | :----: | ----------- |
| peer | InputPeer | The group/supergroup/channel. |
| about | string | The new description |


## Result
Bool

## Possible errors
| Code | Type | Description |
| ---- | :----: | ----------- |
| 400 | CHANNEL_INVALID | The provided channel is invalid. |
| 400 | CHANNEL_PRIVATE | You haven't joined this channel/supergroup. |
| 400 | CHAT_ABOUT_NOT_MODIFIED | About text has not changed. |
| 400 | CHAT_ABOUT_TOO_LONG | Chat about too long. |
| 400 | CHAT_ADMIN_REQUIRED | You must be an admin in this chat to do this. |
| 400 | CHAT_ID_INVALID | The provided chat id is invalid. |
| 400 | CHAT_NOT_MODIFIED | No changes were made to chat information because the new information you passed is identical to the current information. |
| 403 | CHAT_WRITE_FORBIDDEN | You can't write in this chat. |
| 400 | PEER_ID_INVALID | The provided peer id is invalid. |

