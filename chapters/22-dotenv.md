# Simplifying Network Automation with Python dotenv

In today's network engineering world, automation is incredibly important. It helps make tasks smoother, faster, and more efficient. Python has become a top choice for automating network tasks due to its versatility and extensive range of libraries. However, handling sensitive information like passwords and special keys securely within automation scripts can be challenging for newcomers. In this blog, we'll delve into how Python dotenv simplifies this process, making network automation safer and more manageable.

## Understanding Python-dotenv

Python-dotenv is a popular library that simplifies the management of environment variables in Python applications. It allows you to store configuration settings in a `.env` file and easily load them into your script. This means you can keep sensitive information out of your source code and version control, reducing the risk of exposure.

## Key Benefits of Python-dotenv

- Follows 12-factor principles: Python-dotenv adheres to the 12-factor principles for building scalable and maintainable applications, ensuring consistency and reliability.
- Simplifies development and testing: By enabling the use of different `.env` files for specific environments (e.g., development, production), Python-dotenv streamlines the development and testing process.
- Supports various formats: It supports variable expansion, multiline values, and comments in the `.env` file format, providing flexibility and ease of use.
- Cross-platform compatibility: Python-dotenv is compatible with any system, allowing for seamless integration across different environments.
- Integration with other Python libraries: It integrates well with other Python libraries and frameworks, such as Flask, Django, and IPython, enhancing its versatility and utility.

## Getting Started with Python-dotenv

To begin using Python-dotenv in your projects, you'll first need to install it via `pip`:

```bash
pip install python-dotenv
```

Once installed, you can create a `.env` file in the root directory of your project to store your environment variables. Here's an example of what a `.env` file might look like:

```bash
DB_USER=admin
DB_PASS=cisco123
```

Remember, each line in the `.env` file represents a single environment variable, with the key and value separated by an equals sign `=`. It's essential to keep your `.env` file secure and out of version control by adding it to your `.gitignore` file.

## Using Python-dotenv in Your Scripts

With the `.env` file in place, you can load the environment variables into your Python script using Python-dotenv. Here's how you can do it:

```python
import os
from dotenv import load_dotenv

# Load environment variables from .env file
load_dotenv()

# Access environment variables
db_user = os.getenv("DB_USER")
db_password = os.getenv("DB_PASS")
```

By using `os.getenv()`, you can retrieve the values of your environment variables within your script securely.

You can use comments in your `.env` file by prefixing a line with the pound (`#`) character. Comments are ignored by `python-dotenv` when it loads the environment variables from the file. Here's an example of how to use comments in your `.env` file:

```bash
# Database Credentials
DB_HOST=localhost
DB_PORT=5432
DB_USER=myuser
DB_PASSWORD=mypassword

# API configuration
API_SECRET=0987654321fedcba
```

Alternatively, we can use `os.environ.get()` from `os` module to access environment variables directly without `python-dotenv`. This approach is useful when we want to avoid an extra dependency.

### Python Automation Script

Now, let's create a Python script to automate the backup process using the environment variables from the `.env` file:

```python
# Import necessary modules
import os
import paramiko
from dotenv import load_dotenv

# Load environment variables from .env file
load_dotenv()

# Function to connect to device and retrieve configuration
def backup_config():
    # Get environment variables
    device_ip = os.getenv("DEVICE_IP")
    ssh_username = os.getenv("SSH_USERNAME")
    ssh_password = os.getenv("SSH_PASSWORD")

    # Connect to the device
    ssh_client = paramiko.SSHClient()
    ssh_client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    ssh_client.connect(hostname=device_ip, username=ssh_username, password=ssh_password)

    # Execute command to retrieve configuration
    stdin, stdout, stderr = ssh_client.exec_command("show running-config")
    config = stdout.read().decode()

    # Save configuration to a file
    with open(f"{device_ip}_config.txt", "w") as file:
        file.write(config)

    # Close SSH connection
    ssh_client.close()
    print(f"Configuration backup for {device_ip} completed.")

# Execute the backup_config function
if __name__ == "__main__":
    backup_config()
```

When you run this script, it will load the environment variables from the `.env` file and use them to connect to the device via SSH. It will then retrieve the running configuration and save it to a file named after the device's IP address.

By using `python-dotenv`, you can keep your credentials and device information secure in the `.env` file, separate from your codebase. This makes it easier to manage configurations and ensures that sensitive information is not exposed in your scripts.
