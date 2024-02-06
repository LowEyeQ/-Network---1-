
# LAN Card
## LAN Card หรือ Network Interface Card [NIC]
    LAN Card: ย่อมาจาก Local Area Network Card : หมายถึง การ์ดเครือข่ายที่ใช้เทคโนโลยีอีเธอร์เน็ต (Ethernet ในการเชื่อมต่อกับเครือข่ายท้องถิ่น (LAN)) 
LAN Card เป็นประเภทหนึ่งของ NIC

    Network Interface Card (NIC) : หมายถึง การ์ดใดๆ ที่ทำหน้าที่เชื่อมต่อคอมพิวเตอร์กับเครือข่าย โดยไม่จำเป็นต้องระบุเทคโนโลยีที่ใช้ 
NIC เป็นคำศัพท์ทั่วไป หมายถึง การ์ดเครือข่ายทุกประเภท

    Ethernet Network Card : หมายถึง การ์ดเครือข่ายที่ใช้เทคโนโลยีอีเธอร์เน็ตในการเชื่อมต่อกับเครือข่าย ซึ่งเป็นเทคโนโลยีที่ใช้กันแพร่หลายที่สุดในปัจจุบัน

Ethernet Network Card = Network Interface Card (ที่ใช้เทคโนโลยีอีเธอร์เน็ต)

Network Interface Card ≠ Ethernet Network Card (NIC อาจใช้เทคโนโลยีอื่น เช่น Wi-Fi, Bluetooth)

### คำอื่นๆ ที่ใช้เรียก Network Interface Card ได้แก่

* LAN Adapter

* Physical Network Interface

* Network Controller



