
# Interface device

## Linux Show / Display Available Network Interfaces

* สามารถใช้คำสั่งต่อไปนี้เพื่อดู network interfaces ทั้งหมดในระบบปฏิบัติการ Linux:

```bash
ip command
```
คำสั่งนี้ใช้แสดงหรือจัดการเรื่อง routing, devices, policy routing, และ tunnels
```bash
netstat command 
```
ถูกใช้เพื่อ display network connections, routing tables, interface statistics, masquerade connections และ multicast memberships
```bash
ifconfig command
```
ถูกใช้เพื่อ display หรือ configure network interface
```bash
nmcli command
```
คำสั่งเพื่อ show หรือ configure network interface ในระบบปฏิบัติการ Linux
```bash
tcpdump command
```
print รายการของ network interface ที่มีในระบบ

### รายชื่อ Network Interfaces โดยใช้ ip command บน Linux
พิมพ์คำสั่งต่อไปนี้แล้วกด Enter
```bash
ip link show
```
นี่คือสิ่งที่แสดงผล(ชื่อของ network device อาจแตกต่างกันไปบนเซิร์ฟเวอร์ของคุณหรือบนคลาวด์เซิร์ฟเวอร์):
```bash
 1: lo: mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
 2: eth0: mtu 1500 qdisc mq state UP qlen 1000
    link/ether b8:ac:6f:65:31:e5 brd ff:ff:ff:ff:ff:ff
 3: wlan0: mtu 1500 qdisc mq state DOWN qlen 1000
    link/ether 00:21:6a:ca:9b:10 brd ff:ff:ff:ff:ff:ff
 4: vboxnet0: mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
 5: pan0: mtu 1500 qdisc noop state DOWN 
    link/ether c2:10:fa:55:8e:32 brd ff:ff:ff:ff:ff:ff
 6: vmnet1: mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:50:56:c0:00:01 brd ff:ff:ff:ff:ff:ff
 7: vmnet8: mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:50:56:c0:00:08 brd ff:ff:ff:ff:ff:ff
11: ppp0: mtu 1496 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
```
1. lo - Loopback interface
2. eth0 - Ethernet network interface บน Linux บนระบบปฏิบัติการที่เป็น Linux รุ่นใหม่นั้น, eth0 อาจถูกเปลี่ยนชื่อเป็น enp0s31f6 ตามที่ไดรเวอร์กำหนด
3. wlan0 - Wireless network interface บน Linux, WiFi device อาจถูกเปลี่ยนชื่อเป็น wlp82s0 ตามที่ไดรเวอร์กำหนด
4. ppp0 - Point to Point Protocol network interface (PPP) ที่สามารถใช้งานได้กับโมเด็ม Dial-Up, การเชื่อมต่อ VPN แบบ PPTP, หรือโมเด็มไร้สาย USB 3G
5. vboxnet0, vmnet1, vmnet8 - Virtual machine interface ทำงานในโหมดบริดจ์ (Bridge Mode) หรือโหมด NAT (Network Address Translation) บน Linux
### show / display available network interface บน Linux โดยใช้ nmcli
สามารถแสดงรายการอุปกรณ์ที่ใช้งานได้ ( list available devices) และสถานะ (status) ของพวกเขาบน Linux ได้ด้วยการรันคำสั่ง:
```bash
nmcli device status
```
หรือ
```bash
nmcli connection show
```
![Alt text](https://www.linuxtechi.com/wp-content/uploads/2022/01/nmcli-connection-show.png)
source : https://www.linuxtechi.com/configure-ip-with-nmcli-command-linux/
### show ตารางของ network interfaces ทั้งหมดโดยใช้คำสั่ง netstat ใน Linux
พิมพ์คำสั่ง netstat ต่อไปนี้:
```bash
netstat -i
```
นี่คือสิ่งที่แสดง:
```bash
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0   2697347      0      0 0       2630262      0      0      0 BMRU
lo        16436 0      2840      0      0 0          2840      0      0      0 LRU
ppp0       1496 0    102800      0      0 0         63437      0      0      0 MOPRU
vmnet1     1500 0         0      0      0 0            49      0      0      0 BMRU
vmnet8     1500 0         0      0      0 0            49      0      0      0 BMRU
```
### ตรวจสอบ network interfaces บน Linux โดยใช้คำสั่ง tcpdump
พิมพ์คำสั่ง tcpdump ต่อไปนี้ และสำหรับแต่ละ network interface ของ Linux จะปรากฎตัวเลขและ interface name โดยอาจมีคำอธิบายข้อความของ interface ตามนี้:
```bash
tcpdump --list-interfaces
```
นี่คือสิ่งที่แสดง:
```bash
1.lxdbr0 [Up, Running]
2.wg1 [Up, Running]
3.enp0s31f6 [Up, Running]
...
```
> **_NOTE:_**  คำสั่ง ifconfig ถูกประกาศเลิกใช้บน Linux เพื่อสนับสนุนคำสั่ง ip ดังนั้น, คุณอาจได้รับข้อผิดพลาดที่อ่านว่า: "bash: ifconfig: command not found."

พิมพ์คำสั่ง ifconfig ต่อไปนี้:
```bash
/sbin/ifconfig -a
```
ผลลัพธ์ตัวอย่าง:
```bash
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:65:31:e5  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe65:31e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2697529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2630541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2159382827 (2.0 GiB)  TX bytes:1389552776 (1.2 GiB)
          Interrupt:17 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2849 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2849 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2778290 (2.6 MiB)  TX bytes:2778290 (2.6 MiB)
 
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.1.3.105  P-t-P:10.0.31.18  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:102800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:148532544 (141.6 MiB)  TX bytes:4425518 (4.2 MiB)
 
vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.47.1  Bcast:192.168.47.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.232.1  Bcast:172.16.232.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
### จะดู routing table บน Linux ได้อย่างไร?
ใช้ ip command ดังนี้:
```bash
ip r
```
ผลลัพธ์ตัวอย่าง:
```bash
0.0.0.0/1 via 10.8.0.1 dev tun0 
default via 192.168.2.254 dev enp6s0 proto static metric 100 
10.8.0.0/24 dev tun0 proto kernel scope link src 10.8.0.2 
128.0.0.0/1 via 10.8.0.1 dev tun0 
139.59.1.155 via 192.168.2.254 dev enp6s0 
169.254.0.0/16 dev virbr0 scope link metric 1000 linkdown 
192.168.2.0/24 dev enp6s0 proto kernel scope link src 192.168.2.24 metric 100 
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown
```
### จะดูข้อมูล arp cache ที่เชื่อมต่อกับ NIC ของคุณบน Linux ได้ยังไง?
Run arp command:
```bash
arp
arp -a
arp -e
arp -n
# On modern Linux distros use the ip command #
ip neigh
ip -s neigh
```
Outputs:
```bash
Address                  HWtype  HWaddress           Flags Mask            Iface
centos7                  ether   00:01:c0:1c:09:4c   C                     enp6s0
freebsd11-box            ether   00:01:c0:1c:09:4c   C                     enp6s0
192.168.2.203            ether   00:01:c0:1c:09:4c   C                     enp6s0
fw0-pfsense-sg-3100.swe  ether   00:08:a2:0d:05:41   C                     enp6s0
192.168.2.205            ether   00:01:c0:1c:09:4c   C                     enp6s0
192.168.2.202            ether   00:01:c0:1c:09:4c   C                     enp6s0
```
### จะแสดงรายการ network devices  ทั้งหมดที่เชื่อมต่อกับ PCI bus ใน Linux ได้อย่างไร

ใช้คำสั่ง lspci ดังนี้:
```bash
sudo lspci
# Filter out results using the "grep" or "egrep" #
sudo lspci | grep -Ei 'eth|network|ethernet|wireless|wifi'
```
Outputs:
```bash
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (7) I219-LM (rev 10)
52:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a)
```
ดูเหมือนว่าฉันมีอุปกรณ์ Intel Ethernet (00:1f.6) และ Wifi (52:00.0) ที่เชื่อมต่อกับ PCI  bus ของฉัน

หากต้องการทราบข้อมูลเพิ่มเติมเกี่ยวกับอุปกรณ์เหล่านั้นและไดรเวอร์
ลองใช้ตัวเลือก -vss {ID} ที่ lscpi command:
```bash
sudo lspci -vvs 00:1f.6
```
นี่คือสิ่งที่แสดง:
```bash
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (7) I219-LM (rev 10)
	Subsystem: Lenovo Ethernet Connection (7) I219-LM
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 178
	Region 0: Memory at ee500000 (32-bit, non-prefetchable) [size=128K]
	Capabilities: [c8] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee00998  Data: 0000
	Kernel driver in use: e1000e
	Kernel modules: e1000e
