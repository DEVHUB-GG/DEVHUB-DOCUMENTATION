---
description: >-
  This guide helps resolve common issues with the DevHub Laptop script based on
  configuration and setup.
---

# ⚠️ Troubleshooting

## <mark style="color:yellow;">Resource Not Starting</mark>

### Check FiveM Manifest

**Problem:** Resource fails to start or shows errors in console.

**Solution:**

1.  Verify the `fxmanifest.lua` file exists and is properly formatted:

    ```lua
    fx_version 'cerulean'
    games {'gta5'}
    lua54 'yes'
    ```
2.  Ensure the resource name in `server.cfg` matches the folder name:

    ```lua
    ensure devhub_laptop
    ```
3. Check that all required files are present:
   * `fxmanifest.lua`
   * `configs/` folder with all config files
   * `escrowed/` folder with Lua scripts
   * `html/` folder with compiled NUI files

### Check UI Page Configuration

**Problem:** Laptop opens but shows blank screen or doesn't load.

**Solution:**

1.  Verify the `ui_page` in `fxmanifest.lua` is set to production:

    ```lua
    ui_page "html/index.html"
    ```
2. **Note**: The `fxmanifest.lua` file may be protected. If you cannot modify it, ensure the resource was not corrupted during installation.
3. Verify the `html/` folder contains:
   * `index.html`
   * `assets/` folder with JS and CSS files
   * `images/` folder with assets
   * `sounds/` folder with audio files
4. If files are missing, re-download or restore from backup

### Check File Permissions

**Problem:** Resource fails to load files or access data.

**Solution:**

1. Ensure the resource folder has proper read permissions
2.  On Linux, verify ownership and permissions:

    ```bash
    chown -R fivem:fivem /path/to/devhub_laptop
    chmod -R 755 /path/to/devhub_laptop
    ```
3. Check that escrowed files are not corrupted

***

## <mark style="color:yellow;">Database Issues</mark>

### SQL Tables Not Created

**Problem:** Players cannot save data, getting database errors.

**Solution:**

1. Import the `sql.sql` file into your database
2.  Verify tables exist by running:

    ```sql
    SHOW TABLES LIKE 'devhub_laptop%';
    ```
3. Expected tables should include:
   * User profile tables
   * App data tables
   * Crime Traders tables (if using premium app)
4. If tables don't exist, manually execute the SQL file

### Database Connection Errors

**Problem:** Script cannot connect to database.

**Solution:**

1. Verify your database credentials in your framework's config
2. Check that the database server is running
3. Test database connection using MySQL client
4.  Ensure the database user has proper permissions:

    ```sql
    GRANT ALL PRIVILEGES ON database_name.* TO 'user'@'localhost';
    FLUSH PRIVILEGES;
    ```

### Data Not Saving

**Problem:** User changes don't persist after logout or restart.

**Solution:**

1. Check server console for SQL errors
2. Verify the script has write permissions to database
3. Ensure transactions are completing:
   * Check for script errors during save operations
   * Verify no server crashes during data writes
4. Test by manually inserting data to confirm database is writable

***

## <mark style="color:yellow;">NUI Problems</mark>

### Blank Screen or Black Screen

**Problem:** Laptop opens but shows only blank or black screen.

**Solution:**

1. Open browser console (F12) and check for JavaScript errors
2. Common causes:
   * Missing `html/index.html` file
   * Broken JavaScript in compiled assets
   * CORS issues with external resources
3. Verify NUI is enabled in FiveM settings:
   * Check `NUI DevTools` is accessible
4. Try rebuilding the UI:
   * Navigate to Vue project folder
   * Run `npm run build`
   * Copy `dist/` contents to resource `html/` folder

### UI Not Responding to Clicks

**Problem:** Can see laptop but cannot interact with buttons or UI elements.

**Solution:**

1. Check if NUI focus is enabled:
   * Script should call `SetNuiFocus(true, true)` when opening laptop
2. Verify no other resources are stealing NUI focus
3. Check browser console for JavaScript errors
4. Ensure cursor is enabled:
   * Script should enable cursor when laptop opens

### Images or Assets Not Loading

**Problem:** UI loads but images are missing or broken.

**Solution:**

1.  Verify image paths in config files use correct format:

    ```lua
    -- Correct format for local resources:
    "https://cfx-nui-devhub_laptop/html/images/apps/calculator.png"

    -- Or use external CDN URLs:
    "https://upload.devhub.gg/path/to/image.webp"
    ```
2. Check that files exist in `html/images/` folder
3. Verify file extensions match exactly (case-sensitive)
4. Clear FiveM cache and restart

***

