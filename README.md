# Datathon — Network Traffic Analyzer

A Python-based tool that uses **mitmproxy** to intercept, capture, and analyze HTTP/HTTPS traffic from web browsers. Built as part of a datathon competition.

## How It Works

1. Install the mitmproxy CA certificate (`mitmproxy-ca-cert.pem`) on the target machine to enable HTTPS interception
2. Run `remote_start_capture.ps1` to start the proxy on the remote machine
3. Browse normally — traffic is intercepted and logged
4. Run `remote_stop_capture.ps1` to end the capture session
5. Run `parse_mitm_log.py` to parse and extract structured data from the log

## Structure

```
Orchestrator/              # orchestration logic and coordination
parse_mitm_log.py          # parses mitmproxy capture logs into structured data
remote_open_browser.ps1    # opens a browser on the remote machine
remote_start_capture.ps1   # starts mitmproxy capture remotely
remote_stop_capture.ps1    # stops the capture session
config.json                # proxy and target configuration
mitmproxy-ca-cert.pem      # CA certificate for HTTPS interception
test_output.json.txt       # sample captured output
```

## Tech Stack

- **Python** — log parsing and data analysis
- **mitmproxy** — HTTP/HTTPS traffic interception
- **PowerShell** — remote machine automation
