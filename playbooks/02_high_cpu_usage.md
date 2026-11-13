# Runbook: High CPU Usage / Server Slowness

## 🚨 Incident Summary
Users report that the application is extremely slow, or a monitoring alert indicates that the server's CPU usage is at 100%.

## 🔍 Diagnosis
1. Identify the process consuming the most CPU:
   `htop`
   *(Look at the %CPU column. Press `q` to exit).*
2. Alternatively, get a quick snapshot with:
   `top -b -n 1 | head -n 15`
3. Check the system load average:
   `uptime`
   *(A load average higher than the number of CPU cores indicates a bottleneck).*

## 🛠️ Resolution
1. If a specific service is stuck, restart it:
   `sudo systemctl restart <service_name>`
2. If a rogue process is running, terminate it:
   `kill -9 <PID>`

## ✅ Verification
Run `uptime` or `htop` again to confirm that the CPU usage and load average have returned to normal levels.
