# Securing Kali Linux in Windows

This guide is to walk you through on securing your Kali Linux machine.

## Table of Contents

- [Update and Upgrade System](#step-1-update-and-upgrade-system)
- [Configure a Firewall](#step-2-configure-a-firewall)
- [Strengthen SSH](#step-3-strengthen-ssh)
- [Install Intrusion Detection Tools](#step-4-install-intrusion-detection-tools)
- [Minimize the Attack Surface](#step-5-minimize-the-attack-surface)

## Prerequisites

**Active Kali Linux VM on Hyper-V**

**Administrative privileges on both Windows Host and Kali VM**

**Access to the Internet**


## Step 1: Update and Upgrade System

1. **Open Terminal** in Kali.
2. **Execute** the following command to refresh and upgrade all packages: 
    ```bash
    sudo apt update && sudo apt upgrade -y && sudo apt dist-upgrade -y
    ```
3. **Remove** redundant packages once upgrade completes: 
    ```bash
    sudo apt autoremove -y && sudo apt clean
    ```
4. **Reboot** the VM to finalize changes:
    ```bash 
    sudo reboot
    ```

## Step 2: Configure a Firewall

1. **Install UFW** (Uncomplicated Firewall) to manage inbound/outbound traffic: 
    ```bash
    sudo apt install ufw -y
    ```
2. **Set default rules** for incoming and outgoing connections: 
    ```bash
    sudo ufw default deny incoming
    sudo ufw default allow outgoing
    sudo ufw enable
    ```
3. *(Optional)* **Allow** services, such as SSH:
    ```bash
    sudo ufw allow ssh
    ```

## Step 3: Strengthen SSH

1. **Open** SSH configuration file: 
    ```bash
    sudo nano /etc/ssh/sshd_config
    ```
2. **Disable** root login and password authentication by editing these lines:
    ```bash
    PermitRootLogin no
    PasswordAuthentication no
    ```
3. **Use key-based authentication** to enhance scecurity:
    - Generate a key pair on your local machine:
    ```bash
    ssh-keygen.
    ```
    - Copy the public key to your Kali VM:
    ```bash
    ssh-copy-id.
    ```
4. **Restart SSH** to apply changes:
    ```bash
    sudo systemctl restart ssh
    ```

## Step 4: Install Intrusion Detection Tools

1. Consider installing fail2ban: 
    ```bash
    sudo apt install fail2ban -y
    ```
2. Configure fail2ban:
    ```sudo nano /etc/fail2ban/jail.conf``` to tailor settings (like bantime, maxretry).
3. Restart fail2ban: 
    - ```sudo systemctl restart fail2ban```
4. *(Optional)* Incorporate IDS/IPS solutions such as Snort or Suricata.

## Step 5: Minimize the Attack Surface

- Uninstall or disable unnecessary services:
    - Identify running services with systemctl --type=service.
- Stop and disable any superfluous ones.
- Use strong passwords or key-based authentication for all accounts.
- Keep software packages and Kali tools updated:
    - Routinely check for new updates and apply security patches.
- Implement secure permissions on sensitive files: chmod 600 for confidential configs containing private keys or credentials.
