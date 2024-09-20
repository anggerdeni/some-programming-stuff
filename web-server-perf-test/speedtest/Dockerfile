FROM ubuntu:24.04
RUN apt-get update
RUN apt-get install -y net-tools iproute2 netcat-openbsd dnsutils curl iputils-ping tcpdump iperf3

# https://hechao.li/2023/08/28/container-bandwidth-limit/

RUN cat <<EOT >> /entrypoint.sh
#!/bin/sh
tc qdisc replace dev eth0 root handle 1: htb default 11
tc class add dev eth0 parent 1: classid 1:1 htb rate 100mbit
tc class add dev eth0 parent 1:1 classid 1:11 htb rate 100mbit ceil 100mbit
tc qdisc add dev eth0 parent 1:11 handle 11: fq_codel
tc filter add dev eth0 protocol ip prio 1 parent 1: matchall classid 1:11
bash
EOT

RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
