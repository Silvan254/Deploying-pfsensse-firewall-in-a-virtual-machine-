# Deploying-pfsensse-firewall-in-a-virtual-machine-
Deploying pfsensse firewall in a virtual machine 
Prerequisites

Before you begin, ensure you have the following:

    A computer with sufficient resources (CPU, RAM, and disk space). Recommeded vm 2gig ram 20G space 1 vcpu
    VirtualBox installed on your machine.
    pfSense ISO image downloaded from the official website.

Steps
1. Create a New Virtual Machine:
    Open VirtualBox and click on New.
    Enter the name for your VM (e.g., pfSense).
    Set the type to BSD and the version to FreeBSD (64-bit).
    
   
   ![image](https://github.com/user-attachments/assets/45e67bcd-fc2f-45f9-8822-f7d253ef1485)

    Click Next.

3. Allocate Memory

    Allocate at least 1 GB of RAM for pfSense. More RAM may be required depending on your use case.
    Click Next.
   ![image](https://github.com/user-attachments/assets/a63ea7d7-8d2b-43b8-b34f-b495d561326e)


5. Create a Virtual Hard Disk:

    Select Create a virtual hard disk now and click Create.
    Choose VDI (VirtualBox Disk Image) and click Next.

   ![image](https://github.com/user-attachments/assets/0a307e32-dab3-4197-8694-9173edb06d0f)

    Select Dynamically allocated and click Next.
    Set the disk size to at least 10 GB. Click Create.

7. Configure Network Interfaces
    Select your new VM and click on Settings.
    Go to the Network section.
    Adapter 1: Enable and attach it to NAT.
    Adapter 2: Enable and attach it to Host-only Adapter or Bridged Adapter, depending on your network setup. I used internall netwwork
    Click OK.
   
![image](https://github.com/user-attachments/assets/3bea2d31-af30-467e-9d93-13e8e80c60e6)

7. Attach the pfSense ISO:
      In the Settings window, go to the Storage section.
      Under Controller: IDE, click the empty CD/DVD drive.
      Click the disk icon and choose Choose a disk file.
      Select the downloaded pfSense ISO image and click Open.
   Click OK.

9. Start the Virtual Machine
10. Select the pfSense VM and click Start.
![Screenshot from 2024-06-16 10-02-03](https://github.com/user-attachments/assets/16644ee1-a99f-482d-ae79-e45fe1159e9d)


   #The VM will boot from the pfSense ISO image.
    Follow the installation prompts:
    
 Select the default keymap.
        ![Screenshot from 2024-06-16 10-03-08](https://github.com/user-attachments/assets/284d9301-7b12-4bac-8259-0c48ffb52c92)

 Choose Install pfSense and proceed with the default options.
 ![Screenshot from 2024-06-16 10-13-50](https://github.com/user-attachments/assets/294fd417-26c7-4bcb-8517-6bbba058435e)
![Screenshot from 2024-06-16 10-15-35](https://github.com/user-attachments/assets/5254441f-6e99-4062-9341-96979702c789)
![Screenshot from 2024-06-16 10-16-12](https://github.com/user-attachments/assets/9a22c9c0-79a0-47ee-b09c-ed926da9ddec)
![Screenshot from 2024-06-16 10-16-51](https://github.com/user-attachments/assets/418f415d-d5bb-4cd7-8dc0-70c1d7b45e7c)
![Screenshot from 2024-06-16 10-17-07](https://github.com/user-attachments/assets/6afdbfb0-f1c4-41fc-97ef-8bc3288a0f17)

When prompted, select Auto (UFS) for the partitioning method.
![Screenshot from 2024-06-16 10-18-54](https://github.com/user-attachments/assets/867e520d-25fc-462a-8640-ffad7f795149)

![Screenshot from 2024-06-16 10-19-36](https://github.com/user-attachments/assets/92d80f0a-8570-4bd8-a1b7-9d1661311f21)

The installation will proceed and complete. Once done, the VM will reboot.


11. Initial Configuration

    After reboot, pfSense will initialize and ask for initial configuration.
    ![image](https://github.com/user-attachments/assets/b5ab3b9e-8d43-4385-9a8d-12b6a1bdb191)

    Assign interfaces:
        Typically, em0 (or equivalent) will be WAN.
        em1 (or equivalent) will be LAN.
    Follow the prompts to configure the WAN interface (usually set to DHCP) and LAN interface (typically a static IP, e.g., 192.168.1.1/24).

13. Access the Web Interface

    Open a web browser on your any of your vm or host machine:
    I will make sure my LInux mint is connecte to internal network i.e Lan interface of my firewall
    Start my Linux mint vm to access firewall UI through ip 192.168.1.1
    ![image](https://github.com/user-attachments/assets/3d980966-7b9a-4d00-a03c-a4a284e566fc)

    Navigate to the LAN IP address assigned to the pfSense VM (e.g., https://192.168.1.1).
    You may need to bypass a security warning if using a self-signed certificate.
    Log in using the default credentials:
        Username: admin
        Password: pfsense
    Follow the initial setup wizard to complete the configuration.

Conclusion

You have successfully installed pfSense on VirtualBox. You can now start configuring your firewall, routing, and other network services as needed.
