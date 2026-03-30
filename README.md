# 1. 解锁 resolv.conf（新系统一般没锁，先做兼容）
chattr -i /etc/resolv.conf 2>/dev/null

# 2. 停止并禁用 systemd-resolved（温和版，不 mask，避免断网）
systemctl stop systemd-resolved
systemctl disable systemd-resolved

# 3. 删除旧配置，写入你要的 DNS 服务器
rm -f /etc/resolv.conf
cat > /etc/resolv.conf <<EOF
nameserver 64.6.64.6
nameserver 156.154.70.1
nameserver 74.82.42.42
nameserver 195.46.39.39
EOF

# 4. 锁定文件，禁止任何程序修改（包括系统服务）
chattr +i /etc/resolv.conf

# 5. 防止 NetworkManager 覆盖（如果系统安装了 NetworkManager）
if command -v nmcli &> /dev/null; then
    mkdir -p /etc/NetworkManager/conf.d
    cat > /etc/NetworkManager/conf.d/90-dns-none.conf <<EOF
[main]
dns=none
rc-manager=unmanaged
EOF
    systemctl reload NetworkManager
fi

# 6. 验证结果
echo -e "\n✅ DNS 已永久锁定，当前配置："
cat /etc/resolv.conf
echo -e "\n🔍 测试解析："
ping -c 2 google.com



# 1. 解锁 resolv.conf（新系统一般没锁，先做兼容）
chattr -i /etc/resolv.conf 2>/dev/null

# 2. 停止并禁用 systemd-resolved（温和版，不 mask，避免断网）
systemctl stop systemd-resolved
systemctl disable systemd-resolved

# 3. 删除旧配置，写入你要的 DNS 服务器
rm -f /etc/resolv.conf
cat > /etc/resolv.conf <<EOF
nameserver 12.127.16.67
nameserver 12.127.17.71
nameserver 12.166.30.2
nameserver 12.25.232.115
EOF

# 4. 锁定文件，禁止任何程序修改（包括系统服务）
chattr +i /etc/resolv.conf

# 5. 防止 NetworkManager 覆盖（如果系统安装了 NetworkManager）
if command -v nmcli &> /dev/null; then
    mkdir -p /etc/NetworkManager/conf.d
    cat > /etc/NetworkManager/conf.d/90-dns-none.conf <<EOF
[main]
dns=none
rc-manager=unmanaged
EOF
    systemctl reload NetworkManager
fi

# 6. 验证结果
echo -e "\n✅ DNS 已永久锁定，当前配置："
cat /etc/resolv.conf
echo -e "\n🔍 测试解析："
ping -c 2 google.com




lin lin:
2620:74:1b::1:1
2610:a1:1018::1


2606:4700:4700::1001 1.41
2620:119:35::35 12.3
2001:4860:4860::8888 12.4
2001:418:3ff::53 13.8
2a0d:2a00:1::2 13.9
2610:a1:1019::1 14.0

2606:4700:4700::1001
    - 2620:119:35::35
    - 2001:4860:4860::8888
    - 2001:418:3ff::53


    12.166.30.2        超 时
12.180.165.40      超 时
12.25.232.115      超 时
12.32.34.33        超 时
12.49.240.68       超 时
23.244.46.0        超 时
23.244.46.255      超 时
12.127.17.72       21.6 ms
12.127.16.68       21.9 ms
12.127.17.71       22.0 ms
12.127.16.67       22.2 ms



75.126.98.108      超 时
72.22.224.3        10.0 ms
198.153.194.1      20.1 ms
205.171.3.25       21.1 ms
12.127.17.72       21.5 ms
12.127.16.68       21.7 ms
12.127.17.71       22.0 ms
76.14.0.8          22.0 ms
76.14.0.9          22.0 ms
12.127.16.67       22.2 ms
76.14.96.14        22.2 ms
76.14.192.9        23.6 ms
76.14.192.8        23.7 ms
76.14.96.13        23.7 ms
76.77.208.24       28.2 ms
76.77.208.23       29.6 ms
74.222.30.2        29.7 ms
68.238.64.14       33.8 ms
68.238.96.12       35.2 ms
76.10.67.2         35.4 ms
68.238.128.12      40.0 ms
68.238.128.14      41.2 ms
68.238.96.14       43.6 ms
199.7.83.42        46.2 ms
71.250.0.12        46.9 ms
71.250.0.14        47.8 ms
24.233.167.168     52.7 ms
24.233.167.167     54.0 ms
71.252.0.12        56.4 ms
71.252.0.14        57.7 ms
68.238.112.14      58.7 ms
68.238.112.12      59.3 ms
71.242.0.14        60.3 ms
71.242.0.12        60.4 ms
24.237.132.5       72.6 ms
199.91.73.222      205 ms



45.90.28.114
45.90.30.114
45.90.29.208_45.90.29.254



gcore公共dns

95.85.95.85

2.56.220.2


2a03:90c0:999d::1
2a03:90c0:9992::1
