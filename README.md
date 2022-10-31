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
