# Gateway
Gateway คืออุปกรณ์เป็นตัวกลางที่เชื่อมต่อระหว่างเครือข่ายสองเครือข่ายเข้าด้วยกัน 

ในบริบทของ Linux 
Gateway มักถูกใช้เพื่อเชื่อมต่อเครือข่ายท้องถิ่นกับอินเทอร์เน็ต เป็นตัวกลางที่เชื่อมต่อระบบเครือข่ายภายในเครื่อง Linux กับเครือข่ายภายนอก โดยทำหน้าที่เป็นตัวกลางในการส่งข้อมูล

Gateway สามารถเป็นอุปกรณ์ Hardware เช่น Router หรือสามารถเป็นโปรแกรมซอฟต์แวร์ เช่น เซิร์ฟเวอร์พร็อกซี

โดยการใช้ Gateway  สามารถอนุญาตให้คอมพิวเตอร์ในเครือข่ายท้องถิ่นเข้าถึงทรัพยากรบนอินเทอร์เน็ตได้


## พื้นฐาน หรือหลักการทำงาน
Gateway บน Linux ทำงานโดยใช้หลักการของ IP forwarding ซึ่งเป็นการเปิดใช้งานการส่งข้อมูลระหว่างเครื่องในเครือข่ายภายในกับเครือข่ายภายนอก. การตั้งค่า IP forwarding ให้เครื่อง Linux ทำหน้าที่เป็น Gateway โดยสามารถส่งข้อมูลต่อไปยังเครื่องปลายทาง


## วิธีหา Gateway ip ด้วยคำสั่ง ip router บน Linux
```ip route``` หรือ ```ip r``` เมื่อรันคำสั่ง ip route โดยไม่ใส่ arguments ใดๆ หรือจะใช้ arguments ```show``` จะแสดงตารางเส้นทางปัจจุบัน รวมถึงข้อมูลเกี่ยวกับ network destinations, the gateway, and the network interface associated กับเส้นทางแต่ละเส้นทาง

