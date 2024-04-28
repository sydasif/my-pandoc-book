# Simplifying Network Device Management with Netmiko

Netmiko is a powerful Python library designed to simplify SSH management of network devices. It builds upon the Paramiko SSH library and provides a uniform API for interacting with a wide range of network devices. In this guide, we'll explore the key features of Netmiko and demonstrate how to use it for tasks such as executing commands, making configuration changes, handling exceptions, and backing up device configurations.

## What is Netmiko?

Netmiko simplifies SSH management to network devices by providing a unified interface for interacting with devices from different vendors. Its main purposes include:

- Establishing SSH connections to devices
- Executing, retrieving, and formatting show commands
- Sending configuration commands

To install Netmiko, use pip:

```bash
pip install netmiko
```

Netmiko has several requirements, which pip will automatically install for you, including `Paramiko`, `scp`, `pyserial`, and `textfsm`.

Now, let's ensure Netmiko is correctly installed by importing it in Python:

```python
import netmiko
```

## Getting Started with Netmiko

To establish an SSH connection to a device using Netmiko, import the `ConnectHandler` class and provide the necessary device details:

```python
from netmiko import ConnectHandler

# Define device details
device = {
    'device_type': 'cisco_ios',
    'ip': '192.168.10.11',
    'username': 'admin',
    'password': 'cisco',
    'secret': 'cisco',
}

# Connect to the device
net_connect = ConnectHandler(**device)
net_connect.enable()  # Enter enable mode

# Send a show command to the device
output = net_connect.send_command("show ip int brief")
print(output)

# Explanation:
# - Import the ConnectHandler class from Netmiko.
# - Define device details including device type, IP address, username, password, and secret (if required).
# - Use the ConnectHandler method to establish an SSH connection to the device.
# - Enter enable mode on the device.
# - Send a show command ("show ip int brief") to the device and print the output.
```

## Making Configuration Changes

Netmiko makes it easy to configure multiple devices using the `send_config_set()` method. Here's an example of configuring multiple Cisco devices:

```python
from netmiko import ConnectHandler

devices = [
    {
        'device_type': 'cisco_ios',
        'ip': '192.168.10.11',
        'username': 'admin',
        'password': 'cisco',
        'secret': 'cisco',
    },
    {
        'device_type': 'cisco_ios',
        'ip': '192.168.10.12',
        'username': 'admin',
        'password': 'cisco',
        'secret': 'cisco',
    },
    {
        'device_type': 'cisco_ios',
        'ip': '192.168.10.10',
        'username': 'admin',
        'password': 'cisco',
        'secret': 'cisco',
    }
]

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

# Explanation:
# - Iterate through a list of device dictionaries.
# - Connect to each device, enter enable mode, and configure the device with a set of commands.
# - Save the configuration changes and display the updated configuration.
```

## Configuration Changes from a File

Netmiko also allows you to apply configurations from a file using the `send_config_from_file()` method:

```python
from netmiko import ConnectHandler

device = {
    'device_type': 'cisco_ios',
    'ip': '192.168.10.10',
    'username': 'admin',
    'password': 'cisco',
    'secret': 'cisco',
}

file = "config_file.cfg"

with ConnectHandler(**device) as net_connect:
    output = net_connect.send_config_from_file(file)
    output += net_connect.save_config()

print(output)

# Explanation:
# - Define device details for a Cisco device.
# - Specify the path to a configuration file.
# - Use a context manager to establish a connection to the device.
# - Apply configurations from the file to the device and save the changes.
# - Print any output or error messages.
```

## Exception Handling

Handling exceptions is crucial when dealing with network devices. Netmiko provides exception classes to handle common issues such as timeouts and authentication errors:

```python
from netmiko import ConnectHandler
from netmiko.ssh_exception import NetmikoTimeoutException, NetmikoAuthenticationException

devices = [
    {
        'device_type': 'cisco_ios',
        'ip': '192.168.10.12',
        'username': 'admin',
        'password': 'cisco123',  # Wrong Password
    },
    {
        'device_type': 'cisco_ios',
        'ip': '192.168.10.13',  # Wrong IP Address
        'username': 'admin',
        'password': 'cisco',
    }
]

for device in devices:
    try:
        net_connect = ConnectHandler(**device)
        output = net_connect.send_command("show ip int brief")
        print(output)
    except NetmikoTimeoutException:
        print(f"Device {device['ip']} not reachable")
    except NetmikoAuthenticationException:
        print(f"Authentication failed for {device['ip']}")

# Explanation:
# - Iterate through a list of device dictionaries.
# - Attempt to establish a connection to each device and execute a show command.
# - Handle timeout and authentication exceptions gracefully and print appropriate messages.
```

## Backup Device Configuration

Automating device configuration backups is essential for network engineers. Netmiko makes it easy to retrieve and save device configurations:

```python
from netmiko import ConnectHandler
from datetime import datetime
import time

username = "admin"
password = "cisco"

devices = [
    {
        "host": "192.168.10.11",
        "username": username,
        "password": password,
        "device_type": "cisco_ios",
    },
    {
        "host": "192.168.10.12",
        "username": username,
        "password": password,
        "device_type": "cisco_ios",
    }
]

time_stamp = datetime.now().strftime("%d-%b-%Y")

for device in devices:
    net_connect = ConnectHandler(**device)
    print(f"Initiating running config backup for {device['host']}...")
    sh_run = net_connect.send_command('show run')

    with open(f"{device['host']}_{time_stamp}.cfg", 'w') as f:
        f.write(sh_run)
        print("

Backup saved")

print("Finished backup process.")

# Explanation:
# - Define device details for Cisco devices including host, username, password, and device type.
# - Retrieve the running configuration of each device and save it to a file with a timestamp.
# - Print messages to indicate the backup process.
```

## Conclusion

Netmiko is a powerful tool for simplifying SSH management of network devices. By following the examples in this guide, you can automate common tasks such as executing commands, making configuration changes, handling exceptions, and backing up device configurations. For more advanced use cases and additional examples, refer to the [Netmiko GitHub repository](https://github.com/ktbyers/netmiko/blob/develop/EXAMPLES.md).