## <mark style="color:yellow;">Configuration Errors</mark>

### Lua Syntax Errors

**Problem:** Script fails to start with Lua syntax errors in console.

**Solution:**

1. Check all config files for syntax errors:
   * Missing commas in tables
   * Mismatched brackets `{}`, `[]`
   * Unclosed strings `""`
2.  Common mistakes:

    ```lua
    -- WRONG: Missing comma
    Config.Apps = {
        ['calculator'] = { label = "Calculator" }
        ['notepad'] = { label = "Notepad" }
    }

    -- CORRECT:
    Config.Apps = {
        ['calculator'] = { label = "Calculator" },
        ['notepad'] = { label = "Notepad" },
    }
    ```
3. Use a Lua validator or IDE with syntax checking
4. Check for invalid characters or encoding issues

### Missing Configuration Values

**Problem:** Features not working due to missing config values.

**Solution:**

1. Verify all required config tables exist:
   * `Config.DefaultWallpapers`
   * `Config.DefaultAvatars`
   * `Config.DefaultSettings`
   * `Config.PreInstalledApps`
   * `Config.Apps`
   * `Config.AppCategories`
2.  Ensure arrays have at least one value:

    ```lua
    -- WRONG: Empty required table
    Config.DefaultWallpapers = {}

    -- CORRECT: At least one entry
    Config.DefaultWallpapers = {
        "https://cfx-nui-devhub_laptop/html/images/wallpapers/wallpaper_1.webp",
    }
    ```
3. Check that referenced apps in `Config.PreInstalledApps` exist in `Config.Apps`

### Invalid App Configuration

**Problem:** Apps not appearing or causing errors when opened.

**Solution:**

1. Verify each app has all required properties:
   * `label`
   * `img`
   * `path`
   * `category`
   * `rating`
   * `description`
   * `longDescription`
   * `author`
   * `size`
   * `downloads`
   * `class`
2.  Check that `path` matches the Vue component name:

    ```lua
    ['calculator'] = {
        path = "app_calculator",  -- Must match component
    }
    ```
3.  Ensure `category` exists in `Config.AppCategories`:

    ```lua
    -- If category is 'tools', it must be defined:
    Config.AppCategories = {
        ['tools'] = {
            label = "Tools",
            order = 2,
        },
    }
    ```
4. Verify `class` is either `'regular'` or `'premium'`

***

## <mark style="color:yellow;">App-Specific Issues</mark>

### Calculator Not Working

**Problem:** Calculator buttons don't respond or calculations fail.

**Solution:**

1. Check browser console for JavaScript errors
2. Verify calculator component is properly loaded
3. Test with simple operations first (2 + 2)
4. Ensure no invalid characters in expression

### Notepad Cannot Save Notes

**Problem:** Notes don't save or load properly.

**Solution:**

1. Check database connection
2. Verify notepad table exists in database
3. Check server console for SQL errors during save
4. Ensure player identifier is correctly retrieved
5.  Test by checking database manually:

    ```sql
    SELECT * FROM devhub_laptop_notes WHERE player_id = 'identifier';
    ```

### Browser Shows Error Page

**Problem:** Browser displays "Page Not Available" error.

**Solution:**

1. Check if the URL is valid and accessible
2. Verify the website allows iframe embedding:
   * Some sites block iframe display with X-Frame-Options
   * This is a browser security feature, not a script issue
3. Try different websites to isolate the problem
4.  Check browser quick links configuration:

    ```lua
    Config.BrowserQuickLinks = {
        {title = "Google", url = "https://www.google.com/search?igu=1", icon = "fab fa-google"},
    }
    ```
5. Use URLs that support iframe embedding

### Clock Shows Wrong Time

**Problem:** Clock displays incorrect time or timezone.

**Solution:**

1. Verify system time on server is correct
2.  Check timezone configuration in `Config.WorldClocks`:

    ```lua
    Config.WorldClocks = {
        {name = "New York (EST)", timezone = "America/New_York"},
    }
    ```
3. Ensure timezone strings are valid IANA timezone identifiers
4. Test with known working timezones like `"UTC"` or `"America/New_York"`

### CMD Commands Not Working

**Problem:** CMD doesn't respond to commands or shows errors.

**Solution:**

1. Verify command exists in CMD component
2. Available default commands:
   * `help`
   * `clear`
   * `whoami`
   * `date`
3. Check translation strings for CMD in `Config.Lang`
4. Ensure command syntax is correct (case-sensitive)

***

## <mark style="color:yellow;">Premium App Issues</mark>

### Crime Traders Not Accessible

**Problem:** Crime Traders shows "Premium Content" message.

**Solution:**

