Consult in case of a bad SCCM install.

First, check "client actions". Go to control panel, open `Configuration Manager`, and go to the `Actions` tab. Click `Run Now` on each of the listed acions and wait 20-30 minutes.

If there are only 2 or 3 client action options, open Command Prompt and run `C:\Windows\CCM\ccmrepair.exe`. 

Another thing to try is `Configuration Manager Health Check`. This can be found in `Task Scheduler`. Go to the left panel of `Task Scheduler`, open the `Task Scheduler Library` folder, in the `Microsoft` folder, click on `Configuration Manager`. Then right-click on `Configuration Manager Health Evaluation`, and click run.
