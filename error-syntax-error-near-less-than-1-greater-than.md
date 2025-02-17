# ⁉️ Error: syntax error near '<\1>'

## <mark style="color:yellow;">Error: Syntax Error Near</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;">`<\1>`</mark>

### Causes:

{% stepper %}
{% step %}
**Corrupted File Transfer**

* Using **FileZilla** can break the script structure. Use **WinSCP** instead to avoid file corruption.
* If you used **Remote Desktop Control (RDC)** to drag and drop files **one by one**, the files may have been damaged. Instead, **upload a ZIP file** and extract it directly on the server.
{% endstep %}

{% step %}
**Outdated Server Version**

* Your server must be running **at least version 4752** or greater.
*   Check your version by running the following command in the server console:

    ```
    version
    ```
{% endstep %}

{% step %}
**Corrupted or Missing Files**

* f your download was incomplete or corrupted, perform a **clean reinstall** of the script.
* Ensure **all hidden files** (including `.fxap` files) are transferred properly. Some FTP clients may skip these files.
{% endstep %}
{% endstepper %}

***

### How to Fix:

{% stepper %}
{% step %}
#### **Update Your Server Artifacts**

* **Windows:** [FXServer Artifacts](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/)
* **Linux:** [Proot Linux Artifacts](https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/)

**Steps to update:**

* **Stop your server.**
* **Delete the `cache` and `old artifacts` .**
* **Extract the new artifacts:**
*   **Restart your server and verify the new version** by running:

    ```
    version
    ```
{% endstep %}

{% step %}
#### **Use Proper FTP Settings**

* **Switch to WinSCP** instead of FileZilla to prevent file corruption.
* If using FileZilla, enable **binary mode** before uploading.
* **Ensure all files (including hidden ones) are uploaded**, especially `.fxap` files in protected resources.
{% endstep %}

{% step %}
#### **Check for Anti-Cheat Interference**

* Some anti-cheat systems may block or modify scripts, leading to errors.
* If using an **anti-cheat**, disable it or remove **anticheat dump Lua files** and retry.
{% endstep %}

{% step %}
### Clear server cache

Delete the  server `cache`
{% endstep %}
{% endstepper %}
