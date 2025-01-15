# 🛠️ Configuration

## <mark style="color:yellow;">Main Configuration (sh.main.lua)</mark>

### Basic Settings

```lua
Config.MenuCommand = "skill"  // Command to open menu (string or false)
Config.Keybind = "F7"        // Keybind to open menu (string or false) 
Config.Item = false          // Item required to open menu (string or false)
```

***

### XP Settings

```lua
Config.XpBoost = 1.0         // XP multiplier
Config.BaseXp = 100          // Base XP required per level
Config.LevelBasedXp = 50     // Additional XP per level
Config.PointsPerLevel = 1    // Skill points awarded per level
```

***

### System Settings

```lua
Config.CloseUiOnDeath = true         // Close UI on player death
Config.HpRegenerationTimeout = 5000   // HP regen cooldown (ms)
Config.EnableGenerator = true         // Enable skill tree generator (Exclusive only)
Config.EarnXpTick = 1000             // XP earn check interval (ms)
```

***

### XP Earning Activities

```lua
Config.EarnXp = {
    ['running'] = {
        xp = 5,              // XP awarded
        timeout = 10000,     // Cooldown before next award
        addTo = {            // Which skill trees receive XP
            ['personal'] = true
        }
    },
    // Similar settings for: swimming, melee, shooting, driving
}
```

***

### Reset System

```lua
Config.SkillReset = {
    Enabled = false,         // Enable skill reset feature
    PaymentType = false,     // Payment method (cash/item/false)
    Cash = 1000,            // Reset cost if using cash
    Item = {
        Name = "cash",      // Required item name
        Amount = 1000       // Required item amount
    }
}
```

***

### Level & Skills Configuration

```lua
Config.MaxLevel = {
    // ['personal'] = 7,    // Max level per skill tree
}

Config.SkillLoadingOrder = {
    // Control order of skill loading
    // ['skillName'] = priority,
}

Config.MeleeWeapons = {
    // List of weapons affected by melee damage skills
    ["weapon_hammer"] = true,
    // ...other melee weapons
}

Config.SkillDefaultValues = {
    ['moreStamina'] = 100.0,
    ['moreMaxHp'] = 200,
    ['timeUnderwater'] = 10.0,
}

Config.DisableDefaultSkillEffects = {
    ['runFaster'] = false,
    ['swimFaster'] = false,
    ['moreStamina'] = false,
    ['timeUnderwater'] = false,
    ['moreMaxHp'] = false,
}

Config.DisableRefreshOnPedOrPidChanged = false
```

***

## <mark style="color:yellow;">Language Configuration (sh.lang.lua)</mark>

The language file contains all text strings used in the UI. Each string can be customized:

```lua
Config.Lang = {
    ['skill_already_unlocked'] = "Skill already unlocked",
    ['not_enough_points'] = "You don't have enough points",
    // ...more translations
}
```

***

## <mark style="color:yellow;">Server Configuration (s.main.lua)</mark>

Category visibility can be controlled server-side:

```lua
Config.CategoryVisibilityHandler = {
    ['personal'] = function(source)
        // Return false to hide category
        return true
    end,
}

```

***

## <mark style="color:yellow;">Skills Configuration (sh.skills.lua)</mark>

The skills configuration defines all available skills and their properties. Each skill is defined with:

* `uid`: Unique identifier
* `title`: Display name
* `icon`: FontAwesome icon or image URL
* `effect`: Numerical effect value
* `description`: Skill description
* `points`: Points required to unlock
* `img`: Preview image/gif URL
* `lines`: Connection lines to other skills
* `index`: Position in skill grid (171 total slots in 9x19 grid)

Example skill entry:

```lua
{
    description = "Increases running speed by 3%",
    icon = "fa-solid fa-person-running-fast",
    points = 1,
    uid = "runFaster_1", 
    img = "https://example.com/run.gif",
    lines = { top = false, leftTop = false },
    title = "Speed Boost I",
    index = 139,
    effect = 1,
}
```

***

## <mark style="color:yellow;">Ui Configuration (config.js)</mark>

{% hint style="info" %}
W**here to find:** html/config.js
{% endhint %}

```javascript
window.config = {
    numberFormatting: [/\B(?=(\d{3})+(?!\d))/g, " "],
    soundVolume: 0.25,
};
```
