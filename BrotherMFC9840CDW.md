# Introduction #

Setup and Configuration of the Brother MFC 9840 CDW.


# Details #

## Ubuntu Setup ##
  1. Open Synaptic Package Manager
  1. Search for 9840. You should see two packages:
```
brother-cups-wrapper-ac
brother-lpr-driver-ac
```
  1. Select those for installation (along with their required packages).
  1. Go to System->Administration->Printing and press the “New Printer” button.
  1. After a “Search for new printers” message comes up and goes away, expand “Network Printers”.
  1. If you’re lucky like me, you’ll see your printer there. I chose to use the one that was found by IP address (LPD Network Printer via DNS-SD).
  1. Finally, I did System->Preferences->Default Printer to set the new printer as the default.