# Setting Up a Network Lab with GNS3

## Introduction

Networking labs, providing a sandbox for testing, learning, and refining skills. In this blog, we'll delve into the process of setting up a virtual network lab using GNS3 on a Windows PC. This comprehensive guide will walk you through the installation of GNS3 and its virtual machine (GNS3 VM) within VMware. Additionally, we'll explore the integration of an Ubuntu 22 Server, establishing a robust foundation for hands-on networking experimentation.

The key components of this setup include GNS3, a powerful network simulation tool, VMware for virtualization, and an Ubuntu Server for practical application testing. By following the outlined steps, you'll create a cohesive environment that bridges your Windows host, GNS3, and Ubuntu Server, fostering seamless interaction.

This introductory section sets the stage for an insightful journey into the intricacies of building a dynamic virtual network lab. As we progress through the subsequent sections, we'll cover each step in detail, providing clarity and guidance to empower you in constructing a robust and functional network testing environment. Whether you're a network enthusiast, a student, or a professional seeking hands-on experience, this blog aims to equip you with the knowledge to effectively set up and utilize a virtual network lab on your Windows PC.

## Prerequisites of Lab

Before embarking on the journey to set up your virtual network lab with GNS3 on Windows, it's crucial to ensure that you have all the necessary prerequisites in place. Here's a quick rundown of the essential components you'll need:

### Windows PC Minimum Requirements

