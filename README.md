# 🔍 Camera Fusion V1

---

## 📋 Description

CamFusion is a high-performance network scanning tool built to identify IP cameras and camera-related web services within specified IP ranges. It uses parallel scanning techniques to deliver fast results, automatically recognizes common CCTV and web interfaces, and includes route tracing features to help analyze network paths and connectivity.

---

## ✨ Features

### 🚀 High-Speed Scan Mode
- **Parallel scanning engine using hundreds of concurrent threads**
- **Adaptive CPU scaling that automatically adjusts threads based on available cores**
- **Intelligent camera recognition using page titles and response patterns**
- **Live discovery output showing detected devices in real time**
- **Automatic result logging with findings saved to ```SuperFastScan_Results.txt```**

### 🔍 Route Trace Mode
- **Traces the full network path to any target IP or domain**
- **Clear, color-highlighted output for better visibility**
- **Optimized response timing for quicker results**
- **Uses google.com as the default target for instant tracing**

### 📷 Local Network Camera Scanner
- **Automatically detects and scans your local subnet**
- **Finds RTSP-enabled cameras running on port 554**
- **Recognizes popular camera brands including Dahua and Hikvision**
- **Uses multi-threaded scanning with 80 concurrent threads for speed**
- **Generates ready-to-use RTSP stream URLs**
- **Automatically saves all findings to ```NeighboursCameras_Results.txt```**

### 🎯 Camera Identification Engine
**Automatically recognizes:**
- **✅ Web-based camera interfaces including Dahua-type systems**
- **✅ Hikvision cameras and related devices**
- **✅ DVR and NVR systems**
- **✅ Standalone IP cameras**
- **✅ Camera login panels that may indicate active CCTV devices**

###🌐 Network Details Overview
- Displays your **current local IP address**
- Identifies the active **router gateway IP** 
- Supports **gateway detection across multiple platforms**

### 💻 Platform Compatibility

- ✅ Windows (7, 8, 10, 11)
- ✅ Linux distributions including Ubuntu, Debian, and Kali
- ✅ macOS
- ✅ **Termux** on Android with full feature support

---

## 📦 Installation Guide

### Windows / Linux / macOS

#### Prerequisites
- Python 3.7 or higher
- pip (Python package manager)

#### Step 1: Clone the repository and move into the project directory
```bash
git clone https://github.com/aonexyz/CamFusion.git
cd CamFusion
```

#### Step 2: Install Required Packages
**Install all necessary dependencies using pip:**
```bash
pip install -r requirements.txt
```

#### Step 3: Launch the Scanner

Run the tool with Python:
```bash
python W8CameraScanner.py
```

### 📱 Termux (Android)

#### Step 1: Set Up Required Packages
**Update and upgrade Termux packages:**
```bash
pkg update && pkg upgrade -y
```

**Install Python:**
```bash
pkg install python -y
```

**Install git:**
```bash
pkg install git -y
```

**Install traceroute (optional, required for route tracing feature):**
```bash
pkg install traceroute -y
```

#### Step 2: Download and Install
**Clone the project repository:**
```
git clone https://github.com/aonexyz/CamFusion.git
```

```
cd CamFusion
```

# Install required dependencies:

```
pip install -r requirements.txt
```

#### Step 3: Run
**Launch the scanner using Python:**

```bash
python camfusion.py
```

---

## 🎮 Usage

### Main Menu
When you run the tool, you'll see:

```
╔══════════════════════════════════╗
║   IP Range Camera Scanner        ║          
║   IP Scanner                     ║          
╚══════════════════════════════════╝

[*] Developed by: Anik
[*] GitHub: github.com/aonexyz
[*] Termux Supported ✓

[i] Time: 2025-12-23 02:52:49 PM
[i] Your Local IP: 192.168.1.100
[i] Router Gateway: 192.168.1.1

==================================================
Select Mode:
==================================================
1. 🔍 Trace Route
2. ⚡ SUPER FAST SCAN (Camera Scanner)
3. 📷 Neighbours Camera Scanner
4. Exit
==================================================
```

