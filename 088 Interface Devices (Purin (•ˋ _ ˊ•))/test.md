# Interface device

![Alt text](https://cdn.pixabay.com/photo/2016/05/25/18/18/penguin-1415562_1280.png)
source: [linux image](https://pixabay.com/th/vectors/%E0%B9%80%E0%B8%9E%E0%B8%99%E0%B8%81%E0%B8%A7%E0%B8%99-tux-%E0%B8%AA%E0%B8%95%E0%B8%A7-%E0%B8%99%E0%B8%81-%E0%B8%99%E0%B8%B2%E0%B8%A3%E0%B8%81-1415562/)

## บทบาทหน้าที่

interface device มีบทบาทและหน้าที่สำคัญในการเชื่อมต่อระหว่างซอฟต์แวร์และฮาร์ดแวร์

#### ต่อไปนี้คือบางหน้าที่หลักของ interface device ใน Linux
1. การเชื่อมต่อระบบปฏิบัติการกับอุปกรณ์ฮาร์ดแวร์: Interface device เป็นตัวกลางที่ช่วยให้ระบบปฏิบัติการ Linux สามารถติดต่อและทำงานกับอุปกรณ์ฮาร์ดแวร์ต่าง ๆ ได้ เช่น การเชื่อมต่อกับเครือข่าย (Network Interface Card - NIC), การใช้งาน USB devices, หรือการจัดการกับอุปกรณ์เกี่ยวกับเสียงและวีดีโอ

2. การจัดการไดรเวอร์ (Driver Management): Interface device ใน Linux มักต้องใช้ไดรเวอร์เพื่อให้ระบบปฏิบัติการสามารถทำงานกับฮาร์ดแวร์ได้อย่างถูกต้อง การจัดการไดรเวอร์นี้เป็นหน้าที่สำคัญของ interface device เพื่อให้ระบบสามารถรู้จักและปรับให้กับอุปกรณ์ต่าง ๆ ที่เชื่อมต่อ

3. การจัดการการสื่อสาร (Communication Management): Interface device มีหน้าที่ในการจัดการการสื่อสารระหว่างซอฟต์แวร์และฮาร์ดแวร์ นอกจากนี้ยังรวมถึงการจัดการข้อมูลที่ได้รับและส่งออกจากระบบ

4. การทำงานร่วมกับ Kernel: Interface device ทำงานร่วมกับ Linux Kernel เพื่อให้ระบบปฏิบัติการสามารถเข้าถึงและควบคุมฮาร์ดแวร์ได้อย่างเหมาะสม

5. การรับรู้เหตุการณ์ (Event Handling): Interface device สามารถรับรู้เหตุการณ์ที่เกิดขึ้นในระบบ เช่น การกดปุ่ม, การตรวจจับอุปกรณ์ที่เสียหาย, หรือเหตุการณ์อื่น ๆ ที่สำคัญ

6. การจัดการพลังงาน (Power Management): บาง interface device มีบทบาทในการจัดการพลังงานของอุปกรณ์ฮาร์ดแวร์ เพื่อประหยัดพลังงานหรือการจัดการในรูปแบบอื่น ๆ

![Alt text](https://cdn.pixabay.com/photo/2018/03/10/12/00/teamwork-3213924_1280.jpg)
source : [image](https://pixabay.com/th/photos/%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%97%E0%B8%B2%E0%B8%87%E0%B8%B2%E0%B8%99%E0%B9%80%E0%B8%9B%E0%B8%99%E0%B8%97%E0%B8%A1-%E0%B8%84%E0%B8%A7%E0%B8%B2%E0%B8%A1%E0%B8%A3%E0%B8%A7%E0%B8%A1%E0%B8%A1%E0%B8%AD-3213924/)

## พื้นฐานและหลักการทำงาน

พื้นฐานหรือหลักการทำงานของ interface device ใน Linux มีลักษณะดังนี้:

**Device Files:**
* Interface device มักถูกแทนด้วย device file ในระบบไฟล์ของ Linux, ซึ่งประกอบด้วย `/dev` และมักจะมีชื่อเฉพาะสำหรับแต่ละอุปกรณ์ เช่น `/dev/sda` สำหรับ hard drive หรือ `/dev/ttyUSB0` สำหรับ USB serial device

**Kernel Modules:**
- บาง interface device ต้องใช้ kernel module เพื่อทำงานในระบบ โมดูลเหล่านี้จะถูกโหลดหรือถูกสร้างขึ้นเมื่อ interface device ถูกเชื่อมต่อกับระบบ

**Kernel Space vs. User Space:**
* การทำงานของ interface device มักเกิดใน kernel space และ user space ของระบบปฏิบัติการ Linux โดย kernel space มีการทำงานที่ใกล้เคียงกับฮาร์ดแวร์ และ user space มีการทำงานที่เกี่ยวข้องกับแอปพลิเคชันและการให้บริการสู่ผู้ใช้

**Interrupts:**
- Interface device สามารถใช้ interrupts เพื่อแจ้งเหตุการณ์หรือสถานะของอุปกรณ์กับระบบ ซึ่งทำให้ kernel สามารถตอบสนองได้อย่างรวดเร็ว

**File Operations:**
- แต่ละ interface device มี file operations เฉพาะที่ kernel สามารถเรียกใช้เพื่อทำงานกับอุปกรณ์นั้น ๆ เช่น read, write, open, close, ioctl (input output control) ฯลฯ

**Device Drivers:**
- Interface device มักจะต้องมี device driver ที่เป็นโปรแกรมที่ทำหน้าที่ควบคุมการทำงานของอุปกรณ์นั้น ๆ บนระบบปฏิบัติการ Linux

**Sysfs and Procfs:**
- Linux มี sysfs และ procfs ที่ให้ข้อมูลเกี่ยวกับอุปกรณ์และการทำงานของระบบ ผู้ใช้หรือแอปพลิเคชันสามารถอ่านหรือแก้ไขค่าต่าง ๆ ที่เกี่ยวข้องกับ interface device ผ่าน sysfs หรือ procfs

**File Descriptors:**
- Interface device มักถูกเปิดและใช้งานผ่าน file descriptors ซึ่งเป็นเลขที่กำหนดให้กับไฟล์ที่เปิดใช้งานการทำงานของ interface device ใน Linux มีความซับซ้อนและการทำงานที่ทันสมัย เนื่องจากระบบปฏิบัติการ Linux ได้รับการพัฒนาอย่างต่อเนื่องและรองรับหลายประเภทของอุปกรณ์และการเชื่อมต่อต่าง ๆ ในโลกของฮาร์ดแวร์

## เริ่มกันที่ Lspci Command
นี่คือตัวอย่างทั่วไป
```
lspci

```
ในตัวอย่างเราใช้ lspci ปราศจาก ```options``` หรือ ```flag``` คำสั่งนีจะแสดง list ของอุปกรณ์ PCI ทั้งหมด พร้อมกับประเภทและรายละเอียดผู้ผลิต

### การใช้งานขั้นสูงของ Lspci

|**Argument**	 | **Description** | 
| :-------- | :------- | 
| **-v** | แสดงผลลัพธ์อย่างละเอียด (verbose) โดยแสดงข้อมูลเพิ่มเติมเกี่ยวกับแต่ละอุปกรณ์ เช่น ```lspci -nn``` |
|**-nn**|แสดงทั้ง vendor และ device code เช่น `lspci -nn`|
|**-k**|แสดง kernel drivers ที่รับผิดชอบการจัดการกับแต่ละอุปกรณ์ เช่น `lspci -k`|
|**-t**|แสดงอุปกรณ์ในรูปแบบของไดอะแกรมต้นไม เช่น `lspci -t`|
|**-i**|ใช้ไฟล์ PCI ID ที่ระบุแทนที่จะใช้ค่าเริ่มต้น เช่น `lspci -i` หรือ `/path/to/pci.ids`|
|**-d**|แสดงเฉพาะอุปกรณ์ที่มี vendor และ device ID ที่ระบุ เช่น `lspci -d 8086:100e`|
|**-s**|แสดงเฉพาะอุปกรณ์ในบัสที่ระบุเช่น `lspci -s 00:02.0`|
|**-x**|แสดงบางส่วนแรกของพื้นที่การกำหนดค่า เช่น `lspci -x`|
|**-xxx**|แสดงพื้นที่การกำหนดค่าทั้งหมด (***เฉพาะ root เท่านั้น) เช่น `lspci -xxx`|
|**-A**|ใช้วิธีการเข้าถึงที่ระบุเพื่ออ่านพื้นที่การกำหนดค่าฮาร์ดแวร์ของ PCI เช่น `lspci -A intel-conf1`|
|**-D**|แสดงหมายเลขโดเมนเสมอ เช่น `lspci -D`|
|**-F**|อ่านค่าการกำหนดค่าจากไฟล์ที่ระบุ เช่น `lspci -F dump.txt`|

### การแสดงผลลัพธ์อย่างละเอียด
**command**
```
lspci -v
```
**output**
```
00:01.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 6GB] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Gigabyte Technology Co., Ltd GP106 [GeForce GTX 1060 6GB]
	Flags: bus master, fast devsel, latency 0, IRQ 33
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	[virtual] Expansion ROM at f7000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
```
การใช้คำสั่ง ```lspci -v``` ใน Linux จะแสดงข้อมูลเกี่ยวกับอุปกรณ์ที่เชื่อมต่อผ่าน PCI bus โดยรายละเอียด ซึ่งประกอบด้วยข้อมูลเช่น vendor ID, device ID, ที่อยู่ของหน่วยความจำ, ข้อมูล I/O ports, และ driver ที่กำลังใช้งาน


## ทางเลือกอื่นนอกจาก lspci Command
นอกจากคำสั่ง ```lspci```แล้วยังมีเครื่องมือและคำสั่งทดแทนอื่นที่สามารถช่วยจัดการและแสดงรายการอุปกรณ์ PCI ใน Linux ได้
###  lsusb Command
**command**
```
lsusb
```
**output**
```
Bus 002 Device 002: ID 045e:0773 Microsoft Corp.
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation
Bus 001 Device 003: ID 04f2:b685 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation
```
คำสั่ง ```lsusb``` ใน Linux ถูกใช้เพื่อแสดงรายการของอุปกรณ์ USB ที่เชื่อมต่อกับระบบการใช้คำสั่งนี้จะช่วยในการตรวจสอบว่าอุปกรณ์ USB ต่าง ๆ ถูกตรวจพบและเชื่อมต่อกับระบบอย่างไร รายการที่แสดงอาจรวมถึงข้อมูลเชิงละเอียดเกี่ยวกับผู้ผลิต, รหัสผลิตภัณฑ์, และรายละเอียดเพิ่มเติมของอุปกรณ์ USB

### lshw Command
**command**
```

```
**output**
```

```




https://docs.nvidia.com/networking-ethernet-software/cumulus-linux-55/Layer-1-and-Switch-Ports/Interface-Configuration-and-Management/
https://ioflood.com/blog/lspci-linux-command/
https://readme.so/editor
