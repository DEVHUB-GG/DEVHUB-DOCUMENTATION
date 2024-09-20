# 🛠️ Configuration

**configs/sh.main.lua**

```lua
Config.MenuCommand = "skill" -- string or false
Config.Keybind = "F7" -- string or false

Config.XpBoost = 1.0 -- float

Config.BaseXp = 100 -- int | Base xp for each level
Config.LevelBasedXp = 50 -- int | Xp increase for each level (BaseXp + (Level * LevelBasedXp))

Config.PointsPerLevel = 1 -- int | Points given for each level up

Config.CloseUiOnDeath = true -- bool | Close the UI when the player dies , disable ui while dead , must be configured in dh_lib "dh_lib:client:setDeathStatus"

Config.HpRegenerationTimeout = 5000 -- int | If player has unlocked skill, every how many sec he should restore hp

Config.EnableGenerator = true -- bool | Enable the generator for the skill tree [ONLY EXCLUSIVE VERSION]

Config.EarnXpTick = 500 -- int | Time in ms for each tick , check if players is doing actions from Config.EarnXp

Config.EarnXp = {
    -- if you want to disable option , just remove it
    ['running'] = {
        xp = 5, -- int | Xp given for each tick
        timeout = 3000 -- int | Timeout in ms , cooldown for receiving xp
    },
    ['swimming'] = {
        xp = 5,
        timeout = 3000
    },
    ['melee'] = {
        xp = 5,
        timeout = 3000
    },
    ['shooting'] = {
        xp = 5,
        timeout = 3000
    },
    ['driving'] = {
        xp = 5,
        timeout = 3000
    },
}

-- update 1.0.2

Config.SkillReset = {
    Enabled = false, -- bool | Enable the skill reset
    PaymentType = false, -- string , bool | Payment type (cash or item, false to make it for free)
    Cash = 1000, -- int | Price for reseting the skills
    Item = {
        Name = "cash", -- string | Item name
        Amount = 1000 -- int | Amount of item
    }
}

-- update 1.0.4

Config.MaxLevel = {
    -- ['personal'] = 7, -- int | Max level for personal skills
}

-- You can set up custom order for loading events on player loaded
-- Why? In database we store player data as hashmap, so we do not have control over the order of loading
-- Usually you do not need to change this, but sometimes you may want to load some events before others to make sure they overwrite some values
-- It only affect the loading order of events during first time player loading
-- First we execute events no in this table, after that we execute events in this table

Config.SkillLoadingOrder = {
    -- ['betterAccuracy_1'] = 1,
    -- ['betterAccuracy_2'] = 2,
    -- ['fasterReload_1'] = 3,
    -- ['fasterReload_2'] = 4,
}

```

* **Config.MenuCommand**: The command used to open the menu.\
  **Type**: `string` or `false`
* **Config.Keybind**: The keybind used to open the menu.\
  **Type**: `string` or `false`
* **Config.XpBoost**: The multiplier applied to experience points (XP) earned.\
  **Type**: `float`
* **Config.BaseXp**: The base experience points required for each level.\
  **Type**: `int`
* **Config.LevelBasedXp**: The additional experience points required for each level, calculated as `BaseXp + (Level * LevelBasedXp)`.\
  **Type**: `int`
* **Config.PointsPerLevel**: The number of points awarded to the player for each level up.\
  **Type**: `int`
* **Config.CloseUiOnDeath**: Determines whether the UI should close when the player dies.\
  **Type**: `bool`
* **Config.EnableGenerator**: Enable the generator for the skill tree \[ONLY EXCLUSIVE VERSION]\
  **Type**: `bool`
* **Config.EarnXpTick**: Tick checking if players is doing actions from Config.EarnXp\
  **Type**:  `int`
* **Config.EarnXp**: Object with actions for which player will be reward\
  **Type**:  `object`
* **Config.HpRegenerationTimeout**: If player has unlocked skill, every how many sec he should restore hp\
  **Type**:  `int`
* **Config.SkillReset:** Give player option to reset skills\
  **Type**:  `object`
* **Config.MaxLevel:** Set the maximum level for each skill category\
  **Type**:  `object`
* **Config.SkillLoadingOrder:** Define the skill loading order during the player loaded event\
  **Type**:  `object`

