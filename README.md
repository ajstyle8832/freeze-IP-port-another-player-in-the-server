# Tracing Server IP and Ports for BGMI on Android Using Termux

This tutorial explains how to trace the running server IP and ports for the BGMI (Battle Grounds Mobile India) game on an Android device using Termux. Additionally, we'll cover the method to freeze the IP port for another player, emphasizing that such actions may violate the game's terms of service and could potentially lead to a ban. The instructions provided are for educational purposes only.

## Prerequisites

- Android device
- Termux app (available on Google Play Store)

## Steps

### Step 1: Install Termux

First, download and install Termux from the Google Play Store if it's not already installed.

### Step 2: Update the Package List

Open Termux and update your package list to ensure you have the latest versions of available packages.

```bash
pkg update
```

### Step 3: Install Required Packages

Install `net-tools` and `nmap`, which are essential for scanning open ports and managing network configurations.

```bash
pkg install net-tools nmap
```

### Step 4: Find the Game Server IP

We'll use `nmap` to identify open ports on your device associated with BGMI. Since `netstat` is not available by default in Termux, this part can be executed on a Linux machine if necessary.

1. **Scan for Open Ports:**

    ```bash
    nmap -sS -O localhost
    ```

    Identify the ports associated with the BGMI game (commonly ports like 27015, 27016, etc.).

2. **Finding the IP Address:**

    On a Linux machine, use `netstat` to locate the IP address related to the ports:

    ```bash
    netstat -nlp | grep <port_number>
    ```

    Replace `<port_number>` with the port numbers identified previously.

### Step 5: Freeze the IP Port (Optional)

**Note:** This step requires a rooted Android device with custom kernel support for `iptables`.

1. **Allow Incoming Traffic on the Port:**

    ```bash
    iptables -A INPUT -p tcp --dport <port_number> -j ACCEPT
    ```

2. **Block Outgoing Traffic on the Port:**

    ```bash
    iptables -A OUTPUT -p tcp --dport <port_number> -j DROP
    ```

    Replace `<port_number>` with the appropriate port number.

## Disclaimer

The techniques described in this tutorial could be against the Terms of Service of the BGMI game. Using these methods for freezing IP ports or interfering with other players is strongly discouraged and could lead to penalties such as account bans. All information provided here is for educational purposes only.

## Conclusion

This guide provided a walkthrough for tracing server IPs and ports for BGMI on Android using Termux, as well as instructions for potentially freezing an IP port. Remember, it is crucial to respect game rules and not engage in activities that disrupt the gameplay for others. Always use technology ethically and responsibly.
```

This README file provides a step-by-step guide on tracing and potentially interacting with server IP and ports for the BGMI game using Termux on Android devices. It emphasizes responsible use and adherence to game terms of service.
