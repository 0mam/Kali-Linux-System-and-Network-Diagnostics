# Kali Linux System and Network Diagnostics

This project documents practical exercises in **Governance, Risk and Compliance (GRC)**, focusing on Linux system identification, virtual machine resource assessment, and network connectivity testing. Using Kali Linux, the project explores system information, available memory and disk space, kernel version, network latency, packet loss, and the differences between pinging Google's DNS resolver and its website infrastructure.

## Table of Contents

- Project Overview
- Network Topology
- Tools and Technologies
- Configuration Steps
- Results and Findings
- Author

## Project Overview

The purpose of this project was to gain practical experience using Kali Linux terminal commands to inspect a Linux environment and assess basic network connectivity.

The key objectives were to:

- Identify the current Linux username, hostname, and working directory.
- Examine virtual machine memory and disk utilisation.
- Identify the installed Linux kernel version.
- Test network connectivity and measure round-trip time.
- Compare connectivity to Google's public DNS resolver and a Google website IP address.
- Understand how packet loss, latency, and network variability can inform basic troubleshooting.

These exercises provide foundational skills relevant to **cybersecurity, IT operations, network troubleshooting, and Governance, Risk and Compliance (GRC)**.

## Network Topology

The project used a Kali Linux virtual machine to perform local system checks and communicate with external Google network endpoints.

### Network Layout

```text
+----------------------------------+
|       Kali Linux Virtual Machine |
|                                  |
| Username: Kali                   |
| Hostname: Kali                   |
| Kernel: Linux 6.19.14            |
| RAM: Approximately 2 GB          |
|                                  |
| Network Diagnostic Commands      |
+----------------+-----------------+
                 |
                 | Internet Connection
                 |
          +------+------+
          |             |
          v             v
   +-------------+  +------------------+
   | Google DNS  |  | Google Website   |
   | Resolver    |  | IP Address       |
   | 8.8.8.8     |  | 74.125.193.139   |
   +-------------+  +------------------+
```

### System and Network Details

- **Operating system:** Kali Linux.
- **Username:** `Kali`.
- **Hostname:** `Kali`.
- **Working directory:** Home directory.
- **Kernel version:** Linux `6.19.14`.
- **Main disk partition:** `/dev/sda1`.
- **Total disk capacity:** 79 GB.
- **Available disk space:** 59 GB.
- **Disk space used:** 16 GB, approximately 21%.
- **Total RAM:** Approximately 1.9 GiB.
- **Google public DNS resolver:** `8.8.8.8`.
- **Google website IP address:** `74.125.193.139`.
- **Resolved hostname:** `di-in-f139.1e100.net`.

The submitted results do not specify the virtualisation platform, network adapter configuration, subnet, or local IP address.

## Tools and Technologies

- **Kali Linux:** Linux environment used for system and network diagnostic exercises.
- **Linux Terminal:** Command-line interface for executing diagnostic commands.
- **Linux system utilities:** Used to inspect system resources, operating system details, and kernel information.
- **Ping (`ping`):** Used to test IP connectivity and measure round-trip time.
- **Google Public DNS (`8.8.8.8`):** Used as a network connectivity and latency test destination.
- **DNS resolution:** Used to identify the IP address associated with `google.com`.
- **Virtual Machine (VM):** Environment providing approximately 2 GB of RAM and 79 GB of disk capacity.
- **ICMP (Internet Control Message Protocol):** Protocol used by ping to send echo requests and receive echo replies.

## Configuration Steps

1. **Access the Kali Linux environment**

   Open the Kali Linux virtual machine and access the terminal.

2. **Identify the current user and hostname**

   Check the terminal output to establish the current username, machine hostname, and working directory.

   - Username: `Kali`
   - Hostname: `Kali`
   - Working directory: Home directory

3. **Inspect system resources**

   Review the terminal output for memory and disk utilisation.

   Record the total RAM, total disk capacity, available disk space, and percentage of disk space used.

4. **Identify the Linux kernel version**

   Examine the system information output to identify the installed kernel version.

   - Kernel version: `Linux 6.19.14`

5. **Test network connectivity**

   Use the `ping` command to send ICMP echo requests to an external destination and examine the response times and packet loss.

