# Deploying-pfsensse-firewall-in-a-virtual-machine-
Deploying pfsensse firewall in a virtual machine 
Prerequisites

Before you begin, ensure you have the following:

    A computer with sufficient resources (CPU, RAM, and disk space). Recommeded vm 2gig ram 20G space 1 vcpu
    VirtualBox installed on your machine.
    pfSense ISO image downloaded from the official website.

Steps
1. Create a New Virtual Machine

    Open VirtualBox and click on New.
    Enter the name for your VM (e.g., pfSense).
    Set the type to BSD and the version to FreeBSD (64-bit).
   ![image](https://github.com/user-attachments/assets/d8bfbac7-9820-4392-ac98-262b6b4a4df7)

    Click Next.

3. Allocate Memory

    Allocate at least 1 GB of RAM for pfSense. More RAM may be required depending on your use case.
    Click Next.

4. Create a Virtual Hard Disk

    Select Create a virtual hard disk now and click Create.
    Choose VDI (VirtualBox Disk Image) and click Next.
    Select Dynamically allocated and click Next.
    Set the disk size to at least 10 GB. Click Create.

5. Configure Network Interfaces
    Select your new VM and click on Settings.
    Go to the Network section.
    Adapter 1: Enable and attach it to NAT.
    Adapter 2: Enable and attach it to Host-only Adapter or Bridged Adapter, depending on your network setup. I used internall netwwork
    Click OK.
   
![image](https://github.com/user-attachments/assets/3bea2d31-af30-467e-9d93-13e8e80c60e6)

7. Attach the pfSense ISO

    In the Settings window, go to the Storage section.
    Under Controller: IDE, click the empty CD/DVD drive.
    Click the disk icon and choose Choose a disk file.
    Select the downloaded pfSense ISO image and click Open.
    Click OK.

8. Start the Virtual Machine
9. Select the pfSense VM and click Start.
![Screenshot from 2024-06-16 10-02-03](https://github.com/user-attachments/assets/16644ee1-a99f-482d-ae79-e45fe1159e9d)


   #The VM will boot from the pfSense ISO image.
    Follow the installation prompts:
        Select the default keymap.
        Choose Install pfSense and proceed with the default options.
        When prompted, select Auto (UFS) for the partitioning method.
    The installation will proceed and complete. Once done, the VM will reboot.

10. Initial Configuration

    After reboot, pfSense will initialize and ask for initial configuration.
    Assign interfaces:
        Typically, em0 (or equivalent) will be WAN.
        em1 (or equivalent) will be LAN.
    Follow the prompts to configure the WAN interface (usually set to DHCP) and LAN interface (typically a static IP, e.g., 192.168.1.1/24).

11. Access the Web Interface

    Open a web browser on your host machine.
    Navigate to the LAN IP address assigned to the pfSense VM (e.g., https://192.168.1.1).
    You may need to bypass a security warning if using a self-signed certificate.
    Log in using the default credentials:
        Username: admin
        Password: pfsense
    Follow the initial setup wizard to complete the configuration.

Conclusion

You have successfully installed pfSense on VirtualBox. You can now start configuring your firewall, routing, and other network services as needed.
