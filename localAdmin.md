This is the process for creating a local admin account for another user on an RIT-managed computer.

The first couple steps can be done either locally on the machine, or through a remote session in `clientmgmt`. 

For a local machine, you just need to go to the start menu, search for `Computer Management`, and open the first search result. 

For a machine that you can't directly access, open a remote session to `clientmgmt`, then follow the above steps to ge to `Computer Management`. Once there, right click on the first line in the left column of options (should say `Computer Management (Local)`). Then, click on the option `Connect to another computer...`. Finally, enter the hostname of the correct device. 

Once in the correct `Computer Management` instance, use the following steps:

1. Open the `Local Users and Groups` dropdown on the left panel.
2. Open the `Groups` folder. 
3. Right click on the `Administrators` option in the main portion of the window, and click on the `Properties` option.
4. In the bottom left of the new window, click on the `Add...` button.
5. In the new window's text box, input the username of the new admin account. Click the `Check Names` button to autofill the correct information, then click `OK`.
6. Click `Apply`, then close the dialog box, and close the `Computer Management` window. 
7. Restart the machine. This will apply the new group policy.
