# Windows
# Finding and killing the process

1. Find process with port number and their details
command: netstat -aon ^| findstr 8000
C:\Users\xxxx>netstat -a -o -n | find "8000"
  TCP    127.0.0.1:8000         0.0.0.0:0              LISTENING       11024
  TCP    127.0.0.1:8000         127.0.0.1:60613        CLOSE_WAIT      11024
  TCP    127.0.0.1:8000         127.0.0.1:60617        CLOSE_WAIT      11024
  TCP    127.0.0.1:60613        127.0.0.1:8000         FIN_WAIT_2      8332
  TCP    127.0.0.1:60617        127.0.0.1:8000         FIN_WAIT_2      8332
  
  
command: for /f "tokens=5" %a in ('netstat -aon ^| findstr 8000') do tasklist /FI "PID eq %a"

C:\Users\xxxx>tasklist /FI "PID eq 11024"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
python.exe                   11024 Console                    1     31,980 K

C:\Users\patir>tasklist /FI "PID eq 11024"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
python.exe                   11024 Console                    1     31,980 K

C:\Users\patir>tasklist /FI "PID eq 11024"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
python.exe                   11024 Console                    1     31,980 K

C:\Users\patir>tasklist /FI "PID eq 8332"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
chrome.exe                    8332 Console                    1    364,524 K

C:\Users\patir>tasklist /FI "PID eq 8332"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
chrome.exe                    8332 Console                    1    364,524 K

2. Kill the respective pid using:
command: taskkill /F /PID 11024
