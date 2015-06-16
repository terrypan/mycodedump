A one-time import of contact data to the contact app on the emulator is easy. It's just a matter of importing a vcf file. Gmail, for example let's you export your contacts to a vcf file:
  1. Go to your gmail account using a web browser, click 'contacts' on the left sidebar.
  1. Select all the contacts you want on your phone, and choose to export them in vCard format.
  1. This will download a **.vcf file to your computer containing the contacts.**

Push the vcf file to the SD card on your emulator (adb can be found at `<sdk>`/platform-tools):
```
 adb push contacts.vcf /sdcard/contacts.vcf
 adb sync
```

Then open the contacts app on the emulator, and hit menu, import. Choose to import from SD card, and the vCard file will be found and your contacts imported

([Source](http://stackoverflow.com/questions/1114052))