**configs/sh.lang.lua**

```lua
-- Language Configuration
-- Change the value (right side) as needed
-- Do not change the key (left side)
-- Maintain the %{value} format
Config.Lang = {
    ['skill_already_unlocked'] = "Skill already unlocked",
    ['not_enough_points'] = "You don't have enough points",
    ['skill_tree'] = "Skill Tree",
    ['Unknown'] = "Unknown",
    ['Skill'] = "Skill",
    ['Tree'] = "Tree",
    ['skill_tree_generator'] = "Skill Tree Configurator",
    ['view_details'] = "View Details",
    ['unlock_skill'] = "Unlock Skill",
    ['hold'] = "Hold",
    ['click'] = "Click",
    ['close_menu'] = "Close Menu",
    ['tree_generator'] = "Tree Generator",
    ['Generate'] = "Generate",
    ['close_generator'] = "Close Generator",
    ['category_uid'] = "Category Uid",
    ['select_box'] = "SELECT BOX TO EDIT",
    ['generator_c'] = "GENERATOR",
    ['skill_uid'] = "Skill Uid",
    ['unlock_points'] = "Unlock Points",
    ['skill_name'] = "Skill Name",
    ['icon'] = "Icon",
    ['image'] = "Image/Gif",
    ['description'] = "Description",
    ['section_name'] = "Section Name",
    ['skill_effect'] = "Skill Effect",
    ['only_lines'] = "Only Lines",
    ['default_unlocable'] = "Default Unlocable",
    ['actions'] = "Actions",
    ['remove'] = "Remove",
    ['optional'] = "Optional",
    ['skill_info'] = "Skill Info",
    ['level_up'] = "Level Up",
    ['level_up_skill'] = "Skill: %{skill}",
    ['error'] = "Error",
    ['generate_new'] = "Generate new",
    ['edit_existing'] = "Edit existing",
    ["success"] = "Success",
    ['config_copied'] = "Config copied to clipboard, put it into your config and restart script",
    ['category_already_used'] = "This category is already in use",
    ['correct'] = "Correct",
    ['uid_already_used'] = "This uid is already in use",
    ['not_number'] = "This is not a number",
    ['required'] = "Required",
    ['correct'] = "Correct",
    ['wrong'] = "Wrong",
    ['cancel'] = "Cancel",
    ['confirm'] = "Confirm" ,
    ['areUSure'] = "Are you absolutely sure?",
    ['important'] = "This is really important",
    ['close_generator_confirm'] = "Do you want to close without saving ?",
    ['save_generator_confirm'] = "Do you want to close and save config to your clipboard",
}
```

In the `sh.lang.lua` file, you can customize the language settings for various script elements. The keys on the left should not be altered, but you can change the corresponding values on the right to suit your preferences. Ensure that the %`{value}` format remains unchanged.

**configs/sh.skills.lua**

```lua
-- skill = 'CATEGORY_UID', title = 'YOUR_TITLE'
Config.SkillsCategory = {
    {skill = 'personal', title = 'Personal'},
}

-- grid
-- 171 [9x19]

Config.SkillsList = {
    ["personal"] = {
        {
            points = 1,
            lines = { right = false, rightBottom = false, },
            icon = "fa-solid fa-person-rifle",
            index = 6,
            title = "Aim Movement Speed IV",
            description = "Increases your movement speed while aiming by 10%.",
            uid = "aimSpeedMultiplier_4",
            img = "https://upload.devhub.gg/dh_upload/aiming.gif",
            effect = 10,
        },
        {
            lines = { left = false, right = false, },
            index = 7 ,
        },
        {
            lines = { left = false, right = false, },
            index = 8 ,
        },
        {
            points = 1,
            lines = { left = false, right = false, },
            icon = "fa-solid fa-crosshairs",
            index = 9,
            title = "Reduced Recoil IV",
            description = "Reduces weapon recoil by 10% for improved accuracy",
            uid = "betterAccuracy_4",
            img = "https://upload.devhub.gg/dh_upload/recoil.gif",
            effect = 10,
        },
    }
}
```

**Config.SkillsCategory**: Defines the categories of skills available, each with a unique identifier (`skill`) and a display title (`title`).\
\
**Config.SkillsList**: Contains the list of skills organized by categories.
