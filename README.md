# BattleconBot
A Gmail script to facilitate PBP games of BattleCON.

**INSTRUCTIONS**

* You and your opponent choose characters* and come up with a unique game ID between you. This is also where you'll set up the PBP thread, etc.

**I just now realised I didn't build in an option for this. But you can improvise a mutually hidden character selection easily enough using the same bot.*

* Each of you sends an email to sabattleconbot at gmail doot com. The subject line should be your game ID. In the body of the email you should put:

*Required:* "Move:" followed by the move you've chosen.<br />
*Optional:* "Active:" followed by "Y" if you're the active player this beat. For the purposes of finding out who antes first.

(If you use both, make sure they're on different lines.)

If only one of you claims active, that player is set to ante first. If both or neither of you claim active, it goes to whoever's email Battlecon Bot read first.

You should both get a confirmation email, and one of you should get an instruction that it's your turn to ante.

* You ante by sending Battlecon Bot an email containing "Ante:" followed by your ante. So long as the subject line contains your game ID this should work just fine; I know it works if you just click 'reply' to the message Battlecon Bot sent you, so... maybe just do that? And I'll try to make it more robust when I have time.

When you ante, you'll get a confirmation email and your opponent will get an email offering them the chance to ante. These messages go back and forth until both of you pass by anteing nothing.

When both players have passed, Battlecon Bot emails both of you the moves and antes, and then you can hie to your game thread and work out what all that means.

*If you want to improvise a secret character select, make your first move the name of your character then ante nothing. That'll work just fine.*

**HOW IT WORKS**

Basically, the script reads all the unread emails in Battlecon Bot's inbox every minute, and vacuums up anything following the phrases "Move:", "Active:", or "Ante:" as a plain string. It then compares these to what it knows about the game state, checks to see if they're valid inputs, and either returns an error message or records the appropriate details in its companion spreadsheet. 

It never shares anyone's emails -- it sends its messages individually.

After every beat is complete, it wipes that record from the spreadsheet, and it runs a cleanup every night to delete anything that's over 7 days old. In this way I hope to keep the spreadsheet down to a manageable size.
