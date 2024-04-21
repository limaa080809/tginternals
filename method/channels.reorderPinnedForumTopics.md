# channels.reorderPinnedForumTopics
Reorder pinned forum topics

```
updatesTooLong#e317af7e = Updates;
updateShortMessage#313bc7f8 flags:# out:flags.1?true mentioned:flags.4?true media_unread:flags.5?true silent:flags.13?true id:int user_id:long message:string pts:int pts_count:int date:int fwd_from:flags.2?MessageFwdHeader via_bot_id:flags.11?long reply_to:flags.3?MessageReplyHeader entities:flags.7?Vector<MessageEntity> ttl_period:flags.25?int = Updates;
updateShortChatMessage#4d6deea5 flags:# out:flags.1?true mentioned:flags.4?true media_unread:flags.5?true silent:flags.13?true id:int from_id:long chat_id:long message:string pts:int pts_count:int date:int fwd_from:flags.2?MessageFwdHeader via_bot_id:flags.11?long reply_to:flags.3?MessageReplyHeader entities:flags.7?Vector<MessageEntity> ttl_period:flags.25?int = Updates;
updateShort#78d4dec1 update:Update date:int = Updates;
updatesCombined#725b04c3 updates:Vector<Update> users:Vector<User> chats:Vector<Chat> date:int seq_start:int seq:int = Updates;
updates#74ae4240 updates:Vector<Update> users:Vector<User> chats:Vector<Chat> date:int seq:int = Updates;
updateShortSentMessage#9015e101 flags:# out:flags.1?true id:int pts:int pts_count:int date:int media:flags.9?MessageMedia entities:flags.7?Vector<MessageEntity> ttl_period:flags.25?int = Updates;
---functions---
channels.reorderPinnedForumTopics#2950a18f flags:# force:flags.0?true channel:InputChannel order:Vector<int> = Updates;
```

## Parameters
| Name | Type | Description |
| ---- | :----: | ----------- |
| flags | # | Flags, see TL conditional fields |
| force | flags.0?true | If not set, the order of only the topics present both server-side and in order will be changed (i.e. mentioning topics not pinned server-side in order will not pin them, and not mentioning topics pinned server-side will not unpin them).  If set, the entire server-side pinned topic list will be replaced with order (i.e. mentioning topics not pinned server-side in order will pin them, and not mentioning topics pinned server-side will unpin them) |
| channel | InputChannel | Supergroup ID |
| order | Vector<int> | Topic IDs » |


## Result
Updates

## Possible errors
| Code | Type | Description |
| ---- | :----: | ----------- |