![Alt text](https://media.geeksforgeeks.org/wp-content/uploads/20200512170105/To-get-details-of-the-kernel-IP-routing-table-using-ip-command1.png)

source : https://www.geeksforgeeks.org/route-command-in-linux-with-examples/

## วิธีตรวจสอบที่อยู่ Gateway ip ด้วย route command บน Linux
คำสั่ง ```route``` สามารถใช้ตรวจสอบที่อยู่ gateway ip
![Alt text](https://media.geeksforgeeks.org/wp-content/uploads/20200512153722/To-display-the-IP-kernel-routing-table.png)

source : https://www.geeksforgeeks.org/route-command-in-linux-with-examples/

สามารถแสดงตารางเส้นทางในรูปแบบตัวเลขเต็ม โดย ```route -n```
![Alt text](https://media.geeksforgeeks.org/wp-content/uploads/20200512153837/To-display-routing-table-in-full-numeric-form.png)

source : https://www.geeksforgeeks.org/route-command-in-linux-with-examples/

จะแสดงเส้นทางทั้งหมดที่กำหนดค่าในระบบ 
U หมายถึงเส้นทาง 'up' และ 
G บ่งบอกว่านั่นคือ Gateway

## วิธีหา Gateway ip ด้วยคำสั่ง netstat ใน Linux
คำสั่ง ```netstat``` ใช้ดูทุกการเชื่อมต่อเครือข่ายที่ทำงานบนระบบเพื่อหา Gateway โดย Gateway จะปรากฎในคอลัมน์ "Gateway"
![Alt text](https://media.geeksforgeeks.org/wp-content/uploads/kernel.png)

source : https://www.geeksforgeeks.org/netstat-command-linux/

Netstat จะแสดงการเชื่อมต่อเครือข่ายทั้งหมดที่ทำงานและสถานะของพวกมัน

มี Option ที่มาใช้แสดงแค่บางจุด เช่น
- ```-a``` แสดงการเชื่อมต่อทั้งหมด
- ```-r``` แสดงตารางเส้นทาง
- ```-t``` แสดงพอร์ตที่เปิดใช้งานแบบ TCP
- ```-n``` แสดงข้อมูลที่เกี่ยวกับเส้นทาง (route)
- ```-l``` แสดงเฉพาะรายการที่กำลังฟัง (listening)

ถ้าต้องการดูข้อมูลเพิ่มเติมเกี่ยวกับการเชื่อมต่อที่แน่นอน สามารถใช้ตัวเลือก ```-a``` เช่น ถ้าคุณต้องการดูข้อมูลเพิ่มเติมเกี่ยวกับการเชื่อมต่อกับ 192.168.0.0/24 โดยพิมพ์ ```netstat -a | grep 192.168.0.0/24```

## วิธีเปลี่ยน Default gateway บน Linux
คำสั่งในการเปลี่ยนเกตเวย์เริ่มต้นใน Linux คือ ```route``` เช่น ถ้าต้องการเพิ่ม default gateway ใหม่ด้วยที่อยู่ IP 192.168.1.1 

จะใช้คำสั่งต่อไปนี้: ```route add defualt gw 192.168.1.1```

![Alt text](https://lintut.com/wp-content/uploads/2015/01/Add-Default-Gateway.png)

source : https://lintut.com/how-to-use-route-command-on-rhelcentos-linux/

## วิธีการกำหนดค่า Gateway Linux ด้วย Iptables
```iptables``` สามารถใช้ในการกำหนดค่า Gateway NAT ถูกใช้ในการแปลงที่อยู่ IP สาธารณะเป็นที่อยู่ IP ส่วนตัว ซึ่งช่วยให้อุปกรณ์หลายตัวสามารถแบ่งปันที่อยู่ IP สาธารณะเดียวได้ เป็นประโยชน์ในการรักษาความปลอดภัยของเครือข่ายภายในในขณะที่ยังอนุญาตการเข้าถึงจากภายนอก โดยมีขั้นตอนดังนี้

 1. ตั้งค่า Firewall
ขั้นตอนแรกในการกำหนดค่า Gateway Linux ด้วย Iptables คือการตั้งค่า Firewall โดยการสร้างกฎที่ควบคุมการไหลเวียนของการจราจรเข้าและออกจากเครือข่าย กฎนี้สามารถใช้เพื่อบล็อกการจราจรที่เป็นอันตราย อนุญาตเฉพาะการจราจรที่ได้รับอนุญาตเท่านั้น และอื่น ๆ

ในการสร้าง Firewall คำสั่ง ```iptables``` จะต้องใช้ เป็นตัวอย่าง คำสั่งต่อไปนี้จะบล็อกการจราจรทั้งหมดที่มีที่อยู่ IP 192.168.1.2:

ตัวอย่าง Code
```iptables -A INPUT -s 192.168.1.2 -j DROP```

คำสั่งนี้บอกให้ Iptables บล็อกการจราจรทั้งหมดที่มีที่อยู่ IP 192.168.1.2

2. ตั้งค่า Gateway NAT
สร้างกฎที่แปลงที่อยู่ IP สาธารณะเป็นที่อยู่ IP ส่วนตัว จะช่วยให้อุปกรณ์หลายตัวสามารถแบ่งปันที่อยู่ IP สาธารณะเดียวได้ 
ในการสร้าง Gateway NAT คำสั่ง ```iptables ``` จะต้องใช้อีกครั้ง ครั้งนี้คำสั่งนำเข้า Argument และ Option: ที่อยู่ IP สาธารณะที่จะแปลงและที่อยู่ IP ส่วนตัวที่จะแปลงไป

ตัวอย่าง Code
```
iptables -t nat -A POSTROUTING -o eth0 -d 10.0.0.1 -j SNAT --to-source 192.168.1.2
```
- ```-t nat``` : เป็น option ที่ระบุว่าเรากำลังทำงานในตาราง nat ของ iptables
- ```-A``` : เป็น argument ที่ระบุ chain POSTROUTING ในตาราง nat ที่เราต้องการเพิ่มกฎ
- ```-o``` : เป็น option ที่ระบุว่าแพ็คเก็ตจะออกไปทางอินเทอร์เฟสไหน
- ```-d``` : เป็น option ที่ระบุว่าแพ็คเก็ตที่มีที่อยู่ปลายทางเป็นอะไร
- ```-j SNAT --to-source```: เป็น argument ที่ระบุว่าจะให้ใช้ SNAT เพื่อแปลงที่อยู่ IP เป็นที่อยู่ IP ของตนเอง (NAT)

คำสั่งนี้บอกให้ Iptables แปลงที่อยู่ IP สาธารณะ 192.168.1.2 เป็นที่อยู่ IP ส่วนตัว 10.0.0.1

3. ตั้งค่าการตรวจสอบ Port
สร้างกฎที่ส่งต่อการจราจรจาก Port หนึ่งไปยังอีก Port 

สามารถใช้ส่งต่อการจราจรจากที่อยู่ IP สาธารณะไปยังที่อยู่ IP ส่วนตัว หรือส่งต่อการจราจรจากพอร์ตหนึ่งไปยังอีก Port บนเครื่องเดียวกัน
ในการตั้งค่าการตรวจสอบ Port คำสั่ง iptables จะต้องใช้อีกครั้ง  คำสั่งนำเข้า Argument และ Option: Port ที่จะส่งต่อการจราจร, พอร์ตที่จะส่งต่อไป, และที่อยู่ IP ที่จะส่งต่อไป

ตัวอย่าง Code
```
iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j DNAT --to 192.168.1.2:8080
```

- ```-A PREROUTING``` : เป็น argument ที่ระบุ chain PREROUTING ในตาราง nat ที่เราต้องการเพิ่มกฎ
- ```-t``` : เป็น option ที่ระบุว่าเรากำลังทำงานในตาราง nat ของ iptables
- ```-i``` : เป็น option ที่ระบุว่าแพ็คเก็ตเข้าถึงทางอินเทอร์เฟสไหน
- ```-p``` : เป็น option ที่ระบุ protocol ที่ใช้ (ในที่นี้คือ TCP).
- ```--dport``` : เป็น option ที่ระบุว่าแพ็คเก็ตมี Port ปลายทางเป็นอะไร
- ```-j DNAT --to``` : เป็น argument ที่ระบุว่าจะให้ใช้ DNAT เพื่อแปลงที่อยู่ IP เป็นที่อยู่ IP ของตนเองและพอร์ต (Destination NAT).
- ```-I``` : insert rule
- ```-D``` : ลบ rule

คำสั่งนี้บอกให้ Iptables ส่งต่อการจราจรจากพอร์ต 80 ไปยังพอร์ต 8080 บนที่อยู่ IP 192.168.1.2

## ข้อควรระวัง: 
ควรรักษาความปลอดภัยของ Gateway ด้วยการปิดบางบริการที่ไม่จำเป็นและการตั้งค่า Firewall อย่างถูกต้อง และควรตรวจสอบเสมอเพื่อตรวจหาช่องโหว่ในระบบและทำการปรับปรุงหรือปิดไฟล์ที่มีช่องโหว่

## ความแตกต่างระหว่าง Gateway และ Router คืออะไร?
Gateway คืออุปกรณ์ที่เชื่อมต่อระหว่างเครือข่ายสองเครือข่าย 

Router เป็นประเภทหนึ่งของเกตเวย์ที่ใช้เชื่อมต่อระหว่างเครือข่ายคอมพิวเตอร์สองเครือข่ายหรือมากกว่า

## ความแตกต่างระหว่าง Default gateway และ Static route คืออะไร?
Gateway เริ่มต้นคือ Router เครือข่ายที่คอมพิวเตอร์ของคุณใช้เพื่อเชื่อมต่อกับอินเทอร์เน็ต

Static route คือเส้นทางที่ได้รับการกำหนดค่าด้วยผู้ใช้

## Reference
Book
- https://www.lions-wing.net/lessons/networking-1/schroder_-_linux_networking_cookbook_oreilly_2008.pdf?fbclid=IwAR0yWYnolkFhIrIvvNV5EnMBDn2Ys0Pppo55iK0tE7rj02_17-igKMy-ufU

Web site
- https://www.howtouselinux.com/post/linux-command-get-network-gateway

- https://access.redhat.com/documentation/th-th/red_hat_enterprise_linux/6/html/deployment_guide/s1-networkscripts-static-routes

- https://www.cyberciti.biz/faq/how-to-find-gateway-ip-address/

- https://www.geeksforgeeks.org/route-command-in-linux-with-examples/

- https://www.linuxfordevices.com/tutorials/linux/iptables-forward-traffic-in-linux
