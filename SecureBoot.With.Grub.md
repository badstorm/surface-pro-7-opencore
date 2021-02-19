# Secure Boot with Grub
If you want to remove the anoing red bar with the lock icon at boot, you can configure your EFI folder including Grub to load OpenCore. 
Here the steps to follow.

### Get Precompiled Grub
We need a version of Grub precompiled with the certificate used for sign the binary file. For this presuppose we use **Super UEFIinSecureBoot Disk**. Download the [last release](https://github.com/ValdikSS/Super-UEFIinSecureBoot-Disk/releases/download/3/Super-UEFIinSecureBoot-Disk_minimal_v3.zip).

### Extract to EFI Folder
Extract or mount the `.img` file downloaded before (you can use unzip software like *7zip*) and replace the folder `Boot` in your EFI folder with the one included in the `.img` and add the folder `grub` to your EFI folder.
**Remember to also add the file *ENROLL_THIS_KEY_IN_MOKMANAGER.cer* outside your EFI folder**

### Rename Files
Now you must rename the OpenCore `BOOTx64.efi` file present in your `EFI/BOOT` folder in `grubx64_real.efi` replacing the version present in the `.img` file.

### Add the Key and Boot
At this point you can reboot and enable `Secure Boot`. You now get a blue screen with the *Access Denied* error. Is correct. Now follow this instructions (and the illustrated version):

 1. At the error page press OK
 2. Press any key to perform MOK management
 3. Select `Enroll key from disk`
 4. Select `Continue`
 5. Select the disk where you put the `.cer` file
 6. Select `Yes` and then `Reboot`

![Illustrated Steps](https://camo.githubusercontent.com/47a5bd8e778cb6668e612cbd7299ed715af5a8cc27cd879b9cba0fa09b750ca1/68747470733a2f2f7777772e62756770726f6772616d6d65722e6d652f696d616765732f7365637572652d626f6f742d322e706e67)

After you follow this steps, you are now able to load OpenCore with Secure Boot enabled without any interactions.