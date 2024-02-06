
# LAN Card
## LAN Card หรือ Network Interface Card [NIC]
    LAN Card: ย่อมาจาก Local Area Network Card : หมายถึง การ์ดเครือข่ายที่ใช้เทคโนโลยีอีเธอร์เน็ต (Ethernet ในการเชื่อมต่อกับเครือข่ายท้องถิ่น (LAN) 
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



![้hi.](https://techterms.com/img/lg/nic_98.jpg)

Typical Ethernet NIC PCI card



source : [http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking-Add_NIC.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking-Add_NIC.html).

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

## เพิ่มเติม
* Network Interface Card (NIC) : หมายถึง การ์ดใดๆ ที่ทำหน้าที่เชื่อมต่อคอมพิวเตอร์กับเครือข่าย โดยไม่จำเป็นต้องระบุเทคโนโลยีที่ใช้

## Source เนื้อหา
* http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking-Add_NIC.html