```
### วิธี list รายการ physically installed network cards ทั้งหมดใน Linux โดยใช้คำสั่ง lshw, inxi, หรือ hwinfo

> **_ข้อกำหนดเบื้องต้น_**  โดยเริ่มต้น, คำสั่ง lshw, inxi, และ hwinfo อาจไม่ได้ถูกติดตั้งในระบบของคุณ ดังนั้น, ใช้คำสั่ง apk บน Alpine Linux, dnf command/yum command บน RHEL & co, apt command/apt-get command บน Debian, Ubuntu & co, zypper command บน SUSE/OpenSUSE, และ pacman command บน Arch Linux เพื่อติดตั้ง lshw, inxi, และ hwinfo

ก่อนอื่น, ติดตั้งเครื่องมือเหล่านี้ใน Debian หรือ Ubuntu Linux ของคุณโดยใช้คำสั่ง apt ตัวอย่างเช่น
```bash
sudo apt install lshw inxi hwinf
```
list NIC’s:
```bash
sudo hwinfo --short --netcard
sudo lshw -C network -short
sudo inxi -N
```
![Alt text](https://www.cyberciti.biz/media/new/faq/2010/01/How-to-List-Network-Interfaces-in-Linux.png)
source: https://www.cyberciti.biz/
### ใช้ /proc/net/dev เพื่อดู network interfaces ที่มีใน Linux
/proc/net/dev เป็นไฟล์พิเศษที่มีข้อมูลเกี่ยวกับ network device status  ข้อมูลนี้รวมถึงจำนวนของแพ็กเก็ตที่รับและส่ง, จำนวนของข้อผิดพลาดและการชนกันที่เกิดขึ้น และสถิติพื้นฐานอื่น ๆ ใช้ "cat", "bat", "more", หรือ "less" เพื่อดู เช่น:
```bash
cat /proc/net/dev
```
"ผลลัพธ์ต่อไปนี้แสดงว่ามี network interfaces lo, eth0, และ wg0 บนเซิร์ฟเวอร์ WireGuard ของฉัน:"

> **_WireGuard_**  เป็นโปรโตคอล VPN (Virtual Private Network) ที่ถูกออกแบบมาเพื่อให้ความง่ายและมีประสิทธิภาพสูง โดยพัฒนาขึ้นเป็น open-source project โดยนักพัฒนา Jason A. Donenfeld. WireGuard มีลักษณะเด่นด้านความง่ายในการติดตั้งและใช้งาน รวมถึงมีประสิทธิภาพที่ดีในการให้บริการการเชื่อมต่อทางเครือข่ายที่ปลอดภัยและรวดเร็ว
```bash
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:  164243    1526    0    0    0     0          0         0   164243    1526    0    0    0     0       0          0
  eth0: 2372840589 2027484    0    0    0     0          0         0 2467369079 2428370    0    0    0     0       0          0
   wg0: 203283936  601457  640    0    0   640          0         0 2201800868 1830420    0 1061    0     0       0          0
