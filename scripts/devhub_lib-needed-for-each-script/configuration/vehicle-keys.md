# Vehicle keys

#### Vehicle Keys Configuration Guide

To integrate vehicle keys functionality into your script, follow these steps:

***

**1. Open the File**

Navigate to the following file in your project:

```lua
devhub_lib/client/c.functions.lua
```

***

**2. Locate the Function**

Find the function named `Core.SpawnVehicle`.

* It is located approximately at **line 110**.\
  &#xNAN;_(Note: The exact line number may vary based on our changes.)_

***

**3. Add the Code**

After the line:

```lua
SetVehRadioStation(vehicle, 'OFF')
```

Insert the following code:

```lua
local plate = GetVehicleNumberPlateText(vehicle)
```

***

**4. Add Your Key Export**

Directly below the code above, add your key export, for example:

```lua
local plate = GetVehicleNumberPlateText(vehicle)
exports['your_key_resource']:GiveKeys(plate) -- ITS JUST EXAMPLE!!
```

***

**Final Example**

Your function should look like this after the modifications:

```lua
SetVehRadioStation(vehicle, 'OFF')
local plate = GetVehicleNumberPlateText(vehicle)
exports['your_key_resource']:GiveKeys(plate)
```

***

This modification ensures that keys are automatically assigned when a vehicle is spawned using the `Core.SpawnVehicle` function. Save the file and test it in-game to verify functionality.
