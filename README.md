# Network Traffic Analyzer

## 🛠️ Technologies
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![mitmproxy](https://img.shields.io/badge/mitmproxy-grey?style=for-the-badge)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)

## ✨ Features
- HTTP/HTTPS traffic interception via mitmproxy with CA certificate installation for HTTPS decryption
- Remote browser automation via PowerShell scripts (`remote_open_browser.ps1`)
- Orchestrated capture workflow: start → browse → stop via PowerShell scripts
- Log parser (`parse_mitm_log.py`) extracts structured JSON: host, method, path, status code, timestamp, and content-type
- Configurable proxy and target via `config.json`

## 🎯 Uses
Built for a university datathon competition to intercept and analyze network traffic from web browsers. Demonstrates proxy-based traffic analysis: HTTPS decryption, remote machine automation, and parsing raw mitmproxy flows into structured datasets for analysis.

## 🔧 Process
The mitmproxy CA certificate is installed on the target machine to enable HTTPS decryption. PowerShell scripts automate the remote capture session start and stop. The Python parser reads the binary mitmproxy flow log using `mitmproxy.io.FlowReader`, iterates over `HTTPFlow` objects, and writes structured JSON output. The orchestrator coordinates the full workflow across machines.

## 💡 Learnings
- mitmproxy's `FlowReader` provides a clean Python API for parsing binary capture files — no manual HTTP parsing needed
- HTTPS interception requires installing the proxy's CA certificate on the target machine; without it, all HTTPS connections fail
- Cross-platform automation (Python + PowerShell) is effective for coordinating tools across Windows and Linux machines in a competition setting

## ▶️ Running the project

```bash
# 1. Install mitmproxy CA cert on the target machine
# 2. Start capture remotely
./remote_start_capture.ps1

# 3. Browse normally — traffic is intercepted

# 4. Stop capture
./remote_stop_capture.ps1

# 5. Parse the log
python parse_mitm_log.py
```
