# Exports

## DEVHUB Skill Tree - Exports Documentation



### Parameter Types

Common parameters used across exports:

* `categoryUid` (string): Category uid (e.g., 'personal')
* `skillUid` (string): Unique skill identifier (e.g., 'swimming\_1', 'melee\_damage\_1')
* `source` (number): Player server ID (required for server-side)
* `amount` (number): Numeric value for XP/points

### Client Side Exports

#### `reloadDefaultSkills()`

Reloads all skills in the 'personal' category to their default states.

```lua
-- Example: Reload all default skills (can be useful for some people after ambulance respawn)
exports['devhub_skillTree']:reloadDefaultSkills()
```

#### `closeSkillTree()`

Programmatically closes the skill tree UI.

```lua
-- Example: Close skill tree UI
exports['devhub_skillTree']:closeSkillTree()
```

#### `getConfig()`

Returns current configuration of skills and categories.

**Returns:**

```lua
{
    SkillsCategory = Config.SkillsCategory,
    SkillsList = Config.SkillsList
}
```

### Server Side Exports

#### `getPlayerLevel(categoryUid, source)`

Gets the player's level in a specific skill category.

**Parameters:**

* `categoryUid` (string): Skill category name
* `source` (number): Player server ID

**Returns:** Current level (number) or 0 if not found

```lua
-- Example: Get player's personal skill level
local level = exports['devhub_skillTree']:getPlayerLevel('personal', source)
print('Player level:', level)
```

#### `getPlayerXp(categoryUid, source)`

Gets the player's current XP in a specific skill.

**Parameters:**

* `categoryUid` (string): Skill category name
* `source` (number): Player server ID

**Returns:** Current XP (number) or 0 if not found

```lua
-- Example: Get player's current XP
local xp = exports['devhub_skillTree']:getPlayerXp('personal', source)
print('Current XP:', xp)
```

#### `getPlayerPoints(categoryUid, source)`

Gets the player's available points for a specific skill.

**Parameters:**

* `categoryUid` (string): Skill category name
* `source` (number): Player server ID

**Returns:** Available points (number) or 0 if not found

```lua
-- Example: Check if player has points available
local points = exports['devhub_skillTree']:getPlayerPoints('personal', source)
print('Available points:', points)
```

#### `getPlayerTotalXp(categoryUid, source)`

Gets the player's total accumulated XP in a specific skill.

**Parameters:**

* `categoryUid` (string): Skill category name
* `source` (number): Player server ID

**Returns:** Total XP (number) or 0 if not found

```lua
-- Example: Get total XP earned
local totalXp = exports['devhub_skillTree']:getPlayerTotalXp('personal', source)
print('Total XP earned:', totalXp)
```

#### `getPlayerGlobalStats(source)`

Gets the player's global statistics across all skills.

**Parameters:**

* `source` (number): Player server ID

**Returns:**

```lua
{
    totalXp = number,
    totalLevel = number,
    usedPoints = number,
    unlockedSkills = number
}
```

```lua
-- Example: Get player's global stats
local stats = exports['devhub_skillTree']:getPlayerGlobalStats(source)
print('Total levels:', stats.totalLevel)
```

#### `getUnlockedSkills(source)`

Gets all skills unlocked by the player.

**Parameters:**

* `source` (number): Player server ID

**Returns:** Table of unlocked skills or false if player not found

```lua
-- Example: Check unlocked skills
local unlockedSkills = exports['devhub_skillTree']:getUnlockedSkills(source)
if unlockedSkills then
    for skill, _ in pairs(unlockedSkills) do
        print('Unlocked:', skill.categoryUid, skill.uid)
    end
end
```

### Shared Exports

These exports work on both client and server side.

#### `hasUnlockedSkill(categoryUid, skillUid, [source])`

Checks if a player has unlocked a specific skill.

**Parameters:**

* `categoryUid` (string): Skill category name
* `skillUid` (string): Unique identifier of the skill
* `source` (number): Player server ID (server-side only)

**Returns:** `true` if unlocked, `nil` otherwise

```lua
-- Client side example
local hasSkill = exports['devhub_skillTree']:hasUnlockedSkill('personal', 'swimming_1')

-- Server side example
local hasSkill = exports['devhub_skillTree']:hasUnlockedSkill('personal', 'swimming_1', source)
```

#### `addXp(categoryUid, amount, [source])`

Adds XP to a specific skill.

**Parameters:**

* `categoryUid` (string): Skill category name
* `amount` (number): Amount of XP to add
* `source` (number): Player server ID (server-side only)

```lua
-- Client side example
exports['devhub_skillTree']:addXp('personal', 100)

-- Server side example
exports['devhub_skillTree']:addXp('personal', 100, source)
```

#### `addPoints(categoryUid, amount, [source])`

Adds skill points to a specific category.

**Parameters:**

* `categoryUid` (string): Skill category name
* `amount` (number): Amount of points to add
* `source` (number): Player server ID (server-side only)

```lua
-- Client side example
exports['devhub_skillTree']:addPoints('personal', 1)

-- Server side example
exports['devhub_skillTree']:addPoints('personal', 1, source)
```

#### `getSkillEffect(categoryUid, skillUid)`

Gets the effect value of a specific skill.

**Parameters:**

* `categoryUid` (string): Skill category name
* `skillUid` (string): Unique identifier of the skill

**Returns:** Effect value (number) or 5 if not found

```lua
-- Example: Get skill effect value
local effect = exports['devhub_skillTree']:getSkillEffect('personal', 'strength_1')
print('Skill effect:', effect)
```
