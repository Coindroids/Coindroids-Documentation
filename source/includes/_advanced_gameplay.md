
# Advanced Gameplay

Everything in the Coindroids world is deterministic. The Advanced Gameplay guide is here to help you unlock the secrets of the world and begin to full develop your battle strategy. 


## Dynamic Attributes

```shell
# Step 1 – Get the Hash of the Last Block
./bitcoind getbestblockhash 0000000000000000117044f0da99c88f1266c57eee5a7f08e2eaf9a9a83091f9
# Step 2 – Perform a SHA256 Hash of the known details
 SHA256( 0000000000000000117044f0da99c88f1266c57eee5a7f08e2eaf9a9a83091f9*ENERGY*4 )
 88435b0191439b818d5bee558dbc8ed4831f43df17748ee4a8f22b4be1542bf5
# Step 3 – Convert a portion to decimal and evaluate the final Results as a percentage
 88 Hexadecimal = 136 Decimal
 Energy = 136 / 255 = 53.3% 
 
```

```python
import hashlib

def calculate_dynamic_attribute(attribute_type, previous_block_hash, droid_id):
    attribute_input = previous_block_hash + attribute_type + str(droid_id)
    attribute_hash = hashlib.sha256(attribute_input).hexdigest()   // This produces a hash with lower-case letters
    first_byte = int(attribute_hash[0:2], 16)
    attribute_value = first_byte / 255.0
    attribute_value = round(attribute_value, 4)
    
    return attribute_value
```

```javascript
function calculateDynamicAttribute(attributeType, blockHash, droidID) {
    var attribute_input = blockHash + attributeType + droidID.toString();
    var attribute_hash = sha256(attribute_input);
    var first_byte = parseInt(attribute_hash.substring(0, 2), 16);
  
    var value = first_byte / 255.0;
    value = Math.round(value * 10000) / 10000;

    return value;
};

```


Some attributes used within the system are based off of previous block hashes. This is to provide the droids with a fun changing environment to battle within, while still giving them the pleasure of calculating every bit of their strategy. 


|Name|Description|
|----|----|
|Energy| Even powerful Droids need a recharge now and then. Droids with low energy may not be able to run away and their attacks may have reduced strength|
|EMI| Most of a droid is actually held together by magnets. As a droids' EMI fluctuates, this will govern how easily parts and materials fall off during attacks. |
|Cover| Keep an eye on your surroundings. If this value is high that means there are some useful objects around, be them walls, ditches or perhaps some sort of soft woodland creature that you can take cover behind to prevent damage.|

### Calculating Dynamic Attributes
Both of these values can each be calculated using the same algorithm. The value is unique per user and will change every time a new block of transactions is processed. The workflow to calculate these values is as follows:

1. Get the hash of the last solved block for the blockchain in use

2. Using the hash found in step one, referred to as `<highest block hash>`, concatenate this value along with the capitalized name of the attribute being calculated, and the ID of the droid as a single text string. Finally, perform a SHA256 hash of this value. ```SHA256(<best block hash> + <Attribute Name> + <Droid ID>)```

3. Using the result from Step 2, take the first byte (i.e. the first 2 characters) and convert the hexadecimal value to decimal. Finally: with the decimal value, calculate the percentage based on a byte's maximum value to get the attribute value for each variable during this block of transactions.



## The Attack Process


<script type="text/javascript"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

<script>
MathJax.Hub.Config({
  displayAlign: "left",
  tex2jax: {
    skipTags: ['script', 'noscript', 'style', 'textarea', 'pre']
  }
});

MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i=0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>

### Checking Clip Size

Droids only have so much ammunition they can attack with per block. 


### Allocate Incoming Funds 


The amount transferred to the Attack Address is split up and applied to the relevant purses across the system. 

* 75% into the purse of the defending droid
* 24.5% as spilled ammunition 
* 0.5% as service fees



### Calculate Damage

First the base attack is calculated, taking into consideration all upgrades equipped to the droid.  During this calculation, the weapon’s accuracy and the droid’s dynamic attributes are all taken into account for the resulting gross damage. 

$$grossDamage = 2 \times \left ( \frac{Ammo Fired}{Token Size} \times Damage \times \left (Accuracy + (100 - Damage) \times \frac{Energy}{100} \right ) \right ) - \left ( \frac{Damage \times Weapon Unlock}{Level} \right )$$

	


### Calculate the Defender’s Defense

The defense is culculated one of three ways, depending on the status of the defender.

#### Normal Defense
$$netDamage = \frac{grossDamage \times (100 - Defense \times 0.9)}{100} $$

#### Defense when Shielded
$$netDamage = \frac{grossDamage \times (100 - Defender Shield \times 0.9)}{100} $$

#### Defense when Taking Cover
$$netDamage = \frac{grossDamage \times (100 - Cover \times 0.9)}{100} $$


We can then begin to calculate the Net Damage to be taken by the defending droid. The equation for this is as follows: 

$$Net Damage = Gross Damage \times (1 - Droid Defense)$$

Once these calculations are complete, the Net Damage is the actual amount that is then subtracted from the defending droid’s health. 

$$Defending Droid Health = Current Health – Net Damage$$


### Awarding Experience 

The experience gained from a battle is easily calculated for either droid by using the results of each of the above steps. The experience is not applied until the Experience Changes Committed phase of the Game Progression, which means that any leveling up does not occur until all the attacks are complete.

$$Attacker Experience Increase =  100 \times ( \frac{netDamage}{Defenders Current Health}) \times ( \frac{( 2 \times Defenders Level)}{Attackers Level + Defenders Level} )$$


### Item Drop Algorithm

An item drop occurs during an attack depending on the defenders EMI, their own EMS, and the strength of the attack. 


