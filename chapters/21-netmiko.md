# Simplifying Network Device Management with Netmiko

Netmiko is a powerful Python library designed to simplify SSH management of network devices. It builds upon the Paramiko SSH library and provides a uniform API for interacting with a wide range of network devices. In this guide, we'll explore the key features of Netmiko and demonstrate how to use it for tasks such as executing commands, making configuration changes, handling exceptions, and backing up device configurations.

## What is Netmiko?

Netmiko streamlines SSH management to network devices by providing a unified interface for interacting with devices from different vendors. Its main purposes include:

- Establishing SSH connections to devices
- Executing, retrieving, and formatting show commands
- Sending configuration commands

## Installing Netmiko

Netmiko is not part of Python standard library, so you will have to install it using `pip`. The process is similar for all operating systems such as macOS/Linux. To install Netmiko, use `pip` as below:

```bash
pip install netmiko
```

Netmiko has several requirements, which pip will automatically install for you, including `Paramiko`, `scp`, `pyserial`, and `textfsm`.

To ensure Netmiko is correctly installed, you can test by importing it in Python shell.

## Connecting a Single Device

To establish an SSH connection to a device using Netmiko, import the `ConnectHandler` class and provide the necessary device details:

```python
from netmiko import ConnectHandler

connection = ConnectHandler(
    host="172.16.10.12", username="admin", password="cisco", device_type="cisco_ios"
)
output = connection.send_command("show ip interface brief")
print(output)
connection.disconnect()
```

```bash
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            172.16.10.12    YES NVRAM  up                    up      
FastEthernet0/1            unassigned      YES NVRAM  administratively down down    
Loopback0                  1.1.1.0         YES manual up                    up      
Loopback2                  1.1.1.2         YES manual up                    up      
Loopback3                  1.1.1.3         YES manual up                    up      
Loopback4                  1.1.1.4         YES manual up                    up
```

- Import the `ConnectHandler` class from Netmiko.
- Define device details including device type, IP address, username, password, and secret (if required).
- Use the `ConnectHandler` method to establish an SSH connection to the device.
- Send a show command `show ip int brief` to the device and print the output.
- Ensure to disconnect the SSH session by using the `disconnect()` method

> *Note*: Ensure that the cisco device is correctly configured for SSH access and that the Python workstation can successfully SSH into the device.

## Simplify Device Connections with Python Dictionaries in Netmiko

To keep our device inventory organized and accessible, Python dictionaries offer a well-ordered solution for this. Let's say we have a Cisco device with particulars such as: it's running iOS, IP address, and a username and password to access it.

We can pack all these details neatly into a Python dictionary called `SW_01`:

```python
SW_01 = {
    "device_type": "cisco_ios",
    "host": "172.16.10.12",
    "username": "admin",
    "password": "cisco"
}
```

Now, when we want to connect to this device using Netmiko, we simply unpack this dictionary:

```python
from netmiko import ConnectHandler

# Unpacking the dictionary to connect to the device
connection = ConnectHandler(**SW_01)
```

We've established a connection to our device using the credintials stored in our dictionary. Next, we can send commands to our device as usual. Let's fetch the descriptions of its interfaces:

```python
output = connection.send_command('show interface desc')
print(output)
```

And when we're done, we can gracefully close the connection:

```python
connection.disconnect()
```

```bash
Interface                      Status         Protocol Description
Fa0/0                          up             up       
Fa0/1                          admin down     down
```

Using dictionaries for device details not only keeps our code organized but also allows us to reuse this information throughout our script. It's like having all your tools neatly arranged in a toolbox, ready for use whenever you need them.

## Enabling Privilege EXEC Mode with Netmiko

When we're automating tasks on network devices using Netmiko, sometimes we encounter situations where our default login mode doesn't grant us the necessary permissions. For instance, trying to run certain commands like `show run` might result in errors.

To tackle this, Netmiko offers a solution: enabling Privilege EXEC mode. This mode grants us elevated privileges, allowing us to execute a wider range of commands. Let's see how we can do this in a simple and straightforward manner.

First, we define our device details in a Python dictionary, just like before:

```python
SW_01 = {
    "device_type": "cisco_ios",
    "host": "172.16.10.12",
    "username": "admin",
    "password": "cisco",
    "secret": "cisco123"  # Enable password
}
```

