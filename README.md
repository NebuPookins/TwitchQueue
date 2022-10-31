# TwitchQueue

This is a webpage that can be used as an OBS Browser source to implement a
simple queue of players, each of who gets a certain amount of time. In its
default configuration, players join the queue by typing in `!rp` into chat.
The players are added to a list in the order in which they joined. The player
at the top of the queue is the current player, and they get a 5 minute timer
to do whatever it is they need to do. Then, that player is removed from the
list, and the next player's turn starts, with the timer reset. Moderators and
the broadcaster can use `!rp skip` to skip the current player's turn, and
`!rp add 100` to add 100 extra seconds to the timer.

The command is configurable (for example, you can make the command be `!join`
instead of `!rp`), and the default timer length is confiruable (for example,
you can make it be 3 minutes instead of 5 minutes).

Players can't join the queue if their name is already currently on the queue.
That is, a player can't put their name five times in a row. Instead, they
must wait until their turn is over, and their name is removed from the queue.
At that point, they can rejoin by retyping in the join command if they wish.

## How to use

TODO: It's complicated to set up right now. When I have time, I'll try to add
a configuration wizard that'll set it up for you.

Browser source is accessible directly at https://nebupookins.github.io/TwitchQueue/
with an instance configured to point to my (NebuPookins) channel. To
configure the instance (for example, to point it to a different Twitch
channel), you need to provide an Base64 LZMA compressed JSON with the new
configuration values. For example, the URL that points to my channel, but
which has the command be `!join` instead of `!rp` is:
https://nebupookins.github.io/TwitchQueue/?N4Igxg9gtlCGB2ATEAuEBCAVhAlvEAvkA===

For now, the easiest way to configure the instance is to go to
https://nebupookins.github.io/Base64LzmaToJson/ and then paste the following
JSON in the right hand side of the editor:

```json
{
  "twitchChannel": "nebupookins",
  "command": "!rp",
  "turnLengthInSeconds": 300
}
```

When you do that, you'll see the left-hand side of the editor get filled in
with `N4IgLg7glmDGAWBheBDAdmgpgGxALhCwCMBXABwHsKBrKNAZxABoRYKBbd9AE3xAEIATmWbgSgtABlMaAOZh4ASTQBlTGzTdGeAMwAGPQF8gA===`.
That string is what you would put in after the question mark of
`https://nebupookins.github.io/TwitchQueue/?`, so your URL would be
`https://nebupookins.github.io/TwitchQueue/?N4IgLg7glmDGAWBheBDAdmgpgGxALhCwCMBXABwHsKBrKNAZxABoRYKBbd9AE3xAEIATmWbgSgtABlMaAOZh4ASTQBlTGzTdGeAMwAGPQF8gA===`
in this example.

Edit the JSON as needed, and it'll generate a different code for you.
Whatever code it produces is the code you need to put after the question mark
in the URL.
