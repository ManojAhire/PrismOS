# PrismOS Installer

![Apple Silicon](https://img.shields.io/badge/Apple%20Silicon-M1%2C%20M2%2C%20M3%2C%20M4-black)

The PrismOS Installer is a community-driven project that extends the groundbreaking work of **Asahi Linux** to bring full-featured Linux distributions to the very latest Apple Silicon hardware, including the M1, M2, M3, and M4 families.

---

### Standing on the Shoulders of Giants

> This project would be entirely impossible without the monumental reverse-engineering efforts of the **Asahi Linux team**, led by Hector Martin (@marcan) and many other talented developers.
>
> **PrismOS is not a fork.** It is an extension of the official Asahi installer, modified to recognize the latest hardware identifiers before they are officially supported. All credit for the core technology—the `m1n1` bootloader, the custom kernel, the drivers, and the ingenious installation strategy—belongs entirely to the Asahi Linux project.
>
> We are immensely grateful for their open-source philosophy. We strongly encourage you to follow and **[support the official Asahi Linux project](https://asahilinux.org/support/)**.

---

## ✨ Features

-   **Broad Hardware Support**: Provides an installation path for all Apple Silicon chips, from **M1 to M4**.
-   **User-Friendly**: A simple, one-line command kicks off a guided command-line interface.
-   **Safe & Non-Destructive**: Installs alongside macOS without removing it. The installer safely resizes your existing macOS partition.
-   **Firmware Extraction**: Automatically extracts the necessary firmware from your macOS installation to make hardware like Wi-Fi and Bluetooth work correctly.

## ⚙️ How It Works

Installing Linux on Apple Silicon is a complex, two-stage process that the installer automates.

### Stage 1: The macOS Installer

The first stage runs entirely within your existing macOS environment.

1.  **Bootstrap**: The initial `curl` command downloads a bootstrap script.
2.  **Download & Extract**: The bootstrap script downloads the main Python installer application and extracts it to a temporary directory.
3.  **System Analysis**: The Python app starts and gathers information about your Mac, including its Chip ID and Device Class, to ensure it's compatible.
4.  **Partitioning**: It guides you through resizing your main macOS APFS container to free up space.
5.  **Stub OS Creation**: The installer creates a new, minimal "stub" macOS installation in the free space. This stub OS acts as a custom bootloader environment.
6.  **Blessing**: It "blesses" the stub OS, setting it as the default boot volume for the *next* boot only.
7.  **Reboot Prompt**: The installer then instructs you to shut down and boot into the Startup Options menu.

### Stage 2: The Recovery Environment

The second stage finalizes the security setup from within the special stub OS recovery mode.
<img width="1730" height="705" alt="flow" src="https://github.com/user-attachments/assets/68b81784-063e-4813-b471-5ccffd4b7c7f" />
