# Load-Balancing-LB-4-Line-ISP
Load Balance 4 ISP

# mar/27/2024 11:54:20 by RouterOS 6.49.10
# software id = IKZF-7MUV
#
# model = RB450Gx4
# serial number = HD5085X8RFP
/interface ethernet
set [ find default-name=ether1 ] comment=INDOCYBER
set [ find default-name=ether2 ] comment=COMNET mac-address=B8:69:F4:AD:F3:0F
set [ find default-name=ether3 ] comment=BIZNET
set [ find default-name=ether4 ] comment=OXYGEN
set [ find default-name=ether5 ] comment=CLIENT
/interface l2tp-client
add connect-to=103.31.132.90 disabled=no name=l2tp-out1 password=rb750lbpcc \
    user=rb750lbpcc
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/ip firewall layer7-protocol
add name=SpeedTest regexp="^.+(speedtest-+[a-z0-9.]+[a-z]+.net.id|nflxvideo.ne\
    t|ooklaserver.net|speedtestcustom.com|speedtest.net|fast.com|speedtest.+[a\
    -z]+.id|.speedtest.|openspeedtest.com).*\$"
/ip pool
add name=dhcp_pool0 ranges=192.11.0.10-192.11.0.254
/ip dhcp-server
add address-pool=dhcp_pool0 disabled=no interface=ether5 name=dhcp1
/queue simple
add name=TOTAL_SPEED queue=default/default target=192.11.0.0/24,ether5
add name="0.Trafic Internet Rumah" parent=TOTAL_SPEED queue=default/default \
    target=192.11.0.0/24
add max-limit=2M/2M name="Om Puput" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.10/32
add max-limit=2M/2M name=Supriyatin parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.53/32
add max-limit=10M/10M name="Sari Rahayu (tiang tengah)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.39/32
add max-limit=5M/5M name="Siti Fatimah new (belakang)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.231/32
add max-limit=5M/5M name="Leni Belakang Garda" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.73/32
add max-limit=5M/5M name="Imron Kober" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.76/32
add max-limit=30M/30M name="Neneng Mulyanih" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.72/32
add max-limit=7M/7M name="Maidila (tiang tengah Baru)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.98/32
add max-limit=5M/5M name="Ibu Nining saudara Teh Dewi Garda" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.71/32
add max-limit=5M/5M name="Deket Rumah Nita" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.69/32
add max-limit=2M/2M name="Kontrakan No 3 Belakang Kuburan" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.68/32
add max-limit=5M/5M name="Teh Dewi Rumah Belakang Garda" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.67/32
add max-limit=5M/5M name="Linda Arema" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.233/32
add max-limit=5M/5M name="Teh Ai ( tiang tengah)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.64/32
add max-limit=15M/15M name="Mocin - Nita" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.63/32
add max-limit=15M/15M name="Teh Rena" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.36/32
add max-limit=5M/5M name=Lilis parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.82/32
add max-limit=5M/5M name="Tanamal (tiang tengah)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.62/32
add max-limit=5M/5M name=Hans parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.35/32
add max-limit=10M/10M name="Mocin - Mena" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.27/32
add max-limit=5M/5M name="Mocin - fallah/nurdin" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.200/32
add max-limit=5M/5M name=Mala/Maryati parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.244/32
add max-limit=5M/5M name="Mocin - Bu Ade (Rambutan)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.130/32
add max-limit=5M/5M name="AL sodara nurmala (New)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.90/32
add max-limit=3M/3M name="Aas Astuti" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.49/32
add max-limit=2M/2M name="Teh Nindy Arema" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.61/32
add max-limit=8M/8M name="Mocin - Teh Darniti" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.60/32
add max-limit=3M/3M name="Wahyu (Mena)" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.45/32
add max-limit=2M/2M name="Ibu Rika" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.56/32
add max-limit=2M/2M name="Warung Bubble Khanza" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.55/32
add max-limit=2M/2M name="Ibu Firda" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.54/32
add max-limit=2M/2M name="Didu Mena" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.52/32
add max-limit=2M/2M name="Bu Neneng/Pak H.Wahyu" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.51/32
add max-limit=5M/5M name="Tondi (New)" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.50/32
add max-limit=5M/5M name=Fathan parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.48/32
add max-limit=2M/2M name="Dede Permana (Rambutan)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.47/32
add max-limit=5M/5M name="Bu Tini (Rambutan)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.44/32
add max-limit=2M/2M name=Mala parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.42/32
add max-limit=3M/3M name="Rajimon/Sabrina/Nining (tiang ujung)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.104/32
add max-limit=2M/2M name=Dimas parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.41/32
add max-limit=3M/3M name="Dina Yohana" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.38/32
add max-limit=2M/2M name=Fallah/Nurdin parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.37/32
add max-limit=5M/5M name="Nining Suningsih (tiang ujung)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.40/32
add max-limit=5M/5M name=248 parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.248/32
add max-limit=5M/5M name=Nona parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.78/32
add max-limit=2M/2M name="Wahyu Sodara Mena" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.34/32
add max-limit=2M/2M name="Teh Neneg Kontrakan 2 Samping Alika" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.74/32
add max-limit=5M/5M name="Teh Dyen" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.33/32
add max-limit=2M/2M name="Mang Engkos2" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.32/32
add max-limit=30M/30M name="Sita Nurul" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.80/32
add max-limit=10M/10M name="Tes RT" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.103/32
add max-limit=20M/20M name="RT ikin" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.105/32
add max-limit=2M/2M name="Ibu Yogi" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.29/32
add max-limit=5M/5M name="Ibu Helmi" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.30/32
add max-limit=2M/2M name=Piyan parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.28/32
add max-limit=2M/2M name="FATHAN ERZA belakang Warteg" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.106/32
add max-limit=5M/5M name="KHAYRA belakang warteg" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.107/32
add max-limit=5M/5M name="Tata (belakang warteg)" parent=\
    "0.Trafic Internet Rumah" priority=2/2 queue=default/default target=\
    192.11.0.240/32
