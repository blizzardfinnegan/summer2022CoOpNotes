If anything throws Windows Update errors, check into Software Center. Use `ccmrepair.exe` to repair SCCM, if necessary. 

If the issue you're running into is not solved after running the above command, and rebooting, then do the following:

- In admin Command Prompt, run `sc stop wuauserv`. DO NOT CLOSE THIS WINDOW.
- Open Registry Editor.
- Traverse down the folder tree to `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate`
- Open `DisableWindowsUpdateAccess`, and set the value to `0`.
- In the `WindowsUpdate` folder on the left side, open the `AU` folder.
- Open `UsesWUServer`, and set the value to `0`. DO NOT CLOSE THIS WINDOW.
- Go back to the admin Command Prompt, and run `sc start wuauserv`.

Now, do whatever you need to do (install drivers, supplemental fonts, etc). 

Once that is done, stop `wuauserv` again, change the above values back to `1`, and start `wuauserv` again.