Notice the addition of the `secret` parameter. This is where we specify our `enable` password, which is needed to access Privilege EXEC mode. Next, we establish a connection to our device as usual:

```python
connection = ConnectHandler(**SW_01)
```

Now, here comes the helpful function! The `enable()` method provided by Netmiko to switch to Privilege EXEC mode:

```python
connection.enable()
```

This simple line of code elevates our permissions, giving us access to more powerful commands. To verify that we've successfully switched to Privilege EXEC mode, we can use the `find_prompt()` method:

```python
device_prompt = connection.find_prompt()
print(device_prompt)
```

This will print out the prompt of our device, confirming that we're now in Privilege EXEC mode. Now, we can confidently execute commands like `show run` without encountering permission issues:

```python
output = connection.send_command('show run')
print(output)
```

And when we're done, it's good practice to gracefully close the connection:

```python
connection.disconnect()
```

With just a few lines of code, we've unlocked the full potential of our network automation script by enabling Privilege EXEC mode with Netmiko.

## Device Configuration with Netmiko

Netmiko, offers a seamless way to enter Global Configuration Mode, where we can make changes to our device's settings. Let's dive into how we can tackle  the power of Global Configuration Mode using Netmiko.

First, we set up our device details in a Python dictionary, just like before:

```python
SW_01 = {
    "device_type": "cisco_ios",
    "host": "172.16.10.11",
    "username": "admin",
    "password": "cisco",
    "secret": "cisco123"  # Enable password
}
```

We then establish a connection to our device and elevate our permissions to Privilege EXEC mode:

```python
connection = ConnectHandler(**SW_01)
connection.enable()  # Enable method
```

Now, it's time to enter Global Configuration Mode using the `config_mode()` method:

```python
connection.config_mode()  # Global config mode
```

With Global Configuration Mode activated, we can execute configuration commands on our device. For example, let's create an ACL `access-list 1 permit any`:

```python
connection.send_command('access-list 1 permit any')
```

Once we're done with our configuration tasks, it's important to exit Global Configuration Mode using the `exit_config_mode()` method:

```python
connection.exit_config_mode()  # Exit global config mode
```

And just like that, we've seamlessly transitioned back to Privilege EXEC mode, ready to execute show commands or perform other tasks.

As a demonstration, let's fetch the descriptions of our device's interfaces:

```python
show_output = connection.send_command('show interface desc')
print(show_output)
```

Finally, as a best practice, we gracefully close the connection:

```python
connection.disconnect()
```

With Netmiko's Global Configuration Mode, configuring devices becomes as easy as pie. Whether it's creating ACLs, adjusting interface settings, or making other configuration changes, Netmiko empowers us to automate with confidence.

## Safeguarding Passwords in Network Automation with Python's getpass

In the world of network automation, security is paramount. Storing passwords or secrets as plain text is a big mistake. Fortunately, Python provides us with a solution: the `getpass` library, `getpass` allows us to prompt the user for sensitive information, such as passwords, without echoing their input to the terminal. This means the password remains hidden from view, enhancing security.

Let's explore how we can use `getpass` to securely handle passwords in our network automation scripts.

```python
from netmiko import ConnectHandler
import getpass

passwd = getpass.getpass('Please enter the password: ')  # Prompt user for password securely

SW_01 = {
    "device_type": "cisco_ios",
    "host": "172.16.10.11",
    "username": "admin",
    "password": passwd,  # Log in password from getpass
    "secret": passwd  # Enable password from getpass
}

connection = ConnectHandler(**SW_01)
connection.enable()  # Enter Privilege EXEC mode

output = connection.send_command('show interface desc')
print(output)

connection.disconnect()
```

In this script, we use `getpass` to prompt the user for the password interactively. The entered password is then securely saved as a string in the `passwd` variable.

Next, we define our device details, including the username and passwords obtained from `getpass`. These details are then used to establish a connection to the device.

Once connected, we can execute commands on the device as needed. In this example, we fetch the descriptions of the interfaces using the `send_command` method.

Finally, we gracefully close the connection to the device.

By leveraging `getpass`, we ensure that passwords are handled securely in our network automation scripts. No more worries about storing sensitive information in plain text files!

## Sending Multiple Commands

When it comes to network automation, sending a single command to a single device is just the tip of the iceberg. What we really want is the ability to send multiple commands, a mix of show and configuration commands, using a single Python script. Thankfully, Netmiko makes this possible with its powerful `send_config_set` method.