6. **Test connectivity to Google's public DNS resolver**

   Ping `8.8.8.8` and record the reported round-trip time and packet loss.

   The submitted results indicate an average round-trip time of 17.293 milliseconds and no packet loss across two packets.

7. **Resolve and test Google's website address**

   Use the hostname `google.com` as a network test destination and review the resolved IP address and ping statistics.

   - Resolved IP address: `74.125.193.139`
   - Resolved hostname: `di-in-f139.1e100.net`
   - Minimum round-trip time: 40.4 ms
   - Average round-trip time: 73.8 ms
   - Maximum round-trip time: 133.6 ms
   - Mean deviation: Approximately 37 ms

8. **Compare network performance**

   Compare the results for `8.8.8.8` and `google.com` to understand differences in response time and consistency.

   Consider how routing, network congestion, the destination selected by DNS, and Google's distributed infrastructure may affect the results.

9. **Understand the ping count option**

   Review the `-c 4` option, which instructs `ping` to send exactly four ICMP echo requests before stopping.

   Example:

   ```bash
   ping -c 4 google.com
   ```

   This provides a finite set of responses for reviewing connectivity, packet loss, and round-trip time.

## Results and Findings

The exercises provided practical evidence of the Kali Linux system's configuration and its ability to communicate with external network destinations.

### System Resource Assessment

- The virtual machine had approximately **1.9 GiB of RAM**, equivalent to roughly 2 GB.
- The main partition, `/dev/sda1`, had a total capacity of 79 GB.
- Approximately 59 GB of disk space was available.
- Approximately 16 GB of disk space was used, representing around 21% utilisation.
- The installed Linux kernel was version `6.19.14`.

These findings provide a basic picture of the resources available to the virtual machine.

### Network Connectivity Results

| Metric | Google DNS (`8.8.8.8`) | Google Website IP (`74.125.193.139`) |
|---|---:|---:|
| Average round-trip time | 17.293 ms | 73.8 ms |
| Minimum round-trip time | Not specified in the recorded summary | 40.4 ms |
| Maximum round-trip time | Not specified in the recorded summary | 133.6 ms |
| Packet loss | 0% | Not specified in the recorded summary |
| Mean deviation | Not specified in the recorded summary | Approximately 37 ms |

The results show that the recorded test to `8.8.8.8` had a lower average response time and no packet loss across two packets. The test to the resolved Google website IP showed higher latency and greater variation in response times.

### Key Findings

- **System identification:** The exercise established the Linux username, hostname, and kernel version.
- **Resource monitoring:** Reviewing memory and disk utilisation demonstrated how to assess available virtual machine resources.
- **Network connectivity:** The ping tests demonstrated how ICMP echo requests and replies can help establish basic connectivity.
- **Latency measurement:** Round-trip times provided a way to compare network response performance between destinations.
- **Network variability:** The variation in response times to the Google website IP suggested that the network path or destination infrastructure may have contributed to inconsistent latency.
- **DNS and network infrastructure:** The tests illustrated that Google's public DNS resolver and a website IP address can produce different network performance results.

Google's `8.8.8.8` resolver uses anycast routing, which can direct traffic to a nearby network endpoint. A website IP address may follow a different network route or reach different infrastructure. These are plausible explanations for the observed difference, but the ping results alone do not establish the exact cause.

### Conclusion

This project developed foundational skills in Linux system inspection and network diagnostics using Kali Linux. It demonstrated how to review system resources, identify a kernel version, test external connectivity, and interpret basic latency and packet loss statistics.

These skills are useful starting points for further study in cybersecurity, network administration, incident investigation, and GRC, where understanding system configurations and network behaviour supports technical assessment and risk identification.

## Author

**Omamuyovwi Gboboh**

- **Location:** Dublin, Ireland
- **Programme:** GRC-C26-09-EU-035
- **Date:** 24 September 2026
- **Professional interests:** Governance, Risk and Compliance (GRC), cybersecurity, IT operations, business analysis, and network security.
- **GitHub:** https://github.com/0mam
- **LinkedIn:** www.linkedin.com/in/omamuyovwi-gboboh