1. This is expected behavior for premium apps
2. Server must have premium access to enable this app
3. Contact script developer to verify premium status
4. Check if `class = 'premium'` is set in app configuration
5. Premium apps require special licensing

### Crime Traders Data Not Loading

**Problem:** App opens but shows no traders or tasks.

**Solution:**

1. Verify `Config.CrimeTradersTraders` table is properly configured
2.  Check that traders have valid `shopItems` defined:

    ```lua
    Config.CrimeTradersTraders = { 
        ['trader_1'] = {
            name = 'Marcus',
            image = './images/avatars/trader_1.webp',
            order = 1,
            shopItems = {
                ['1'] = {
                    {name = 'weapon_pistol', price = 150, amount = 1},
                },
            }
        },
    }
    ```
3. Ensure database tables for Crime Traders exist
4. Check server console for errors when opening app

### XP or Level Not Updating

**Problem:** Players complete tasks but don't gain XP or level up.

**Solution:**

1. Check `Config.XpRequirements` table is properly configured
2.  Verify XP values are progressive:

    ```lua
    Config.XpRequirements = {
        [1] = 0,
        [2] = 100,
        [3] = 250,
    }
    ```
3.  Check database to see if XP is being saved:

    ```sql
    SELECT * FROM devhub_laptop_crimetraders WHERE player_id = 'identifier';
    ```
4. Look for server-side errors during XP reward calculation

### Cannot Purchase Items

**Problem:** Purchase button doesn't work or shows errors.

**Solution:**

1. Verify player has enough Crime Points (CP)
2. Check that player meets level requirement for item
3.  Ensure item configuration is valid:

    ```lua
    {
        name = 'weapon_pistol',  -- Valid item or 'money'
        price = 150,              -- Must be positive number
        amount = 1                -- Must be positive number
    }
    ```
4. Check server console for errors during purchase
5. Verify item giving function works in your framework

***

## <mark style="color:yellow;">Performance Issues</mark>

### Laptop Lags or Stutters

**Problem:** UI is slow or unresponsive, frame drops when using laptop.

**Solution:**

1. Check if too many apps are running simultaneously
2. Reduce number of gallery images for apps
3. Optimize image sizes:
   * Use WebP format instead of PNG
   * Compress large images
   * Keep images under 500KB each
4.  Disable debug mode in production:

    ```lua
    Config.Debug = false
    ```
5. Close other resource-heavy scripts while testing

### High Memory Usage

**Problem:** Resource uses excessive memory.

**Solution:**

1. Check for memory leaks in custom modifications
2. Ensure apps properly clean up when closed
3. Limit number of cached images
4.  Monitor memory usage in F8 console:

    ```
    resmon
    ```
5. Restart resource periodically if needed

### Slow Database Queries

**Problem:** Lag when saving/loading data.

**Solution:**

1.  Add indexes to frequently queried columns:

    ```sql
    CREATE INDEX idx_player_id ON devhub_laptop_notes(player_id);
    ```
2. Optimize database queries in custom code
3. Consider using connection pooling
4. Clean up old or unused data periodically

***

## <mark style="color:yellow;">User Experience Issues</mark>

### Face ID Not Working

**Problem:** Face ID authentication fails or doesn't trigger.

**Solution:**

1. Ensure Face ID was enabled during setup
2. Check that player character model hasn't changed drastically
3. Verify Face ID callback functions are working
4. Test password login as fallback
5. Player can disable and re-enable Face ID in settings

### Apps Not Installing

**Problem:** Download button doesn't work or app doesn't appear on desktop.

**Solution:**

1. Check if app is already installed
2. Verify app configuration is valid in `Config.Apps`
3. Check browser console for errors during installation
4. Ensure database is saving installed apps list
5. Try restarting laptop to refresh app list

### Apps Not Uninstalling

**Problem:** Uninstall button doesn't work or app remains on desktop.

**Solution:**

1.  Check if app has `dontAllowUninstall = true`:

    ```lua
    ['appStore'] = {
        dontAllowUninstall = true,  -- Cannot be uninstalled
    }
    ```
2. System apps typically cannot be uninstalled
3. Verify database is updating installed apps list
4. Check for errors in server console during uninstall

### Settings Not Saving

**Problem:** Changes to settings don't persist after logout.

**Solution:**

1. Check database connection
2. Verify settings save callback is working
3. Check server console for SQL errors
4.  Test by manually checking database:

    ```sql
    SELECT * FROM devhub_laptop_settings WHERE player_id = 'identifier';
    ```
5. Ensure no errors when closing settings panel

### Notifications Not Showing

**Problem:** System notifications don't appear.

**Solution:**

