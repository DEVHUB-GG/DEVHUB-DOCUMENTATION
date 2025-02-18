# ⛽ Vehicle fuel

## <mark style="color:yellow;">Pre configured scripts</mark>

* LegacyFuel
* ps-fuel
* ox\_fuel
* cd\_fuel
* custom

***

## <mark style="color:yellow;">Auto detection of resource</mark>

By default, the script will try to automatically detect the correct resource.

```lua
Shared.VehicleFuel = "AUTO DETECT"
```

***

## <mark style="color:yellow;">Auto detection failed</mark>

If auto detect failed in **shared.lua**, set `Shared.VehicleFuel` to use the appropriate keys resource or set it to custom and configurate it yourself.

***

## <mark style="color:yellow;">Custom functionality</mark>

Go to **frameworks/c.vehicleFuel.lua** and customize your fuel logic

```lua
Core.SetVehicleFuel = function(vehicle, amount)
    SetVehicleFuelLevel(vehicle, formatFuel(amount)) -- custom or default
end
```

