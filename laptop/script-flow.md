---
description: >-
  This guide explains how the DevHub Laptop system works from initial boot to
  application usage.
---

# 🌊 Script Flow

## <mark style="color:yellow;">System Architecture</mark>

### Overview

The DevHub Laptop is a Vue.js-based NUI application that runs inside FiveM. It provides a complete operating system experience with multiple applications, user authentication, and persistent data storage.

### Technology Stack

* **Frontend**: Vue 3 with Vite build system
* **UI Framework**: Tailwind CSS for styling
* **State Management**: Pinia stores
* **Backend**: FiveM Lua server/client scripts
* **Database**: SQL for persistent storage

### Resource Structure

The resource consists of the following structure:

* **`configs/`** (User Accessible): Configuration files that can be modified
  * `sh.config.lua` - Main configuration
  * `sh.apps.lua` - Apps and App Store settings
  * `sh.crimeTraders.lua` - Crime Traders configuration
  * `sh.lang.lua` - Translation strings
* **`escrowed/`** (Protected): Core Lua scripts (cannot be modified)
  * Client scripts
  * Server scripts
  * App logic
* **`html/`** (Protected): Compiled NUI interface (cannot be modified)
  * Compiled HTML/JS/CSS
  * Images and assets
  * Sound files

**Note**: Only files in the `configs/` folder can be edited. All other files are protected and cannot be modified.

***

## <mark style="color:yellow;">First Boot Phase</mark>

### Player Opens Laptop

1. Player executes a command or uses an item to open the laptop
2. Client script triggers NUI display
3. System checks if this is the first time the laptop has been used
4. If first boot detected, system begins setup wizard

### Loading Sequence

The laptop displays a loading screen with multiple initialization steps:

1. **Loading DevhubOS Files**: Initial file system check
2. **Initializing system**: Core system components start
3. **Checking hardware compatibility**: Virtual hardware validation
4. **Initializing system files**: File system preparation
5. **Loading kernel modules**: Core modules load
6. **Configuring system components**: System settings applied
7. **Preparing user environment**: User space setup
8. **Setting up user interface**: UI components ready
9. **Almost ready**: Final preparations
10. **Starting up**: System boot complete

### User Profile Configuration

Player configures their laptop profile:

1. **Username Selection**:
   * Player enters desired username
   * Username stored in database
2. **Avatar Selection**:
   * Player chooses from available avatars
   * Avatars defined in `Config.DefaultAvatars`
   * Selected avatar stored in profile
3. **Wallpaper Selection**:
   * Player chooses from available wallpapers
   * Wallpapers defined in `Config.DefaultWallpapers`
   * Selected wallpaper becomes active background

### Security Settings

Player configures device security:

1. **Password Protection**:
   * Player enters password
   * Player confirms password
   * System validates passwords match
   * Password encrypted and stored
2. **Face ID Setup** (optional):
   * Player can enable Face ID authentication
   * Face ID uses player's character model
   * Enables quick unlock without password

### Setup Completion

1. System saves all configuration to database
2. Pre-installed apps are registered
3. Default settings applied from `Config.DefaultSettings`
4. Welcome message displays
5. System transitions to home screen

***

## <mark style="color:yellow;">Login Phase</mark>

### Standard Boot

When player opens laptop after initial setup:

1. System loads saved user profile from database
2. Login screen displays with username and avatar
3. Player must authenticate to access system

### Authentication Methods

#### Password Login

1. Player enters password in text field
2. System validates against stored password
3. If correct, system grants access
4. If incorrect, error message displays

#### Face ID Login

If Face ID is enabled:

1. System displays "Scanning Face" animation
2. System validates player character model
3. If match, automatic login occurs
4. If no match, "Face Scan Failed" message shows
5. Player can use password as fallback

### Login Success

1. System plays startup sound (if sounds enabled)
2. Home screen loads with user's desktop
3. Installed apps appear on home screen
4. Taskbar displays at bottom
5. Settings and power options available

