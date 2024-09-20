# Beat generating

**Step 1: Upload Music**

1. Upload your desired music in `.ogg` format to the `dh_cardance/html/song` folder.

**Step 2: Restart the Server**

2. Restart your server to apply changes.

**Step 3: Generate Beats**

3. Join the server.
4.  In the **server console**, enter the following command to generate beats for your music file:

    ```bash
    generate_beat file_name.ogg
    ```
5. Do not exit the server until you see the message **"Beat finished successfully"**.

**Step 4: Update Configuration**

6. Navigate to the `configs/shared.lua` file.
7.  Add your song to `Shared.Sounds` with the following format:

    ```lua
    { name = "SONG_DISPLAY_NAME", time = "SONG:DURATION", url = "file_name.ogg", difficulty = "easy" }, -- difficulty options: easy, medium, hard
    ```

**Step 5: Restart the Script**

8. Restart the script to apply the new configurations. Your Car Dancing script should now be fully functional.

#### Example Configuration

Here is an example configuration entry for `shared.lua`:

```lua
Shared.Sounds = {
    { name = "Song Display Name", time = "3:45", url = "song_file.ogg", difficulty = "easy" },
    -- Add more songs here
}
```

By following these steps, you'll be able to enjoy the Car Dancing script with your favorite music tracks.
