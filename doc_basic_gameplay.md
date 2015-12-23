---
title: Basic Gameplay
tags: [rules, help]
keywords: help, play, what, how, token, attack 
last_updated: December 9, 2015
summary: "An intro to Coindroids gameplay"

---


## High Level Details 

Coindroids is a battle game where your objective is to attack and destroy other robots by blasting them with cryptocurrency. The game is played by sending coins to various addresses during a certain block. These transactions attack other droids, or purchase items that magnify the offensive or defensive capabilities of your droid.

## Why would I spend money to attack a virtual robot?

Coindroids is a strategy game that is played with cryptocurrency transactions. When you kill another droid, you win the contents of their purse.
For example, if your attack spent 3 tokens to kill a robot with 5 tokens in his purse, you just earned a profit of 2 tokens! Your profitability depends entirely on the strategy you use to choose which droid to attack, how much to spend on your attack, and whether or not you should attack now or wait for another block that has a better 'environment' ([FOCUS and ENERGY](doc_game_specification_droids.html#dynamic-attributes)) for your robot.


### Round

A round within Coindroids is one unit of time as measured by a block in the blockchain. Actions (i.e. transactions) that occur within the same block all "occur" simultaneously. If two people attack and kill the same target, the target's purse is split proportionally amongst all attackers.

## Attacking Other Players

The hardest part about Coindroids is choosing who to attack this round - if anyone. Details of every droid in the Coindroids universe is available from the Coindroids website or the API. You will want to look at the `health_current` of the droid to get an idea of how much damage you need to deal to kill them, as well as their `purse_current` to get an idea of how much would be won when they die.

### Minimum Attack Size

There is a minimum attack size of 0.0001 BTC. All attacks smaller than this are considered "dust" and are accepted as donations and will not be returned.

### Attack Bonuses

Your damage will be multiplied by bonuses found on any item you have equipped, and divided by bonuses found on any item your target has equipped. Your droid is affected by two environment variables: `focus` and `energy` which alter your weapons' damage and the strength of your defensive armaments. Details about these calculations can be found in the [Attack](doc_game_specification_attack_process.html#Attack) section of this documentation.


## Buying Items

If you need to become a more effective killing machine, you can buy items to augment your abilities. New weapons can increase your attacks with a multiplier (so you can deal the same damage by sending 0.0002 instead of sending 0.0004!), or increase your droid's defensive abilities with a multiplier (so enemies need to send more coins to deal the same amount of damage against you). Other items can give your droid a counter-attack ability that damages everyone who attacks you, as well as other neat duration effects that last multiple blocks (i.e. heal 50 hitpoints per block for the next 3 blocks, or give me 20% chance to evade attacks for the next 5 blocks).

In Coindroids, you buy items by sending the purchase price to an item’s purchase address. You can find the purchase addresses for all items by visiting the Unlocks page on the site, or querying the [Item](doc_object_item.html) view on the API.

For information about how Items work, take a look at the [Item](doc_game_specification_items.html) documentation within the Core Rules section.

## Statistics

Droids have a number of attributes but these are the two key to understand. 

### Health

* Level 1 players have a maximum of 100 health points

* This limit increases as you level up.

* If your health reaches 0, you die and the contents of your purse are distributed to your attacker(s)

* Your droid will be repaired automatically and return to maximum health when the next block is mined

* There are some items that can heal your droid before it dies if you’d rather not lose your purse!

### Purse

* Level 1 players can hold up to 100 tokens in their purse

* This limit increases as you level up.

* Players start the game with 0 tokens in their purse

* Tokens are added to your purse whenever you or your enemies buy items or attack each other

* When your purse is full, all tokens that can’t fit will be sent to your payout address immediately. This means that if your droid's purse is full, everyone who attacks your droid will be giving money to you! Stay alive to keep your purse filled and your profits flowing!

