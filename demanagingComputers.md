For computers that are no longer managed, there are a few things to do.

For Macs:
It is important to note that the Mac de-management process is different, depending on whether the user has previously used Bootcamp (or a similar program) on the device. The first 3 steps are always the same.
1. Retire the device in Apple School Manager.
2. Remove the device from MDM/Workspace One.
3. Remove the device from CLAWS.

For Macs that have not been Bootcamped...
4. Boot to recovery. 
5. Either use the included recovery software, or an external disk to reinstall MacOS.

For  Macs that have been Bootcamped...
4. Boot the Mac into a Linux drive.
5. Using a partition management tool, remove all partitions, and create one partition, with the size of the drive.
6. Power the Mac off.
7. Connect the Mac to be demanaged to another currently-functional and powered-on Mac, using a high-bandwidth cable such as a Thunderbolt cable. (This may require adapters on one or both ends). 
8. Holding the `T` key, power the Mac to be demanaged back on. 
9. The demanaged Mac should show as an uninitialized disk on the functioning Mac. Format the drive as APFS.
10. Power the demanaged Mac down, and unplug it from the functional Mac.
11. Turn the demanaged Mac on, and boot it to the MacOS install disk. With older Macs, this is done by holding `Option` on boot. On newer Macs, this is done by holding the power button until a prompt appears.
12. Reinstall MacOS following the prompts.

For Windows machines:
1. Remove the object from AD.
2. Remove the device from CLAWS.
3. Reinstall Windows, in the standard process.

If the Windows computer picks up its registry, or it has a sticker on it denoting a product key, then use that on install. Otherwise, the user is on their own for registration.

