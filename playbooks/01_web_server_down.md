# Runbook: Web Server Down (Connection Refused)

## 🚨 Incident Summary
A customer or monitoring tool reports that the website is completely offline and returning a "Connection Refused" error.

## 🔍 Diagnosis
Run the following commands to confirm the issue:
1. Check if the service is running: 
   `sudo systemctl status nginx`
   *(Look for `Active: inactive (dead)`)*.
2. Test the connection: 
   `curl -I http://localhost`
   *(Expected error: `Failed to connect... Connection refused`)*.
3. Check the error logs for recent crashes: 
   `sudo tail -n 20 /var/log/nginx/error.log`

## 🛠️ Resolution
Restart the Nginx service:
`sudo systemctl start nginx`

## ✅ Verification
Test the connection again: 
`curl -I http://localhost`
*(The output must return `HTTP/1.1 200 OK` to confirm the site is back online).*