Let's delve into how we can leverage this feature to streamline our configuration tasks.

First, let's set the stage by gathering the necessary details to connect to our device. We'll prompt the user to enter the password securely:

```python
from netmiko import ConnectHandler
import getpass

passwd = getpass.getpass('Please enter the password: ')

SW_01 = {
    "device_type": "cisco_ios",
    "host": "172.16.10.11",
    "username": "admin",
    "password": passwd,  # Log in password from getpass
    "secret": passwd  # Enable password from getpass
}
```

With our device details in place, we establish a connection and elevate our permissions to Privilege EXEC mode:

```python
connection = ConnectHandler(**SW_01)
connection.enable()
```

Now, let's define a list of configuration commands that we want to push to the device:

```python
config_commands = ['interface gi0/0', 'description WAN', 'exit', 'access-list 1 permit any']
```

Using the `send_config_set` method, we can send this list of commands to the device. This method automatically enters Global Configuration Mode, executes the commands, and then exits Global Configuration Mode:

```python
connection.send_config_set(config_commands)
```

And just like that, we've pushed multiple configuration commands to our device with a single Python script. No need to manually enter each command one by one.

To verify that our configurations have been applied, we can run show commands on the device:

```python
print(connection.send_command('show interfaces description'))
print(connection.send_command('show access-lists'))
```

Finally, as we wrap up, let's gracefully close the connection:

```python
connection.disconnect()
```

With Netmiko's `send_config_set` method, configuring devices becomes a breeze. Whether it's setting descriptions on interfaces, creating ACLs, or making other configuration changes, Netmiko empowers us to automate with ease.

## Connecting to Multiple Devices with Netmiko

In network management, efficiency is key, especially when dealing with multiple devices. Netmiko, with its versatility, allows us to seamlessly connect and manage multiple devices with ease. Let's explore how we can harness the power of Netmiko to connect to multiple devices and execute commands across them.

To begin, let's set up our script to connect to multiple devices and retrieve some basic information. We'll use a list of dictionaries to store the details of each device, such as its IP address, username, and password.

```python
from netmiko import ConnectHandler
import getpass
import json

passwd = getpass.getpass('Please enter the password: ')

# List of device IPs
ip_list = ["172.16.10.11", "172.16.10.12"]

# Create a list of dictionaries for each device
device_list = []

# Populate the device list with device details
for ip in ip_list:
    device = {
        "device_type": "cisco_ios",
        "host": ip,
        "username": "admin",
        "password": passwd,  # Log in password from getpass
        "secret": passwd  # Enable password from getpass
    }
    device_list.append(device)

# Print human-readable device details using JSON formatting
json_formatted = json.dumps(device_list, indent=4)
print(json_formatted)

# Iterate over each device and connect to it
for each_device in device_list:
    connection = ConnectHandler(**each_device)
    connection.enable()
    print(f'Connecting to {each_device["host"]}')
    output = connection.send_command('show run | incl hostname')
    print(output)
    print(f'Closing Connection on {each_device["host"]}')
    connection.disconnect()
```

In this script, we first prompt the user to enter the password securely using the `getpass` library. We then define a list of device IPs and iterate over each one to create a list of dictionaries containing the device details.

Using Netmiko's `ConnectHandler` method, we establish a connection to each device in the list. We print the hostname of each device by executing the `show run | incl hostname` command and then gracefully close the connection.

With this script, we can efficiently connect to and retrieve information from multiple devices, streamlining our network management tasks. Netmiko's flexibility and ease of use make it a valuable tool for network automation.

By leveraging Netmiko's capabilities, we can simplify complex network operations and enhance our overall efficiency in managing network infrastructure.

## Simplifying Network Configuration with Netmiko

Managing configurations across multiple network devices can be a daunting task, but with Netmiko, it becomes a seamless process. Let's explore how we can leverage Netmiko to streamline configuration tasks across various devices.

### Send Configuration Commands to Multiple Devices

With Netmiko's `send_config_set()` method, configuring multiple devices becomes a breeze. Take a look at the complete script below:

