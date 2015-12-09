---
title: The Attack Process
tags: [game-specifications, attacks]
keywords: api, authentication 
last_updated: November 21, 2015
summary: "A breakdown of all algorithms used during battle"

---

<script type="text/javascript"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

<script>
MathJax.Hub.Config({
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



## Allocate Incoming Funds 


The amount transferred to the Attack Address is split up and applied to the relevant purses across the system. 

* 75% into the purse of the defending droid
* 20% as spilled ammunition 
* 5% as service fees

_Purse Check: If any of the updated purses now have more than their Purse Maximum, the difference is immediately paid out to those players and their Purse is deducted to reflect that._  


## Check for Evasion

If a defending droid has an item equipped that increases their ability to evade, this is the point in the Attack Process where that evasion takes place.

The calculation to find out if a droid will evade an attack involves the equipment upgrades they have, as well as their dynamic attributes Energy and Focus.
If the following is true, then the droid successfully evades the attack and takes no damages.  The Awarding Experience section is skipped if there is a successful evasion.    

```Sum(Droid’s Evasion Attributes) => (Focus + Energy) / 2 ```

_Reminder: Focus and Energy change dynamically every block, but they can be determined through the means discussed in Calculating Dynamic Attributes._


## Attack

Assuming the defending droid has not evaded, the actual attack is now calculated. 


### Calculate Damage

First the base attack is calculated, taking into consideration all upgrades equipped to the droid.  During this calculation, the weapon’s accuracy and the droid’s dynamic attributes are all taken into account for the resulting gross damage. 

$$GrossDamage = Tx Amount \times \left (  2 \times \left (Primary AtkMultiplier \times \frac{Primary Accuracy + \frac{Energy + \left (Focus \times   2 \right ) }{3}}{2}\right ) + \left ( Seconday AtkMultiplier \times  \frac{Secondary Accuracy + \frac{Energy + \left (Focus \times   2 \right ) }{3}}{2} \right ) \right )$$

Your Primary Weapon’s damage, after the accuracy is taken into consideration, is multiplied by two (2). The Secondary Weapon’s damage is not multiplied.  

Once the Gross Damage of the droid’s attributes is calculated, active items belonging to the droid are then calculated. Each item uniquely increase damage through a percentage-based multiplier, calculated against the Gross Damage found in the step above. 

_If the droid has no active items, or if no active items have damage multipliers, then this step is skipped._  

```
Gross Damage =
	Gross Damage 
+ (Gross Damage * (1 / First Item Attack Multiplier))
+ (Gross Damage * (1 / N Item Attack Multiplier))
```

The result of all of the above calculations now reflect what is considered the final Gross Damage to be performed by this droid in this attack. 	


### Calculate the Defender’s Defense

The defense of the defending droid is calculated based on their own equipment upgrades and any purchased items, and then applied against the attacking droid’s Gross Damage (as calculated in the step above). 

First, we take the droid’s defense attributes from their chassis and upgrades. 

```
Droid Defense = 
(
  Droid Chassis Defense
+ Shield Defense 
+ Armor Defense
) 
/ 300
* 90%
```

_The value found by adding the Chassis, Shield and Armor is then divided by 300 to get the average percentage of all three defensive attributes. This result is then multiplied by 90% to prevent it from ever blocking 100% of the damage._ 

We can then begin to calculate the Net Damage to be taken by the defending droid. The equation for this is as follows: 

```
Net Damage = Gross Damage * (1 - Droid Defense)
```

Then we can apply the active items that have defensive attributes. 

```
Net Damage = 
	Net Damage 
- (Gross Damage * (1-(First Item Defense))
- (Gross Damage * (1-(N Item Defense))
```

Once these calculations are complete, the Net Damage is the actual amount that is then subtracted from the defending droid’s health. 

```Defending Droid Health = Current Health – Net Damage```


## Counter-Attack

If a defending droid has any upgrades and/or items that provide them a counter-attack, attacks against the originating attacker are now attempted.

A counter-attack only succeeds if the probability is greater than the current energy of the droid. *Unsuccessful counter-attacks are not included in this equation*. A droid may have multiple successful counter-attacks depending on their upgrades and items.

### Calculate Counter-Attack Damage

```
Counter-Attack Gross Damage = 
Attribute One Counter-Attack Damage 
+ Attribute N Counter-Attack Damage
```

Once the Counter-Attack Gross Damage is calculated, this is compared against the original attacker droid’s defenses.

### Calculate Counter-Attack Defenses

```
Counter-Attack Net Damage = 
Counter-Attack Gross Damage * (1 – Attacker Droid Defense) 
```

Finally, the Counter-Attack Net Damage is the actual amount that is then subtracted from the original attacking droid’s health. 

Attacking Droid Health = Current Health – Counter-Attack Net Damage

_The wording here may be a bit confusing but just remember that the Attacking Droid is the player who initiated the attack. The droid performing the Counter-Attack is still considered the Defending Droid._ 

## Awarding Experience 

The experience gained from a battle is easily calculated for either droid by using the results of each of the above steps. The experience is not applied until the Experience Changes Committed phase of the Game Progression, which means that any leveling up does not occur until all the attacks are complete.

```
Attacker Experience Increase = 
Gross Damage
+ (Counter-Attack Gross Damage – Counter-Attack Net Damage) 

Defender Experience Increase = 
(Gross Damage – Net Damage)
+ Counter-Attack Gross Damage
```

_If an evasion occurred then Net Damage, Counter-Attack Gross Damage and Counter-Attack Net Damage will all be zero._
