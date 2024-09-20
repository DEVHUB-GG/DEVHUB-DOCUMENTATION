# Listeners

**This are client events that are trigger during different actions , you can connect them to your custom functions like displaying received xp in your hud**

***

Will be triggered as client event when user unlocks new skill or after player is loaded

{% code fullWidth="false" %}
```lua
RegisterNetEvent('dh_skillTree:client:listener:skillUnlocked',function(skill, uid) end)
```
{% endcode %}

Arguments:&#x20;

* skill - skill category name
* uid - skill uid

***

Will be triggered as client event when new xp is added

```lua
RegisterNetEvent('dh_skillTree:client:listener:newXp',function(skill, xp) end)
```

Arguments:

* skill - skill category name
* xp - number

***

Will trigger client event when user resets his skills

```lua
RegisterNetEvent('dh_skillTree:client:listener:skillReset',function(skill) end)
```

Arguments:&#x20;

* skill - skill category name
