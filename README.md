<p align="center">
  <img src="/images/RevenantAccBuilderIcon.png" alt="Header Image" width="300">
</p>

<h1 align="center" style="color: #3AA4B7;">Revenant Account Builder</h1>

---

## Table of Contents
1. [Preset Builds](#preset-builds)
2. [Adding Tasks](#adding-tasks)
3. [Setup Selector](#setup-selector)
4. [Misc Settings](#misc-settings)
5. [Antiban Settings](#antiban-settings)
6. [Save/Load Settings](#save-load-settings)

---

## Preset Builds
If you don't want to create your own tasks/profiles, you can select a preset from the presets section and just press start. This will build the account with the selected stats/items depending on which preset you choose.

**Note:** Presets are **not recommended** as many users will use these, creating a pattern. It is recommended that you add your tasks manually and create your own profiles.

![Presets](/images/presets.gif)

---

## Adding Tasks
There are 3 types of tasks to choose from:

- **Skill**
- **Quest**
- **Break**

Tasks are completed in the order that they are added. You can change the order of the tasks using the up/down arrows and dispose of a task using the **X** button.

![Adding Tasks](/images/AddingTasks.gif)

---

## Setup Selector

### Opening the Setup Selector
You can open the setup selector by pressing the **Inventory/Equipment** button after adding a Task that requires you to set up the Inventory/Equipment items.

The items you select will be used for **this task only**.

![Setup Selector Button](/images/setup-selector-button.png)

### Setup Selector Guidelines
Upon opening the Setup Selector, you will be greeted with the Setup Selector Guidelines. If you have not read these already, please ensure that you do for a smooth experience.

![Setup Selector Guidelines](/images/setup-selector-guidelines.jpg)

### Selecting Your Ranged Levels
First, select your range levels for which you want to use this Equipment/Inventory setup. In this example, I have selected from level 1 Ranged to level 20 Ranged. This means that whatever equipment/inventory items I add, this is what the bot will use to train from level 1 to 20 Ranged.

![Selecting Range Levels](/images/selecting-range-level.gif)

### Adding Items
To add items to your equipment or inventory, first select the equipment or inventory panel and then select items from the list of items.

When selecting equipment items, if you already have selected an item for a slot such as a weapon, selecting another weapon will overwrite your previous choice.

![Adding Items](/images/adding-items-to-selector.gif)

### Clearing Your Selections
To clear your selections, simply double-click on the panel you want to clear.

![Clearing Selections](/images/clearing-setup-selector.gif)

### Adding More Setups
You can add more setups so that the bot will switch into different equipment/inventory setups automatically for different range levels.

![Adding More Setups](/images/adding-new-setup-tab.gif)

### Saving and Loading Setups
You can load/save your setups and use them for later use to save time.

![Saving/Loading Setups](/images/load-save-setup-profile.gif)

---

## Misc Settings

### Muling
If your bot is running low on money to buy supplies, it will meet the mule at the location and world that you set and receive coins from the mule. Make sure you are running the **"Saints Mule"** script if you enable muling, or you will have to trade the bot manually.

### Micro Breaks
Micro breaks will act like your character is going AFK. It will not log out of the game.

You can set the break duration and how often it should take a micro break. You can set the thresholds so it does not always take breaks at the same time.

For example, if I set it to take a break every 30 minutes with a threshold of 10 minutes, it will randomly take a break somewhere between 20 and 40 minutes.

### Discord Settings
You can enter your Discord webhook URL to receive Discord notifications.

![Misc Settings](/images/misc-settings.png)

---

## Antiban Settings

![Antiban Settings](/images/antiban-settings.png)

### Antiban Manager
Once you have created Antiban Profile(s), add them to the Added profiles section of the Antiban Manager to allow the bot to use them. If you add multiple profiles the bot will rotate between profiles at random times depending on the min/max values you set. This may simulate a normal player who might have different play styles depending on fatigue etc.

![Antiban Manager](/images/antiban-manager.gif)

### Creating an Antiban Profile

#### Banking Settings
These will affect interactions that take place during banking, such as withdrawing and depositing items.

![Banking Settings](/images/banking-settings.png)

#### Grand Exchange Settings
These will affect interactions that take place during using the Grand Exchange, such as buying/selling items and interacting with anything in the Grand Exchange interface.

![Grand Exchange Settings](/images/ge-settings.png)

#### Entity Settings
These will affect interactions that take place when interacting with NPCs or game objects, such as talking/attacking/trading an NPC or interacting with a game object such as a Dwarven Cannon or a Tree.

![Entity Settings](/images/entity-settings.png)

#### Inventory Settings
These will affect interactions that take place when interacting with items in your inventory, such as eating food, drinking a potion, or equipping an item.

![Inventory Settings](/images/inventory-settings.png)

#### Interaction Settings Explanation
- **Interaction Delay**: An interaction delay is a delay that takes place before a bot performs an action.

For example, imagine you are killing cows in Lumbridge. When the cow is killed, you wouldn't instantly click the next cow to attack. A real human would have a small delay before moving onto the next cow. This is the interaction delay.

- **Interaction Delay Example Settings**:
  - **min = 50ms**: The minimum possible delay.
  - **max = 1500ms**: The maximum possible delay.
  - **target = 100ms**: The ideal or desired delay.
  - **deviation = 300ms**: The allowed deviation from the target.

**Without Weighted Distribution (Uniform Distribution)**:
If `weightedDistribution` is `false`, the timing will be uniformly distributed between `min` (50ms) and `max` (1500ms). This means:
- Every value between 50ms and 1500ms is equally likely to occur.
- The `target` (100ms) and `deviation` (300ms) have no effect on the distribution.

**Outcome**:
- The timing could be any value between 50ms and 1500ms, with no preference for values closer to the target (100ms).
- For example, you might get 50ms, 500ms, 1000ms, or 1500ms, all with equal probability.

**With Weighted Distribution**:
If `weightedDistribution` is `true`, the timing will be weighted towards the `target` (100ms), with the `deviation` (300ms) influencing how tightly the values cluster around the target. This means:
- Values closer to the target (100ms) are more likely to occur.
- Values farther from the target are less likely to occur.
- The `deviation` (300ms) determines the spread of the distribution around the target.

**Outcome**:
- Most of the timing values will fall within the range of `target ± deviation`, i.e., 100ms ± 300ms, or between -200ms and 400ms.
- Since the `min` is 50ms, the effective range for the weighted distribution will be 50ms to 400ms.
- Values outside this range (400ms to 1500ms) are possible but much less likely.

**Example**:
- You might frequently get values like 100ms, 150ms, or 200ms.
- Values like 50ms or 400ms are less likely but still possible.
- Values like 1000ms or 1500ms are very unlikely.

**Key Differences**:
| Aspect | Without Weighted Distribution | With Weighted Distribution |
|--------|-------------------------------|----------------------------|
| Range | 50ms to 1500ms (uniform) | 50ms to 1500ms (weighted towards 100ms) |
| Likely Values | Any value between 50ms and 1500ms | Values close to 100ms (e.g., 50ms to 400ms) |
| Effect of Target | No effect | Values cluster around 100ms |
| Effect of Deviation | No effect | Determines spread around 100ms |

**Example Outcomes**:
- **Without Weighted Distribution**: 50ms, 200ms, 800ms, 1200ms, 1500ms (all equally likely).
- **With Weighted Distribution**: 100ms (most likely), 150ms, 200ms, 300ms (likely), 50ms, 400ms (less likely), 1000ms, 1500ms (very unlikely).

**Practical Implications**:
- **Without Weighted Distribution**: Useful when you want completely random timing within a wide range, with no preference for any specific value.
- **With Weighted Distribution**: Useful when you want timing to generally stay close to a target value but still allow for some variability. For example, simulating user behavior where most actions take around 100ms, but occasionally take longer.

---

## Save/Load Settings
You can save your current settings and load them later for convenience.

---

