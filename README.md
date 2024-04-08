-----------------
# Windows 7 on x570 and x670 
- All of the required tools are here to get Windows 7 Patched fully and have Updates resume working and have full working IO, etc.
-------------------------------------

Download Link
- Windows 7 Ultimate x64 .WIM : https://mega.nz/file/ZSJBDTQA#l2blkZk5j9g_DpBsH8sBTtFCYdewlTIbDxZ8ivAstQ8
  

------------------------------
How To Set Up And Install
------------------------------
                                ///////Stupid Write Up By SuperSystem32--8-Bit-Canadian\\\\\\\




/// Stage 1 // Game Planning ///              
Prepare a Windows 7 x64 SP1 USB drive, As well Prepare a Hiren Boot CD USB Drive.


Two Options; 

OPTION 1: you have x470 or lower chipset and you can just use Gigabyte Windows 7 USB Utility for 
your .ISO file and you're golden.

OPTION 2 [The FUN WAY]: Time to break out the PS2 peripherals!, and i hope you're familliar with
PCI Subsystem layout ID's! 

Once we are into the OS we need to do a few things, first thing we need to do is install chipset
drivers, and a few other utilities to make sure we have fully functioning SATA, USB, and all other
IO because we want to only have to do all this setup once.

Once all of your drivers and other essential programs you will need are installed, head to 
C:/windows/system32/sysprep/sysprep.exe and select the tick box [ENTER OOBE/ GENERATE] and in the drop down menu select 
"shut down," now hit start and wait.




/// Stage 1 1/2 // The WHY ///

*Here i'm going to explain why we have to take two different routes. With the x570 BIOS, [Not the Chipset]
The USB Host controller Is a child/parent relation with the CPU itself (for simplicity terms i don't wanna
bore you to death) same goes for the new x670 motherboards as well.
Prior to this the USB host controller was present in the motherboard and controlled independently by the 
BIOS until handed over to the kernel so the OS can do it's thing, now yes this does make USB faster the new 
way. Alas it makes things much harder when we are doing low level patch work to make things work.*

/// Stage 2 // Game Time - Let's Try It ///

- Boot into HirenBootCD from BIOS , once loaded launch CMD. 

*Command Line Time*

- cd c:\
- dism /capture-image /Imagefile:"X:\install.wim" /CaptureDir:C:\ /Name:NaMeDFiLe /compress:max            *** X  = YOUR TARGET DRIVE ***

Now WAIT patiently for your file to finish. Once complete, re boot your system back into Windows.

/// Stage 3 // Put it all together ///

- Format either a new drive or a blank partition, set drive/partition as active and convert to MBR.

Download WindowsNTSetup; https://mega.nz/file/4KQ2QbzK#EewmMv1XDAGYG3e5fNGYcrJ76nSuC3SSaaC1kOhTeZE

  - Launch WindowsNTSetup; select location of boot drive, you should see a highlighted green box
 on the drive we configured a moment ago. next, at the top right there is a windows logo in grey
 click that and go down to "bootice."

 - Under "Physical disk" tab, find your drive once again and then select process MBR, you wanna 
 select the option "Windows NT 5/6 MBR" and then install config, and close.
 
 - Next, select "Process PBR" and again , look for the option "BOOTMGR boot record" select that
 and then select "install config" and close.

 - Now that we have done the hard part first, head back up to the top and find the WIM file we 
 made earlier and select that, and for the bottom option Select the location of the Install Drive
 it's going to be the same as the boot drive.

*Now click start and watch the magic happen!* 
