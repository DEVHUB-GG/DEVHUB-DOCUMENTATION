# 💪 Skill Tree connection

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Make sure **Config.UseDataFromSkillTree** is set to <mark style="color:yellow;">**true**</mark>
{% endhint %}

## <mark style="color:yellow;">Usage</mark>

In **Config.Abilities** connect skill **category** and skill **uid.**

Script automatically detects unlocked skills and will display locked icon on skill that are not yet unlockd.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

## <mark style="color:yellow;">Example</mark>

```lua
Config.Abilities = {
    ['personal'] = { -- category name from skill tree !!!
        name = "Personal",
        displayOrder = 1,
        isVisible = function(source)
            return false
        end,
        abilities = {
            ['moreHp_1'] = {  -- skill uid from skill tree !!!
                label = "More Hp 1",
                icon = "more_hp1.png",
                useCooldown = 5,
                onUse = function()
                    -- execute client side code here
                    print("More hp 1 used by "..GetPlayerName(PlayerId()))
                end
            },
            ['moreHp_2'] = {  -- skill uid from skill tree !!!
                label = "More Hp 2",
                icon = "more_hp2.png",
                useCooldown = 5,
                onUse = function()
                    -- execute client side code here
                    print("More hp 2 used by "..GetPlayerName(PlayerId()))
                end
            },
        }
    },
}
```
