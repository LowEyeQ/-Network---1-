# Wireless Adapter
## Wireless Adapter คืออะไร
Wireless Adapter หรือ Wireless USB Adapter คืออุปกรณ์ที่ใช้สำหรับเชื่อมต่อกับเครือข่ายคอมพิวเตอร์แบบไร้สาย หรือเรียกง่าย ๆ ว่า ตัวรับสัญญาณไวไฟ จำเป็นต้องใช้งานกับจุดที่มีเราท์เตอร์ปล่อยสัญญาณไวไฟ เน้นใช้งานร่วมกับคอมพิวเตอร์ โดยวิธีการใช้งานเพียงแค่เชื่อมต่อผ่านพอร์ต USB ก็สามารถรับสัญญาณไวไฟได้ทันที ไม่สามารถปล่อยสัญญาณไปให้อุปกรณ์อื่น ๆ เป็นอุปกรณ์ที่มีขนาดเล็ก ใช้งานง่ายสำหรับพีซี แล็ปท็อป และอุปกรณ์อัจฉริยะต่าง ๆ เช่น ทีวี เครื่องควบคุมอุณหภูมิแบบตั้งโปรแกรมได้ กล้องวงจรปิด และอุปกรณ์ที่คล้ายกัน โดยจะประกอบด้วยเครื่องส่งสัญญาณไวไฟ หรือสัญญาณวิทยุ เมื่อทำการเชื่อมต่อแล้ว จะช่วยให้อุปกรณ์สามารถเชื่อมต่อแบบไร้สายกับอุปกรณ์อื่นหรืออินเทอร์เน็ตได้
  ______
Wireless USB Adapter สำหรับพีซีและอุปกรณ์ที่คล้ายกันเป็นอุปกรณ์ Plug-and-Play ที่เพียงแค่เสียบเข้ากับพอร์ตก็สามารถใช้งานได้ทั้ง Windows และ macOS ในเวอร์ชันปัจจุบันจะโหลดไดรเวอร์ที่จำเป็นอัตโนมัติ อุปกรณ์ USB ทั้งหมดนั้นเป็นแบบ Hot-swappable หมายความว่าสามารถเชื่อมต่อและยกเลิกการเชื่อมต่อได้โดยไม่ต้องรีบูตอุปกรณ์โฮสต์

![image](https://www.dlink.co.th/wp-content/uploads/2021/07/DWA-185-2.jpg) ![image](https://res.cloudinary.com/itcity-production/image/upload/f_jpg,q_80/v1651032195/product/product-master/cku9huiny6siibse8xm0.jpg)

(source : https://www.tp-link.com/ae/blog/378/what-is-a-wifi-adapter-and-how-to-pick-the-best-one-for-you-/#:~:text=A%20WiFi%20adapter%20allows%20your,to%20the%20latest%20WiFi%20generation.)

## Wireless Adapter เหมาะกับใคร
- **ใช้คอมพิวเตอร์รุ่นเก่าหรือ PC ประกอบเอง** ไม่มีการ์ด wifi ทำให้ไม่สามารถเชื่อมต่ออินเทอร์เน็ตได้ 
- **สัญญาณไวไฟค่อนข้างช้า** หากคอมพิวเตอร์เชื่อมต่อสัญญาณได้ แต่รู้สึกว่าสัญญาณช้ากว่าที่ควรจะเป็น อาจเป็นไปได้ว่าการ์ด wifi มีปัญหาหรืออยู่ห่างจากจุดปล่อยสัญญาณมากเกินไป อุปกรณ์นี้ช่วยให้การดึงสัญญาณไวไฟทำได้ดีขึ้น

## การตั้งค่า Wireless adapter บน Linux
   โดยการตั้งค่า Wireless adapter บน Linux จะเกี่ยวข้องกับหลายขั้นตอน โดยจะมีขั้นตอนการติดตั้งไดรเวอร์ การกำหนดการตั้งค่าเครือข่าย และการเชื่อมต่อกับเครือข่ายไร้สาย 
   1. **ระบุ Wireless Adapter** : จะใช้คำสั่ง **lspci** เพื่อแสดงรายการอุปกรณ์ PCI (Peripheral Component Interconnect) ทั้งหมดที่มีการเชื่อมต่อกับระบบ โดยรวมถึงอุปกรณ์ต่าง ๆ เช่น network adapters, graphics cards, sound cards, USB controllers และอื่นๆ หรือ **lsusb** เพื่อระบุผู้ผลิตและรุ่นของ Wireless adapter เพื่อช่วยค้นหาไดรเวอร์ที่เหมาะสม
  ตัวอย่างผลลัพธ์ของ `lspci` :
```00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
...
```
