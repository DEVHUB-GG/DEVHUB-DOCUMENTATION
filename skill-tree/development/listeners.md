# Listeners

## <mark style="color:yellow;">Client Events</mark>

### Skill Unlock Event

Triggered when a player unlocks a new skill and after player is loaded first time to server. This should be used if you have skill which apply effect one time, its good for optimalization.

```lua
local moreHp = 0
RegisterNetEvent('devhub_skillTree:client:listener:skillUnlocked', function(categoryUid, skillUid)
    local ped = PlayerPedId()
    local maxHp = GetEntityMaxHealth(ped)
    if categoryUid == 'personal' and skillUid == 'moreHp' then
        moreHp = moreHp + 50
    end
    SetPedMaxHealth(ped, maxHp + moreHp)
end)
```

**Parameters:**

* `categoryUid` (string): Category name (e.g., 'personal')
* `skillUid` (string): Unique identifier of the unlocked skill

***

### XP Gain Event

Triggered when a player receives new XP.

{% hint style="info" %}
XP from the personal category is cached on the client side and refreshed every few minutes
{% endhint %}

```lua
RegisterNetEvent('devhub_skillTree:client:listener:newXp', function(categoryUid, amount)
    exports['your-hud']:ShowNotification({
        type = 'xp',
        message = string.format('+%d XP (%s)', amount, categoryUid),
        duration = 3000
    })
end)
```

**Parameters:**

* `categoryUid` (string): Category name (e.g., 'personal')
* `amount` (number): Amount of XP received

***

### Skill Reset Event

Triggered when a player resets their skills in a category.

```lua
local effectApplied = true
RegisterNetEvent('devhub_skillTree:client:listener:skillReset', function(categoryUid)
    if categoryUid == 'personal' then
        effectApplied = false
    end
end)
```

**Parameters:**

* `categoryUid` (string): Category name (e.g., 'personal')

***

### Level Up Event

Triggered when a player levels up in a skill category.

```lua
RegisterNetEvent('devhub_skillTree:client:listener:levelUp', function(categoryUid, newLevel)
    exports['your-hud']:ShowNotification({
        type = 'level',
        message = string.format('Level up! %s reached level %d', categoryUid, newLevel),
        duration = 3000
    })
end)
```

**Parameters:**

* `categoryUid` (string): Category name (e.g., 'personal')
* `newLevel` (number): The new level achieved