```python
from netmiko import ConnectHandler

# Define device details for Cisco devices
devices = [
    {
        'device_type': 'cisco_ios',
        'ip': '172.16.10.11',
        'username': 'admin',
        'password': 'cisco',
        'secret': 'cisco123',
    },
    {
        'device_type': 'cisco_ios',
        'ip': '172.16.10.12',
        'username': 'admin',
        'password': 'cisco',
        'secret': 'cisco123',
    },
]

# Iterate through a list of device dictionaries
for device in devices:
    print(f"Connecting to {device['ip']}...")
    net_connect = ConnectHandler(**device)
    net_connect.enable()

    # Configure the device
    config_commands = ['username admin pri 15 password cisco']
    net_connect.send_config_set(config_commands)
    net_connect.save_config()

    # Display the updated configuration
    output = net_connect.send_command('show running-config | section username')
    print(output)

    print(f'Closing Connection on {device["ip"]}')
    net_connect.disconnect()
```

- **Iterate through Devices**: Loop through a list of device dictionaries, each containing device details.
- **Connect and Configure**: Establish a connection to each device, enter enable mode, and configure it with a set of commands.
- **Save and Display**: Save the configuration changes and display the updated configuration for verification.

### Configuration Changes from a File

Netmiko also allows for applying configurations from a file using the `send_config_from_file()` method. Here's how you can do it:

```python
from netmiko import ConnectHandler

# Define device details for a Cisco device
device = {
    'device_type': 'cisco_ios',
    'ip': '172.16.10.11',
    'username': 'admin',
    'password': 'cisco',
    'secret': 'cisco123',
}

file = "config_file.cfg"

# Use a context manager to establish a connection to the device
with ConnectHandler(**device) as net_connect:
    output = net_connect.send_config_from_file(file)
    output += net_connect.save_config()

print(output)
```

- **Establish Connection**: Define device details and use a context manager to connect to the device.
- **Apply Configurations**: Apply configurations from the specified file to the device and save the changes.
- **Print Output**: Print any output or error messages for reference.

### Exception Handling

Handling exceptions is crucial when dealing with network devices. Netmiko provides exception classes to handle common issues such as timeouts and authentication errors. Here's how you can handle exceptions in your script:

```python
from netmiko import ConnectHandler
from netmiko.ssh_exception import NetmikoTimeoutException, NetmikoAuthenticationException

# Define device details for Cisco devices with potential authentication errors
devices = [
    {
        'device_type': 'cisco_ios',
        'ip': '172.16.10.11',
        'username': 'admin',
        'password': 'cisco123',  # Wrong Password
    },
    {
        'device_type': 'cisco_ios',
        'ip': '172.16.10.12',  # Wrong IP Address
        'username': 'admin',
        'password': 'cisco',
    }
]

# Attempt to establish a connection to each device and execute a show command
for device in devices:
    try:
        net_connect = ConnectHandler(**device)
        output = net_connect.send_command("show ip int brief")
        print(output)
    except NetmikoTimeoutException:
        print(f"Device {device['ip']} not reachable")
    except NetmikoAuthenticationException:
        print(f"Authentication failed for {device['ip']}")
```

- **Handle Exceptions**: Gracefully handle timeout and authentication exceptions and print appropriate messages for troubleshooting.

### Backup Device Configuration

Automating device configuration backups is essential for network engineers. Netmiko simplifies this process:

```python
from netmiko import ConnectHandler
from datetime import datetime

# Define device details for Cisco devices
devices = [
    {
        "host": "172.16.10.11",
        "username": "admin",
        "password": "cisco",
        "device_type": "cisco_ios",
    },
    {
        "host": "172.16.10.12",
        "username": "admin",
        "password": "cisco",
        "device_type": "cisco_ios",
    }
]

# Get current timestamp
time_stamp = datetime.now().strftime("%d-%b-%Y")

# Retrieve the running configuration of each device and save it to a file with a timestamp
for device in devices:
    net_connect = ConnectHandler(**device)
    print(f"Initiating running config backup for {device['host']}...")
    sh_run = net_connect.send_command('show run')

    with open(f"{device['host']}_{time_stamp}.cfg", 'w') as f:
        f.write(sh_run)
        print("Backup saved")

print("Finished backup process.")
```

- **Backup Configuration**: Retrieve the running configuration of each device and save it to a file with a timestamp for archival purposes.

## Conclusion

Netmiko empowers network engineers with the ability to automate common configuration tasks across multiple devices. By following the examples outlined above, you can streamline network management operations and enhance overall efficiency. Dive deeper into Netmiko's capabilities and explore additional examples in the [Netmiko GitHub repository](https://github.com/ktbyers/netmiko/blob/develop/EXAMPLES.md).