```
สามารถใช้คำสั่ง ls เพื่อแสดงข้อมูลเดียวกันโดยใช้ไดเรกทอรี /sys/class/net/ เช่นเดียวกัน:
```bash
ls -l /sys/class/net/
```
Outputs:
```bash
total 0
lrwxrwxrwx    1 root     root             0 Jun 17 13:30 eth0 -> ../../devices/pci0000:00/0000:00:04.0/virtio2/net/eth0
lrwxrwxrwx    1 root     root             0 Jun 17 13:30 lo -> ../../devices/virtual/net/lo
lrwxrwxrwx    1 root     root             0 Jun 17 13:31 wg0 -> ../../devices/virtual/net/wg0
```
### การรับชื่อ (getting name) ของ interface จาก /sys/class/net

นี่คือตัวอย่าง for loop ใน bash เพื่อแสดงรายการนั้นในรูปแบบที่ดี:
```bash
list=$(find /sys/class/net -type l)
for nic in $list
do
    echo "*** [ NIC: $nic ] ***"
    cat "${nic}/uevent"
    echo "" 
done
```
มันทำงานอย่างไร?
+ list=$(find /sys/class/net -type l) ใช้คำสั่ง find เพื่อค้นหา symbolic links (-type l) ภายใน /sys/class/net ผลลัพธ์ของคำสั่ง find ซึ่งประกอบด้วยรายการของ NICs ถูกเก็บไว้ในตัวแปร shell ชื่อว่า $list
+ for nic in $list เริ่มต้นด้วยการใช้ลูป for ใน bash ซึ่งวนลูปตามทุกรายการในตัวแปร list กล่าวอีกนัยหนึ่งคือ ทุกรายการจะถูกนำมาใส่ในตัวแปร $nic ตามลำดับ
+ ตัวแปร $nic คือตัวแปร shell ที่เก็บชื่อของ NIC ปัจจุบัน
+  echo "*** [ NIC: $nic ] ***" ทำหน้าที่เป็นส่วนหัวที่บ่งชี้ถึง NIC ปัจจุบันที่กำลังถูกประมวลผล
+  cat "${nic}/uevent" ทำหน้าที่อ่านและแสดงผลเนื้อหาของไฟล์ uevent ที่เกี่ยวข้องกับ NIC ปัจจุบัน, ไฟล์ uevent ให้ข้อมูลเกี่ยวกับ NIC และแอตทริบิวต์ที่เกี่ยวข้อง การใช้ "${nic}/uevent" นี้บ่งบอกรูปแบบการใช้ค่าของตัวแปร $nic เพื่อสร้างเส้นทางของไฟล์สำหรับคำสั่ง cat ได้
+  echo "" ทำหน้าที่เพิ่มบรรทัดว่างเพื่อแยกแยะผลลัพธ์สำหรับแต่ละ NIC และทำให้อ่านง่ายขึ้นในทีออน Linux โดยใช้ echo commmand

เมื่อคุณรันคำสั่งเหล่านี้ใน Linux terminal คุณจะได้รับข้อมูลต่อไปนี้เกี่ยวกับ network interfaces ใน Linux system
![alt text](https://www.cyberciti.biz/media/new/faq/2010/01/Listing-physical-network-cards-in-Linux-using-the-sys-class-net-file-1-617x1024.png)
source: https://www.cyberciti.biz/
## สรุปผล
วิธีการแสดงรายการ network interface ทั้งหมดที่ใช้ได้ใน Linux system โดยใช้ command line เพื่อดูข้อมูลเพิ่มเติมเกี่ยวกับคำสั่งที่ใช้ คุณสามารถใช้ man command/help command ร่วมกับชื่อคำสั่งที่สนใจเพื่อดูเอกสารคำสั่งและความช่วยเหลือ
```bash
man ip
ip --help
man ifconfig
man nmcli
man arp
```


## บรรณานุกรม 
website : https://www.cyberciti.biz/

chatgpt
