# TelegramWrt

<img src="https://raw.githubusercontent.com/ilblogdicristiangallo/TelegraWrt/main/logo_telegramwrt.jpg" alt="TelegramWrt OpenWRT Logo" width="400">

TelegramWrt is a modular package for OpenWrt that integrates a Telegram bot with advanced diagnostics, monitoring, and remote control capabilities. Each plugin is designed to be extensible, reproducible, and compatible across multiple architectures.

## 📦 Requirements

Before using TelegramWrt, make sure the following packages are installed:
<pre>
opkg update
opkg install wget
opkg install jq
opkg install curl
opkg install bash
</pre>

⚙️ Initial Configuration
After installation, configure the bot by editing the file:
<pre>vi /usr/lib/TelegramWrt/config
</pre>

Insert your TOKEN and CHATID:

<pre>TOKEN="123456789:ABCdefGhIjKlMnOpQrStUvWxYz"
CHATID="987654321"
</pre>

# 🔐 The TOKEN is generated via BotFather on Telegram. The CHATID can be retrieved by sending a message to the bot and reading the response via logging or diagnostic plugins.

# 🚀 Installation
Install the .ipk package with:
<pre>opkg install /tmp/telegramwrt_1.0.1_all.ipk
</pre>

The package installs the bot and all plugins under /usr/lib/TelegramWrt/.

🧩 Supported Telegram Commands
TelegramWrt includes the following modules, each triggered via a Telegram command:

<markdown-accessiblity-table data-catalyst="">
<table border="1">
  <thead>
    <tr>
      <th>Telegram Command</th>
      <th>Function</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>/ssh_status</td><td>Check if SSH is active and which port is used</td></tr>
    <tr><td>/open_ports</td><td>List open ports and active services</td></tr>
    <tr><td>/firewall_rules</td><td>Show current firewall rules</td></tr>
    <tr><td>/block_ip</td><td>Block a specific IP address</td></tr>
    <tr><td>/mac_watch</td><td>Alert if unknown MAC addresses connect</td></tr>
    <tr><td>/vpn_status</td><td>Show VPN connection status</td></tr>
    <tr><td>/devices</td><td>List connected devices via DHCP and Wi-Fi</td></tr>
    <tr><td>/wifi_status</td><td>Show wireless interface status</td></tr>
    <tr><td>/wan_ip</td><td>Display public IP and gateway</td></tr>
    <tr><td>/ping_sweep</td><td>Scan subnet for active IPs (confirmation required)</td></tr>
    <tr><td>/ping_test</td><td>Run a ping test to an external host</td></tr>
    <tr><td>/dns_status</td><td>Show current DNS configuration</td></tr>
    <tr><td>/dhcp_leases</td><td>List active DHCP leases</td></tr>
    <tr><td>/status</td><td>Show bot status and connection</td></tr>
    <tr><td>/uptime</td><td>Display router uptime</td></tr>
    <tr><td>/cpu_load</td><td>Show CPU load and temperature</td></tr>
    <tr><td>/ram_usage</td><td>Display memory usage</td></tr>
    <tr><td>/disk_space</td><td>Show available disk space</td></tr>
    <tr><td>/log_tail</td><td>Show last system log entries</td></tr>
    <tr><td>/reboot</td><td>Reboot the router</td></tr>
    <tr><td>/restart_bot</td><td>Restart the Telegram bot</td></tr>
    <tr><td>/update_bot</td><td>Update bot script from remote source</td></tr>
    <tr><td>/backup_config</td><td>Backup OpenWrt configuration</td></tr>
    <tr><td>/restore_config</td><td>Restore configuration from backup</td></tr>
    <tr><td>/start</td><td>Show this command list</td></tr>
    <tr><td>/help</td><td>Extended command descriptions</td></tr>
    <tr><td>/opkg_installed</td><td>List installed packages (names only)</td></tr>
    <tr><td>/opkg_update</td><td>Update package repositories</td></tr>
    <tr><td>/opkg_install</td><td>Install a package from repository by name</td></tr>
    <tr><td>/opkg_remove</td><td>Remove an installed package by name</td></tr>
  </tbody>
</table>
</markdown-accessiblity-table>


# 📤 Usage Example

Once configured, send a command to the bot:
<pre>/status
</pre>

# 🔁 Automatic Bot Startup

To ensure that TelegramWrt starts automatically every time your OpenWrt device reboots, add the following command to the rc.local file:
<pre>bash /usr/lib/TelegramWrt/telegram.sh &
</pre>

# 📌 Steps:

Open the rc.local file with a text editor:

<pre>vi /etc/rc.local</pre>

Insert the command before the line exit 0:

<pre>bash /usr/lib/TelegramWrt/telegram.sh &</pre>

Save and exit (ctrt+c, then :wq!).

# ✅ The & symbol is essential: it runs the bot in the background, preventing it from blocking the boot process.

# 🖥️ Installing TelegramWrt with WinSCP
WinSCP is a Windows SFTP client that allows easy file transfers between your PC and OpenWrt router using a graphical interface.

# Requirements
OpenWrt router with SSH access enabled

WinSCP installed on your PC: Download WinSCP

telegramwrt_1.0.0_all.ipk file saved on your computer

# 📌 Steps
Launch WinSCP and create a new connection:

Protocol: SCP or SFTP

Host name: Router IP (e.g., 192.168.1.1)

Username: root

Password: (your router password)

Connect and navigate to the /tmp directory on the router.

Drag and drop the telegramwrt_1.0.1_all.ipk file from your PC into the router’s /tmp folder.

Open a terminal session directly from WinSCP (menu “Commands” → “Open Terminal”) or use PuTTY.

Install the package with the command:

<pre>opkg install /tmp/telegramwrt_1.0.1_all.ipk
</pre>

# Screen use TelegramWrt_V1.0.1

<img src="https://github.com/ilblogdicristiangallo/TelegramWrt/blob/main/telegram_screen_1.01.png?raw=true" 
     alt="TelegramWrt bot interface screenshot" 
     width="600" />

<img src="https://github.com/ilblogdicristiangallo/TelegramWrt/blob/main/telegram_screen_1.01_2.png?raw=true" 
     alt="TelegramWrt bot interface second screenshot" 
     width="600" />

