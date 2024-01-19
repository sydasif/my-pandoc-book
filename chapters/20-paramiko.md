# Streamlining Network Operations with Python and Paramiko

When it comes to network automation, Python stands out as a versatile language, and Paramiko, a Python library, takes the center stage in simplifying secure communication over SSH. In this blog post, we'll explore the capabilities of Paramiko through practical examples that showcase its effectiveness in automating network configurations.

## Getting Started with Paramiko

Paramiko serves as a robust implementation of the SSHv2 protocol, offering both client and server functionality. It plays a crucial role in the toolkit of network engineers, enabling seamless automation of tasks on networking devices. Let's delve into the core features and a simple example of its application.

### Installation

Before diving into the examples, ensure that you have Paramiko installed. You can do this effortlessly using the following pip command:

```bash
pip install paramiko
```

### Basic Example: Secure Connection and Command Execution

The following Python script demonstrates a secure connection to a network device, executes a command, and prints the output. This foundational example sets the stage for more advanced automation tasks.

```python
import paramiko
import time

# Create an instance of the SSHClient class from Paramiko
client = paramiko.SSHClient()
# Set the policy for handling keys
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

# Connect to the remote device
client.connect(
    "192.168.10.11",
    username="admin",
    password="cisco",
    look_for_keys=False,
    allow_agent=False,
)

# Start an interactive shell
ssh_client = client.invoke_shell()
# Send command to the remote device
ssh_client.send("sh ip int bri\n")
# Wait for the command to be finished
time.sleep(3)

# Retrieve and print the output
output = ssh_client.recv(5000)
print(output.decode("ascii"))

# Close the remote connection
client.close()
```

This script provides a foundation for more complex automation scenarios, showcasing the basics of establishing a secure connection, sending commands, and handling output.

### Advanced Example: Creating Loopback Interfaces

In the next example, we employ a `for` loop and the `range()` function to create loopback interfaces on a Cisco router.

```python
import paramiko
import time

# Create an SSH client instance
client = paramiko.SSHClient()
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

# Connect to the remote device
client.connect(
    "192.168.10.11",
    username="admin",
    password="cisco",
    look_for_keys=False,
    allow_agent=False,
)

# Start an interactive shell
ssh_client = client.invoke_shell()
print("=====>>  Creating loopback interfaces <<=====")

# Enter privileged EXEC mode
ssh_client.send("enable\n")
ssh_client.send("cisco\n")
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
print("### Done ###")
```

This advanced example demonstrates the flexibility of Paramiko for configuring network devices programmatically. The script showcases the creation of loopback interfaces, providing a practical illustration of how automation can simplify repetitive tasks.

### Connecting to Multiple Devices

Expanding our horizons, the following example demonstrates using a `for` loop to connect to multiple devices sequentially.

```python
import paramiko
import time

client = paramiko.SSHClient()
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

# For loop and range() function to connect to multiple devices
for device in range(11, 13):
    ip = "192.168.10." + str(device)
    print("\n##### Connecting to the device " + ip + " #####")

    client.connect(
        ip, username="admin", password="cisco", look_for_keys=False, allow_agent=False
    )

    ssh_client = client.invoke_shell()
    ssh_client.send("enable\n")
    ssh_client.send("cisco\n")
    ssh_client.send("show ip int brief\n")
    time.sleep(3)
    output = ssh_client.recv(65000)
    print(output.decode("ascii"))
    client.close()
print("### Done ###")
```

This script demonstrates the scalability of Paramiko, allowing network engineers to connect and interact with multiple devices seamlessly.

### Connecting to Multiple Devices with a List

In this example, we use a `for` loop and a list to connect to multiple devices. This approach provides greater flexibility and ease of maintenance.

```python
import paramiko
import time

username = "admin"  # username
password = "cisco"  # password

# IP list for network devices
devices = ["192.168.10.11", "192.168.10.12"]

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

    ssh_client.send("enable\n")
    ssh_client.send("cisco\n")
    ssh_client.send("config t\n")

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

In conclusion, the Paramiko library in conjunction with Python empowers network engineers to automate and streamline network operations efficiently. Whether establishing secure connections, configuring interfaces, or managing multiple devices, Paramiko proves to be a valuable tool in the network automation arsenal.

As networks evolve, the role of automation becomes increasingly pivotal. The examples provided serve as a foundation for creating customized automation workflows tailored to specific network requirements. Embrace the power of Paramiko and Python to adapt and thrive in the dynamic landscape of network management.
