# DNS-NTP-SFTP-Stack

A Docker stack running DNS, NTP and an SFTP Server. The NTP server cannot run inside a swarm because it needs hightened privs. Therefore run the NTP server as a standalone container first, it will take a few mins to sync with the Stratum 1 server.

1. docker run --rm -d --cap-add SYS_RESOURCE --cap-add SYS_TIME -p 123:123/udp --name ntp milobahg/ntpd:latest

2. docker compose -f compose.yml stack

3. docker stack ps stack  #Test status of the stack

Ports that will be published: 

2222 for SFTP
53/udp for DNS
123/udp for NTP
