---
title: Droids 
tags: [Droids, Game-Specifications]
keywords: droids 
last_updated: November 21, 2015
summary: "Understanding Droids"

---

Every player in the game is a Droid, a futuristic robot with many attributes. These attributes dictate how well they perform in a battle, be they attackers or defenders. They can also be purely cosmetic and simply make the character cool, hip and/or scary.

## Static Attributes



### Basic Droid Attributes

|Name|Description|Starting Value|
|----|----|----|
|Level|The current level of the player. The level of a player dictates some other elements including Purse Maximum, Health Maximum, as well as what items can be purchased. | 1 |
|Experience| This value is increased every time the droid is involved in a battle. More of this will be described in the Attack Process section.|0|
|Purse|The current amount of cryptocurrency that will be distributed to the droid’s next murderer(s).|0|
|Purse Maximum|The amount of cryptocurrency the purse will hold before paying out excess funds to the droid’s owner.|Dependant on cryptocurrency|
|Health|The amount of health remaining for the droid.|100|
|Health Maximum|The amount of health the droid will have upon resurrection|100|
|Build| The collection of items that make up the droids equipment| Base Model of the users choice|
|Inventory| The collection of usable items active on the droid| |


### Build & Inventory Influencing Attributes 

|Name|Description|
|----|----|
|Attack Multiplier|A value that is used to multiply the amount of base damage being performed by the attacking Droid during the Attack Process.|
|Accuracy| A percentage dictating the amount of base damage that will be successfully performed during an attack (prior to the victim Droid’s defense).|
|Defense| A value that dictates the ability of the Droid to absorb damage during an attack.|
|Evasion| A percentage dictating the likelihood that a Droid will successfully dodge an attack from another Droid.|
|Counter-Attack| A percentage dictating the likelihood that the Droid will try to cause damage to the originally attacking player during the Attack Process.|

## Dynamic Attributes

These attributes are a bit more complicated than the others. They are dynamic, meaning they change regularly without user interaction, however they are also still deterministic. When taken into consideration by a player, these dynamic values allow for a much more strategic element of the Attack Process based on timing.

|Name|Description|
|----|----|
|Energy| Even powerful Droids need a recharge now and then. Droids with low energy may not be able to run away and their attacks may have reduced strength|
|Focus|A Droid distracted by other processes and interfaces may not notice incoming attacks. Similarly, their shots may not be as accurate.|

### Calculating Dynamic Attributes
Both of these values can each be calculated using the same algorithm. The value is unique per user and will change every time a new block of transactions is processed. The workflow to calculate these values is as follows:

#### Step 1 – Get the Hash of the Last Block

Get the hash of the last solved block for the blockchain in use. As an example, this can be done with bitcoind like so:

```
	./bitcoind getbestblockhash 0000000000000000117044f0da99c88f1266c57eee5a7f08e2eaf9a9a83091f9
```

#### Step 2 – Perform a SHA256 Hash of the known details

Using the hash found in step one, referred to as `<highest block hash>`, concatenate this value along with the capitalized name of the attribute being calculated, and the ID of the droid as a single text string. Finally, perform a SHA256 hash of this value.

```
	SHA256(<best block hash> + <Attribute Name> + <Droid ID>)
```

Continuing on with a real example, the sha256 function for each attribute would be calculated like so:

##### Energy

```
	SHA256( 0000000000000000117044f0da99c88f1266c57eee5a7f08e2eaf9a9a83091f9ENERGY4 )
	88435b0191439b818d5bee558dbc8ed4831f43df17748ee4a8f22b4be1542bf5
```

##### Focus

```
	SHA256( 0000000000000000117044f0da99c88f1266c57eee5a7f08e2eaf9a9a83091f9FOCUS4 )
	e106950e4cb0ca0d87a0c74a1d6862a6c9bfda6dcebd71480ddb04f68cad85de
```

#### Step 3 – Convert a portion to decimal

Using the result from Step 2, take the first byte (i.e. the first 2 characters) and convert the hexadecimal value to decimal.

##### Energy

```
	88 Hexadecimal = 136 Decimal
```

##### Focus

```
	e1 Hexadecimal = 225 Decimal
```

#### Step 3 – Evaluate the final Results as a percentage

Finally: with the decimal value, calculate the percentage based on a byte's maximum value to get the attribute value for each variable during this block of transactions.

```
	Energy = 136 / 255 = 53.3% 
	Focus = 225 / 255 = 88.2%
```

Programmatically (and pythonically...), this looks like the following:

```
import hashlib

def calculate_energy(previous_block_hash, droid_id):
    energy_input = previous_block_hash + 'ENERGY' + str(droid_id)
    energy_hash = hashlib.sha256(energy_input).hexdigest()
    first_byte = int(energy_hash[0:2], 16)
    energy_value = first_byte / 255.0
    
    return energy_value

def calculate_focus(previous_block_hash, droid_id):
    focus_input = previous_block_hash + 'FOCUS' + str(droid_id)
    focus_hash = hashlib.sha256(focus_input).hexdigest()
    first_byte = int(focus_hash[0:2], 16)
    focus_value = first_byte / 255.0
    
    return focus_value
```

## Leveling
As Droids gain experience, their level increases at certain targets. Leveling up allows a Droid to handle bigger and better upgrades and items.
At each level, the Droid’s Purse Maximum and Health Maximum attributes both increase at steady rates.

```SQL
     WHILE ((next_level^5)-(next_level^4)+(next_level^2)+300*next_level) < new_experience LOOP
      next_level      = next_level + 1;
      new_health_max  = new_health_max + (next_level * 10);
      new_purse_max   = greatest( ( (new_health_max * token_size_ ) / 2)::BIGINT, (100 * token_size_) );
    END LOOP;
```
