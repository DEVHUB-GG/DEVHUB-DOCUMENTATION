# 🛠️ Configuration

## <mark style="color:yellow;">Main Configuration (sh.main.lua)</mark>

### Basic Settings

```lua
Config.MenuCommand = "skill"  -- Command to open menu (string or false)
Config.Keybind = "F7"        -- Keybind to open menu (string or false) 
Config.Item = false          -- Item required to open menu (string or false)
--client event | devhub_skillTree:client:openSkillTree
```

***

### XP Settings

```lua
Config.XpBoost = 1.0         -- XP multiplier
Config.BaseXp = 100          -- Base XP required per level
Config.LevelBasedXp = 50     -- Additional XP per level
Config.PointsPerLevel = 1    -- Skill points awarded per level
```

***

### System Settings

```lua
Config.CloseUiOnDeath = true         -- Close UI on player death
Config.HpRegenerationTimeout = 5000   -- HP regen cooldown (ms)
Config.EnableGenerator = true         -- Enable skill tree generator (Exclusive only)
Config.EarnXpTick = 1000             -- XP earn check interval (ms)
Config.DisableXpEarnWhileDead = false  -- Disable XP earning while dead
```

***

### XP Earning Activities

```lua
Config.EarnXp = {
    ['running'] = {
        xp = 5,              -- XP awarded
        timeout = 10000,     -- Cooldown before next award
        addTo = {            -- Which skill trees receive XP
            ['personal'] = true
        }
    },
    -- Similar settings for: swimming, melee, shooting, driving
}
```

***

### Reset System

```lua
Config.SkillReset = {
    Enabled = false,         -- Enable skill reset feature
    PaymentType = false,     -- Payment method (cash/item/false)
    Cash = 1000,            -- Reset cost if using cash
    Item = {
        Name = "cash",      -- Required item name
        Amount = 1000       -- Required item amount
    }
}
```

***

### Level & Skills Configuration

```lua
Config.MaxLevel = {
    ['personal'] = 7,    -- Max level per skill tree
}

Config.SkillLoadingOrder = {
    -- Control order of skill loading
    ['skillName'] = 1,
}

Config.MeleeWeapons = {
    -- List of weapons affected by melee damage skills
    ["weapon_hammer"] = true,
    -- ...other melee weapons
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

Config.XpCacheLimit = 20 -- int | Used for xp virtualization in all categories from Config.EarnXp, how many ticks should be cached before sending to server
-- How it works? When player earns xp, it is cached in client side and sent to server only when player has enough ticks to send

```

### **Custom Skill Unlock Requirements**

```lua
Config.UnlockHandlerForSkills = {
    ['CATEGORY_UID'] = { -- skill category uid
        ['SKILL_UID'] = {
            unlockRequirementMessage = 'You need to have energy drink to unlock this skill', -- string | Message shown when unlock fail and when they inspect skill in ui
            handler = function(source)
                -- this is triggered server side
                -- return false to prevent unlocking the skill
                -- to use your core in here set it up in /configs/s.main.lua
                return false
            end
        },
        ['SKILL_UID_1,SKILL_UID_2'] = { -- multiple skills in one handler, separated by comma ","
            unlockRequirementMessage = 'You need to have energy drink to unlock this skill', -- string | Message shown when unlock fail and when they inspect skill in ui
            handler = function(source)
                -- this is triggered server side
                -- return false to prevent unlocking the skill
                -- to use your core in here set it up in /configs/s.main.lua
                return false
            end
        },
    },
}
```

***

## <mark style="color:yellow;">Language Configuration (sh.lang.lua)</mark>

The language file contains all text strings used in the UI. Each string can be customized:

```lua
Config.Lang = {
    ['skill_already_unlocked'] = "Skill already unlocked",
    ['not_enough_points'] = "You don't have enough points",
    -- ...more translations
}
```

***

## <mark style="color:yellow;">Server Configuration (s.main.lua)</mark>

### Category visibility

```lua
Config.CategoryVisibilityHandler = {
    ['personal'] = function(source)
        -- Return false to hide category
        return true
    end,
}

```

### Logging Configuration

```lua
Config.Logs = {
    ['addXp'] = "webhook_url",            -- Log XP additions
    ['addPoints'] = "webhook_url",        -- Log point additions
    ['removePoints'] = "webhook_url",     -- Log point removals
    ['removeXp'] = "webhook_url",         -- Log XP removals
    ['levelUp'] = "webhook_url",          -- Log level ups
    ['unlockSkill'] = "webhook_url",      -- Log skill unlocks
    ['skillReset'] = "webhook_url",       -- Log skill resets
    -- Security logs
    ['suspiciousActivityLowPriority'] = "webhook_url",   -- Logs for potential cheating might also be issues (lag/connection)
    ['suspiciousActivityHighPriority'] = "webhook_url"   -- Logs for most likely cheating attempts
}
```

### Security Settings

{% hint style="warning" %}
It is highly advised to keep this option enabled and transition scripts to utilize server-side exports only.
{% endhint %}

```lua
Config.DisableSensitiveClientExports = true  -- Disable client-side sensitive exports
```

#### Suspicious Activity Handler

```lua
Config.SuspiciousActivity = function(source, privateReason, priority)
    -- Called when suspicious activity is detected
    -- priority: 
        -- 'high' (likely cheating)
        -- 'low' (cheater or possible connection issues)
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