1. Check if notifications are enabled in settings
2. Verify notification component is loaded
3. Check browser console for JavaScript errors
4. Test with simple notification:
   * Try error messages that should trigger notifications
   * Verify notification sound plays (if enabled)
5. Ensure notification translations exist in `Config.Lang`

***

## <mark style="color:yellow;">Development Issues</mark>

### Configuration Not Taking Effect

**Problem:** Changes to config files don't appear in-game.

**Solution:**

1. Ensure you saved the config file after editing
2.  Restart the resource:

    ```
    restart devhub_laptop
    ```
3. If still not working, restart the entire server
4. Check server console for Lua syntax errors
5. Verify you edited the correct config file in `configs/` folder

### Cannot Modify UI or Scripts

**Problem:** Want to change UI appearance or add custom functionality.

**Solution:**

1. **UI Changes**: Not possible - the `html/` folder is protected
2. **Script Changes**: Not possible - the `escrowed/` folder is protected
3. **Available Customization**: Limited to `configs/` folder only:
   * App configuration
   * Translation strings
   * Settings and defaults
   * Crime Traders configuration
4. Contact script developer for:
   * Custom feature requests
   * UI modifications
   * Additional functionality
   * Source code access (if available)

***

## <mark style="color:yellow;">Compatibility Issues</mark>

### Framework Compatibility

**Problem:** Script not working with specific framework.

**Solution:**

1. This script is designed for ESX framework
2. Framework integration is handled by protected escrowed files
3. Ensure you're using a compatible ESX version
4. Verify your framework resource name matches expected values
5. Contact developer for:
   * QBCore conversion (if available)
   * Framework-specific support
   * Compatibility with custom frameworks

### Conflict with Other Resources

**Problem:** Other resources interfere with laptop functionality.

**Solution:**

1. Identify conflicting resources:
   * Check for resources that use same key bindings
   * Look for resources that steal NUI focus
   * Identify resources that modify same database tables
2. Test by disabling other resources one by one
3. Adjust resource start order in `server.cfg`
4. Use unique key bindings to avoid conflicts

### Outdated Client Version

**Problem:** Features not working on older FiveM versions.

**Solution:**

1. Update FiveM to latest version
2. Check minimum required FiveM version
3. Ensure server artifacts are up to date
4. Verify client and server versions match

***

## <mark style="color:yellow;">Advanced Troubleshooting</mark>

### Enable Debug Mode

To get detailed error information:

1.  Enable debug mode in config:

    ```lua
    Config.Debug = true
    ```
2. Check server console for debug messages
3. Open browser console (F12) for NUI errors
4. Monitor network tab for failed requests

### Check Resource Order

Ensure proper resource start order in `server.cfg`:

```lua
ensure devhub_lib              # Required dependency
ensure es_extended             # Framework
ensure devhub_laptop           # This resource
```

### Clear Cache

If experiencing persistent issues:

1. Clear FiveM cache:
   * Close FiveM
   * Delete cache folder in FiveM application data
   * Restart FiveM
2. Clear browser cache:
   * Press Ctrl + F5 when laptop is open
   * Or use F12 > Network > Disable cache
3. Restart server and resource

### Database Verification

Check database integrity:

```sql
-- Verify tables exist
SHOW TABLES LIKE 'devhub_laptop%';

-- Check for corrupt data
SELECT * FROM devhub_laptop_users WHERE data IS NULL;

-- Verify relationships
SELECT COUNT(*) FROM devhub_laptop_notes;
```

### Log Analysis

Examine logs for patterns:

1. Server console logs
2. FiveM client logs
3. Browser console errors
4. Network request failures

Look for recurring errors or warnings that indicate the root cause.

***

## <mark style="color:yellow;">Getting Help</mark>

### Before Requesting Support

1. Check this troubleshooting guide thoroughly
2. Enable debug mode in `configs/sh.config.lua` and collect error messages
3. Test with minimal other resources running
4. Verify all configuration files in `configs/` folder are correct
5. Check database tables exist and have data
6. Try on a clean server install
7. Confirm you haven't modified any files outside the `configs/` folder

### Information to Provide

When requesting support, include:

1. FiveM server version
2. Framework name and version
3. Full error messages from console
4. Browser console errors (F12)
5. Configuration files (if modified)
6. Steps to reproduce the issue
7. What you've already tried

### Support Channels

Visit the documentation at: https://docs.devhub.gg/

Contact DevHub support through their official channels for:

* Premium app issues
* Licensing questions
* Feature requests
* Bug reports

***

**Remember**: Most issues are caused by configuration errors or missing dependencies. Always verify your setup matches the requirements before assuming a script bug.
