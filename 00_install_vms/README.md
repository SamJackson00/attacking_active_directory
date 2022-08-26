# 00 - Install VMs


1. Install Windows Server 2022 as a Virtual Machine in VMWare Workstation

2. Install Windows 11 as a Virtual Machine in VMWare Workstation
    - May need TPM workaround
    - Shift + F10 in Windows setup to bring up command prompt
    - run regedit
    - Create a new key in HKEY_LCCAL_MACHINE\SYSTEM\Setup called 'LabConfig'
    - Create new DWORDs called 'ByPassTPMCheck', 'BypassSecureBoot' and 'BypassRAMCheck' and set their values to 1
    - Close regedit and command prompt and continue with installation

3. Download upates on both Server and Win11

4. Shutdown both machines, create a snapshot, turn on template mode (VM settings > advanced > enable template mode)

5. Sort templates into folders

6. Clone both machines as needed