* **ps command output**

──(abdul2045㉿LAPTOP-TF63SPE6)-\[\~]

└─$ ps -ef                                                                                                                                                                                                                                   

UID          PID    PPID  C STIME TTY          TIME CMD

root           1       0  0 16:45 ?        00:00:02 /sbin/init

root           2       1  0 16:45 ?        00:00:00 /init

root           9       2  0 16:45 ?        00:00:00 plan9 --control-socket 7 --log-level 4 --server-fd 8 --pipe-fd 10 --log-truncate

root          52       1  0 16:45 ?        00:00:00 /usr/lib/systemd/systemd-journald

root          63       1  0 16:45 ?        00:00:04 /usr/lib/systemd/systemd-udevd

root          99       1  0 16:45 ?        00:00:00 /usr/libexec/accounts-daemon

root         103       1  0 16:45 ?        00:00:00 /usr/sbin/cron -f

message+     108       1  0 16:45 ?        00:00:04 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only

polkitd      122       1  0 16:45 ?        00:00:01 /usr/lib/polkit-1/polkitd --no-debug --log-level=notice

root         138       1  0 16:45 ?        00:00:00 /usr/lib/systemd/systemd-logind



* top command



top - 19:40:57 up  2:56,  1 user,  load average: 0.00, 0.00, 0.00

Tasks: 101 total,   1 running, 100 sleeping,   0 stopped,   0 zombie

%Cpu(s):  0.2 us,  0.6 sy,  0.0 ni, 99.2 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 

MiB Mem :   7599.2 total,   6088.8 free,   1109.5 used,    625.0 buff/cache     

MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.   6489.7 avail Mem 



&#x20;   PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                                                               

&#x20;  3010 abdul20+  20   0 1042336  78848  69840 S   3.3   1.0   0:22.32 qterminal                                                                                                                                                             

&#x20;  1309 abdul20+  20   0  378032 132288  69908 S   0.7   1.7   1:22.99 Xtigervnc                                                                                                                                                             

&#x20;   212 root      20   0 1703420  46388  35456 S   0.3   0.6   0:17.08 containerd                                                                                                                                                            

&#x20;  1371 abdul20+  20   0 1933424 111852  87360 S   0.3   1.4   0:49.09 xfwm4                                                                                                                                                                 

&#x20;  1568 abdul20+  20   0  371852 118132  20564 S   0.3   1.5   0:39.25 wrapper-2.0                                                                                                                                                           

&#x20;  1578 abdul20+  20   0  276524  28724  21736 S   0.3   0.4   1:04.65 wrapper-2.0                                                                                                                                                           

&#x20;  1599 abdul20+  20   0 1427308  34724  26928 S   0.3   0.4   0:09.23 wrapper-2.0                                                                                                                                                           

&#x20;  1774 root      20   0  315992   9216   7936 S   0.3   0.1   0:14.83 upowerd                                                                                                                                                               

&#x20;     1 root      20   0   24116  13824  10624 S   0.0   0.2   0:02.89 systemd   



* pgrep 



└─$ pgrep nginx

243

244

245

246

247

248

249

250

251

252

253

254

255



* systemctl



systemctl status nginx

● nginx.service - A high performance web server and a reverse proxy server

&#x20;    Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: disabled)

&#x20;    Active: active (running) since Tue 2026-05-19 16:45:06 IST; 2h 58min ago

&#x20;Invocation: 61777210b74c44cbb0fa052805043d1f

&#x20;      Docs: man:nginx(8)

&#x20;   Process: 199 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master\_process on; (code=exited, status=0/SUCCESS)

&#x20;   Process: 236 ExecStart=/usr/sbin/nginx -g daemon on; master\_process on; (code=exited, status=0/SUCCESS)

&#x20;  Main PID: 243 (nginx)

&#x20;     Tasks: 13 (limit: 9107)

&#x20;    Memory: 9.7M (peak: 15.1M)

&#x20;       CPU: 238ms



* I inspect SSH using systemctl for status, journalctl for logs, ps for process, and ss to verify it is listening on port 22.





┌──(abdul2045㉿LAPTOP-TF63SPE6)-\[\~]

└─$ systemctl status ssh 

● ssh.service - OpenBSD Secure Shell server

&#x20;    Loaded: loaded (/usr/lib/systemd/system/ssh.service; disabled; preset: disabled)

&#x20;    Active: active (running) since Tue 2026-05-19 19:52:11 IST; 1min 52s ago

&#x20;Invocation: 89c438cb502948d984c346cec6cfd7e9

&#x20;      Docs: man:sshd(8)

&#x20;            man:sshd\_config(5)

&#x20;   Process: 95705 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)

&#x20;  Main PID: 95708 (sshd)

&#x20;     Tasks: 1 (limit: 9107)

