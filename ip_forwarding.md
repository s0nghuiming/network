# Linux IP Forwarding

## using ip route
```bash
echo "On server side"
echo Current IP Forwarding is $(cat /proc/sys/net/ipv4/ip_forward)
old_ip_fwd=$(cat /proc/sys/net/ipv4/ip_forward)
echo 1 > /proc/sys/net/ipv4/ip_forward
# /etc/sysctl.conf
# net.ipv4.ip_forward = 1 for persistant.
ip route add 10.0.0.0/24 via 192.168.0.15 dev enp0s3

echo "On client side"
ip route add 192.168.0.0/24 via 10.0.0.15 dev enp0s3
```

## using nc
```bash
scp -i cbai_key.pem ubuntu@52.32.67.94:/DLRM/songhuiming/
cat ~/.ssh/config
ProxyCommand /bin/nc -X 5 -x proxy.<myproxy>.com %h %p
```