### Option 1: Trace Route 🔍
- Automatically traces route to **google.com**
- Shows all network hops
- Color-coded results (Green = Success, Red = Timeout)
- Displays total hop count

### Option 2: Super Fast Scan ⚡
- Enter **Start IP** and **End IP** (or press Enter for single IP)
- Scans ports **80** and **8080**
- **Multi-threaded** for maximum speed
- Shows only **cameras** (filters out regular web servers)
- Saves results to `SuperFastScan_Results.txt`

### Option 3: Neighbours Camera Scanner 📷
- **Auto-detects** your local network subnet
- Scans all 254 IPs in your subnet automatically
- Finds **RTSP cameras** on port 554
- Identifies **Dahua** and **Hikvision** cameras
- Generates **RTSP URLs** for easy access
- Saves results to `NeighboursCameras_Results.txt`

---

## 📸 Examples

### Example 1: Scan Single IP
```
Enter Start IP: 192.168.1.1
Enter End IP (press Enter for single IP): [Press Enter]

[✓] Camera Found: 192.168.1.1:80 - WEB SERVICE
```

### Example 2: Scan IP Range
```
Enter Start IP: 192.168.1.1
Enter End IP (press Enter for single IP): 192.168.1.255

[✓] Camera Found: 192.168.1.10:80 - Camera - Login
[✓] Camera Found: 192.168.1.50:8080 - Camera - DVR
[✓] Camera Found: 192.168.1.100:80 - Camera - WEB SERVICE

[i] Total IPs scanned: 255
[i] Cameras found: 3
[i] Time taken: 45.23 seconds
[i] Speed: 1128 ports/sec
```

### Example 3: Neighbours Camera Scanner
```
Select Mode: 3

[📷] NEIGHBOURS CAMERA SCANNER [📷]
==================================================

[i] Detected Subnet: 192.168.1.x
[*] Scanning for RTSP cameras (port 554)...
[*] This may take a few minutes...

[✓] Camera Found: 192.168.1.100 - xyz-IPC-HDW1230M
[✓] Camera Found: 192.168.1.101 - NiggaTv CAMERA

[*] Found 2 RTSP CAMERAS:

[1] 192.168.1.100
    Name: xyz-IPC-HDW1230M
    RTSP URL: rtsp://192.168.1.100:554

[2] 192.168.1.101
    Name: NiggaTv CAMERA
    RTSP URL: rtsp://192.168.1.101:554

[✓] Results saved to: NeighboursCameras_Results.txt

[i] Total IPs scanned: 254
[i] Cameras found: 2
[i] Time taken: 12.45 seconds
```

### Example 4: Results File
Results are automatically saved to `SuperFastScan_Results.txt`:
```
============================================================
SUPER FAST SCAN - CAMERAS FOUND
============================================================

IP: 192.168.1.10:80
Title: Login Page
Server: nginx/1.18.0
Type: Camera - Login
URL: http://192.168.1.10
------------------------------------------------------------

IP: 192.168.1.50:8080
Title: DVR System
Server: Unknown
Type: Camera - DVR
URL: http://192.168.1.50:8080
------------------------------------------------------------
```

---

## ⚡ Performance

- **Speed:** Up to 1000+ ports per second
- **Threads:** Automatically scales to your CPU (up to 500 threads)
- **Efficiency:** Only shows cameras, filters out regular web servers
- **Memory:** Low memory footprint (~50MB)

### Performance Benchmarks
| IP Range | Time | Speed | System |
|----------|------|-------|--------|
| 256 IPs (/24) | ~45s | 1128 ports/sec | 4-core CPU |
| 1024 IPs (/22) | ~3min | 1138 ports/sec | 8-core CPU |
| Single IP | <1s | Instant | Any |

---

## 🎨 Features Breakdown

