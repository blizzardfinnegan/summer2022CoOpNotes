OU = Organizational Unit

MDM = Mobile Device Management (Apple classroom?)

Emails are through outlook, not Gmail

Main landing page is at `help.rit.edu/navpage.do`. There's a link there for accidental missed punch-ins

Slack is used for internal messaging

Generally log in with `bfdst`, the admin account should be used sparingly.

General job tasks:

- Image computers
  - turn on, mash F2 or Delete to get to BIOS
  - Note Service ID and MAC Address; make new computer in CLAWS
    - Service ID should be written in under "Tags" as "Serial:XXXXXXX"
    - Assign hostname according to convention (generally for desktops: `<building>-<room#>-<last 2 of fiscal year><iterative number>`)
    - new network device should be (for desktop devices) "Wired". Enter MAC Address, change IP drop-down to "Roamer". Change "Select Preset" to "SCCM - Rochester"; CLICK APPLY PRESET.
  - Change storage settings to be AHCI rather than RAID
  - reboot, mash F12 to open boot-order menu
  - boot to IPv4 network device
  - Hit enter on prompt
  - When prompted enter ||`letmein`|| as password
  - choose default option, hit enter
  - remote in to `clientmgmt`, create an object for the computer. Just name it the same as the hostname. Put the object in the right folder
  - wait until next day; check that all programs have installed properly in Software Center
  - Reboot machine
- Make sure that they have the correct permissions in Active Directory
  - Active Directory and SCCM are managed through RDP to `clientmgmt`
  - Software is installed locally with Software Center (Win10/11) or Managed Software Center (Mac)
- Check slack/email
- Remote assist staff, when necessary using Bomgar/BeyondTrust
- Generally, be an IT person
