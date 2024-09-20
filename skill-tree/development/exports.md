# Exports

**CLIENT / SERVER**

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