add max-limit=8M/8M name=Wiyatni parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.24/32
add max-limit=5M/5M name="Mocin - Sumi" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.95/32
add max-limit=5M/5M name=Nana/Sopian parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.22/32
add max-limit=5M/5M name="Mang Engkos1" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.21/32
add max-limit=5M/5M name="Nurul Apriani (anaknya Pak RW)" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.102/32
add max-limit=2M/2M name="Bu Ferdi" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.19/32
add max-limit=2M/2M name="Wa Lili" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.18/32
add max-limit=2M/2M name="Sunarya/Pak Narya" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.17/32
add max-limit=2M/2M name="Teh Nunung" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.253/32
add max-limit=2M/2M name="Warung Alika" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.15/32
add max-limit=2M/2M name="Bu Teti" parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.14/32
add max-limit=2M/2M name=Anggi/Karni parent="0.Trafic Internet Rumah" queue=\
    default/default target=192.11.0.13/32
add max-limit=10M/10M name="Saudara Arema Linda" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.101/32
add max-limit=2M/2M name="Mocin - Rayyan" parent="0.Trafic Internet Rumah" \
    queue=default/default target=192.11.0.12/32
add max-limit=4M/4M name="Mocin - Dina yohana" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.38/32
add max-limit=4M/4M name="Mocin - Atar / ibu Firda" parent=\
    "0.Trafic Internet Rumah" queue=default/default target=192.11.0.245/32
