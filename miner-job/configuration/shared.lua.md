---
description: Documentation for shared.lua Configuration
---

# shared.lua

**XP Calculation Function**

```lua
Shared.CalculateNeedXP = function(level)
    return math.floor(100 * (level ^ 1.5))
end
```

* **Description**: Determines the XP required for a given level.
* **Formula**: `100 * (level ^ 1.5)`, rounded down.

**Economy Configuration**

```lua
Shared.Economy = {
    xp = 100,
    money = 250,
    mulitplerPerLevel = 0.01,
}
```

* **xp**: XP earned per finished job.
* **money**: Money earned per finished job.
* **mulitplerPerLevel**: Additional reward percentage per player level.

**Skill Tree Integration**

```lua
Shared.Enable_SkillTree = true
```

* **Description**: Enables or disables the skill tree feature.
* YOU NEED SKILL TREE SCRIPT, [NORMAL](https://store.devhub.gg/package/6438994) OR [EXCLUSIVE](https://store.devhub.gg/package/6441349)&#x20;
* **Note**: Must ensure the script is loaded after `dh_skillTree`.

**Quest Configuration**

```lua
Shared.Quests = {
    {
        uid = "diamond",
        description = "Collect diamonds",
        value = 2,
        reward = {
            xp = 1000,
            money = 1000,
        },
        rewardMultiplerPerLevel = 0.1,
        questMultiplerPerLevel = 0.8,
    },
    -- Additional quests...
}
```

* **uid**: Unique identifier for the quest.
* **description**: Describes the quest objective.
* **value**: Number of items or actions required to complete the quest.
* **reward**: XP and money granted upon completion.
* **rewardMultiplerPerLevel**: Multiplier applied to rewards based on player level.
* **questMultiplerPerLevel**: Adjusts the difficulty based on player level.

**Ore Configuration**

```lua
Shared.Ores = {
    {
        props = {
            "dh_miner_ore_diamond1",
            "dh_miner_ore_diamond3",
        },
        item = "diamond",
        label = "Diamond",
        maxInQuest = 3,
        amountOnMap = 5,
        chanceToDrop = 80,
        coords = {
            vec3(2928.759033, 2745.326660, 53.625084),
            -- Additional coordinates...
        }
    },
    -- Additional ores...
}
```

* **props**: Defines the models used for the ore.
* **item**: Item name corresponding to the collected ore.
* **label**: Display name for the ore.
* **maxInQuest**: Maximum quantity that can be collected during a quest.
* **amountOnMap**: Number of ore entities that spawn on the map.
* **chanceToDrop**: Probability (in percentage) of successfully collecting the ore.
* **coords**: Positions where ores can be found.

**Language Configuration**

```lua
Shared.Lang = {
    ['Your'] = "Your",
    ['Mission'] = "Mission",
    ['Minigame'] = "Minigame",
    ['Time'] = "Time",
    ['JobName'] = "Miner",
    ['JobDescription'] = "As a miner, your job is to extract raw ores from designated mining areas...",
    -- Additional language entries...
}
```

* **Description**: Customizes text used throughout the script's UI.
* **Usage**: Adjust the right-side values to localize or customize messages.
* **Note**: Keep `${value}` format unchanged to ensure dynamic values work correctly.
