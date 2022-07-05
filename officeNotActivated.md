Office on some machines fails to register that it has been activated. 

# Windows
First, remotely run Group Policy updates (`gpupdate /force` in the command prompt). If the issues persist, open Root command prompt, and run the following commands:
```
cd C:\Program Files (x86)\Microsoft Office\Office[tab complete]
cscript ospp.vbs /dstatus
cscript ospp.vbs /act
```

# MacOS
Run the following command:
```
pkgutil --forget com.microsoft.pkg.licensing.volume
```
Then, open Managed Software Center and check for updates.

If issue persists on either platform, reach out in Slack.
