# Node Pi Network On Linux
**How to Install and Run Pi Node on Linux?**</br>
Here is a detailed and professional guide to installing and running Pi Node on Linux system, based on the official documentation from Pi Network. This guide includes steps to set up a new node, upgrade an existing node, and important notes. I will present it in a clear structure, with code commands formatted for easy copy and implementation.</br>
# Note before starting
* Information from the Pi Network Core Team: <a href="minepi.com/blog/pi-linux-node">minepi.com/blog/pi-linux-node</a></br>
* Installation Guide <a href="minepi.com/pi-blockchain/pi-node/linux/">minepi.com/pi-blockchain/pi-node/linux</a></br>
* How can I link my Linux node to my Pi account and get node rewards?</br>
Linking a Linux node to a Pi account is not currently supported, which is why it is not directly linked to node rewards.</br>
* How can I get Pi Desktop for my Linux node?</br>
Node Linux does not have a Pi Desktop, only nodes. Account linking, Pi Desktop, and port checking will be added in future Linux releases.</br>
* Can I use an existing Node private key when setting up a Linux node?</br>
The Linux installer allows reusing an existing Linux node private key when upgrading or setting up a replacement Linux node. Windows/macOS node private keys cannot be reused on Linux.</br>
* Can I move an existing node to another computer?</br>
The Pi Core team recommends against copying your node configuration and recommends keeping all Docker settings at default. Do a fresh install and follow the Core Team’s official instructions.</br>
* What Linux distributions can be used for a Pi Node?</br>
Linux nodes can run on many distributions. Most Debian-based distributions will work. For starters, Ubuntu LTS or LMDE is recommended.</br>
* Can I run both a Windows/macOS node and a Linux node?</br>
Pi policy only allows 1 node per Pi account. As long as the Linux node is not connected to your account, you can run both a Windows/macOS node (connected to your account) and a Linux node (unconnected).</br>
* Are Pioneer nodes connected to testnet or mainnet?</br>
Windows/macOS Pioneer nodes are currently running on testnet2, while new Linux nodes run on mainnet.</br>
# System Requirements
* 8 CPU Cores
* 16 GB RAM
* 120 GB Disk Space
* Get started with a low-budget VPS for as low as $8! <a href="https://hetzner.cloud/?ref=HzbJgr48g79y">Purchase here</a>

# Prerequisites
* Linux operating system (Ubuntu 20.04 LTS or later recommended).</br>
* Docker and Docker Compose v2 should already be installed. If not, run the following commands to install Docker:</br>
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl start docker
sudo systemctl enable docker
```
# Set Up New Nodes
**Step 1: Install Prerequisite Packages**
```
sudo apt-get update
sudo apt-get install -y ca-certificates curl gnupg
```
**Step 2: Add the Repository GPG Key**
```
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://apt.minepi.com/repository.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/pinetwork-archive-keyring.gpg
sudo chmod a+r /etc/apt/keyrings/pinetwork-archive-keyring.gpg
```
**Step 3: Add the APT Source**
```
echo 'deb [arch=amd64 signed-by=/etc/apt/keyrings/pinetwork-archive-keyring.gpg] https://apt.minepi.com stable main' | sudo tee /etc/apt/sources.list.d/pinetwork.list > /dev/null
sudo apt-get update
```
**Step 4: Install the Pi Node Package**
```
sudo apt-get install -y pi-node
pi-node --version
pi-node --help
```
**Step 5: Initialize Pi Node**
```
pi-node initialize
```
* For additional information: pi-node initialize --help.
* During initialization, you’ll be prompted for options such as the storage directory, PostgreSQL password, and NODE_SEED (if applicable).

**About Auto-Update**

* Auto-update will automatically upgrade your Mainnet node to the latest version upon release, including necessary migrations (which may take hours).
* If you prefer manual control, disable auto-update and use the `pi-node updateNode` command for updates.
* Recommendation: Enable auto-update for individual users; disable it for partners or those needing greater control.

**After initialization, the node will start running. Use these commands to manage it:**

* Check status: `pi-node status`
* View logs: `docker compose -f "$HOME/pi-node/docker-compose.yml" logs -f`
* Restart: `docker compose -f "$HOME/pi-node/docker-compose.yml" restart`
* Stop: `docker compose -f "$HOME/pi-node/docker-compose.yml" down`
* Go to <a href="https://piscan.io/nodes">https://piscan.io/nodes</a> CTRL+F = IP address running node =>> Status: `Connected` ==>> Done

# Important Notes

* Security: The NODE_SEED is your node’s private key. Never share or store it publicly.
* Common Issues: If you encounter permission errors, check directory permissions with chmod or run with sudo. Ensure Docker is running.
* Updates and Maintenance: Monitor updates from Pi Network. Use auto-update for automation, but check logs periodically.
* Support: For issues, refer to the official documentation at <a href="https://minepi.com/pi-blockchain/pi-node/linux/">https://minepi.com/pi-blockchain/pi-node/linux/</a> or the Pi Network community forums.
* Environment: This guide is for amd64 architecture. For arm64 (e.g., Raspberry Pi), check for separate compatibility instructions.

If you encounter specific errors or need clarification on any step, provide more details, and I’ll assist further! Telegram: <a href="https://t.me/@thuanit">@Thuanit</a>
