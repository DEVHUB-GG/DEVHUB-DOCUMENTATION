# 🛠️ Configuration

### <mark style="color:yellow;">Shared Configuration (shared.lua)</mark>

#### Debug Configuration

Controls debug output for the gym system.

```lua
Shared.Debug = {
    Enabled = true, -- Set to false to disable all debug prints
    Levels = {
        Info = true,    -- General information
        Success = true, -- Success operations
        Warning = true  -- Warnings and potential issues
    }
}
```

* **Enabled**: Enables/disables all debug prints.
* **Levels**: Controls specific debug message types.

***

#### DevHub Skill Tree Integration

Enable or disable integration with the DevHub Skill Tree system.

```lua
Shared.DevhubSkillTreeEnabled = true -- Set to false if you don't want to use devhub_skillTree
```

* **DevhubSkillTreeEnabled**: Set to `true` to use the skill tree system.

***

#### Exercises Configuration

Defines all available gym stations and their properties.

```lua
Shared.Exercises = {
    {
        uid = "kettlebellswing",
        weight = 10, -- Default weight in kg
        maxReps = 10, -- Maximum reps per session
        placeOnTheGround = true, -- Place prop on ground
        propName = "devhub_gym_kettlebell_rack",
        propCoords = vec4(...),
        playerCoords = vec4(...),
    },
    -- Add more exercise stations as needed
}
```

* **uid**: Unique identifier for the exercise type.
* **weight**: Default weight for the exercise.
* **maxReps**: Maximum repetitions per session.
* **placeOnTheGround**: Whether to place the prop on the ground.
* **propName**: The prop model name.
* **propCoords**: World coordinates for the prop.
* **playerCoords**: Where the player stands during the exercise.

***

### <mark style="color:yellow;">Client Configuration (client.lua)</mark>

#### Minigames

Defines the available minigames and their settings for each difficulty.

```lua
Config.Minigames = {
    ['minigame_1'] = { settings = { ... } },
    -- ...
}
```

* **Minigames**: Table of minigame configurations, each with settings for `easy`, `medium`, and `hard` difficulties.

***

#### Exercise Types

Maps each exercise to its minigames and skill tree XP rewards.

```lua
Shared.ExercisesTypes = {
    ["boxing"] = {
        minigames = { 1, 2, 3, 4 },
        skillTrees = { ["gym"] = 30 },
    },
    -- ...
}
```

* **minigames**: List of minigame IDs for the exercise.
* **skillTrees**: XP rewards for each skill tree.

***

#### Weight Boosts

Defines XP and difficulty scaling for different weights.

```lua
Config.WeightBoost = {
    ["1"] = { skillUid = false, boost = 1.0, difficulty = "easy" },
    ["5"] = { skillUid = "gym_weights_1", boost = 1.1, difficulty = "easy" },
    -- ...
}
```

* **skillUid**: Skill required to use this weight (or `false` for no requirement).
* **boost**: XP multiplier for the weight.
* **difficulty**: Minigame difficulty for the weight.

***

### <mark style="color:yellow;">Server Configuration (server.lua)</mark>

#### XP System Integration

Awards XP to players after completing exercises if the skill tree system is enabled.

```lua
Config.AddXP = function(source, xp)
    if Shared.DevhubSkillTreeEnabled then
        exports['devhub_skillTree']:addXp('personal', xp, source)
    end
end
```

* **AddXP**: Function to add XP to a player, using the skill tree system if enabled.

***

### <mark style="color:yellow;">Exercise Flow</mark>

1. **Player approaches a gym prop** (e.g., kettlebell, punch bag).
2. **Minigame starts** based on exercise type and weight.
3. **Player completes reps**; XP is calculated and awarded.
4. **Skill tree integration** (if enabled) grants XP to the appropriate skill.

***

### <mark style="color:yellow;">Customization</mark>

* Add or remove exercises in `shared.lua`.
* Adjust minigame settings and difficulties in `client.lua`.
* Integrate with other systems by modifying the XP function in `server.lua`.

***
