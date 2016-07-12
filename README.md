# BattleconBot
A Gmail script to facilitate PBP games of BattleCON.

**INSTRUCTIONS**

* You and your opponent choose characters* and come up with a unique game ID between you. This is also where you'll set up the PBP thread, etc.

**I just now realised I didn't build in an option for this. But you can improvise a mutually hidden character selection easily enough using the same bot.*

* Each of you sends an email to sabattleconbot at gmail doot com. The subject line should be your game ID. In the body of the email you should put:

*Required:* "Move:" followed by the move you've chosen.<br /> **OR** "MoveSkip:" followed by the move if you know you're not going to ante.
*Optional:* "Active:" followed by "Y" if you're the active player this beat. For the purposes of finding out who antes first.

(If you use both, make sure they're on different lines.)

If only one of you claims active, that player is set to ante first. If both or neither of you claim active, it chooses at random.

If both players use MoveSkip, no ante step will be carried out -- the game will jump straight to reveal. If one of you uses MoveSkip then the bot will prompt the other player for ante, and if they pass will jump straight to reveal. If they ante something then you will have a chance to respond.

Players will get a confirmation email when their move is selected, and assuming at least one of you didn't choose to skip ante then one of you will get an email telling you it's your turn to ante.

* You ante by sending Battlecon Bot an email containing "Ante:" followed by your ante. So long as the subject line contains your game ID this should work just fine; I know it works if you just click 'reply' to the message Battlecon Bot sent you, so... maybe just do that? And I'll try to make it more robust when I have time.

When you ante, you'll get a confirmation email and your opponent will get an email offering them the chance to ante. These messages go back and forth until both of you pass by anteing nothing.

When both players have passed, Battlecon Bot emails both of you the moves and antes, and then you can hie to your game thread and work out what all that means.

*If you want to improvise a secret character select and discards/finishers, use MoveSkip and follow it with the name of the character or the discards/finishers.*

**HOW IT WORKS**

Basically, the script reads all the unread emails in Battlecon Bot's inbox every minute, and vacuums up anything following the phrases "Move:", "MoveSkip:", "Active:", or "Ante:" as a plain string. It then compares these to what it knows about the game state -- that is, whether you're selecting moves or antes and whose move or ante it's waiting for -- and if the correct player has submitted the right kind of thing it records the string in its companion spreadsheet.

Note: It doesn't perform any checking on the strings themselves to see if they're game-legal. It assumes that you know what you're doing.

It never shares anyone's emails -- it sends its messages individually.

After every beat is complete, it wipes that record from the spreadsheet, and it runs a cleanup every night to delete anything that's over 7 days old. In this way I hope to keep the spreadsheet down to a manageable size.
