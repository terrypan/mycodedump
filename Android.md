## Introduction ##

Not much to introduce here. This is a work in progress documentation of very specific things to know in the domain of Android development.


## Details ##

  * [Adding contact data on emulator](ContactsTestData.md)

## Hacks ##

### Exchange Active Sync -- Failed to create the account. Please try again later. ###

The universal fix for the "Failed to create the account please try again later" while adding exchange server on android roms is

  1. Add your account in Settings -> Accounts & Sync
  1. In the second last step, uncheck all three options (mail, contacts, calendar)
  1. Finish the configuration and your account should get created (here is where it would usually fail if you have not unchecked the options)
  1. Click on the created account and check back the three options (mail, contacts, calendar)