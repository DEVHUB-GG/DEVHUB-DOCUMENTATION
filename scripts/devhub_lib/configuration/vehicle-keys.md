# 🔑 Vehicle Keys

## <mark style="color:yellow;">Auto detection of resource</mark>

By default, the script will try to automatically detect the correct resource.

```lua
Shared.VehicleKeys = "AUTO DETECT"
```

***

## <mark style="color:yellow;">Auto detection failed</mark>

If auto detect failed in **shared.lua**, set `Shared.VehicleKeys` to use the appropriate keys resource or set it to custom and configurate it yourself.

***

## <mark style="color:yellow;">Custom functionality</mark>

Go to **frameworks/c.vehicleKeys.lua** and customize your keys logic

```lua
if Shared.VehicleKeys ~= "custom" then
    Core.AddVehicleKeys = function(plate, vehicle)
        -- Add your custom vehicle keys logic here
    end
end
```

