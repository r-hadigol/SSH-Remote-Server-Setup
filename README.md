# SSH Remote Server Setup Project
[https://roadmap.sh/projects/ssh-remote-server-setup
](https://roadmap.sh/projects/static-site-server)
https://roadmap.sh/projects/basic-dns
## Project Goal

Learn how to set up and connect to a Linux server via SSH, configure basic security, and understand remote server management.

## Steps to Complete the Project

### 1. Set up a Linux server

* For local testing, use a Linux virtual machine (e.g., Ubuntu) in VirtualBox or VMware.
* The VM will act as the remote server.

### 2. Generate SSH keys on your local machine

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

* This creates a public key (`id_rsa.pub`) and a private key (`id_rsa`).
* Keep the private key safe and **never push it to GitHub**.

### 3. Add your public key to the remote server

* On the server VM, create the `.ssh` directory if it doesn’t exist:

```
mkdir -p ~/.ssh
chmod 700 ~/.ssh
```

* Add your public key to `authorized_keys`:

```
nano ~/.ssh/authorized_keys
# paste your public key here
chmod 600 ~/.ssh/authorized_keys
```

### 4. Test SSH connection from your local machine

```
ssh -i ~/.ssh/id_rsa user@server-ip
```

* Replace `user` with the server username and `server-ip` with the VM’s IP.

### 5. Optional: Configure `~/.ssh/config` for easier access

```
Host myserver
    HostName 192.168.x.x
    User your-username
    IdentityFile ~/.ssh/id_rsa
```

* Then you can simply connect with:

```
ssh myserver
```

### 6. Install `fail2ban` for security

* Install and enable fail2ban to protect against brute-force attacks:

```
sudo apt update
sudo apt install fail2ban
sudo systemctl enable --now fail2ban
```

### 7. Security Notes

* **Never push your private key** or any sensitive data to a public repository.
* Only this README.md should be uploaded to GitHub.

### 8. Outcome

* Successfully connected to a Linux server via SSH.
* Configured basic security and key-based authentication.
* Documented all steps in this REA
