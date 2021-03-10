# OA3-Activiation
Being that I have had to spend a lot of time dealing with OA3, and will forget it, I thought I would put some key things here.

At the simpliest level Online Activation for Windows stores a key in the UEFI of the system. This means that you can re-image your machine or do work without loosing a product key.  You can always download windows versions from https://www.microsoft.com/en-au/software-download/windows10 and then re-install your system with that.  They key is liensing.  Here is a quick PowerShell script that will activate using OA3.  

Before you re-image, you may want to check if it has OA3.  This is usually a sticker on the bottom of the system. Or you can run the following command to determine it

Run from elevated PowerShell
<code>Get-WmiObject -Class softwarelicensingservice -Property OA3xOriginalProductKey</code>

If that returns a value you are set. After you install Windows run the following command
<code>Get-WmiObject -Class softwarelicensingservice -Property OA3xOriginalProductKey | foreach-object {cscript.exe slmgr.vbs /ipk $_.OA3xOriginalProductKey}</code> and you will be running the correct version of Windowa. 
