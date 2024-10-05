---
description: >-
  Use these OpenVPN3 aliases to easily list, start, stop, and restart VPN
  sessions from the terminal, simplifying VPN management with quick commands.
---

# Useful Shortcuts for VPN with OpenVPN3

Here are some useful terminal aliases for managing VPN connections with OpenVPN3, allowing you to list, start, stop, and restart VPN sessions more efficiently.

#### **Aliases**

1.  **List Active VPN Sessions**:

    ```bash
    openvpn3 sessions-list
    ```

    This command lists all currently active VPN sessions.\

2.  **Start VPN Session**:

    ```bash
    openvpn3 session-manage --cleanup ; vpn-stop ; openvpn3 session-start --config {FileConfig}
    ```

    This alias cleans up previous sessions, stops any running VPN connections, and starts a new VPN session using the specified configuration file (`{FileConfig}`).\

3.  **Stop All VPN Sessions**:

    ```bash
    openvpn3 sessions-list | grep "Path" | awk '\''{print $2}'\'' | xargs -I {} openvpn3 session-manage --disconnect --path {}
    ```

    This command stops all active VPN sessions by listing the session paths and disconnecting each one.\

4.  **Restart VPN Session**:

    ```bash
    openvpn3 session-manage --config {FileConfig} --restart
    ```

    Restarts the VPN session using the specified configuration file (`{FileConfig}`).

#### Command Descriptions

* **`openvpn3 session-manage --cleanup`**:\
  Cleans up any stale or invalid VPN sessions that might be lingering from previous connections, helping to ensure a clean start.
* **`grep "Path" | awk '{print $2}'`**:\
  Extracts the path of each active VPN session by filtering the output of `openvpn3 sessions-list` for the "Path" field and using `awk` to isolate the path value.
* **`xargs -I {} openvpn3 session-manage --disconnect --path {}`**:\
  For each session path retrieved, this command disconnects the active VPN session by passing the path to `openvpn3 session-manage --disconnect`.



### Adding VPN Aliases to Your Shell Configuration

You can add these aliases to your shell configuration file, such as `.bashrc` (for Bash users) or `.zshrc` (for Zsh users).

**Add the VPN Aliases**: Copy and paste the following aliases into the file:

```bash
alias vpn-list='openvpn3 sessions-list'
alias vpn-start='openvpn3 session-manage --cleanup ; vpn-stop ; openvpn3 session-start --config {FileConfig}'
alias vpn-stop='openvpn3 sessions-list | grep "Path" | awk '\''{print $2}'\'' | xargs -I {} openvpn3 session-manage --disconnect --path {}'
alias vpn-restart='openvpn3 session-manage --config {FileConfig} --restart'
```

Replace `{FileConfig}` with the actual path to your VPN configuration file.\