/ip address
add address=192.11.0.1/24 interface=ether5 network=192.11.0.0
/ip dhcp-client
add add-default-route=no disabled=no interface=ether1
add add-default-route=no disabled=no interface=ether2
add add-default-route=no disabled=no interface=ether3
add add-default-route=no disabled=no interface=ether4
/ip dhcp-server network
add address=192.11.0.0/24 gateway=192.11.0.1
/ip dns
set allow-remote-requests=yes servers=8.8.8.8,8.8.4.4
/ip firewall address-list
add address=192.168.0.0/24 list=LOCAL
add address=192.168.18.0/24 list=LOCAL
add address=192.168.100.0/24 list=LOCAL
add address=192.168.1.0/24 list=LOCAL
add address=192.11.0.0/24 list=LOCAL
/ip firewall mangle
add action=accept chain=prerouting comment="Accept All LOCAL IP" \
    dst-address-list=LOCAL src-address-list=LOCAL
add action=accept chain=postrouting dst-address-list=LOCAL src-address-list=\
    LOCAL
add action=accept chain=forward dst-address-list=LOCAL src-address-list=LOCAL
add action=accept chain=input dst-address-list=LOCAL src-address-list=LOCAL
add action=accept chain=output dst-address-list=LOCAL src-address-list=LOCAL
add action=mark-routing chain=output connection-mark=via-INDOCYBER \
    new-routing-mark=via-ISP1 passthrough=yes
add action=mark-routing chain=output connection-mark=via-COMNET \
    new-routing-mark=via-ISP2 passthrough=yes
add action=mark-routing chain=output connection-mark=via-BIZNET \
    new-routing-mark=via-ISP3 passthrough=yes
add action=mark-routing chain=output connection-mark=via-OXYGEN \
    new-routing-mark=via-ISP4 passthrough=yes
add action=mark-connection chain=prerouting dst-address-list=!LOCAL \
    dst-address-type=!local new-connection-mark=via-INDOCYBER passthrough=yes \
    per-connection-classifier=both-addresses-and-ports:4/0 src-address-list=\
    LOCAL
add action=mark-connection chain=prerouting dst-address-list=!LOCAL \
    dst-address-type=!local new-connection-mark=via-COMNET passthrough=yes \
    per-connection-classifier=both-addresses-and-ports:4/1 src-address-list=\
    LOCAL
add action=mark-connection chain=prerouting dst-address-list=!LOCAL \
    dst-address-type=!local new-connection-mark=via-BIZNET passthrough=yes \
    per-connection-classifier=both-addresses-and-ports:4/2 src-address-list=\
    LOCAL
add action=mark-connection chain=prerouting dst-address-list=!LOCAL \
    dst-address-type=!local new-connection-mark=via-OXYGEN passthrough=yes \
    per-connection-classifier=both-addresses-and-ports:4/3 src-address-list=\
    LOCAL
add action=mark-routing chain=prerouting connection-mark=via-INDOCYBER \
    dst-address-list=!LOCAL new-routing-mark=via-ISP1 passthrough=yes \
    src-address-list=LOCAL
add action=mark-routing chain=prerouting connection-mark=via-COMNET \
    dst-address-list=!LOCAL new-routing-mark=via-ISP2 passthrough=yes \
    src-address-list=LOCAL
add action=mark-routing chain=prerouting connection-mark=via-BIZNET \
    dst-address-list=!LOCAL new-routing-mark=via-ISP3 passthrough=yes \
    src-address-list=LOCAL
add action=mark-routing chain=prerouting connection-mark=via-OXYGEN \
    dst-address-list=!LOCAL new-routing-mark=via-ISP4 passthrough=yes \
    src-address-list=LOCAL
add action=add-dst-to-address-list address-list=SpeedTest-ListLayer7 \
    address-list-timeout=1h chain=prerouting comment=SpeedtestLayer7 \
    dst-address-list=!LOCAL layer7-protocol=SpeedTest src-address-list=LOCAL
add action=mark-routing chain=prerouting dst-address-list=SpeedTest dst-port=\
    80,443 new-routing-mark=ISP1 passthrough=no protocol=tcp \
    src-address-list=LOCAL
