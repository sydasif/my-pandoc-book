# Paramiko - Secure SSH Connections in Python

Paramiko is a Python library that provides a pure-Python implementation of SSHv2 for secure communication between Python applications and remote devices over SSH. Its primary purpose is to facilitate secure remote access and management of network devices, servers, and other systems.

Paramiko offers a range of capabilities essential for building robust and secure SSH connections in Python. These capabilities include:

- Establishing encrypted SSH connections
- Authenticating users using various methods (e.g., passwords, SSH keys)
- Executing commands on remote hosts and retrieving responses
- Transferring files securely between hosts using SFTP
- Handling SSH negotiation, key exchange, and encryption algorithms

## Setting up Paramiko for SSH Communication

Before using Paramiko in Python scripts, it's essential to install the library and set up the development environment. Paramiko can be installed via `pip`, the Python package manager, using the following command:

```bash
pip install paramiko
```

Once installed, developers can import the Paramiko module in their Python scripts and start using its classes and functions to establish SSH connections and interact with remote devices.

## Establishing Secure Connections to Network Devices

Paramiko allows developers to establish secure SSH connections to network devices, servers, and other systems. The process involves creating a Paramiko SSH client object, specifying connection parameters such as the hostname, port, and authentication credentials, and then initiating the connection.

```py
import paramiko

# Create SSH client
client = paramiko.SSHClient()

# Set policy to automatically add hosts to known hosts file
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

# Connect to the remote host
client.connect(
    hostname="172.16.10.11",
    username="admin",
    password="cisco",
    look_for_keys=False,
    allow_agent=False,
)

# Perform operations on the remote host

# Close the connection
client.close()
```

## Executing Commands and Handling Responses Asynchronously

Once a secure SSH connection is established, developers can execute commands on the remote host and handle the command output asynchronously using Paramiko. This allows for efficient execution of multiple commands and parallel processing of command responses.

```py
import paramiko
import time

# Create SSH client
client = paramiko.SSHClient()

# Set policy to automatically add hosts to known hosts file
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

# Connect to the remote host
client.connect(
    hostname="172.16.10.12",
    username="admin",
    password="cisco",
    look_for_keys=False,
    allow_agent=False,
)

# Open an interactive SSH session
ssh_client = client.invoke_shell()

# Send command
ssh_client.send("sh ip int bri\n")

# Wait for the command to be finished
time.sleep(3)

# Receive and process command output
output = ssh_client.recv(65000)
print(output.decode("ascii"))

# Close the SSH session
ssh_client.close()

# Close the connection
client.close()
```

## Handling Exceptions and Error Scenarios Gracefully

In network automation and remote system management, it's crucial to handle exceptions and error scenarios gracefully to ensure the robustness and reliability of the application. Paramiko provides mechanisms for catching and handling exceptions that may occur during SSH communication, such as authentication errors, connection timeouts, and network failures.

```py
import paramiko
import time


# Create SSH client
try:

    client = paramiko.SSHClient()

    # Set policy to automatically add hosts to known hosts file
    client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

    # Connect to the remote host
    client.connect(
        hostname="172.16.10.12",
        username="admin",
        password="cisco",
        look_for_keys=False,
        allow_agent=False,
    )

    # Open an interactive SSH session
    ssh_client = client.invoke_shell()

    # Send command
    ssh_client.send("sh ip int bri\n")

    # Wait for the command to be finished
    time.sleep(3)

    # Receive and process command output
    output = ssh_client.recv(65000)
    print(output.decode("ascii"))

    # Close the SSH session
    ssh_client.close()

    # Close the connection
    client.close()

except paramiko.AuthenticationException:
    print("Authentication failed. Please verify your credentials.")
```

By effectively handling exceptions and error scenarios, developers can build resilient and fault-tolerant Python applications for secure SSH communication using Paramiko.

## Advanced Example: Creating Loopback Interfaces

In the next example, we employ a for loop and the range() function to create loopback interfaces on a Cisco router.

```python
import paramiko
import time

# Create an SSH client instance
client = paramiko.SSHClient()
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

# Connect to the remote device
client.connect(
    "172.16.10.11",
    username="admin",
    password="cisco",
    look_for_keys=False,
    allow_agent=False,
)

# Start an interactive shell
ssh_client = client.invoke_shell()
print("###### Creating loopback interfaces ######")

# ssh_client.send("cisco\n")
ssh_client.send("conf ter\n")

# Use a for loop and range() to create loopback interfaces
for interface_number in range(0, 2):
    ssh_client.send(f"int lo {interface_number}\n")
    ssh_client.send(f"ip address 1.1.1.{interface_number} 255.255.255.255\n")

# Wait for the configurations to take effect
time.sleep(1)
ssh_client.send("end\n")
ssh_client.send("show ip int brief\n")

# Wait for the output and retrieve it
time.sleep(3)
output = ssh_client.recv(65000)
print(output.decode("ascii"))

# Close the SSH connection
client.close()
```

This advanced example demonstrates the flexibility of Paramiko for configuring network devices programmatically. The script showcases the creation of loopback interfaces, providing a practical illustration of how automation can simplify repetitive tasks.

## Connecting to Multiple Devices

Expanding our horizons, the following example demonstrates using a for loop to connect to multiple devices sequentially.

```python
import paramiko
import time

client = paramiko.SSHClient()
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

# For loop and range() function to connect to multiple devices
for device in range(11, 13):
    ip = "172.16.10." + str(device)
    print("\n##### Connecting to the device " + ip + " #####")

    client.connect(
        ip, username="admin", password="cisco", look_for_keys=False, allow_agent=False
    )

    ssh_client = client.invoke_shell()
    ssh_client.send("show ip int brief\n")
    time.sleep(3)
    output = ssh_client.recv(65000)
    print(output.decode("ascii"))
    client.close()
```

This script demonstrates the scalability of Paramiko, allowing network engineers to connect and interact with multiple devices seamlessly.

## Connecting to Multiple Devices with a List

In this example, we use a for loop and a list to connect to multiple devices. This approach provides greater flexibility and ease of maintenance.

```python
import paramiko
import time

username = "admin"  # username
password = "cisco"  # password

# IP list for network devices
devices = ["172.16.10.11", "172.16.10.12"]

# For loop and list to connect to multiple devices
for device in devices:
    print("\n #### Connecting to the device " + device + " ####\n")

    client = paramiko.SSHClient()
    client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

    client.connect(
        device,
        port=22,
        username=username,
        password=password,
        look_for_keys=False,
        allow_agent=False,
    )

    ssh_client = client.invoke_shell()
    ssh_client.send("config ter\n")

    # For loop and range() function to create loop back interface
    for num in range(2, 5):
        ssh_client.send("int lo " + str(num) + "\n")
        ssh_client.send("ip address 1.1.1." + str(num) + " 255.255.255.255\n")

    time.sleep(1)
    ssh_client.send("do term length 0\n")
    ssh_client.send("do show ip int brief\n")
    time.sleep(3)
    output = ssh_client.recv(65000)
    print(output.decode("ascii"))

    client.close()
```

This script introduces a more modular approach, where devices are managed through a list, providing simplicity and ease of maintenance.

## Conclusion

Paramiko plays a pivotal role in network automation, empowering network engineers to streamline and automate various tasks efficiently. By leveraging Paramiko for secure SSH communication with networking devices, network engineers can enhance network operations' efficiency and reliability.

The examples provided serve as foundational knowledge for creating customized automation workflows tailored to specific network requirements. Embrace the power of Paramiko and Python to adapt and thrive in the dynamic landscape of network management.