***

## <mark style="color:yellow;">Home Screen Operations</mark>

### Desktop Layout

The home screen displays:

* **Wallpaper**: Active background image
* **App Icons**: Grid of installed applications
* **Taskbar**: Bottom bar with quick access tools
* **System Tray**: Settings, WiFi, battery, time indicators
* **Notification Area**: System and app notifications

### App Management

#### Opening Apps

1. Player clicks app icon on desktop
2. System checks if app is installed
3. App window opens with specified size
4. App loads its Vue component
5. App appears in taskbar
6. App receives focus

#### App Window Controls

Each app window has controls:

* **Minimize**: Hides window, keeps app running in background
* **Maximize**: Expands window to full screen (if supported)
* **Close**: Exits app and closes window

#### Multiple Apps

Players can:

* Run multiple apps simultaneously
* Switch between apps using taskbar
* Minimize apps to taskbar
* Close individual apps

### System Settings Access

Player can open settings panel to:

1. Toggle WiFi on/off
2. Toggle Bluetooth on/off
3. Enable/disable sound effects
4. Enable/disable ECO mode
5. Adjust screen brightness
6. Adjust system volume
7. Change wallpaper
8. Update security settings
9. Edit username and avatar

### Power Options

From taskbar menu, player can:

* **Shut Down**: Closes laptop, saves state, returns to game

***

## <mark style="color:yellow;">App Store Flow</mark>

### Browsing Apps

1. Player opens App Store from desktop
2. App Store loads available apps from `Config.Apps`
3. Apps displayed by category
4. Recommended apps shown at top (if configured)

### App Categories

Apps are organized into categories:

* **System**: Core system applications
* **Premium**: Premium/paid applications
* **Other**: Additional applications
* Custom categories defined in `Config.AppCategories`

### Searching Apps

1. Player enters search term
2. System filters apps by name and description
3. Results update in real-time
4. Player can clear search to show all apps

### Viewing App Details

1. Player clicks on an app card
2. App details page opens showing:
   * App name and icon
   * Rating and author
   * File size and download count
   * Short and long descriptions
   * Gallery screenshots
   * User reviews
   * Install/Uninstall button

### Installing Apps

#### Regular Apps

1. Player clicks "Download" button
2. System checks if app is already installed
3. App added to user's installed apps
4. App icon appears on desktop
5. Success notification displays

#### Premium Apps

1. Player clicks on premium app
2. Premium content message displays
3. System checks if server has premium access
4. If no access, player cannot install
5. Message directs player to contact server owner

### Uninstalling Apps

1. Player opens App Store
2. Player navigates to installed app
3. Player clicks "Uninstall" button
4. System checks `dontAllowUninstall` property
5. If allowed, app removed from desktop
6. App data may be preserved (app-specific)

***

## <mark style="color:yellow;">Individual App Flows</mark>

### Calculator

1. Player opens Calculator app
2. Calculator interface displays
3. Player clicks number and operator buttons
4. Expression builds in display
5. Player clicks equals to calculate result
6. Result displays or error shown if invalid

### Notepad

1. Player opens Notepad app
2. Notepad loads saved notes from database
3. Player can create new note
4. Player enters note title and content
5. Player clicks Save button
6. Note stored in database
7. Player can select, edit, or delete existing notes

### CMD (Command Line)

1. Player opens CMD app
2. Terminal displays welcome message
3. Player types commands and presses Enter
4. System processes command
5. Output displays in terminal
6. Available commands:
   * `help`: Show available commands
   * `clear`: Clear terminal screen
   * `whoami`: Display current username
   * `date`: Show current date and time

### Browser

1. Player opens Browser app
2. Browser opens in full-screen mode
3. Home page displays with quick links
4. Player can:
   * Enter URL in address bar
   * Click quick link buttons
   * Navigate to websites
   * Use iframe to display web content
