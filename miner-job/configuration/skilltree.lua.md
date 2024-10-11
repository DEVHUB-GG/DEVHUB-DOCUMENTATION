---
description: Documentation for skillTree.lua Configuration
---

# skillTree.lua

**Skills List**

```lua
Shared.SkillsList = {
    ["miner"] = {
        {
            uid = "cash_boost_4",
            title = "Golden Touch IV",
            description = "Increases cash earned by 5%.",
            effect = 5,
            points = 1,
            index = 9,
        },
        -- Additional skills...
    },
}
```

* **uid**: Unique identifier for the skill.
* **title**: Name of the skill.
* **description**: Explains the effect of the skill.
* **effect**: Value of the skill's effect (e.g., 5% bonus).
* **points**: Points required to unlock the skill.
* **index**: Skill's position in the skill tree.
