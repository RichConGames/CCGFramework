![RichCon Games](https://image.ibb.co/j4o1hc/Rich_Con_Games_Logo_First_Revision_With_Background_Small.png "RichCon Games")
# `CCG Framework - 1.0.0.0`
**A collectible card game development framework, targeting the .NET standard and Unity in C#.**

*Copyright © Connor Richards & RichCon Games 2018. All rights reserved.*

## Installation
__`-`__ Copy the `CCGFramework.dll` and `CCGFramework.pdb` files from _'CCG Framework\bin\Framework'_ into your project resources directory.

__`-`__ Add a reference to `CCGFramework.dll` in it's new resources directory to your project / script / code.

__`-`__ Add the namespace to your code : `using CCGFramework;`

__`-`__ You can now access the `CCGFramework` namespace in your project.

## Reference Tables


### Class reference table highlighting the overall functionality and structure of the CCG Framework :

| __NAME__        | __TYPE__          | __INPUTS__  | __RETURNS__ | __FUNCTION__ |
| ------------- |:-------------:| -----:| -----:  | -----:  |
| VirtualCard()          | `Class` | `string` cardName, `string[,]` cardLibraryData, `string[,]` classesLibraryData |`VirtualCard` Instance|The primary class used to create cards from supplied data libraries.|
| VirtualCardUnity()     | `Class` | `string` cardName, `string[,]` cardLibraryData, `string[,]` classesLibraryData |`VirtualCardUnity` Instance|The same as `VirtualCard` but with added `Texture2D` support for Unity card graphics.|
| VirtualCardAbilities() | `Class` | `void` |`VirtualCardAbilities` Instance|Stores a library of core card ability methods, used to create skills and abilities for gameplay.|
| VirtualCardLibraries() | `Class` | `void` |`VirtualCardLibraries` Instance|Stores a library of core methods for creating readable, structured data from supplied `Card`, `Classes` and `Deck` libraries.|



### Method reference table highlighting the use and functionality of the CCG Framework Class Structure :

| __METHOD__        | __PARENT CLASS__          | __INPUTS__  | __RETURNS__ | __FUNCTION__ |
| ------------- |:-------------:| -----:| -----:  | -----:  |
| NewCardLibrary() | `VirtualCardLibraries()` | `string` csvPath |`string[,]` cardLibraryData|A method used to generate a 2D data structure storing all `Card` library data for use in `VirtualCard` generation.
| NewClassesLibrary() | `VirtualCardLibraries()` | `string` csvPath |`string[,]` classesLibraryData|A method used to generate a 2D data structure storing all `Classes` library data for use in `VirtualCard` generation.
| NewDeckLibrary() | `VirtualCardLibraries()` | `string` csvPath |`string[,]` deckLibraryData|A method used to generate a 2D data structure storing all `Deck` library data for use in `VirtualCard` storage and accumulation, referencing an existing `VirtualCard`.
|||||
| Damage`Type`() | `VirtualCard()` & `VirtualCardUnity()` | `int` amount |`void`|A set of methods that apply damage to a member in the `VirtualCard` by type, eg: Physical Armor, Vitality, etc. . .
| Siphon`Type`() | `VirtualCard()` & `VirtualCardUnity()` | `int` amount |`void`|A set of methods that apply siphoning damage or debuff to a member in the `VirtualCard` by type, eg: Physical Armor, Vitality, etc. . .
| Regen`Type`() | `VirtualCard()` & `VirtualCardUnity()` | `int` amount |`void`|A set of methods that regenerate or buff a member in the `VirtualCard` by type, eg: Physical Armor, Vitality, etc. . .
|||||
| `enum` DamageType | `VirtualCardAbilities()` | `enum` |`enum` Physical, `enum` Special| An enumeration used to determine the kind of damage to be applied to a `VirtualCard` by an `Ability` method.
| `enum` ConditionType | `VirtualCardAbilities()` | `enum` |`enum` Injure,`enum` Poison,`enum` Silence,`enum` Rust,`enum` Void,`enum` Hinder| An enumeration used to determine the kind of condition to be applied to a `VirtualCard` by an `Ability` method.
| `enum` Siphon/Regen/DrainType | `VirtualCardAbilities()` | `enum` |`enum` Vitality,`enum` Vigour,`enum` Verve,`enum` PhysicalArmor,`enum` SpecialArmor,`enum` Speed| An enumeration used to determine the kind of `Siphoning`, `Regeneration` or `Draining` type to be applied to a `VirtualCard` by an `Ability` method.
|||||
| Attack() | `VirtualCardAbilities()` | `VirtualCard` caster, `VirtualCard` target, `DamageType` damageType, `int` multiplyer |`void`| A method used to apply attack damage from the caster to a target's armor and statistics based on `DamageType`. Statistics only take damage once armor of it's type has been completely destroyed.
| ApplyCondition() | `VirtualCardAbilities()` | `VirtualCard` caster, `VirtualCard` target, `ConditionType` conditionType, `int` multiplyer |`void`| A method used to apply condition damage from the caster to a target's statistics based on `ConditionType`. Conditions effect specific statistics directly by the caster's `ConditionPower`, eg : `Injure` damages `Vitality`, `Poison` damages `Vigour`, etc. . .
| Siphon() | `VirtualCardAbilities()` | `VirtualCard` caster, `VirtualCard` target, `DamageType` damageType, `int` multiplyer |`void`| A method used to apply siphon damage from the caster to a target's statistics and regeneration from the target's damage to the caster based on `SiphonType`. Eg : Caster instantly regenerates 10 `Vitality` after applying 10 `Vitality` `SiphonType` damage to the target, etc. . .
| Drain() | `VirtualCardAbilities()` | `VirtualCard` caster, `VirtualCard` target, `DamageType` damageType, `int` amount |`void`| A method used to apply direct damage from the caster to a target's specific statistic based on `DrainType` and by the amount specified.
| Regen() | `VirtualCardAbilities()` | `VirtualCard` caster, `VirtualCard` target, `DamageType` damageType, `int` multiplyer |`void`| A method used to regenerate statistics from the caster to a target's specific statistic based on `RegenType` and by the caster's `RegenPower`.
|||||
| Special Ability Examples | `VirtualCardAbilities()` | `VirtualCard` caster, `VirtualCard` target, `string` abilityName|`void`| A collection of methods used as examples of implementing the core abilities from `VirtualCardAbilities` to create new, hybrid abilities : `VampiricEmbrace()`, `PaladinsCall()`, `Flay()`, `PiercingThrust()`, `GreatStrike()` & `GreatSurge()`.