5. Browser loads external websites
6. Player can return home or enter new URL

### Clock

1. Player opens Clock app
2. Clock displays:
   * Current local time
   * Current day of week
   * World clocks from `Config.WorldClocks`
3. Each world clock shows:
   * Location name
   * Current time in that timezone
   * Time difference from local time

### Crime Traders (Premium)

1. Player opens Crime Traders app
2. System checks premium access
3. If no access, premium message displays
4. If access granted:
   * Player sees Tasks and Traders sections
   * Player can view available crime actions
   * Player can browse trader shops
   * Player earns XP and Crime Points (CP)
   * Player levels up with traders
   * Player purchases items with CP

#### Tasks Flow

1. Player navigates to Tasks section
2. Available crime actions display by category
3. Player selects a task
4. Player joins queue for task
5. Player waits for turn
6. Task completes, rewards available
7. Player claims XP, money, and CP rewards
8. Cooldown period begins

#### Traders Flow

1. Player navigates to Traders section
2. Available traders display
3. Player selects a trader
4. Shop items display by level
5. Items locked until level requirement met
6. Player purchases items with CP
7. Item added to inventory
8. CP balance updated

***

## <mark style="color:yellow;">Data Persistence</mark>

### Client-Side Storage

The following data is stored locally in browser storage:

* Active wallpaper selection
* Window positions and states
* App preferences
* UI state

### Server-Side Database

The following data is stored in SQL database:

* User profile (username, avatar)
* Security settings (password, Face ID status)
* Installed apps list
* Notepad notes content
* Crime Traders progress (XP, level, CP)
* App-specific data

### Save Triggers

Data is saved automatically when:

* Player changes settings
* Player installs/uninstalls apps
* Player saves notepad notes
* Player completes crime tasks
* Player purchases from traders
* Player shuts down laptop

### Data Loading

Data is loaded when:

* Player opens laptop
* Player logs in
* App requests saved data
* System checks premium access

***

## <mark style="color:yellow;">NUI Communication</mark>

### Client to NUI

Client scripts send data to NUI using:

```lua
SendNUIMessage({
    action = "actionName",
    data = {}
})
```

Common actions:

* Open/close laptop
* Update user data
* Send notifications
* App-specific commands

### NUI to Client

NUI sends data to client using fetch requests:

```javascript
fetch(`https://${resourceName}/callbackName`, {
    method: 'POST',
    body: JSON.stringify(data)
})
```

Common callbacks:

* Save settings
* Install/uninstall apps
* Open/close apps
* Database operations

### Server Integration

Client communicates with server for:

* Database queries
* User authentication
* Item giving/removing
* Cross-player features
* Premium access validation

***

## <mark style="color:yellow;">Sound System</mark>

### Sound Events

The laptop plays sounds for various actions:

* **System Startup**: When laptop boots up
* **Click**: Button and UI interactions
* **Switch On**: Enabling settings
* **Switch Off**: Disabling settings
* **Notification**: New notifications
* **Delete App**: Uninstalling applications

### Sound Configuration

Sounds can be controlled via:

* `soundless` setting in user preferences
* `Config.DefaultSettings.soundless` in config
* Individual volume control in settings

Sound files located in:

* `html/sounds/` folder
* OGG and MP3 formats

***

## <mark style="color:yellow;">Error Handling</mark>

### Client-Side Errors

When errors occur in NUI:

1. Error caught by JavaScript error handlers
2. Error logged to browser console
3. User-friendly notification displayed
4. System attempts graceful degradation

### Server-Side Errors

When errors occur in Lua scripts:

1. Error logged to server console
2. Client receives error response
3. Error message displayed to player
4. Transaction rolled back if applicable

### Common Error Scenarios

* App not found or invalid
* Database connection failure
* Premium access denied
* Invalid user input
* Network timeout
* File not found

Each error displays appropriate message from `Config.Lang` translations.
