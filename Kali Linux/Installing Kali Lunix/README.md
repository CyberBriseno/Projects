# Installing Kali Linux

This project provides step-by-step instructions for setting up a Docker environment on a Kali Linux VM. Screenshots are provided for clarity.

## Table of Contents

- [Downloading Hyper-V](#downloading-hyper-v)
- [Downloading Kali](#downloading-kali)
- [Installing the VM](#installing-the-vm)
- [Setting up Kali](#setting-up-kali)
- [Configuring Kali](#configuring-kali)
- [Installing Docker](#installing-docker)

## Step 1: Downloading Hyper-V

If Hyper-V is not already enabled on your Windows machine:

1. **Open Control Panel**:
   - Press the Windows key, type "Control Panel," and hit Enter.

2. **Navigate to Programs**:
   - Click on **Programs**.

3. **Turn Windows features on or off**:
   - Under **Programs and Features**, click on **Turn Windows features on or off**.

4. **Enable Hyper-V**:
   - Scroll down and check the box for **Hyper-V**.
   - Ensure that **Hyper-V Management Tools** and **Hyper-V Platform** are both checked.

5. **Apply Changes and Restart**:
   - Click **OK** and wait for the features to be installed.
   - Restart your computer to apply the changes.

![Download Hyper-V](./screenshots/1.%20Downloading%20Hyper-V/)

## Step 2: Downloading Kali Linux ISO

Before creating a VM, you need to download the Kali Linux ISO.

1. **Visit Kali Linux Download**:
    - Click this link to go to the [Kali Linux Downloads](https://www.kali.org/get-kali/#kali-installer-images) page.

2. **Choose Installer Images**:
    - The Installer Image should be the first box presented.

3. **Download NetInstaller 64bit**:
    - Ensure you verify the hash once the download is complete.

![Download Kali Linux ISO](./screenshots/2.%20Downloading%20Kali/)

## Step 3: Installing the VM

1. **Connect to Local Machine**:
    - In Windows search, type "Hyper-V Manager" and hit Enter.
    - When the window pops up, right-click "Hyper-V Manager."
    - Click **Connect to Server**.
    - Click the radio button that states "Local computer."

2. **Create VM**:
    - Right-click your local computer name.
    - Highlight **New** and click **Virtual Machine**.

3. **VM Configurations**:
    - Name: Your choice.
    - Generation: **Generation 2**.
    - Memory: **2GB minimum** (Uncheck Dynamic Memory).
    - Connection: **Default Switch**.
    - Virtual Disk: Create new, designate path, name file, designate size.
    - Install OS from the ISO file you downloaded.
    - Click **Finish**.

4. **VM Settings**:
    - Right-click your VM and select **Settings**.
    - Select **Firmware** and ensure DVD Drive is first and Hard Drive is second.
    - Select **Security** and uncheck **Enable Secure Boot**.
    - Click **Apply** and **OK**.

5. **Start VM**:
    - Right-click the VM.
    - Click **Connect...**.
    - Click **Start**.

![Install VM](./screenshots/3.%20Installing%20VM/)

## Step 4: Setting up Kali

1. **Setup Kali**:
    - Use your mouse and keyboard to navigate and press Enter to select highlighted options.
    - Select **Install**.
    - Follow the prompts (if you need detailed walk-through, use screenshots linked below).
    - Partition disks using **Guided - use entire disk**.
    - Select **All files in one partition**.
    - Select **Finish Partitioning and write changes to disk**.
    - Navigate and select **<Yes>**.
    - Skip proxy setup unless needed.
    - Use TAB to highlight **<Continue>** and press Enter to launch Kali.

![Setting up Kali](./screenshots/4.%20Setting%20up%20Kali/)

## Step 5: Configuring Kali

1. **Open Terminal**.
2. **Type and run the following command**:
    ```bash
    sudo apt update && sudo apt upgrade -y && sudo apt dist-upgrade -y && sudo apt autoremove -y && sudo apt clean
    ```
![Configuring Kali](./screenshots/5.%20Configuring%20Kali/)
