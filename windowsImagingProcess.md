# Latitude and Optiplex Devices

1. Boot the device. Immediately after booting, go to the BIOS by pressing F2 repeatedly as soon as you presss the power button, until the screen turns on, and changes to an interface.
2. On the initial page, write down the Service Tag or Serial number of the device. Scroll down to find the Ethernet MAC address (often labeled "LOM MAC Address"). These are used in later steps. 
3. Move to the `Storage` tab, and change the `SATA/NVMe` setting to the `AHCI` option (on most Dell devices, it defaults to `RAID On`). 
4. Move to the `Boot Configuration` tab, and turn off SecureBoot.
5. On another RIT-managed Windows device, open Remote Desktop Connection (searchable from the Start menu) and connect to `clientmgmt`. This will require you to enter the admin password, which is found in Bitwarden. Once connection is established, the remote computer will then request a 2FA option. Click the "Call Me" option, and press `1` on the keypad once the call comes through.
6. Now that you have logged in, double-click the icon on the desktop labeled `ADUC+GPMC`. Navigate through the folder structure to the location of where the computer will be assigned. All computers will start in `main.ad.rit.edu`, in the `RITOU` folder. As an example, Color Science is a part of the College of Science, so to get to Color Science, first enter the `COS` folder, then the `Color Science` folder. This will show you the naming convention of the location.
7. Leave the remote session, and open a browser. Navigate to `claws.rit.edu` and log in with the standard employer account (look in Bitwarden, search for username `bfdst`). 
8. Once in CLAWS, click on the `Computers` tab off to the left side, and type in the general format of the computer you are setting up. In the case of a Color Science laptop being added in June 2022, your search query would be `cos-color22%`. The percent sign is important, as it will show all objects in CLAWS with that format. 
9. Skim this search, and find the highest numbered example (in the above example, it is `COS-COLOR2206`). Now, create a new computer using the button off to the left side in the `Computers` tab. Fill the information out as shown below:
		- label: Your formatted hostname, incremented 1 higher than the biggest option. (i.e. `COS-COLOR2207`)
		- User role: The main user, if it exists. If not, fill in with `cos-netadmins`.
		- Owner and Group roles: Change the dropdown to `Group`, then enter `cos-netadmins` in the text box.
		- Tag: There should be 1 tag, formatted as `Serial:XXXXXX`. This is the previously mentioned Service Tag/Serial Number.
		- Notes: Write down the model number here
		- OSs: This should be `Windows 10`.
		- Hostname: should be identical to label.
		- Networking:
			1. Create a new network device on the page. 
			2. Enter the saved MAC address in the MAC address.
			3. Change the dropdown next to the MAC address field to say `Roamer`.
			4. Change the `Preset` dropdown to `SCCM - Rochester (UEFI only)`
			5. CLICK APPLY.
10. Once all this is done, go back to the remote session, and create a new object in `ADUC+GPMC` in the correct directory, with the same name as the hostname of the new computer. Then, click `Next`/`Finish` until the new object is created.
11. Reboot the new device, this time pressing F12 repeatedly until it allows you to select boot options. Choose the `Integrated NIC (IPv4)` option. Watch the device, and when it prompts you to press enter, do so. The device will start downloading an image to boot from.
12. Once the downloaded image is loaded, enter `letmein` in the password field. Click next until the imaging process starts. This will take a while (an hour is reasonable). During this process, the device cannot lose power, or Ethernet connection. You can tell that the device is done when a message shows up in Slack in the `#sccm-ts-alerts` channel. 
13. Once the image is complete, log in once to ensure that it was set up properly. Then, leave the device powered on and plugged in overnight. It is recommended, but not required, that you log out of the device first. This will run any necessary updates in the background overnight.

# All Other Devices

Steps 1-10 listed above should be followed. Afterwards:

1. Install Windows 10 Enterprise on the computer. Do not install with a Windows key, as binding to the network will provide it with a key. The computer will reboot from the Windows 10 installer to its first boot procedure. Ensure that the computer is not connected to the network via ethernet, then, when prompted for internet access, tell it you do not have internet access (blue text most likely in the bottom left corner of the screen). Confirm you would like to install with "limited" setup, and install using a temporary local account. Specific details of this account are not important, as it won't last long on the device.
2. Once you are logged in, open Settings, navigate to System, then the section labeled "About". On the right side of the window should be a list of hyperlinks, including one labeled "Rename this PC (advanced)". This will open a "System Properties" window, click on the button with the label "To rename this computer or change its domain or workgroup, click Change." Go through the prompts, using your admin account, the computer's hostname, and `MAIN.AD.RIT.EDU` for the domain. Reboot the computer.
3. Log in with your admin account. Open File Explorer, click on the address bar, and type in `\\main.ad.rit.edu\shares\FA\ITS_SCCMClient\latest` and run the `ccmsetup` application. This will install Software Center, and will take some time. Note that this runs in the background, and can only be observed through Task Manager. Once this is complete, reboot again.
4. Log back in with your admin account, and open Software Center from the Start menu. If you do not get an orange banner at the top of the window, or you get prompted for a Windows or Microsoft account, close the application and run `C:\Windows\CCM\ccmrepair.exe` from an admin command prompt. Once all of this is complete, log out, and log in with your standard account. If this works properly, the setup process is complete, and you can transition the user to their device.

# Troubleshooting

If a computer that has previously been imaged is now not imaging properly, there could be a conflicting SCCM object. Delete this object, then try again to re-image.
