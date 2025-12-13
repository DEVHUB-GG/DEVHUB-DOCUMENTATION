# config.lua

{% code fullWidth="true" %}
```lua
Config = {}

Config.OpenGuideBook = {
    command = "guidebook",
    key = {                         -- can be nil
        defaultMapper = "KEYBOARD", -- https://docs.fivem.net/docs/game-references/input-mapper-parameter-ids/
        defaultParameter = "L"      -- https://docs.fivem.net/docs/game-references/input-mapper-parameter-ids/
    }
}

Config.SfxVolume = {
    changequestsize = 0.1, -- 0-1.0
    clickcustombutton = 0.1, -- 0-1.0
    completequest = 0.1, -- 0-1.0
    completequeststage = 0.1, -- 0-1.0
    enablequests = 0.1, -- 0-1.0
    turnpage = 0.1, -- 0-1.0
}

Config.UiScale = 1.3

Config.Book = {}

Config.Book.HomePage = {
    author = {
        title = "Author",
        name = "DEVHUB",
        img =
        "https://upload.devhub.gg/dh_upload/devhubLogo.webp",
    },
    fadingText = "GUIDEBOOKGUIDEBOOKGUIDEBOOK",
    title = "GUIDE ",
    titleExtra = "BOOK",
    subtitle = "Master your experience",
    description =
    "This comprehensive manual is designed to help you navigate and master various jobs and civilian activities available in our server. Inside, you'll find step-by-step instructions, tips, and tricks to excel in your chosen path.",
    image =
    "https://a-static.besthdwallpaper.com/grand-theft-auto-v-los-santos-sunset-panorama-wallpaper-3440x1440-19341_15.jpg",
}

Config.Book.Content = {
    {
        label = "Jobs",
        icon = "fa-solid fa-suitcase", -- https://fontawesome.com/icons
        pages = {
            -- {
            --     title = "How to become a miner",
            --     description =
            --     "Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum.", -- can be nil
            --     image =
            --     "https://wiki.highliferoleplay.net/uploads/images/gallery/2023-05/soapymining.png",                                                                                                                                                                                                                                                                                 -- can be nil                                                                                                                                                                                                                                                                        -- link to image or false
            --     steps = {                                                                                                                                                                                                                                                                                                                                                           -- can be nil
            --         {
            --             title = "Step 1",
            --             text =
            --             "Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam "
            --         },
            --         {
            --             title = "Step 2",
            --             text =
            --             "Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam "
            --         }
            --     },
            --     customButtons = { -- can be nil
            --         {
            --             title = "Example Button",
            --             style = "primary", -- "primary" or "secondary"
            --             func = function()
            --                 -- your code
            --                 print("TEST")
            --                 return tru
            --             end
            --         },
            --         {
            --             title = "Example Button 2",
            --             style = "secondary", -- "primary" or "secondary"
            --             func = function()
            --                 -- your code
            --                 print("TEST2")
            --                 return true
            --             end
            --         }
            --     }
            -- }
            {
                title = "How to become a Miner",
                description = "As a miner, your job is to extract raw ores from designated mining areas. Once you've gathered enough ores, you transport them to a smelting facility where they are refined into bars. After refining, take the bars to the jeweler, who will purchase them from you.",
                image = "http://upload.devhub.gg/dh_upload/guidebook/miner.png",
                steps = {
                    {
                        title = "Step 1 - Talk to the Miner NPC",
                        text = "Head to the mining area and speak with the Miner Job NPC to open the job menu. From here you can view your level, select a uniform, rent a vehicle, and start your mining shift."
                    },
                    {
                        title = "Step 2 - Equip and Start the Job",
                        text = "Choose your miner outfit, rent a work vehicle, and press 'Start Job' to begin. You will receive a drill tool and your task will be to collect ores like Diamond, Emerald, Gold, Silver, Steel, or Ruby."
                    },
                    {
                        title = "Step 3 - Mine the Ores",
                        text = "Drive to the mining zone and look for ore deposits. Use your drill on the ores and complete the minigame to successfully extract them. Collect the required amount shown in your task list."
                    },
                    {
                        title = "Step 4 - Smelt the Ores",
                        text = "Once you have collected enough ores, follow your GPS to the Smelting location. Interact with the smelter and complete the minigame to refine your ores into ingots."
                    },
                    {
                        title = "Step 5 - Sell the Ingots",
                        text = "After smelting, drive to the Selling location marked on your GPS. Sell your ingots to complete the job and receive your XP and cash rewards. Complete quests for bonus rewards!"
                    }
                },
                customButtons = {
                    {
                        title = "Go to Start Location",
                        style = "primary",
                        func = function()
                            SetEntityCoords(PlayerPedId(), 2832.3860, 2798.6382, 57.4497)
                            return true
                        end
                    }
                }
            },
        },
    },
}

Config.AutoEnableQuests = true -- enable quests on playerLoaded | if false you need to call server event "dh_guidebook:server:enableQuests" from client to start quests (example: TriggerServerEvent("dh_guidebook:server:enableQuests"))

Config.QuestsKeybinds = {
    changeSize = {
        defaultMapper = "KEYBOARD", -- https://docs.fivem.net/docs/game-references/input-mapper-parameter-ids/
        defaultParameter = "U"      -- https://docs.fivem.net/docs/game-references/input-mapper-parameter-ids/
    },
    cancel = {
        defaultMapper = "KEYBOARD", -- https://docs.fivem.net/docs/game-references/input-mapper-parameter-ids/
        defaultParameter = "H"      -- https://docs.fivem.net/docs/game-references/input-mapper-parameter-ids/
    },
    useHint = {
        defaultMapper = "KEYBOARD", -- https://docs.fivem.net/docs/game-references/input-mapper-parameter-ids/
        defaultParameter = "M"      -- https://docs.fivem.net/docs/game-references/input-mapper-parameter-ids/
    }
}

Config.Quests = {
    {
        title = "First Radio Connection",
        photo = "http://upload.devhub.gg/dh_upload/guidebook/radio.png",
        description = "Get a radio item and connect to any radio channel for the first time. Use /radio command or the radio item from your inventory.",
        hint = {
            coords = false,
            text = "Get a radio item and connect to any channel.",
        },
        amount = 1,
        events = { "devhub_radio:connectedToRadio" },
        rewards = {
            {
                item = "money",
                count = 1000
            }
        },
        collectedText = "Radio connections:",
        rewardText = "$1,000"
    },
}

```
{% endcode %}