![้hi.](https://www.shutterstock.com/shutterstock/photos/472460401/display_1500/stock-photo-network-lan-card-for-computer-isolated-on-white-background-clipping-path-for-use-472460401.jpg)

Typical Ethernet NIC PCI card



source : [https://www.shutterstock.com/th/image-photo/network-lan-card-computer-isolated-on-472460401](https://www.shutterstock.com/th/image-photo/network-lan-card-computer-isolated-on-472460401).

## การเพิ่ม NIC ใน Linux Networking
โดยทั่วไปแล้ว การ์ดเครือข่ายอีเธอร์เน็ต (Ethernet network interface) จะถูกติดตั้งไว้ภายในเมนบอร์ดของคอมพิวเตอร์รุ่นใหม่ส่วนใหญ่ โดยเฉพาะอย่างยิ่งสำหรับระบบเซิร์ฟเวอร์ ซึ่งมักจะมีการ์ดเครือข่ายติดตั้งอยู่ภายในเมนบอร์ดจำนวนสองอัน นอกจากนี้ ยังสามารถติดตั้งการ์ดเครือข่ายเพิ่มเติมลงในสล็อตเสริม PCI ได้อีกด้วย


ลองใช้คำสั่ง `lspci -vv` เพื่อดูว่าฮาร์ดแวร์ถูกตรวจจับอย่างถูกต้องหรือไม่ และโมดูลเคอร์เนลใด (ถ้ามี) กำลังถูกกำหนด:

    01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
        Subsystem: Hewlett-Packard Company Device 1309
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 52
        Region 0: Memory at f7000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: tg3
        Kernel modules: tg3

วิธีการอ่านผลลัพธ์:

    00:00.0: หมายเลขบัส อุปกรณ์ และฟังก์ชัน
    Host bridge: ประเภทอุปกรณ์
    Intel Corporation Xeon E5-2600/3600 v3/4th Gen Core Processor PCIe Express Root Port 1: ชื่ออุปกรณ์
    rev 06: เวอร์ชันอุปกรณ์
    Flags: คุณสมบัติอุปกรณ์
    Device: รหัส PCI ของอุปกรณ์
    Kernel driver in use: โมดูลเคอร์เนลที่ใช้อยู่

ลองใช้คำสั่ง `lspci -vv | grep Ethernet` เพื่อให้ได้ผลลัพธ์ที่ specifically มากขึ้น
ได้ผลลัพธ์

    1:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
    37:09.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)

คุณสมบัติอุปกรณ์ : 
* bus master: อุปกรณ์สามารถเข้าถึงหน่วยความจำหลักโดยตรง
* fast devsel: อุปกรณ์รองรับการเข้าถึง DMA ที่รวดเร็ว
* latency 0: อุปกรณ์มีความหน่วงเวลาต่ำ
* cap_list: อุปกรณ์รองรับ PCI Capabilities List
* 64bit: อุปกรณ์รองรับ PCI 64-bit
* pci_exp: อุปกรณ์เป็นอุปกรณ์ PCIe
* msi: อุปกรณ์รองรับ MSI (Message Signaled Interrupts)
* pciexpress: อุปกรณ์เป็นอุปกรณ์ PCIe Express
* vga_arbiter: อุปกรณ์รองรับ VGA arbiter
* rom_bar: อุปกรณ์มี ROM BAR (Base Address Register)
* netdev: อุปกรณ์เป็นอุปกรณ์เครือข่าย

### เครื่องมือสำหรับการกำหนดค่าเครือข่ายและไฟล์กำหนดค่าเครือข่ายนั้นแตกต่างกันไปตามระบบปฏิบัติการที่ใช้ โดยแบ่งเป็นสองกลุ่มใหญ่ๆ คือ:
**1. ระบบปฏิบัติการแบบ Debian/Ubuntu:**
* เครื่องมือ: นิยมใช้ `netplan` เป็นหลัก ซึ่งเป็นเครื่องมือจัดการคอนฟิกเครือข่ายแบบ declarative โดยกำหนดค่าเป็น YAML นอกจากนี้ ยังมีตัวเลือกอื่นๆ เช่น `ifupdown `และ `NetworkManager`
* ไฟล์กำหนดค่า: มักเก็บอยู่ในไดเร็กทอรี่ `/etc/netplan` สำหรับไฟล์ YAML ของ netplan และ `/etc/network/interfaces` สำหรับไฟล์ของ ifupdown
**เน้นความยืดหยุ่นและกำหนดค่าด้วยตนเอง ผ่านไฟล์ YAML ใน netplan

**2. ระบบปฏิบัติการแบบ Red Hat/Fedora:**
* เครื่องมือ: ส่วนใหญ่ใช้ `systemd-networkd` ซึ่งเป็นบริการที่มาพร้อมกับ systemd สำหรับการจัดการเครือข่าย หรือ `NetworkManager`
* ไฟล์กำหนดค่า: ไฟล์หลักมักเก็บอยู่ในไดเร็กทอรี่ `/etc/systemd/network` สำหรับ systemd-networkd และ `/etc/NetworkManager/conf.d` สำหรับ NetworkManager
**เน้นความสะดวกและการจัดการอัตโนมัติ ผ่าน systemd-networkd

## Linux configuration for a new card (การกำหนดค่า Linux สำหรับการ์ดใหม่) :
start network :

    sudo /etc/init.d/networking start
stop network : 

    sudo /etc/init.d/networking stop
restart network : 

    sudo /etc/init.d/networking restart

## Ubuntu network configuration:
โดยดั้งเดิม Ubuntu มีเครื่องมือ GUI สำหรับการกำหนดค่าเครือข่ายชื่อว่า **gnome-nettool** ซึ่งสามารถติดตั้งได้ด้วยคำสั่ง `apt-get install gnome-nettool`

**gnome-nettool ถูกยกเลิกการใช้งานใน Ubuntu 17.10 (Artful Aardvark) **และถูกลบออกจากที่เก็บอย่างสมบูรณ์ใน Ubuntu 18.04 (Bionic Beaver). ดังนั้น หากคุณใช้ Ubuntu เวอร์ชันใดที่ใหม่กว่า 17.10 คุณจะไม่สามารถติดตั้งหรือใช้ gnome-nettool ได้อีกต่อไป

***การกำหนดค่าเครือข่ายใน Ubuntu เวอร์ชันใหม่**
* **Netplan**: เครื่องมือหลักที่แนะนำสำหรับการกำหนดค่าเครือข่ายใน Ubuntu เวอร์ชันใหม่กว่า 17.10 ใช้ไฟล์ YAML แบบ declarative ทำให้กำหนดค่าได้ง่ายและยืดหยุ่น

จุดเด่น:

    - ใช้งานง่าย

    - กำหนดค่าได้ละเอียด

    - รองรับการเชื่อมต่อเครือข่ายหลากหลาย

    - ทำงานร่วมกับ NetworkManager ได้

ข้อจำกัด:

    - อาจจะยากสำหรับผู้ใช้ใหม่

    - ต้องการความรู้เกี่ยวกับ YAML

* **NetworkManager**: เครื่องมือ GUI ยอดนิยมสำหรับการจัดการเครือข่าย สามารถติดตั้งได้ด้วยคำสั่ง sudo apt install network-manager-gnome

จุดเด่น:

    - ใช้งานง่าย

    - อินเทอร์เฟซผู้ใช้ที่ใช้งานง่าย

    - รองรับการเชื่อมต่อเครือข่ายหลากหลาย

ข้อจำกัด:

    - ตัวเลือกการกำหนดค่าอาจจำกัดสำหรับผู้ใช้ขั้นสูง
    
    - อาจจะไม่เสถียรเท่า Netplan

* **nmtui**: เครื่องมือบรรทัดคำสั่งสำหรับ NetworkManager ใช้งานง่าย เหมาะสำหรับผู้ใช้ขั้นสูง

จุดเด่น:

    - ใช้งานง่าย

    - กำหนดค่าได้ละเอียด

    - ทำงานร่วมกับ NetworkManager ได้

ข้อจำกัด:

    - ไม่เหมาะสำหรับผู้ใช้ทั่วไป
    
    - อาจจะยากสำหรับผู้ใช้ใหม่

* **การแก้ไขไฟล์กำหนดค่าเครือข่ายด้วยตนเอง**: วิธีนี้เหมาะสำหรับผู้ใช้ขั้นสูงเท่านั้น โดยไฟล์กำหนดค่าหลักของ Netplan อยู่ในไดเร็กทอรี่ /etc/netplan

จุดเด่น:

    - กำหนดค่าได้ละเอียด

    - ควบคุมการทำงานของเครือข่ายได้เต็มที่

ข้อจำกัด:

    - ยากและซับซ้อน
    
    - อาจจะทำให้ระบบทำงานผิดพลาดได้

### - Example How to Configure Networking on Ubuntu with Netplan
1. ขั้นแรก ค้นหาชื่อของอินเทอร์เฟซเครือข่ายที่ใช้งานอยู่ที่คุณต้องการกำหนดค่า โดยให้รันคำสั่งต่อไปนี้:

        $ ip a

1. ไฟล์การกำหนดค่าเริ่มต้นของ Netplan อยู่ภายใต้ไดเร็กทอรี/etc/netplanคุณจะพบว่าใช้คำสั่งต่อไปนี้:

        $ ls /etc/netplan/

1. หากต้องการดูเนื้อหาของไฟล์การกำหนดค่าเครือข่าย Netplan ให้รันคำสั่งต่อไปนี้:

        $ cat /etc/netplan/*.yaml

1. เปิดไฟล์การ configuration file ในที่นี้ใช้ Nano เพื่อแก้ไขไฟล์การกำหนดค่า ดังนั้นจึงเรียกใช้:

        $ sudo nano /etc/netplan/*.yaml

1.  อัปเดตไฟล์การกำหนดค่าตามความต้องการด้านเครือข่าย สำหรับการกำหนดที่อยู่ IP แบบ static เพิ่มที่อยู่ IP, Gateway, DNS ในขณะที่แบบ dinamic ม่จำเป็นต้องเพิ่มข้อมูลนี้เนื่องจากจะได้รับข้อมูลนี้จากเซิร์ฟเวอร์ DHCP โดยให้รันคำสั่งต่อไปนี้:

        network:
            Version: 2
            Renderer: NetworkManager/ networkd
            ethernets:
            DEVICE_NAME:
                Dhcp4: yes/no
                Addresses: [IP_ADDRESS/NETMASK]
                Gateway: GATEWAY
                Nameservers:
                    Addresses: [NAMESERVER_1, NAMESERVER_2]

โดยที่
* DEVICE_NAME: ชื่อ interface.
* Dhcp4: "yes" or "no" ขึ้นอยู่กับการกำหนดที่อยู่ IP แบบ dynamic or static
* Addresses: IP address ในรูป prefix notation. อย่าใช้ netmask.
* Gateway: ที่อยู่ IP ของ Gateway เพื่อเชื่อมต่อกับเครือข่ายภายนอก
* Nameservers: ที่อยู่ของ DNS name servers

-ข้อควรระวัง-
**YAML ค่อนข้างเข้มงวดในการเยื้อง ใช้ช่องว่างในการเยื้อง ไม่ใช่แท็บ มิฉะนั้นคุณจะพบข้อผิดพลาด**


## How to Enable (UP)/Disable (DOWN) Network Interface Port (NIC) in Linux?

ip command : แสดงข้อมูลการ์ดอินเทอร์เฟซเครือข่ายที่มีอยู่ในระบบ Linux

    # ip a
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
        inet6 ::1/128 scope host 
        valid_lft forever preferred_lft forever
    2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether 08:00:27:c2:e4:e8 brd ff:ff:ff:ff:ff:ff
        inet 192.168.1.4/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s3
        valid_lft 86049sec preferred_lft 86049sec
        inet6 fe80::3899:270f:ae38:b433/64 scope link noprefixroute 
        valid_lft forever preferred_lft forever
    3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether 08:00:27:30:5d:52 brd ff:ff:ff:ff:ff:ff
        inet 192.168.1.3/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s8
        valid_lft 86049sec preferred_lft 86049sec
        inet6 fe80::32b7:8727:bdf2:2f3/64 scope link noprefixroute 
        valid_lft forever preferred_lft forever

## 1) Bring UP/Down Network Interface, using ifconfig command
`ifconfig` ทำงานใน boot time เพื่อตั้งค่าอินเทอร์เฟซเครือข่ายและให้ข้อมูลเกี่ยวกับ NIC

Common Syntax for ifconfig:

    # ifconfig [NIC_NAME] Down/Up

Example : **down** "enp0s3"

    ifconfig enp0s3 down

output

    # ip a sh dev enp0s3
    2: enp0s3: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
        link/ether 08:00:27:c2:e4:e8 brd ff:ff:ff:ff:ff:ff

Example : **up** "enp0s3"

    # ifconfig enp0s3 up

output

    # ip a sh dev enp0s3
    2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether 08:00:27:c2:e4:e8 brd ff:ff:ff:ff:ff:ff
        inet 192.168.1.4/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s3
        valid_lft 86294sec preferred_lft 86294sec
        inet6 fe80::3899:270f:ae38:b433/64 scope link noprefixroute 
        valid_lft forever preferred_lft forever

## 2) How to enable and disable Network Interface using ifdown/ifup command?

คำสั่ง `ifdown` จะทำให้ Network interface down ในขณะที่คำสั่ง `ifup` 
จะทำให้ Network interface up

Common Syntax for ifdown/ifup:

    # ifdown [NIC_NAME]

    # ifup [NIC_NAME]

Example : **down** and **up** "enp0s3"

    # ifdown eth1

    # ifup eth1

output

    "down"
    # ip a sh dev eth1
    3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
        link/ether 08:00:27:d5:a0:18 brd ff:ff:ff:ff:ff:ff

    "up"
    # ip a sh dev eth1
    3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
        link/ether 08:00:27:d5:a0:18 brd ff:ff:ff:ff:ff:ff
        inet 192.168.1.7/24 brd 192.168.1.255 scope global eth1
        inet6 fe80::a00:27ff:fed5:a018/64 scope link tentative dadfailed 
        valid_lft forever preferred_lft forever

**ifup และ ifdown ไม่รองรับอุปกรณ์อินเทอร์เฟซล่าสุดที่มีชื่อเช่น `enpXXX`**

## 3) Bringing UP/Down Network Interface using ip command?

Common Syntax for ip:

    # ip link set  Down/Up

Example : **down** and **up** "enp0s3"

    # ip link set enp0s3 down

    # ip link set enp0s3 up

output

    # ip a sh dev enp0s3
    2: enp0s3: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
        link/ether 08:00:27:c2:e4:e8 brd ff:ff:ff:ff:ff:ff

    # ip a sh dev enp0s3
    2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether 08:00:27:c2:e4:e8 brd ff:ff:ff:ff:ff:ff
        inet 192.168.1.4/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s3
        valid_lft 86294sec preferred_lft 86294sec
        inet6 fe80::3899:270f:ae38:b433/64 scope link noprefixroute 
        valid_lft forever preferred_lft forever

## 4) How to enable & disable Network Interface using nmcli command?

คำสั่ง `nmcli` สามารถใช้แทน `nm-applet` ได้ nmcli ใช้เพื่อสร้าง แสดง แก้ไข ลบ เปิดใช้งานและปิดใช้งานการเชื่อมต่อเครือข่าย รวมถึงควบคุมและแสดงสถานะอุปกรณ์เครือข่าย

คำสั่ง nmcli ดำเนินงานส่วนใหญ่โดยใช้ `profile name` แทน `device name` รันคำสั่งต่อไปนี้เพื่อระบุชื่ออินเทอร์เฟซ

    # nmcli con show
    NAME                UUID                                  TYPE      DEVICE 
    Wired connection 1  3d5afa0a-419a-3d1a-93e6-889ce9c6a18c  ethernet  enp0s3 
    Wired connection 2  a22154b7-4cc4-3756-9d8d-da5a4318e146  ethernet  enp0s8 

Common Syntax for nmcli:

    # nmcli con  Down/Up

เริ่มจากการใส่ `profile name` แทนการใส่ `device name` เพื่อ down interface และ up interface 

    # nmcli con down 'Wired connection 1'
    Connection 'Wired connection 1' successfully deactivated (D-Bus active path: /org/freedesktop/NetworkManager/ActiveConnection/6)


    # nmcli con up 'Wired connection 1'
    Connection successfully activated (D-Bus active path: /org/freedesktop/NetworkManager/ActiveConnection/7)

output

    # nmcli dev status
    DEVICE  TYPE      STATE         CONNECTION         
    enp0s8  ethernet  connected     Wired connection 2 
    enp0s3  ethernet  disconnected  --                 
    lo      loopback  unmanaged     --  


    # nmcli dev status
    DEVICE  TYPE      STATE      CONNECTION         
    enp0s8  ethernet  connected  Wired connection 2 
    enp0s3  ethernet  connected  Wired connection 1 
    lo      loopback  unmanaged  --  

## 5) Bringing UP/Down Network Interface using systemctl command?

คำ สั่ง `systemctl` สามารถใช้เพื่อใช้การกำหนดค่าใหม่สำหรับบริการเครือข่ายซึ่งจะ brings down and brings up >> Network Interface Cards (NIC) ทั้งหมดขึ้นมาเพื่อโหลดการกำหนดค่าใหม่

    # systemctl restart network

    # systemctl restart network.service

## 6) Bringing UP/Down Network Interface using nmtui tool?

`nmtui` เป็นแอปพลิเคชัน TUI ใช้สำหรับการโต้ตอบกับ Network Manager ช่วยให้เราสามารถกำหนดค่าอินเทอร์เฟซเครือข่ายบนระบบ Linux โดยใช้ GUI ได้อย่างง่ายดาย
รันคำสั่ง `# nmtui` เพื่อเรียกใช้   interface nmtui 
- เลือก “Activate a connection”
- กด “OK”
- เลือก interface ที่ต้องการ 
- กด “Deactivate”
- สำหรับการเปิดใช้งาน ทำตามขั้นตอนเดียวกับข้างต้นได้เลย แต่เป็นกด “Activate”









## เพิ่มเติม
* Network Interface Card (NIC) : หมายถึง การ์ดใดๆ ที่ทำหน้าที่เชื่อมต่อคอมพิวเตอร์กับเครือข่าย โดยไม่จำเป็นต้องระบุเทคโนโลยีที่ใช้

## Source เนื้อหา
* http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking-Add_NIC.html
* https://vitux.com/how-to-configure-networking-with-netplan-on-ubuntu/
* https://www.2daygeek.com enable-disable-up-down-nic-network-interface-port-linux/

