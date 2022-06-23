To reimage a new Mac:

1. Boot the Mac into recovery mode. (With newer Macs, this is done by holding the power button for a VERY long time, then clicking on "Options". Older Macs required holding Command-R) 
2. Open the terminal, and run the following commands:
```
hdiutil attach http://macbootstrap.rit.edu
/Volumes/init/install
```

To reimage an old Mac:
1. Boot into recovery mode.
2. Open the terminal, and run the following commands:
```
hdiutil mount http://macbootstrap.rit.edu/mds
/Volumes/mds/run
```
