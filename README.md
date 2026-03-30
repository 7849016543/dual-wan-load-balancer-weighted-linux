# dual-wan-load-balancer-weighted-linux
Linux Dual WAN Load Balancer with Weighted Routing (65:35) and Automatic Failover


# 🚀 Dual WAN Load Balancer (Weighted 65:35)

Linux-based dual WAN load balancer with unequal bandwidth handling and automatic failover.

---

## 📌 Features

- ✅ Weighted Load Balancing (65% / 35%)
- ✅ Automatic failover
- ✅ Automatic recovery
- ✅ Slack alerts
- ✅ Policy-based routing
- ✅ Multipath routing with weights

---

## ⚖️ Load Balancing Logic

- ISP1 (eno1) → 1 Gbps → weight 65
- ISP2 (lan0) → 400 Mbps → weight 35

```bash
ip route replace default \
  nexthop via ISP1 weight 65 \
  nexthop via ISP2 weight 35

⚙️ Setup
sudo cp scripts/*.sh /usr/local/bin/
sudo chmod +x /usr/local/bin/*.sh

 Setup service
sudo cp systemd/*.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable ue-ratio-monitor
sudo systemctl start ue-ratio-monitor

 Configure network
sudo cp network-config/*.network /etc/systemd/network/
sudo systemctl restart systemd-networkd

🧪 Testing
sudo ip link set eno1 down
sudo ip link set eno1 up

🧠 Key Concepts
Policy Routing (ip rule)
Multipath Routing
Weighted Load Balancing
High Availability Networking