### Smart Camera Detection
**The scanner detects camera devices using multiple analysis layers**
- **Page title analysis:** Searches for keywords such as Web, Login, DVR, Camera, and IPCam
- **Content fingerprinting:** Matches known camera-related signatures like web services, login pages, and DVR identifiers
- **Response behavior analysis:** Evaluates HTTP response patterns commonly used by camera systems
- **RTSP protocol scanning:** Discovers streaming-enabled cameras on port 554
- **Vendor recognition:** Identifies popular brands including xyz (xyz-series) and xyz devices

### Filtered Results Output

**The scanner displays only relevant camera-related targets:**
- ✅ IP cameras and DVR/NVR systems
- ✅ RTSP-enabled streaming cameras
- ❌ Standard web servers are automatically excluded
- ❌ Empty or invalid responses are ignored

---

## 🛠️ Technical Details

### Ports Scanned
- **Port 80** (HTTP) - Super Fast Scan
- **Port 8080** (Alternative HTTP) - Super Fast Scan
- **Port 554** (RTSP) - Neighbours Camera Scanner
- **Port 37777** (Dahua) - Camera identification
- **Port 8000** (Hikvision) - Camera identification

### Timeouts
- **Port Check:** 0.3-0.5 seconds
- **HTTP Request:** 1-2 seconds
- **RTSP Check:** 0.3 seconds
- **Optimized for speed**

### Detection Methods
1. **Title Extraction** - Parses HTML `<title>` tags
2. **Content Analysis** - Searches for camera signatures
3. **Server Headers** - Identifies server types
4. **Response Patterns** - Matches known camera patterns
5. **RTSP Protocol** - Detects RTSP streaming cameras
6. **Brand Detection** - Identifies Dahua and Hikvision models

---

## 📝 Requirements

### Python Packages
- **colorama** - For colored terminal output

### System Requirements
- **Python:** 3.7+
- **RAM:** 512MB minimum
- **Disk:** 10MB
- **Network:** Internet connection

---

## 👽 Troubleshooting

### Issue: "colorama not found"
**Solution:**
```bash
pip install colorama
```

### Issue: "Traceroute command not found" (Linux/Termux)
**Solution:**
```bash
# For Termux
pkg install inetutils

# For Debian/Ubuntu
sudo apt install traceroute

# For Arch Linux
sudo pacman -S traceroute
```

### Issue: No cameras found
**Possible reasons:**
- No cameras in the IP range
- Firewall blocking connections
- Network timeout
- Cameras using different ports

**Try:**
- Scan your local network (192.168.x.x)
- Check if IPs are reachable
- Increase timeout values

---

## Author

- **Anik** – [GitHub: aonexyz](https://github.com/aonexyz)

---

## Buy me a coffee ☕
Love the bot? Wanna fuel more WAGMI vibes? Drop some crypto love to keep the charts lit! 🙌
- **SUI**: `0x6e20d8f6c15aeb42887608eec65b29385f21fa21cfd23302c54fabd813d8cd38`
- **USDT (TRC20)**: `TMoPwVpeC8A2yTc5qotKj8gVXaGTqQwc3L`
- **BNB (BEP20)**: `0x068ff5934e0c30d8763012a6faa0033e7fdcc455`
- **Binance UID**:`899350787`

Every bit helps me grind harder and keep this bot stacking bags! 😎
---

## 🪪 License
MIT © 2026


## ⭐ Support

If you find this tool useful, please:
- ⭐ **Star** this repository
- 🐛 **Report issues** on GitHub
- 🔀 **Fork** and contribute
- 📢 **Share** with others

---

## ⚠️ Disclaimer

This tool is for **educational and authorized testing purposes only**. 

- ✅ Use on your own networks
- ✅ Use with proper authorization
- ❌ Do NOT use on unauthorized networks
- ❌ Do NOT use for illegal activities

**The author is not responsible for misuse of this tool.**

---

## 🚀 Future Updates

- [ ] IPv6 support
- [ ] Custom port scanning
- [ ] Export to CSV/JSON
- [ ] GUI version
- [ ] More camera signatures
- [ ] Proxy support
- [ ] Save credentials detection


