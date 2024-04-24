# Netmiko Module

Netmiko is a multi-vendor library that simplifies SSH management to network devices, this library is based on the Paramiko SSH library. Netmiko supports a wide range of devices.

## What is Netmiko?

Netmiko simplifies SSH management to network devices. The purposes of this library are the following:

- Successfully establish an SSH connection to the device.
- Simplify the execution, retrieval, and formatting of show commands.
- Simplify the execution of configuration commands.
- Provide a (relatively) uniform API for interacting with devices.

To install netmiko simply use pip for installation.

```bash
pip install netmiko
```

Netmiko has the following requirements (which pip will install for you)

- Paramiko >= 2.4.3
- scp >= 0.13.2
- pyserial
- textfsm

Then import netmiko from the Python shell to make sure the module is correctly installed.

```python
[$] <> python3 
Python 3.8.10 (default, Mar 15 2022, 12:22:08) [GCC 9.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import netmiko
>>>
```
