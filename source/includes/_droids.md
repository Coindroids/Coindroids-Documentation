
# Droids

Every player in the game is a Droid, a futuristic robot with many attributes. These attributes dictate how well they perform in a battle, be they attackers or defenders. They can also be purely cosmetic and simply make the character cool, hip and/or scary.

All droids have some pretty basic attributes:


|Name|Description|Starting Value|
|----|----|----|
|Level|The current level of the player. The level of a player dictates some other elements including Purse Maximum, Health Maximum, as well as what items can be purchased. | 1 |
|Experience| This value is increased every time the droid is involved in a battle. More of this will be described in the Attack Process section.|0|
|Purse|The current amount of cryptocurrency that will be distributed to the droid’s next murderer(s).|0|
|Health|The amount of health remaining for the droid.|100|
|Health Maximum|The amount of health the droid will have upon resurrection|100|
|Build| The collection of items that make up the droids equipment| Base Model of the users choice|
|Inventory| The collection of usable items active on the droid| |


## Chassis 

Your chassis starts with a Torso, with some other items tacked on for either style of function. Perhaps you fancy a set of legs, or maybe even arms. The parts you choose have a number of effects, so choose carefully. 

When you are starting out, you can choose from any of the following sets:

### Tank Training 

> ![Tank Training](images/droid_TANK.png)

| Item Type | Class | Defense | Defense at Unlock | Defense Set Percentage| 
|-----------+-------+----------+----------+----------|
| Head      | Tank  | 0        | 0        | 0.1|
| Torso     | Tank  | 0        | 0        | 0.4|
| Arm       | Tank  | 0        | 0        | 0.1|
| Arm       | Tank  | 0        | 0        | 0.1|
| Leg       | Tank  | 0        | 0        | 0.3|

|Item Type | Class | Damage |  Accuracy (Likely)  | Clip Size | 
-----------+-------+----------+------------+----------
| Weapon    | Tank  | 1        | 0.5 (0.75) | 1|

### Assault Training

> ![Tank Training](images/droid_ASSAULT.png)

| Item Type | Class | Defense | Defense at Unlock | Defense Set Percentage| 
|-----------+-------+----------+----------+----------|
| Head      | Assault | 0        | 0        | 0.1|
| Torso     | Assault | 0        | 0        | 0.5|
| Arm       | Assault | 0        | 0        | 0.1|
| Arm       | Assault | 0        | 0        | 0.1|
| Leg       | Assault | 0        | 0        | 0.1|
| Leg       | Assault | 0        | 0        | 0.1|

|Item Type | Class | Damage |  Accuracy (Likely)  | Clip Size | 
-----------+-------+----------+------------+----------
| Weapon    | Assault | 1        | 0.5 (0.75) | 1|


### Scout Training

> ![Tank Training](images/droid_SCOUT.png)


| Item Type | Class | Defense | Defense at Unlock | Defense Set Percentage| 
|-----------+-------+----------+----------+----------|
| Head      | Scout | 0        | 0        | 0.1|
| Torso     | Scout | 0        | 0        | 0.3|
| Arm       | Scout | 0        | 0        | 0.15|
| Arm       | Scout | 0        | 0        | 0.15|
| Leg       | Scout | 0        | 0        | 0.15|
| Leg       | Scout | 0        | 0        | 0.15|

|Item Type | Class | Damage |  Accuracy (Likely)  | Clip Size | 
-----------+-------+----------+------------+----------
| Weapon    | Scout | 1        | 0.5 (0.75) | 1|

## Weaponry 

TODO: Explain how weaponry works


## Defenses


TODO: Explain how defense works here

## Inventory

Droids bodys are pretty efficient and don't have a lot of spare space to carry items around. As such, there is a very limited amount of items you can carry with you. A limit of 1 to be exact. Add an item to your inventory and it will be used until it expires (based on the Lasts attribute).

## Player Garage

Your garage can store all those parts you aren't using at the moment. There is a LOT of space in this place, so there is no limit to the parts, materials or magic objects that you can store here. You can even store items beyond your droids equip restrictions (i.e. level and scope)

## Dynamic Attributes

These attributes are a bit more complicated than the others. They are dynamic, meaning they change regularly without user interaction, however they are also still deterministic. When taken into consideration by a player, these dynamic values allow for a much more strategic element of the Attack Process based on timing.

|Name|Description|
|----|----|
|Energy| Even powerful Droids need a recharge now and then. Droids with low energy may not be able to run away and their attacks may have reduced strength|
|Cover| This value reflects the amount of good cover around that you can take advantage of |
|EMI| Electro-Magnetic Interference. More interference means less grasp on your parts and materials|


<aside class='notice'>
For more information on calculating these dynamic values, see Advanced Gameplay
</aside>
