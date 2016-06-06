# Basic Gameplay

Your goal is to destroy other droids and reap the benifits of their holdings in the process, all while trying to stay robo-alive. Roam the world looking for droids with high purses & low health, but make sure your own energy is prime for an attack, otherwise you may want to consider shielding or taking cover instead.  

After you register your droid and go through the wallet sync step, the system will be able to recognize your transactions and assocaite them with your Droid.


Each other droid has a unique Attack Address, which you can use rain cryptocurrency bullets upon their person. 


## Game Progression

A round within Coindroids is one unit of time as measured by a block in the blockchain. Actions (i.e. transactions) that occur within the same block all "occur" simultaneously. If two people attack and kill the same target, the target's purse is split proportionally amongst all attackers.

In each round, you can choose to perform one of three actions (Attack, Shield and Cover). Depending on the current state of your own droid, your foes, and the environment around you, it may be better to perform some actions over others. 


Important: If there is a fork in the blockchain, Coindroids will undo all transactions from the previous block and reprocess the longer chain. Experience, upgrades and all other game data will be rolled back and will only be reprocessed if the relevant transactions are included in the longer chain.

### Deficit Payment

Due to forks, in very rare circumstances, you may have received a payout on one side of that fork that differs on the winning chain. In this case, either we will automatically payout the difference, or we will require a deficit payment to retreive the erroneously sent funds back from you.

You could always not pay it, but then you need to start a new droid :(


### Registration Transactions

Players registering new wallets by sending small sums to a registration address will be recognized and confirmed. This is done first so that any game actions by the droid are recognized even if the player has just registered.

### Purchase Transactions

All transactions from registered addresses to known Item Addresses are analyzed. All successful purchases of upgrades are equipped on the associated droid and items are added to the droid’s inventory.


### Item Equip

If you have queued up a new build, this will be applied here.

### Item Use

Any relevant Action Items are now used, including those that were just purchased. This step is primarily for Action Items that affect a droid’s health

### Shielding Transactions

All shield transactions are the first of the three main actions to be run. Droids who are shielding will shield against all attacks taken against them this round. 

### Taking Cover Transactions

Droids who are taking cover will do so against all attacks taken against them this round. 

### Attack Transactions

All the transactions from known Player Addresses to droid Attack Addresses trigger the Attack Process.

### Health Changes Committed

At this point, all damage done by other Droids from attack transactions is applied to the droid’s health. This is when we learn if a player has succumbed to their attackers or if the Droid has survived.

### Purse Rewards Calculated

All instances where a Droid has died are processed. Dead droids’ purses are divided up proportionately based on the amount of damage dealt by each of its attackers during this block. Damage performed in previous blocks is not counted towards this reward.


### Experience Changes Committed

Experience earned by the Droid through attacks and defensive maneuvers are now committed to the Droid at this time. Droids with enough experience level up (See Leveling)

### Droid Resurrection

The droids who have died, and served their time, are rebuilt and enter for the next round of battles. 


## Attack

Rawr!

<aside class="warning">
Your droid only has so much ammunition to throw around per block. Make sure to check your clip-size and take this into consideration before crafting all your attacks. 
</aside>

<aside class="warning">
All attacks a droid is making will be voided if the droid also atttempts to take a shield or cover action. 
</aside>

## Shield

Oh shit D:

<aside class="warning">
If you don't have a shield equiped, your attempt to shield probably won't go very well. 
</aside>

<aside class="warning">
All attacks a droid is making will be voided if the droid also atttempts to take a shield action. 
</aside>


## Cover

FUCK FUCK FUCK

<aside class="warning">
All attacks a droid is making will be voided if the droid also atttempts to take a cover action. 
</aside>


## Using a Consumable

## Item Drops

## Death & Taxes

## Leveling

As your droid gains experience through successful attacks, they will level up after hitting specific milestones:


|Level|Experience Needed|
|---|----|
|1|0 |
|2|600|
|3|1887 |
|4|3896|
|5|6653|
|6|10176|
|7|14483|
|8|19585|
|9|25495|
|10|32221|

Leveling up allows you to equip better items to your droid. 
