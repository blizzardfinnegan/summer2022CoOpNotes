Windows
---
Consult in case of a bad SCCM install.

First, check "client actions". Go to control panel, open `Configuration Manager`, and go to the `Actions` tab. Click `Run Now` on each of the listed acions and wait 20-30 minutes.

If there are only 2 or 3 client action options, open Command Prompt and run `C:\Windows\CCM\ccmrepair.exe`. 

Another thing to try is `Configuration Manager Health Check`. This can be found in `Task Scheduler`. Go to the left panel of `Task Scheduler`, open the `Task Scheduler Library` folder, in the `Microsoft` folder, click on `Configuration Manager`. Then right-click on `Configuration Manager Health Evaluation`, and click run.

Mac
---
All programs are installed through Managed Software Center. If an install breaks, check the logs. They are stored at `/Library/Managed Installs/Logs/ManagedSoftwareUpdate.log`

As a nuclear option, log in as admin, then run the following commands:
```
sudo launchctl unload /Library/LaunchDaemons/com.googlecode.munki.*
sudo rm -rf "/Applications/Utilities/Managed Software Update.app" 
sudo rm -rf "/Applications/Managed Software Center.app"  
sudo rm -f /Library/LaunchDaemons/com.googlecode.munki.*
sudo rm -f /Library/LaunchAgents/com.googlecode.munki.*
sudo rm -rf "/Library/Managed Installs"
sudo rm -f  /usr/local/munki
sudo rm -f /etc/paths.d/munki
sudo pkgutil --forget com.googlecode.munki.admin
sudo pkgutil --forget com.googlecode.munki.app
sudo pkgutil --forget com.googlecode.munki.core
sudo pkgutil --forget com.googlecode.munki.launchd
sudo pkgutil --forget com.googlecode.munki.appusage
sudo shutdown now
```
Note that Macs do not allow the use of `su`, but you can run all of the `rm` commands as one call.

Once the Mac has turned off, reboot into recovery mode (press and hold the power button until the prompt shows up. If no prompt shows up, press and hold the power button to turn the Mac off, then press the power button while holding `command-R`.). Once in recovery mode, go to the top bar, and find the Terminal button. From there, run the following.

```
hdiutil attach http://macbootstrap.rit.edu
/Volumes/init/install
reboot
```
Note that the middle line in the above codeblock appears as though it is a failed command run. However, this is the command working properly.

