# MessagePeerVote
How a user voted in a poll

```
messagePeerVote#b6cc2d5c peer:Peer option:bytes date:int = MessagePeerVote;
messagePeerVoteInputOption#74cda504 peer:Peer date:int = MessagePeerVote;
messagePeerVoteMultiple#4628f6e6 peer:Peer options:Vector<bytes> date:int = MessagePeerVote;
```

## Constructors
| Constructor | Description |
| ---- | ----------- |
| messagePeerVote | How a peer voted in a poll |
| messagePeerVoteInputOption | How a peer voted in a poll (reduced constructor, returned if an option was provided to messages.getPollVotes) |
| messagePeerVoteMultiple | How a peer voted in a multiple-choice poll |


## Methods
| Method | Description |
| ---- | ----------- |


