---
description: >-
  Use netstat -an | grep LISTEN to quickly check all open ports on your machine
  that are actively listening for connections.
---

# Checking Locally Open Ports

The command `netstat -an | grep LISTEN` is a quick and useful way to check all open ports on your machine that are currently in a "listening" state.

#### **Command Breakdown**

* **`netstat -an`**: Lists all network connections and listening ports, displaying the IP addresses and port numbers in numeric format.
* **`grep LISTEN`**: Filters the output to show only the ports that are actively in the "LISTEN" state, meaning they are open and waiting for connections.

**Example:**

```bash
netstat -an | grep LISTEN
```

**Output**: You'll see a list of IP addresses and port numbers, like this:

```textile
tcp        0      0 0.0.0.0:80            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22            0.0.0.0:*               LISTEN
```

This indicates that the machine is listening on ports 80 (HTTP) and 22 (SSH).