Ensure that you have a Windows PC that meets the system requirements for running GNS3 and VMware smoothly. This includes adequate RAM, CPU, and disk space. See the [website](https://docs.gns3.com/docs/getting-started/installation/windows/#minimum-requirements)

### GNS3 and GNS3 VM Installed in VMware

Make sure you have successfully installed GNS3 and its virtual machine (GNS3 VM) within VMware. You can download GNS3 from the official [website](https://www.gns3.com/) and follow the installation [instructions](https://docs.gns3.com/docs/getting-started/installation/windows/#introduction). See this [video](https://www.youtube.com/watch?v=x9pGYyEqLYs) and this [video](https://www.youtube.com/watch?v=lFEDmM_lsxI) for installation.

### Ubuntu 22 Server Installed in VMware

Install Ubuntu 22 Server as a virtual machine in VMware. This server will be an integral part of your network lab. Ensure that the VM is configured with sufficient resources for optimal performance.

Now that you've confirmed the presence of these fundamental components, you're ready to proceed to the next steps.

## Starting the Lab Environment

With the prerequisites in place, it's time to kick off the virtual network lab environment. This section outlines the steps to start GNS3, launch the GNS3 VM in VMware, and initiate the Ubuntu 22 Server.

### Start GNS3

Open GNS3 on your Windows PC. Navigate through any initial setup wizards or configurations if prompted. Once the GNS3 interface is accessible, you're ready to proceed.

### Launch GNS3 VM in VMware

Ensure that VMware is installed on your Windows PC. Start VMware and locate the GNS3 VM in your virtual machine library. Power on the GNS3 VM to establish the connection between GNS3 and the virtual machine.

### Configuring Ubuntu Server

In this section, we'll focus on configuring the Ubuntu 22 Server within your virtual lab environment. A crucial step in this process is setting up a bridge network for the Ubuntu Server in VMware. Follow these steps to ensure seamless connectivity:

### Open VMware Settings for Ubuntu Server

1. In VMware, locate the Ubuntu 22 Server virtual machine.
2. Ensure the VM is powered off.
3. Right-click on the VM and select "Settings."

### Configure Network Adapter to Bridge Mode

1. In the VM Settings window, navigate to the "Network Adapter" tab.
2. Change the network connection mode to "Bridged."
3. Select the network adapter connected to your physical network.
4. Click "OK" to save the changes.

![bridge mode](images/vm-br-nt.jpg)

### Start Ubuntu Server

1. Power on the Ubuntu 22 Server virtual machine in VMware.
2. Allow the VM to boot up and log in using the credentials you configured during the Ubuntu setup.

### Verify Network Configuration

1. Open a terminal in Ubuntu.
2. Use the following command to check the network interfaces:

```bash
ip a
```

1. Ensure that the network interface is associated with an IP address and is in the "UP" state.

By configuring a bridge network, you enable direct communication between the Ubuntu Server and your physical network, facilitating connectivity with other devices in the virtual lab. With the network settings in place, proceed to Section 4, where we guide you through adding a cloud node to GNS3 and selecting your network.

## Adding Cloud Node to GNS3

In this section, we'll expand your virtual network lab in GNS3 by adding a cloud node. The cloud node serves as a bridge between the GNS3 environment and your physical network, enabling connectivity to external devices. Follow these steps to seamlessly integrate the cloud node:

### Access the GNS3 Workspace

1. In the GNS3 interface, navigate to the workspace where you plan to build your network topology.

### Add Cloud Node

1. From the GNS3 toolbar, locate and drag the "Cloud" node into the workspace.
2. Connect the cloud node to your existing devices using appropriate link types (Ethernet, Wifi).

### Configure Cloud Node

1. Right-click on the cloud node and select "Configure."
2. In the "Node Configurations" window, select the "Ethernet Interface" tab.
3. Choose the network adapter that corresponds to your physical network.

![cloud node](images/cloud-node.jpg)

### Apply Changes

1. Click "OK" to apply the changes to the cloud node.
2. Save the GNS3 project to preserve the current configuration.

By adding a cloud node and configuring it to use your physical network, you establish a vital link between GNS3 and external devices. This integration sets the stage for comprehensive testing and interaction within your virtual network lab.

## Installing VSCode and SSH Extension

In this section, we'll enhance your virtual network lab environment by integrating Visual Studio Code (VSCode) and installing the SSH extension. VSCode provides a versatile platform for code development and, with the SSH extension, allows seamless interaction with your Ubuntu Server. Follow these steps to set up this essential coding and remote connection environment:

### Download and Install VSCode

1. Visit the official VSCode website at [VSCode Downloads](https://code.visualstudio.com/download) to download the installer.
2. Run the installer and follow the on-screen instructions to complete the installation.

### Open VSCode

Once VSCode is installed, open the application on your Windows PC.

### Install SSH Extension

1. In VSCode, go to the Extensions by clicking on the Extensions icon in the Activity Bar on the side of the window or using the shortcut `Ctrl+Shift+X`.
2. Search for "Remote - SSH" in the Extensions view search box.
3. Click "Install" next to the "Remote - SSH" extension.

![ssh ext](images/ssh-ext.jpg)

### Configure SSH Connection

In the bottom-left corner of the VSCode window, click on the blue square icon (Remote Explorer).
Click on the "Connect to Host" to add a new SSH target.
Enter the SSH connection details for your Ubuntu Server (username, IP address).

![ssh con](images/re-con.jpg)

With VSCode and the SSH extension installed, you now have a powerful coding environment directly linked to your Ubuntu Server. This integration streamlines the process of writing and testing Python scripts for your network lab.

## Connecting VSCode to Ubuntu Server

In this section, we'll establish a direct connection between Visual Studio Code (VSCode) and your Ubuntu Server within the GNS3 virtual network lab. This connection allows you to seamlessly write, test, and execute Python scripts on the Ubuntu Server. Follow these steps to ensure a smooth integration:

### Access Remote Explorer

1. In the bottom-left corner of the VSCode window, click on the square icon (Remote Explorer).
2. You should see the SSH target you added in the previous section.

### Connect to Ubuntu Server

1. Click on the SSH target representing your Ubuntu Server.
2. VSCode will establish an SSH connection to the Ubuntu Server, and you'll be prompted for the password. Enter the password for your Ubuntu Server.

### Verify Connection

1. Once connected, you should see the Ubuntu Server's file system in the VSCode Explorer.
2. Open a terminal in VSCode and run basic commands to verify the SSH connection.

### Create and Test Python Scripts

1. In VSCode, create a new Python file.
2. Write a simple Python script (e.g., print("Hello, GNS3!")) and save the file.
3. Use the VSCode terminal to navigate to the directory containing your Python script and run it.

With this connection established, you can seamlessly develop, debug, and test Python scripts directly on your Ubuntu Server from within the VSCode environment. This integration empowers you to leverage the full potential of your virtual network lab for scripting and automation tasks.

## Finalizing the Lab Setup

Congratulations on successfully setting up your virtual network lab with GNS3, Ubuntu Server, and Visual Studio Code (VSCode). In this section, we'll recap the key components of your lab setup and highlight the benefits of the interconnected environment you've created.

### Recap of Components

Let's review the core elements of your virtual network lab:

- **GNS3:** The network simulation tool providing a platform to design and test complex network topologies.
- **Ubuntu Server:** A virtual machine running in VMware, serving as a network device for practical testing and application deployment.
- **Visual Studio Code (VSCode):** Your coding environment with the added capability of connecting directly to the Ubuntu Server for Python script development.

### Achieved Connections

Through the steps outlined in this guide, you've achieved the following connections:

- **GNS3 and Ubuntu Server:** GNS3 is integrated with the Ubuntu Server, allowing for dynamic interactions and testing within the simulated network environment.
- **Windows PC and GNS3:** Your Windows host is the control center for GNS3, facilitating topology design, configuration, and monitoring.
- **VSCode and Ubuntu Server:** VSCode is directly connected to the Ubuntu Server via SSH, enabling seamless coding, script execution, and testing.

### Benefits of the Lab Setup

By creating this integrated virtual network lab, you've gained several advantages:

- **Hands-on Learning:** Actively engage with networking concepts through practical exercises and experiments.
- **Scripting and Automation:** Leverage Python scripts to automate network configurations and tasks.
- **Real-world Simulation:** Mimic real-world network scenarios and challenges within the GNS3 environment.

### Next Steps

As you continue your network exploration, consider the following next steps:

- **Expand Your Topology:** Add more devices to your GNS3 topology to simulate complex network architectures.
- **Experiment with Python:** Explore advanced Python scripts to handle various networking tasks.
- **Document Your Lab:** Maintain comprehensive documentation of your lab setup, including configurations and scripts, for future reference.

## Conclusion

In conclusion, you've successfully created a virtual network lab that serves as an invaluable resource for testing Python code on networking devices. This hands-on environment, comprising GNS3, Ubuntu Server, and VSCode, empowers you to refine your networking and coding skills in a dynamic and controlled setting.