add action=mark-routing chain=prerouting dst-address-list=SpeedTest \
    new-routing-mark=ISP1 passthrough=no src-address-list=LOCAL
/ip firewall nat
add action=masquerade chain=srcnat out-interface=ether1 src-address=\
    192.11.0.0/24
add action=masquerade chain=srcnat out-interface=ether2 src-address=\
    192.11.0.0/24
add action=masquerade chain=srcnat out-interface=ether4 src-address=\
    192.11.0.0/24
add action=masquerade chain=srcnat out-interface=ether3 src-address=\
    192.11.0.0/24
/ip firewall raw
add action=add-dst-to-address-list address-list=SpeedTest \
    address-list-timeout=1h chain=prerouting comment=SpeedTest content=\
    speedtest.net dst-address-list=!Lokal src-address-list=Lokal
add action=add-dst-to-address-list address-list=SpeedTest \
    address-list-timeout=1h chain=prerouting content=speedtest- \
    dst-address-list=!Lokal src-address-list=Lokal
add action=add-dst-to-address-list address-list=SpeedTest \
    address-list-timeout=1h chain=prerouting content=speedest. \
    dst-address-list=!Lokal src-address-list=Lokal
add action=add-dst-to-address-list address-list=SpeedTest \
    address-list-timeout=1h chain=prerouting content=speedtest.cbn.id \
    dst-address-list=!Lokal src-address-list=Lokal
add action=add-dst-to-address-list address-list=SpeedTest \
    address-list-timeout=1h chain=prerouting content=openspeedtest.com \
    dst-address-list=!Lokal src-address-list=Lokal
add action=add-dst-to-address-list address-list=SpeedTest \
    address-list-timeout=1h chain=prerouting content=speedof.me \
    dst-address-list=!Lokal src-address-list=Lokal
add action=add-dst-to-address-list address-list=SpeedTest \
    address-list-timeout=1h chain=prerouting content=speedcheck.org \
    dst-address-list=!Lokal src-address-list=Lokal
add action=add-dst-to-address-list address-list=SpeedTest \
    address-list-timeout=1h chain=prerouting content=fast.com \
    dst-address-list=!Lokal src-address-list=Lokal
add action=add-dst-to-address-list address-list=SpeedTest \
    address-list-timeout=1h chain=prerouting content=speedtestcustom. \
    dst-address-list=!Lokal src-address-list=Lokal
add action=add-dst-to-address-list address-list=SpeedTest \
    address-list-timeout=1h chain=prerouting content=speedtestcustom.com \
    dst-address-list=!Lokal src-address-list=Lokal
/ip route
add check-gateway=ping distance=1 gateway=1.0.0.1 routing-mark=via-ISP1 \
    target-scope=30
add check-gateway=ping distance=1 gateway=1.0.0.2 routing-mark=via-ISP2 \
    target-scope=30
add check-gateway=ping distance=1 gateway=1.0.0.3 routing-mark=via-ISP3 \
    target-scope=30
add check-gateway=ping distance=1 gateway=1.0.0.4 routing-mark=via-ISP4 \
    target-scope=30
add comment=SPEEDTEST distance=1 gateway=ether1 routing-mark=ISP1
add check-gateway=ping distance=1 gateway=1.0.0.1 target-scope=30
add check-gateway=ping distance=2 gateway=1.0.0.2 target-scope=30
add check-gateway=ping distance=3 gateway=1.0.0.3 target-scope=30
add check-gateway=ping distance=4 gateway=1.0.0.4 target-scope=30
add distance=1 dst-address=1.0.0.1/32 gateway=192.168.0.1
add distance=1 dst-address=1.0.0.2/32 gateway=192.168.100.1
add distance=1 dst-address=1.0.0.3/32 gateway=192.168.18.1
add distance=1 dst-address=1.0.0.4/32 gateway=192.168.1.1
/system clock
set time-zone-name=Asia/Jakarta
