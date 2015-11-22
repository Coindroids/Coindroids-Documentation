---
title: Game Progression
tags: [game-specifications]
keywords: game, flow, execution 
last_updated: November 21, 2015
summary: "How the Coindroids game progresses through a block"

---

The state of the Coindroids system progresses every time there is a new block found within the cryptocurrency network. All related game transactions within the new block are processed in the order laid out below.

Important: If there is a fork in the blockchain, Coindroids will undo all transactions from the previous block and reprocess the longer chain. Experience, upgrades and all other game data will be rolled back and will only be reprocessed if the relevant transactions are included in the longer chain.

## Registration Transactions

Players registering new wallets by sending small sums to a registration address will be recognized and confirmed. This is done first so that any game actions by the droid are recognized even if the player has just registered.

## Purchase Transactions

All transactions from registered addresses to known Item Addresses are analyzed. All successful purchases of upgrades are equipped on the associated droid and items are added to the droid’s inventory.

## Item Use

Any relevant Action Items are now used, including those that were just purchased. This step is primarily for Action Items that affect a droid’s health

## Attack Transactions

All the transactions from known Player Addresses to droid Attack Addresses trigger the Attack Process.

## Health Changes Committed

At this point, all damage done by other Droids from attack transactions is applied to the droid’s health. This is when we learn if a player has succumbed to their attackers or if the Droid has survived.

## Purse Rewards Calculated

All instances where a Droid has died are processed. Dead droids’ purses are divided up proportionately based on the amount of damage dealt by each of its attackers during this block. Damage performed in previous blocks is not counted towards this reward.

```
Payout = Percent of Damage Dealt * Droid Purse
```

## Experience Changes Committed

Experience earned by the Droid through attacks and defensive maneuvers are now committed to the Droid at this time. Droids with enough experience level up (See Leveling)
