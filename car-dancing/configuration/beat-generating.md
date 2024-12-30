# Beat generating

## <mark style="color:yellow;">**1: Upload Music**</mark>

1. Upload your desired music in `.ogg` format to the `dh_cardance/html/song` folder.

***

## <mark style="color:yellow;">**2: Restart the Server**</mark>

2. Restart your server to apply changes.

***

## <mark style="color:yellow;">**3: Generate Beats**</mark>

3. Join the server.
4.  In the **server console**, enter the following command to generate beats for your music file:

    ```bash
    generate_beat file_name.ogg
    ```
5. Do not exit the server until you see the message **"Beat finished successfully"**.

***

## <mark style="color:yellow;">**4: Update Configuration**</mark>

6. Navigate to the `configs/shared.lua` file.
7.  Add your song to `Shared.Sounds` with the following format:

    ```lua
    { name = "SONG_DISPLAY_NAME", time = "SONG:DURATION", url = "file_name.ogg", difficulty = "easy" }, -- difficulty options: easy, medium, hard
    ```

***

## <mark style="color:yellow;">**5: Restart the Script**</mark>

8. Restart the script to apply the new configurations. Your Car Dancing script should now be fully functional.

***

## <mark style="color:yellow;">Example Configuration</mark>

Here is an example configuration entry for `shared.lua`:

```lua
Shared.Sounds = {
    { name = "Song Display Name", time = "3:45", url = "song_file.ogg", difficulty = "easy" },
    -- Add more songs here
}
```

By following these steps, you'll be able to enjoy the Car Dancing script with your favorite music tracks.
