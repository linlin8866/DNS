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