&#x20;    Memory: 5.4M (peak: 25.4M)

&#x20;       CPU: 173ms

&#x20;    CGroup: /system.slice/ssh.service

&#x20;            └─95708 "sshd: /usr/sbin/sshd -D \[listener] 0 of 10-100 startups"



May 19 19:52:11 LAPTOP-TF63SPE6 systemd\[1]: Starting ssh.service - OpenBSD Secure Shell server...

May 19 19:52:11 LAPTOP-TF63SPE6 sshd\[95708]: Server listening on 0.0.0.0 port 22.

May 19 19:52:11 LAPTOP-TF63SPE6 sshd\[95708]: Server listening on :: port 22.

May 19 19:52:11 LAPTOP-TF63SPE6 systemd\[1]: Started ssh.service - OpenBSD Secure Shell server.

May 19 19:53:27 LAPTOP-TF63SPE6 sshd-session\[96209]: Accepted password for abdul2045 from 127.0.0.1 port 46612 ssh2

May 19 19:53:28 LAPTOP-TF63SPE6 sshd-session\[96209]: pam\_unix(sshd:session): session opened for user abdul2045(uid=1000) by abdul2045(uid=0)

May 19 19:53:28 LAPTOP-TF63SPE6 sshd-session\[96209]: pam\_env(sshd:session): Unable to open env file: /etc/default/locale



┌──(abdul2045㉿LAPTOP-TF63SPE6)-\[\~]

└─$ systemctl is-enabled ssh 

disabled



┌──(abdul2045㉿LAPTOP-TF63SPE6)-\[\~]

└─$ journalctl -u ssh 

Hint: You are currently not seeing messages from other users and the system.

&#x20;     Users in the 'systemd-journal' group can see all messages. Pass -q to

&#x20;     turn off this notice.

May 19 19:52:11 LAPTOP-TF63SPE6 systemd\[1]: Starting ssh.service - OpenBSD Secure Shell server...

May 19 19:52:11 LAPTOP-TF63SPE6 sshd\[95708]: Server listening on 0.0.0.0 port 22.

May 19 19:52:11 LAPTOP-TF63SPE6 sshd\[95708]: Server listening on :: port 22.

May 19 19:52:11 LAPTOP-TF63SPE6 systemd\[1]: Started ssh.service - OpenBSD Secure Shell server.

May 19 19:53:27 LAPTOP-TF63SPE6 sshd-session\[96209]: Accepted password for abdul2045 from 127.0.0.1 port 46612 ssh2

May 19 19:53:28 LAPTOP-TF63SPE6 sshd-session\[96209]: pam\_unix(sshd:session): session opened for user abdul2045(uid=1000) by abdul2045(uid=0)

May 19 19:53:28 LAPTOP-TF63SPE6 sshd-session\[96209]: pam\_env(sshd:session): Unable to open env file: /etc/default/locale



┌──(abdul2045㉿LAPTOP-TF63SPE6)-\[\~]

└─$ ps aux | grep ssh 

abdul20+    1355  0.0  0.0  10676  3480 ?        Ss   16:45   0:00 /usr/bin/ssh-agent -s

root       95708  0.0  0.1  11764  7808 ?        Ss   19:52   0:00 sshd: /usr/sbin/sshd -D \[listener] 0 of 10-100 startups

abdul20+   97385  0.0  0.0   6612  2304 pts/2    S+   19:54   0:00 grep --color=auto ssh



┌──(abdul2045㉿LAPTOP-TF63SPE6)-\[\~]

└─$ ss -tulnp | grep 22 

tcp   LISTEN 0      128           0.0.0.0:22         0.0.0.0:\*                                        

tcp   LISTEN 0      128              \[::]:22            \[::]:\*                                        



┌──(abdul2045㉿LAPTOP-TF63SPE6)-\[\~]

└─$ journalctl -u ssh -n 5 

Hint: You are currently not seeing messages from other users and the system.

&#x20;     Users in the 'systemd-journal' group can see all messages. Pass -q to

&#x20;     turn off this notice.

May 19 19:52:11 LAPTOP-TF63SPE6 sshd\[95708]: Server listening on :: port 22.

May 19 19:52:11 LAPTOP-TF63SPE6 systemd\[1]: Started ssh.service - OpenBSD Secure Shell server.

May 19 19:53:27 LAPTOP-TF63SPE6 sshd-session\[96209]: Accepted password for abdul2045 from 127.0.0.1 port 46612 ssh2

May 19 19:53:28 LAPTOP-TF63SPE6 sshd-session\[96209]: pam\_unix(sshd:session): session opened for user abdul2045(uid=1000) by abdul2045(uid=0)

May 19 19:53:28 LAPTOP-TF63SPE6 sshd-session\[96209]: pam\_env(sshd:session): Unable to open env file: /etc/default/locale





&#x20;     

