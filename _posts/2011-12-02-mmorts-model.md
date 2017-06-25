---
layout: post
title: MMORTS Model
---
So I recently [answered a question](http://gamedev.stackexchange.com/questions/20469/what-has-stopped-mmorts-games-from-being-successful/20474#20474) on the [Game Development Stack Exchange](http://gamedev.stackexchange.com/) site related to an MMORTS (Massively Multiplayer Online Real-Time Strategy) and why that had never come to fruition. And, a few years ago now, some friends and I tried to tackle this very problem and find out how we could do just that. This was before WOW became what it is today, and was more around the time of Everquest. None of us played Everquest, but we were familiar with the mechanics and loved to play Starcraft and Warcraft 3, so we set out at designing what it would look like to have an RTS in a persistent world.

The following are some of the issues we foresaw as being problems in translating the genre to an MMO and also listed are our ideas for solving these problems. By no means is this perfect, and it skips over a lot of the aspects we'd planned for story-wise as well. This is not a copy of the design document; I wouldn't subject anyone to that. We were 14 at the time, and while we were okay at writing (for our age), and were inspired, looking back I can now say with absolute certainty our game never would have made it anywhere.

## Issues we addressed

### Offline

The issue that stands out first is really the fact that in a persistent world, the user will be offline, but the world will not. So, in an RTS, what does that mean? In an RPG like WOW, it's easy. You are a character, and the world can function without you for the most part (the heroine may go unsaved, or have moved castles, but the baddies can keep on being bad). But in an RTS, you are the drive for the world. The environment can go on, but you play God for all of the people, so what are they going to do when you're not around? Well, you might think "easy again" they continue on, just like the environment would. They don't do anything drastic, but continue to mine gold, forage for food, etc.

But if they exist still, and don't blink from existence like you would in an RPG, what about other users? Can they interact with you? Start a trade route or something? What if you get a bad deal? What if they attack? To solve these issues, we actually looked to our story. Since you are not a physical entity in an RTS, but a top down commander, we couldn't just take you out of the equation. But in many RTS games, you play in the role of a commander, or a leader. The units respond not as if you are God, but as if you are entity issuing orders. Adding in that physical entity gives us something to take out of the equation, but it still doesn't solve the problem. Unless, that is, we don't allow trade or attacks without prior knowledge.

This is where the story comes in, and we'll see it can be used to solve a lot of problems. Consider the world not as a system of continents, but a system of planets. Each person has a world, unique to themselves that they can build and explore upon in traditional RTS fashion. But, when they decide to become space bound, they enter into one of two 'factions' (now you should be seeing the similarities with an MMORPG). These factions have some agreements amongst themselves, and have a few agreements with the opposing faction. Now, you have a system by which you can implement rules that all users must follow. When a user goes offline, a defense surrounds their planet, and other planets cannot attack, trades are unable to be completed, but can be initiated, and various other simple protections for the offline user.

But what about those trying to exploit those protections. I'll cover more in the PVP section, but the simple end of it is that a skirmish in progress affords only minor protections, and new skirmishes cannot be initiated. Again, more will be covered in the PVP section.

### The World

You get a planet. That was our solution. I'll talk more about how you get your planet in the New Players section, but when it comes down to it, that's what you do. And you expand. On the basic level, it is like SimCity. Each player gets a planet to 'Rule' and so no player can encroach on another player's planet. Unless you win one (PVP), but no two players can own the same planet at the same time. They can exist on the same planet, but everyone has a series of 'Home' planets which they run, unopposed *by players*.

### PVE

This part was probably the toughest part initially when we first started designing this. In fact, even now, I don't think we had a very good idea for solving this problem. We had some interesting extra things, but there wasn't a lot you could do to seek out PVE.

Our basic idea was that on home planets, you would have factions to fight, rebels to weed out, and competing civilizations to destroy. You planet would in itself be an RTS/RPG (See Death and New Players) game for you to play. And other players from your faction could assist you in your hunt. A multiplayer RTS when it comes down to it. We'd also planned on having Alien planets. These would act as 'dungeons' of a sort in which players could band together, and send out an army to conquer (or accomplish a task). These could also include special ideas and challenges for players, just like raids do, where players have basically face bosses.

The more fun one (and the one also involved in Death, see below) is one of a rebellion. The idea was that you hear reports of rebellions trying to overthrow or assassinate you, and you have to try to stop them. Once you take the job, it can vary on how you have to do it. This is were you can have fun and blur lines between genre's of games, and things really start to pick up. Though, since the game never made it very far, we didn't get a chance to do much else with this.

### PVP

#### In Faction

Within a faction there are still wars. You can still 'skirmish' with your friends, just like you can duel in an RPG. There are two ways to initiate a skirmish, and each has a corresponding element in an RPG. The first method is to flat out declare war. You set the terms of battle (if you can attack offline, what that means, where battles can take place, what the stakes are, etc.) and you battle it out. "Community support is provided for duels to repair buildings", so that, just like dueling, it can be for fun. Wars can involve 2 people or more, and can span a single planet or all of them.

The second method is dependent on the active server. Just like in an RPG, you can have PVE or PVP servers. In a PVP server, you can also perform sneak attacks. These cannot be done while a user is offline, and is initiated by one of the parties. If both are doing a sneak attack, then it is just who gets there first. If there is a significant difference in level, assistance is provided by the faction to the lower level player. A sneak attack can be accepted as a declaration of war, or it can be written off as water under the bridge, which allows the attacked person to effectively decline the duel. If it goes off successfully and the duel is ceded, losses are not completely taken care of by the 'community' and take a half hour to 'repair'. This means that you can't deny the duel just to ensure they have no advantage. There would likely also need to be other rules in place, but we didn't get that far.

#### Opposing Factions

Opposing factions run heavily on the same rules, and also rely on the server type for how combat is handled. Unlike in faction duels, these attacks count towards the overall structure, and you can loose and die. Death is explained below, but the stakes of initiating it are much higher. It is also an open declaration of war and, just like in MMORPGs, attacking one person means you are open to attack from others.

There would also be contested worlds, on which players can build 'temporary' bases to fight out with other random sets of players in an arena style play.

### New Players

New players all have to become ruler of their planet before they can join a faction. This would build like a normal RTS likely with some twists. Once they join a faction, other rules come into play. This 'tutorial' of sorts would get them used to the system and how it works, and allow an introduction to things. Sadly, this part was not designed very well, so this would probably need to be discussed a lot if we ever chose to implement any of this.

### Death (or the fun part)

Death is honestly a great part. We'd considered it like assassin's creed with a twist. Once you die, you essentially start on a quest to regain control over your planet and its resources by starting a rebellion and successfully getting back to power. This would switch to more of an action game or RPG and there would be a few ways in which you could go about it. You could gather people to get an army and switch to an RTS take over. Or you could assassinate the ambassador on the planet to regain control. While the other player is in control of your kingdom, for all the time you are online, they gain resources. If it took too long, there would probably be a mechanism to get users back up without having to complete this mini-game.

## Issues we did not address

### The point

We never came up with a good cohesive reason for playing the game. PVE and PVP were decent, but would occur after a period of time, and resources had been acquired, so they wouldn't be initial motivators. We'd also considered a force opposed to both factions, and that would probably be a decent hook if done well, but we never developed it, so this was really untackled.

### Scale

This all scales terribly. User-side loading is easy enough to manage, but having to keep storage information for an entire world for every user, even a small world, is not feasible. Storage was the biggest issue with this, and as 14 year-olds, we just gave up at that point. We knew that even if it could be done, we didn't have enough money or a good enough idea to do it successfully. Potentially people smarter than I could figure out a way to design it in which storage was less of an issue, but that's to be seen.

A lot of work for a game never made, but I think there are nuggets of good ideas in there. If someone can take them and successfully turn it into a working game, you can definitely sign me up.
