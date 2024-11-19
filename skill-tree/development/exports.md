# Exports

<mark style="color:yellow;">**CLIENT / SERVER**</mark>

```lua
exports['dh_skillTree']:hasUnlockedSkill(skill ,uid ,source)
```

Arguments:&#x20;

* skill - skill category name
* uid - skill uid
* source (SERVER SIDE)&#x20;

Returns: nil **or** true\


```lua
exports['dh_skillTree']:addXp(skill ,xp ,source)
```

Arguments:&#x20;

* skill - skill category name
* xp - number
* source (SERVER SIDE) \


```lua
exports['dh_skillTree']:addPoints(skill ,points ,source)
```

Arguments:&#x20;

* skill - skill category name
* points -  number
* source (SERVER SIDE) \


```lua
exports['dh_skillTree']:getSkillEffect(skill ,uid)
```

Arguments:&#x20;

* skill - skill category name
* uid - skill uid

Returns: effect from config **or** 0



<mark style="color:yellow;">**SERVER ONLY**</mark>

```lua
exports['dh_skillTree']:getPlayerLevel(skill ,source)
```

Arguments:&#x20;

* skill
* source

Returns: level or 0



```lua
exports['dh_skillTree']:getPlayerXp(skill ,source)
```

Arguments:

* skill
* source

Returns: xp or 0



```lua
exports['dh_skillTree']:getPlayerPoints(skill ,source)
```

Arguments:

* skill
* source

Returns: points or 0



```lua
exports['dh_skillTree']:getPlayerTotalXp(skill ,source)
```

Arguments:

* skill
* source

Returns: totalXp or 0



```lua
exports['dh_skillTree']:getPlayerGlobalStats(source)
```

Arguments:&#x20;

* source

Returns: globalStats or { totalXp = 0, totalLevel = 0, usedPoints = 0, unlockedSkills = 0, }\
\
<mark style="color:yellow;">**CLIENT ONLY**</mark>

```lua
exports['dh_skillTree']:reloadDefaultSkills()
```

Some people might need that for their ambulance scripts
