# Example skill

**configs/sh.skills.lua**

```lua
["test"] = {
            {
                        points = 1,
                        lines = { right = false, rightTop = false, left = false, },
                        icon = "fa-solid fa-heart-circle-plus",
                        index = 165,
                        title = "More HP I",
                        description = "Increases your maximum health by 10%.",
                        uid = "more_hp",
                        img = "https://upload.devhub.gg/dh_upload/max_hp.gif",
                        effect = 10,
            },
            {
                        points = 1,
                        lines = { right = false, rightTop = false, left = false, },
                        icon = "fa-solid fa-dollar-sign",
                        index = 166,
                        title = "Bank Access",
                        description = "You can enter bank",
                        uid = "bank_access",
                        img = "https://upload.devhub.gg/dh_upload/bank.gif",
            },
 },
```

**your\_script.lua**

<pre class="language-lua"><code class="lang-lua"><strong>-- EXAMPLE 1 usage of listener and skill effect
</strong><strong>RegisterNetEvent('dh_skillTree:client:listener:skillUnlocked',function(skill, uid)
</strong>    if skill == 'test' and uid == 'more_hp' then
        local moreHp = 200
        local effect = exports['dh_skillTree']:getSkillEffect(skill,uid) or 0
        moreHp = moreHp + effect
<strong>        SetEntityMaxHealth(PlayerPedId(),moreHp)
</strong>    end
end)

-- EXAMPLE 2 usage of has unlocked skill
RegisterCommand('bank',function()
    local isAllowed = exports['dh_skillTree']:hasUnlockedSkill('test', 'bank_access') or false
    if isAllowed then 
        print('SKILL UNLOCKED')
    else
        print('DO NOT HAVE SKILL')
    end
end)
</code></pre>

