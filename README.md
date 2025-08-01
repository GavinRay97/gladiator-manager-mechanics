Mechanics for the game Gladiator Manager on Android

https://play.google.com/store/apps/details?id=com.rene.gladiatormanager&hl=en_US

---

- [Gladiator Traits](#gladiator-traits)
  - [Complete Trait Table](#complete-trait-table)
  - [Legend](#legend)
  - [Acquisition Methods](#acquisition-methods)
  - [Training-Specific Traits](#training-specific-traits)
  - [Special Condition Traits](#special-condition-traits)
    - [Titanic Strength: Requirements](#titanic-strength-requirements)
    - [Trait Incompatibilities](#trait-incompatibilities)
    - [Class-Specific Requirements](#class-specific-requirements)
    - [Tournament-Specific Traits](#tournament-specific-traits)
    - [Underground Tournament Progression](#underground-tournament-progression)
    - [Life Force Drain Progression](#life-force-drain-progression)
    - [League Championship Traits](#league-championship-traits)
    - [Special Legendary Interactions](#special-legendary-interactions)
- [Trait Learning Mechanics](#trait-learning-mechanics)
  - [The Role of Cunning](#the-role-of-cunning)
    - [For Gladiators](#for-gladiators)
    - [For Beasts](#for-beasts)
    - [Other Uses for Cunning](#other-uses-for-cunning)
  - [Complete Trait Learning Formula](#complete-trait-learning-formula)
  - [Trait Learning Probability Tables](#trait-learning-probability-tables)
    - [Scenario 1: Early Career Gladiator](#scenario-1-early-career-gladiator)
    - [Scenario 2: Mid-Career Gladiator](#scenario-2-mid-career-gladiator)
    - [Scenario 3: Veteran Gladiator (Trait Saturation)](#scenario-3-veteran-gladiator-trait-saturation)
  - [Trait Learning Calculation Examples](#trait-learning-calculation-examples)
    - [Example 1: Greek Prodigy](#example-1-greek-prodigy)
    - [Example 2: Punic Veteran](#example-2-punic-veteran)
    - [Example 3: Low Cunning Struggle](#example-3-low-cunning-struggle)
- [Injury and Training Mechanics](#injury-and-training-mechanics)
  - [Injury System Overview](#injury-system-overview)
    - [Injury Types and Recovery](#injury-types-and-recovery)
    - [Injury Prone Calculation](#injury-prone-calculation)
  - [Training Injury Risks](#training-injury-risks)
  - [Severe Injury and Permanent Traits](#severe-injury-and-permanent-traits)
    - [Severe Injury Trait Acquisition](#severe-injury-trait-acquisition)
    - [Special Immunity](#special-immunity)
  - [Injury Roll Calculations](#injury-roll-calculations)
    - [Core Injury Formula](#core-injury-formula)
    - [Injury Type Mapping](#injury-type-mapping)
    - [Sample Calculations](#sample-calculations)
    - [Key Insights](#key-insights)

---

## Gladiator Traits

### Complete Trait Table

| Trait Name                  | STR | HP  | INI | CUN | LOY | TEC | INJ | How to Obtain                                                                                  |
| :-------------------------- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :--------------------------------------------------------------------------------------------- |
| **Adventurous**             | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Agile**                   | -1  |  0  | +2  |  0  |  0  |  0  |  0  | Random initiative trait learning, Starting trait (Tetraites)                                   |
| **Albino**                  |  0  | +5  |  0  |  0  |  0  |  0  |  0  | Random trait, Beast reincarnation                                                              |
| **Alert**                   |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random initiative trait learning, Random trait learning                                        |
| **All In**                  | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning, Random trait learning                                          |
| **Alpha**                   | +1  | +5  |  0  |  0  |  0  |  0  |  0  | Random beast trait learning, Beast creation (Bear, Gorilla)                                    |
| **Ambidextrous**            |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random initiative trait learning, Intense training (3% chance)                                 |
| **Anemic**                  | -2  |  0  | -1  |  0  |  0  |  0  | +1  | Life force drain progression                                                                   |
| **Animal Instinct**         |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random beast trait learning                                                                    |
| **Annum Champion**          |  0  | +5  | +1  | +1  |  0  |  0  |  0  | League championship reward                                                                     |
| **Apollo's Blessing**       |  0  | +5  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Arena Champion**          | +1  |  0  | +1  | +1  |  0  |  0  |  0  | Win major tournament (non-underground, 11+ rounds)                                             |
| **Arrogant**                |  0  |  0  | -2  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Ascended**                | +2  |  0  | +2  |  0  |  0  |  0  |  0  | Win Ascension tournament                                                                       |
| **Assassin**                |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random initiative trait learning                                                               |
| **Axe Specialist**          |  0  |  0  |  0  |  0  |  0  |  0  |  0  | Combat effect: +2 damage with axes                                                             |
| **Axial Momentum**          | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Bacchus Champion**        |  0  | +5  | -1  |  0  |  0  |  0  |  0  | League championship reward                                                                     |
| **Bane of Tigris**          | +2  |  0  |  0  |  0  |  0  |  0  |  0  | Win 14+ underground tournaments                                                                |
| **Beast Tamer**             |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random cunning trait learning, Bestiarii training (1% chance), Starting trait (Carpophorus)    |
| **Best Boy**                | +2  |  0  | +2  | +1  |  0  |  0  |  0  | Random trait                                                                                   |
| **Bestia Summum**           | +1  | +5  | +1  | +1  |  0  |  0  |  0  | Bestiarii training for beasts (15% chance)                                                     |
| **Bestiarii**               |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random cunning trait learning, Bestiarii training (20% chance), Starting trait (Beast Master)  |
| **Blade Whisperer**         |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Blind**                   |  0  |  0  | -2  |  0  |  0  |  0  |  0  | Injury progression, Beast reincarnation                                                        |
| **Blind Fighter**           |  0  |  0  | +1  | +1  |  0  |  0  |  0  | Random initiative trait learning                                                               |
| **Bloodstarved**            | -4  |  0  | -2  |  0  |  0  |  0  | +2  | Life force drain progression                                                                   |
| **Bum Leg**                 | -2  |  0  | -4  |  0  |  0  |  0  |  0  | Severe injury recovery (50% chance)                                                            |
| **Careful**                 |  0  |  0  | -1  | +1  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Carnivorous**             | +1  |  0  | +1  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Cataphractoi**            | +2  |  0  | -1  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Celestial Champion**      | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Colossus Slayer**         |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Win 8+ underground tournaments                                                                 |
| **Concussion**              |  0  |  0  | -1  |  0  |  0  |  0  |  0  | Severe injury recovery (50% chance)                                                            |
| **Conditioning**            |  0  | +5  | +1  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Crippled**                | -5  |  0  | -5  |  0  |  0  |  0  |  0  | Severe injury recovery (50% chance), Life force drain progression                              |
| **Dagger Master**           |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Combat effect: Enhanced dagger damage                                                          |
| **Dagger Specialist**       |  0  |  0  |  0  |  0  |  0  |  0  |  0  | Combat effect: +2 damage with daggers                                                          |
| **Deadeye**                 |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random initiative trait learning, Random trait learning                                        |
| **Deafening Crackle**       | +2  |  0  | +2  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Demanding Freedom**       |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Devotion**                | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Doctore**                 |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random trait                                                                                   |
| **Dual Wield**              |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random initiative trait learning, Random trait learning                                        |
| **Enforcer**                | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Eques Slayer**            |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random trait learning                                                                          |
| **Exotic Fighting Style**   |  0  |  0  | +1  | +1  |  0  |  0  |  0  | Random initiative trait learning, Random trait learning                                        |
| **Explosive Release**       | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Fanatic**                 | +1  | +10 | +1  |  0  |  0  |  0  | +1  | Random strength trait learning                                                                 |
| **Feral Intelligence**      |  0  |  0  |  0  |  0  |  0  |  0  |  0  | Random beast trait learning, Beast creation (Gorilla)                                          |
| **First Blood**             |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Win Rookie tournament                                                                          |
| **Fists of Steel**          | +3  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Force of Nature**         | +1  | +5  | +1  | +1  |  0  | +1  |  0  | Random beast trait learning                                                                    |
| **Freedom**                 |  0  | +5  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Fury**                    | +2  | +5  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Giant**                   | +2  | +5  | -2  |  0  |  0  |  0  |  0  | Random trait, Beast reincarnation (from Titan)                                                 |
| **Glory Seeker**            | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Good Boy**                |  0  | +5  |  0  |  0  |  0  |  0  |  0  | Random trait, Beast reincarnation (from Best Boy)                                              |
| **Herculean Strength**      | +4  | +10 | +1  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Hero**                    | +1  |  0  | +1  | +1  |  0  |  0  |  0  | Random trait                                                                                   |
| **Hoplite**                 | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning (with Spartan Dynasty upgrade)                                  |
| **Horrible Disfigurement**  |  0  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning, Severe injury recovery (50%)                                   |
| **Hunter**                  |  0  |  0  | +1  | +1  |  0  |  0  |  0  | Random initiative trait learning                                                               |
| **Impact**                  | +2  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Indomitable**             | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning, Random trait learning                                          |
| **Inspiring**               |  0  | +5  |  0  | +1  |  0  |  0  |  0  | Random initiative trait learning                                                               |
| **Intangible**              |  0  |  0  | +2  |  0  |  0  |  0  | -2  | Random trait                                                                                   |
| **Jupiter Champion**        | +1  |  0  | +1  | +1  |  0  |  0  |  0  | League championship reward                                                                     |
| **Killer**                  | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Lawbringer**              | +1  |  0  | +1  |  0  |  0  |  0  |  0  | Win revolt event (lawful side)                                                                 |
| **Life Bringer**            |  0  |  0  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Lightning Speed**         |  0  |  0  | +2  |  0  |  0  |  0  |  0  | Random initiative trait learning, Intense training (rare)                                      |
| **Lord of Cinders**         | +1  | +5  | +1  | +1  |  0  | +1  | -1  | Solar Champion + Gwyn legendary type                                                           |
| **Lost Family**             | +1  |  0  | +1  | +1  |  0  |  0  |  0  | Random trait                                                                                   |
| **Loyal**                   |  0  | +5  |  0  |  0  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Lunar Champion**          |  0  | +5  | +1  |  0  |  0  |  0  |  0  | League championship reward                                                                     |
| **Lycanthropy**             |  0  |  0  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Made of Glass**           |  0  | -5  | +4  |  0  |  0  |  0  | +1  | Random initiative trait learning                                                               |
| **Many Heads**              |  0  | +50 |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Marksman**                |  0  |  0  | +1  | +1  |  0  |  0  |  0  | Random initiative trait learning                                                               |
| **Master Horseman**         |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random initiative trait learning                                                               |
| **Missing Fingers**         | -1  |  0  | -1  |  0  |  0  |  0  |  0  | Severe injury recovery (50% chance)                                                            |
| **Mithridatism**            |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Mythical**                |  0  | +5  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **One Man Army**            | +1  | +5  |  0  | +1  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Pankration Champion**     |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Win Pankration tournament                                                                      |
| **Paranoid**                |  0  | -5  | +1  |  0  |  0  |  0  |  0  | Random initiative trait learning                                                               |
| **Partially Blind**         |  0  |  0  | -1  |  0  |  0  |  0  |  0  | Severe injury recovery (50% chance)                                                            |
| **Piercing Precision**      |  0  |  0  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Pit Champion**            |  0  | +5  | +1  | +1  |  0  |  0  |  0  | Win 5+ underground tournaments                                                                 |
| **Pit Fighter**             |  0  | +5  |  0  | +1  |  0  |  0  |  0  | Win 2+ underground tournaments                                                                 |
| **Pit Legend**              | +1  | +10 | +2  | +1  |  0  |  0  |  0  | Win 10+ underground tournaments                                                                |
| **Plotting Uprising**       |  0  | +5  |  0  | +1  |  0  |  0  |  0  | Random trait                                                                                   |
| **Poison Master**           |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random cunning trait learning, Random trait learning                                           |
| **Poisoned Claws**          |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Preparation**             |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random cunning trait learning, Random trait learning                                           |
| **Psychopath**              | +1  | +10 | +2  | +1  |  0  |  0  |  0  | Random trait                                                                                   |
| **Pugilist**                | +1  |  0  | +1  |  0  |  0  |  0  |  0  | Random strength trait learning, Random trait learning                                          |
| **Pyromaniac**              |  0  |  0  | +1  | +1  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Quick Study**             |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random initiative trait learning, Random trait learning                                        |
| **Raised in the Arena**     | +2  | +5  | +1  | +1  |  0  |  0  |  0  | Win Junior tournament                                                                          |
| **Rebel General**           | +2  | +20 | +2  | +2  |  0  |  0  |  0  | Random trait                                                                                   |
| **Rebel Leader**            | +1  | +5  | +1  | +1  |  0  |  0  |  0  | Random trait                                                                                   |
| **Rebel Slayer**            | +1  | +5  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Recaptured**              |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random trait                                                                                   |
| **Reincarnated**            | +2  |  0  | +2  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Reincarnated Beast**      | +1  |  0  | +1  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Reunited With Family**    |  0  | +5  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Revolt Leader**           | +1  | +5  | +1  | +1  |  0  |  0  |  0  | Win revolt event (rebel side)                                                                  |
| **Rudiarius**               |  0  | +5  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Ruthless**                | +2  |  0  |  0  | +1  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Self Preservation**       | -1  | +5  |  0  |  0  |  0  |  0  |  0  | Random beast trait learning                                                                    |
| **Shadow Blade**            |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Sharpened Claws**         | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random beast trait learning                                                                    |
| **Showman**                 |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random initiative trait learning                                                               |
| **Sneaky**                  |  0  |  0  | +1  | +1  |  0  |  0  |  0  | Random cunning trait learning, Random trait learning                                           |
| **Solar Champion**          | +1  |  0  |  0  | +1  |  0  |  0  |  0  | League championship reward                                                                     |
| **Spartan Resolve**         |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Spear Master**            |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Combat effect: Enhanced spear damage                                                           |
| **Spear Specialist**        |  0  |  0  |  0  |  0  |  0  |  0  |  0  | Combat effect: +2 damage with spears                                                           |
| **Strong**                  | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning, Intense training (50% chance)                                  |
| **Sudden Death**            |  0  |  0  | +1  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Survival of the Fittest** |  0  | +5  | +1  |  0  |  0  |  0  | -1  | Random beast trait learning, Beast creation (Lion, Elephant)                                   |
| **Sword Master**            | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Sword Specialist**        |  0  |  0  |  0  |  0  |  0  |  0  |  0  | Combat effect: +2 damage with swords                                                           |
| **Tactician**               |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random cunning trait learning, Random trait learning                                           |
| **Talented**                |  0  |  0  | +1  |  0  |  0  | +1  |  0  | Random initiative trait learning                                                               |
| **Temperamental**           | +2  |  0  | +1  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Thief**                   |  0  |  0  | +2  | +1  |  0  |  0  |  0  | Random initiative trait learning                                                               |
| **Thick Hide**              |  0  | +5  |  0  |  0  |  0  |  0  |  0  | Beast creation (Lion, Elephant, Bear)                                                          |
| **Titan**                   | +4  | +10 | -2  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Titanic Strength**        | +4  |  0  | -2  |  0  |  0  |  0  |  0  | Special condition: Giant/Titan + Sword/Axe proficient + Barbarus/Murmillo/Dimachaerus + 16 STR |
| **Tomb Raider**             |  0  |  0  |  0  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Tough**                   | +1  | +5  | -2  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **True Grit**               |  0  | +5  |  0  |  0  |  0  |  0  | -1  | Random strength trait learning                                                                 |
| **Underdog**                | -1  |  0  | +1  | +1  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Undeath**                 |  0  |  0  | -2  |  0  |  0  |  0  |  0  | Random trait                                                                                   |
| **Underhanded**             |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Untrustworthy**           |  0  |  0  |  0  | +1  |  0  |  0  |  0  | Random cunning trait learning                                                                  |
| **Veteran**                 | +1  |  0  |  0  |  0  |  0  |  0  |  0  | Random strength trait learning                                                                 |
| **Vulcan Champion**         | +1  | +5  |  0  |  0  |  0  |  0  |  0  | League championship reward                                                                     |
| **World Champion**          | +1  | +5  | +1  | +1  |  0  |  0  |  0  | Win Invader tournament                                                                         |

---

### Legend

- **STR**: Strength
- **HP**: Health (Max Life)
- **INI**: Initiative
- **CUN**: Cunning
- **LOY**: Loyalty
- **TEC**: Technique Points

---

### Acquisition Methods

- **Random Trait Learning**: Weekly chance based on level and Cunning.
- **Tournament Rewards**: Specific tournaments grant specific traits upon victory.
- **Training**: Intense or specialized training has a small chance to grant certain traits.
- **Injury Recovery**: Recovering from severe injuries can result in permanent negative (or occasionally neutral) traits.
- **Special Conditions**: Some powerful traits require a combination of other traits, stats, or class.
- **Beast Traits**: Beasts have a unique trait pool and learning system.
- **League Rewards**: Winning league championships grants powerful champion traits.

---

### Training-Specific Traits

- **Intense Training (3% chance to trigger)**
  - **Strong**: 50% chance
  - **Ambidextrous**: 50% chance
  - **Lightning Speed**: Can also trigger if the gladiator does not have **Giant** or **Titan**.
- **Technique Training (1% chance to trigger)**
  - **Talented**
  - **Exotic Fighting Style**
- **Specialized Training Bonuses**
  - **Bestiarii Training**: 20% chance for **Bestiarii**, 1% for **Beast Tamer**.
  - **Spartan Training**: 10% chance for **Conditioning**, 3% for **Indomitable**.

---

### Special Condition Traits

#### Titanic Strength: Requirements

All of the following conditions must be met:

1.  Has the **Giant** OR **Titan** trait.
2.  Is proficient with **Sword** OR **Axe** weapons.
3.  Is a **Barbarus**, **Murmillo**, OR **Dimachaerus** class.
4.  Has a base Strength of 16 or higher.
5.  Does not already have the **Titanic Strength** trait.

#### Trait Incompatibilities

- A gladiator cannot have both **Giant** and **Titan** simultaneously.
- The underground tournament traits are a direct progression. Higher-tier traits replace the lower-tier ones.
  - `Pit Fighter` → `Pit Champion` → `Pit Legend`

#### Class-Specific Requirements

- **Hoplite**: This trait can only be learned through strength-based random trait learning if the ludus has the "Spartan Dynasty" upgrade.

#### Tournament-Specific Traits

- **World Champion**: Win the Invader tournament.
- **Arena Champion**: Win a major tournament (11+ rounds, non-underground).
- **First Blood**: Win the Rookie tournament.
- **Raised in the Arena**: Win the Junior tournament.
- **Pankration Champion**: Win the Pankration tournament.
- **Ascended**: Win the Ascension tournament.

#### Underground Tournament Progression

- **Pit Fighter**: Win 2+ underground tournaments.
- **Pit Champion**: Win 5+ underground tournaments (replaces _Pit Fighter_).
- **Colossus Slayer**: Win 8+ underground tournaments.
- **Pit Legend**: Win 10+ underground tournaments (replaces _Pit Champion_).
- **Bane of Tigris**: Win 14+ underground tournaments.

#### Life Force Drain Progression

These traits are acquired sequentially through life force drain events:

1.  **Anemic** (`-2 STR`, `-1 INI`)
2.  **Bloodstarved** (`-4 STR`) - replaces _Anemic_
3.  **Crippled** (`-5 STR`, `-2 INI`) - can be acquired if both previous traits are present.

#### League Championship Traits

Winning a specific league championship awards a corresponding trait, such as **Solar Champion**, **Lunar Champion**, **Vulcan Champion**, etc.

#### Special Legendary Interactions

- **Lord of Cinders**: Can only be obtained if a gladiator is of the "Gwyn" legendary type and already possesses the **Solar Champion** trait.

---

## Trait Learning Mechanics

### The Role of Cunning

Cunning is the single most important attribute for weekly random trait acquisition. It also provides other non-combat benefits.

#### For Gladiators

A higher Cunning score dramatically increases the chance of learning a new trait each week. Each existing trait provides a small stacking penalty to the roll, representing diminishing returns.

#### For Beasts

Beasts use a different formula where Cunning is still important, but the penalty for existing traits is much higher (`-4` per trait vs. `-1` for gladiators).

#### Other Uses for Cunning

- **Intrigue**: Affects success rates for actions like raids, sabotage, and assassinations.
- **Expeditions**: Increases the chance of successful outcomes.
- **Combat**: Used for Cunning-based technique checks.

---

### Complete Trait Learning Formula

The probability of a gladiator learning a new trait each week is determined by the following formula:

```
Bonus = ((Level + (Cunning × 2) + OriginBonus - TraitCount - 5) × Multiplier)
isSuccess = (random(0-79) + Bonus) >= 80
```

- **`Level`**: The gladiator's current level.
- **`Cunning × 2`**: The Cunning stat is doubled, highlighting its high impact.
- **`OriginBonus`**: `+10` for Punic origin, `0` for all others.
- **`TraitCount`**: The number of traits the gladiator already has.
- **`Multiplier`**: `2.0` for Greek heritage, `1.0` for all others.

The final `Bonus` value is the number of successful outcomes out of 80 total possibilities, so the probability is `Bonus / 80`.

---

### Trait Learning Probability Tables

#### Scenario 1: Early Career Gladiator

_Conditions: Level 3, 0 Traits_
| Cunning | Normal Heritage | Greek Heritage |
| :---: | :---: | :---: |
| 8 | 38% | 76% |
| 12 | 48% | 86% |
| 16 | 58% | 96% |
| 20 | 68% | 100% |

#### Scenario 2: Mid-Career Gladiator

_Conditions: Level 8, 2 Traits_
| Cunning | Normal Heritage | Greek Heritage |
| :---: | :---: | :---: |
| 12 | 46% | 84% |
| 16 | 56% | 94% |
| 20 | 66% | 100% |
| 24 | 76% | 100% |

#### Scenario 3: Veteran Gladiator (Trait Saturation)

_Conditions: Level 15, 20 Cunning_
| Traits | Normal Heritage | Greek Heritage |
| :---: | :---: | :---: |
| 5 | 61% | 100% |
| 8 | 58% | 96% |
| 10 | 56% | 94% |
| 12 | 54% | 92% |

---

### Trait Learning Calculation Examples

#### Example 1: Greek Prodigy

_Level: 5, Cunning: 18, Traits: 1, Heritage: Greek_

```
Bonus = (5 + (18 × 2) + 0 - 1 - 5) × 2.0
Bonus = (35) × 2.0 = 70
Probability = 70 / 80 = 87.5%
```

#### Example 2: Punic Veteran

_Level: 12, Cunning: 15, Traits: 4, Heritage: Normal, Origin: Punic_

```
Bonus = (12 + (15 × 2) + 10 - 4 - 5) × 1.0
Bonus = (43) × 1.0 = 43
Probability = 43 / 80 = 53.75%
```

_Note: The original document had a calculation error here. The correct bonus is 43, not 38._

#### Example 3: Low Cunning Struggle

_Level: 8, Cunning: 6, Traits: 2, Heritage: Normal_

```
Bonus = (8 + (6 × 2) + 0 - 2 - 5) × 1.0
Bonus = (13) × 1.0 = 13
Probability = 13 / 80 = 16.25%
```

---

## Injury and Training Mechanics

### Injury System Overview

#### Injury Types and Recovery

1.  **Flesh Wound**: 2 weeks, -10% HP in combat
2.  **Broken Bones**: 3 weeks, -15% HP in combat
3.  **Severely Wounded**: 4 weeks, -30% HP in combat
4.  **Multiple Injuries**: 5 weeks, -45% HP in combat
5.  **Dead**: Permanent
6.  **Ill**: 2 weeks, -15% HP in combat

#### Injury Prone Calculation

A gladiator's baseline risk of injury is determined by their `InjuryProne` value.

```
InjuryProne = AgeBonus + TraitBonuses + SpecialBonuses
```

- **Age Bonus**: Risk increases significantly outside of a gladiator's prime (15-27).
  - **0-3**: +3
  - **4-7**: +2
  - **8-14**: +1
  - **15-27**: 0
  - **28-32**: +1
  - **33-39**: +2
  - **40-45**: +4
  - **46-58**: +5
  - **59+**: +6 to +8
- **Trait Bonuses**: Certain traits increase or decrease this value.
- **Special Bonuses**: Some legendary gladiators (like Spartacus) have innate injury resistance.

---

### Training Injury Risks

The logic for training injury is:

```js
let num = randomBetween(0, 1);
if (num < 1) {
  // no injury possible
} else {
  // use injury risk modifier from training type
}
```

| Training Type | 50% Chance    | 50% Chance     |
| ------------- | ------------- | -------------- |
| **Light**     | 0 injury risk | +1 injury risk |
| **Standard**  | 0 injury risk | +2 injury risk |
| **Technique** | 0 injury risk | +2 injury risk |
| **Intense**   | 0 injury risk | +4 injury risk |

This means the **effective injury risks** are actually:

- **Light Training**: 50% chance of +1 risk = **0.5 average risk**
- **Standard/Technique**: 50% chance of +2 risk = **1.0 average risk**
- **Intense Training**: 50% chance of +4 risk = **2.0 average risk**

A higher-level Medicus provides protection, directly subtracting from the injury risk.

- **Level 1**: `-1` protection
- **Level 2**: `-2` protection

---

### Severe Injury and Permanent Traits

#### Severe Injury Trait Acquisition

When recovering from **Severely Wounded** or **Multiple Injuries**, there is a **50% chance** to gain a permanent negative trait. The trait is chosen randomly from the following pool:

- Horrible Disfigurement
- Partially Blind
- Bum Leg (`-2 STR`)
- Crippled (`-5 STR`, `-2 INI`)
- Missing Fingers (`-1 STR`)
- Concussion (`+1 CUN`)

#### Special Immunity

The **Hand of Midas** item grants immunity to acquiring the _Missing Fingers_ trait.

---

### Injury Roll Calculations

#### Core Injury Formula

An injury occurs if the final `InjuryRoll` is greater than 10.

```
// Step 1: Calculate the final risk modifier
InjuryInput = (InjuryProne + TrainingRisk) - (MedicusLevel + OtherBonuses)

// Step 2: Generate the final roll
InjuryRoll = random(0-10) + InjuryInput

// Step 3: Determine the outcome
if (InjuryRoll <= 10) -> No Injury
if (InjuryRoll > 10)  -> Injury Occurs
```

#### Injury Type Mapping

The severity of the injury is mapped from the `InjuryRoll` value. The roll is capped at 15.

- **Roll 11**: Flesh Wound
- **Roll 12**: Broken Bones
- **Roll 13**: Severely Wounded
- **Roll 14**: Multiple Injuries
- **Roll 15**: Dead

#### Sample Calculations

**Example 1: Young, Healthy Gladiator (Low Risk)**

- **Profile**: 22 years old (`AgeBonus: 0`), `True Grit` trait (`TraitBonus: -1`), Light Training (`Risk: +1`), Medicus Lvl 1 (`Protection: -1`).
- **Calculation**:
  ```
  InjuryProne = 0 (age) - 1 (trait) = -1
  InjuryInput = (-1 + 1) - (1 + 0) = -1
  InjuryRoll = random(0-10) - 1 = range of -1 to 9
  ```
- **Result**: **Safe**. The maximum possible roll is 9, which is less than 11. No injury is possible.

---

**Example 2: Middle-Aged Gladiator (Moderate Risk)**

- **Profile**: 35 years old (`AgeBonus: +2`), No relevant traits, Technique Training (`Risk: +2`), No Medicus.
- **Calculation**:
  ```
  InjuryProne = 2 (age) + 0 (traits) = 2
  InjuryInput = (2 + 2) - (0 + 0) = 4
  InjuryRoll = random(0-10) + 4 = range of 4 to 14
  ```
- **Result**: **Risky**. There is a 4/11 (\~36%) chance of injury, ranging from a Flesh Wound to Multiple Injuries.

---

**Example 3: Old, Injury-Prone Gladiator (High Risk)**

- **Profile**: 55 years old (`AgeBonus: +5`), `Bloodstarved` (`TraitBonus: +2`), `Anemic` (`TraitBonus: +1`), Intense Training (`Risk: +4`), No Medicus.
- **Calculation**:
  ```
  InjuryProne = 5 (age) + 3 (traits) = 8
  InjuryInput = (8 + 4) - (0 + 0) = 12
  InjuryRoll = random(0-10) + 12 = range of 12 to 22 (capped at 15)
  ```
- **Result**: **Injury is Guaranteed**. The minimum roll is 12 (Broken Bones). There is a 7/11 (\~64%) chance of rolling 15 or higher, resulting in death.

---

**Example 4: Well-Protected Gladiator (Injury Prevention)**

- **Profile**: 28 years old (`AgeBonus: +1`), `Survival of the Fittest` (`TraitBonus: -1`), Intense Training (`Risk: +4`), Medicus Lvl 2 (`Protection: -2`), high-level facilities (`Bonus: -2`).
- **Calculation**:
  ```
  InjuryProne = 1 (age) - 1 (trait) = 0
  InjuryInput = (0 + 4) - (2 + 2) = 0
  InjuryRoll = random(0-10) + 0 = range of 0 to 10
  ```
- **Result**: **Safe**. Investments in a high-level Medicus and facilities completely negate the risk of intense training.

#### Key Insights

1.  **Age is critical**: Injury risk skyrockets for gladiators over 40.
2.  **Medicus is essential**: High-level Medicus facilities are the most effective way to mitigate training injuries.
3.  **Traits matter**: Protective traits like _True Grit_ provide a significant safety buffer, while negative traits like _Bloodstarved_ make training exceptionally dangerous.
4.  **Intense training requires investment**: For older gladiators, intense training is a death sentence without proper protection from a Medicus and/or defensive traits.
5.  **Stacking bonuses is key**: Combining a good Medicus, protective traits, and facility bonuses can render even the most strenuous training completely safe.
