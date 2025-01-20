# Securing Kali Linux in Windows

This guide provides concise, methodical instructions for safeguarding your Kali Linux VM running on Windows. Follow each step meticulously to fortify your environment and ensure optimal protection.

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

- Open Terminal in Kali.
- Type: 
    - ```sudo apt update && sudo apt upgrade -y && sudo apt dist-upgrade -y```
- Clean up redundant packages: 
    - ``` sudo apt autoremove -y && sudo apt clean```
- Reboot the VM to finalize updates.

## Step 2: Configure a Firewall

- Install ufw (Uncomplicated Firewall): 
    - ```sudo apt install ufw -y```
- Enable and configure basic rules: 
    - ```sudo ufw default deny incoming```
    - ```sudo ufw default allow outgoing```
    - ```sudo ufw enable```
- (Optional) Customize rules for specific services (e.g., SSH:
    - ```sudo ufw allow ssh```

## Step 3: Strengthen SSH

- Edit SSH configuration: 
    - sudo nano /etc/ssh/sshd_config
- Disable root login and password authentication:
    - PermitRootLogin no 
    - PasswordAuthentication no
- Use key-based authentication whenever feasible:
- Generate a key pair on your local machine with ssh-keygen.
- Copy the public key to the VM using ssh-copy-id.
- Restart SSH: 
    - ```sudo systemctl restart ssh```

## Step 4: Install Intrusion Detection Tools

- Consider installing fail2ban: 
    - ```sudo apt install fail2ban -y```
- Configure fail2ban:
    - ```sudo nano /etc/fail2ban/jail.conf``` to tailor settings (like bantime, maxretry).
- Restart fail2ban: 
    - ```sudo systemctl restart fail2ban```
- (Optional) Incorporate IDS/IPS solutions such as Snort or Suricata.

## Step 5: Minimize the Attack Surface

- Uninstall or disable unnecessary services:
    - Identify running services with systemctl --type=service.
- Stop and disable any superfluous ones.
- Use strong passwords or key-based authentication for all accounts.
- Keep software packages and Kali tools updated:
    - Routinely check for new updates and apply security patches.
- Implement secure permissions on sensitive files: chmod 600 for confidential configs containing private keys or credentials.
