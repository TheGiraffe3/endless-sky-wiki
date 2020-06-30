# Introduction

The [syntax](DataFormat#grammar-specifications) for the definition of a fleet is:

```html
fleet <name>
	government <name>
	names <phrase>
	fighters <phrase>
	cargo <cargo#>
	commodities <commodity>...
	outfitters <outfitter>...
	personality <type>...
		<type>...
		confusion <amount#>
	variant [<weight#>]
		<model> [<count#>]
		...
```

# Basic fleet characteristics

```html
fleet <name>
```

The fleet name must be unique. Using this fleet name, this fleet can be spawned by systems or missions.

```html
government <name>
```

The name of the [government](CreatingGovernments) that this fleet is a part of. All ships spawned by this fleet will be a part of this government.

```html
names <phrase>
fighters <phrase>
```

The names of the ships in this fleet, constructed from the given [phrase](CreatingPhrases). If only `names` is listed, then all ships in the fleet will pull their name from that phrase. If `fighters` is also listed, then the fighters and drones in the fleet will pull their names from that phrase, while all other ships will still use the `names` phrase.

```html
cargo <cargo#>
commodities <commodity>...
```

The number of types of commodities that this fleet will carry as cargo and a list of the types of those commodities. If no `cargo` number is given, then the default number of commodity types carried is 3. If no `commodities` are listed, then the commodities can be of any type. The amount of each commodity will be a random number from 0 to the cargo capacity of the ship.

```html
outfitters <outfitter>...
```

Ships can also carry outfits as cargo, specified by the [outfitters](CreatingOutfits#sales) listed here. If no outfitters are listed, then ships will carry outfits from the outfitters of the system they spawn in and the outfitters of all systems linked directly to the spawn system.

```html
personality <type>...
	<type>...
	confusion <amount#>
```

The [personalities](ShipPersonalities) that specify how this fleet acts. Each personality can be listed on a single line or as a child of `personality`, but `confusion` must be listed as a child of `personality` on its own line. The default confusion if not listed is 10.

# Variants

```html
variant [<weight#>]
	<model> [<count#>]
	...
```

Variants define what model and number of [ships](CreatingShips) are spawned by this fleet. A number of variants can be listed under a single fleet. When the fleet is spawned, one of these variants will be chosen at random according to their weights. The chance for any single variant to be spawned is `variant weight / sum of all variant weights`. For example, if a variant has a weight of 4 and the sum of all variant weights in the fleet is 20, then that variant has a 4/20 chance of being spawned.

If no weight is given for the variant (or no count for a ship model), then the weight (or count) is 1.