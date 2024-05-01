# What is Napalm?

[NAPALM](https://napalm.readthedocs.io/en/latest/index.html) (Network Automation and Programmability Abstraction Layer with Multi-vendor support) is a Python library that implements a set of functions to interact with different network device Operating Systems using a unified API. It provides a unified interface, allowing the same code to configure multi-vendor devices.

## Supported Network Operating Systems

NAPALM is used to interact with various hardware networking vendors. It works as an API on top of other APIs, adding another level of abstraction. Here are some of the supported operating systems:

- Arista EOS
- Cisco IOS
- Cisco IOS-XR
- Cisco NX-OS
- Juniper JunOS

### How does NAPALM work?

NAPALM adds an abstraction layer that enables using the same function to perform the same action on different operating systems. Without this layer, programming across diverse network device OSs would be challenging.

### Installation

You can install Napalm with pip:

```bash
pip install napalm
```

### NAPALM CLI

NAPALM installation includes a CLI tool for direct usage. You can access the help menu with:

```bash
napalm --help
```

Here's an example of using NAPALM CLI to ping a device:

```bash
napalm --user admin --password cisco --vendor ios 192.168.10.10 call ping --method-kwargs "destination='192.168.10.10'"
```

### IOS Prerequisites

For IOS devices, Napalm uses the Netmiko library for interaction. Here are some prerequisites:

- Enable the archive functionality for auto-rollback.
- Ensure configuration files start with a version and end marker.
- Enable SCP for file transfers.

### Selecting the right driver

You can specify the OS you're communicating with, and NAPALM will select the correct NetworkDriver. Here's how to do it:

```python
from napalm import get_network_driver

driver = get_network_driver('ios')
```

### Programming samples

Here's a basic example of connecting to a device and retrieving facts:

```python
from napalm import get_network_driver

driver = get_network_driver('ios')
device = driver('192.168.10.11', 'admin', 'cisco') 
device.open()

output = device.get_facts()
print(output)

device.close()
```

And here's how you can retrieve interface information:

```python
import json
from napalm import get_network_driver

driver = get_network_driver('ios')
device = driver('192.168.10.10', 'admin', 'cisco')
device.open()

output = device.get_interfaces()
print(json.dumps(output, indent=4))

device.close()
```

### Configuration support Method

NAPALM offers various methods for configuration support, such as replace, merge, commit confirm, compare config, atomic changes, and rollback. You can find more details in the [official docs](https://napalm.readthedocs.io/en/latest/base.html).
