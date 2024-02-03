# Gateway
Gateway คืออุปกรณ์เป็นตัวกลางที่เชื่อมต่อระหว่างเครือข่ายสองเครือข่ายเข้าด้วยกัน 

ในบริบทของ Linux 
Gateway มักถูกใช้เพื่อเชื่อมต่อเครือข่ายท้องถิ่นกับอินเทอร์เน็ต เป็นตัวกลางที่เชื่อมต่อระบบเครือข่ายภายในเครื่อง Linux กับเครือข่ายภายนอก โดยทำหน้าที่เป็นตัวกลางในการส่งข้อมูล

Gateway สามารถเป็นอุปกรณ์ Hardware เช่น Router หรือสามารถเป็นโปรแกรมซอฟต์แวร์ เช่น เซิร์ฟเวอร์พร็อกซี

โดยการใช้Gateway  สามารถอนุญาตให้คอมพิวเตอร์ในเครือข่ายท้องถิ่นเข้าถึงทรัพยากรบนอินเทอร์เน็ตได้


## พื้นฐาน หรือหลักการทำงาน
Gateway บน Linux ทำงานโดยใช้หลักการของ IP forwarding ซึ่งเป็นการเปิดใช้งานการส่งข้อมูลระหว่างเครื่องในเครือข่ายภายในกับเครือข่ายภายนอก. การตั้งค่า IP forwarding ให้เครื่อง Linux ทำหน้าที่เป็น Gateway โดยสามารถส่งข้อมูลต่อไปยังเครื่องปลายทาง


## การเรียกใช้งานและผลลัพธ์ที่ได้
[Comment]: # (แต่ละ Command ที่เกี่ยวข้องนั้น มี Options หรือ Arguments อะไรที่ควรทราบ และได้อะไรออกมา
- ตัวอย่าง Code การเรียกใช้งานที่ต้องการผลลัพธ์แบบต่างๆ)

## วิธีหา Gateway ip ด้วยคำสั่ง ip router บน Linux
```ip route``` หรือ ```ip r``` เมื่อรันคำสั่ง ip route โดยไม่ใส่ arguments ใดๆ หรือจะใช้ arguments ```show``` จะแสดงตารางเส้นทางปัจจุบัน รวมถึงข้อมูลเกี่ยวกับ network destinations, the gateway, and the network interface associated กับเส้นทางแต่ละเส้นทาง

![Alt text](https://media.geeksforgeeks.org/wp-content/uploads/20200512170105/To-get-details-of-the-kernel-IP-routing-table-using-ip-command1.png)
source : https://www.geeksforgeeks.org/route-command-in-linux-with-examples/

## วิธีตรวจสอบที่อยู่ gateway ip ด้วย route command บน Linux
คำสั่ง ```route``` สามารถใช้ตรวจสอบที่อยู่ gateway ip
![Alt text](https://media.geeksforgeeks.org/wp-content/uploads/20200512153722/To-display-the-IP-kernel-routing-table.png)
source : https://www.geeksforgeeks.org/route-command-in-linux-with-examples/

สามารถแสดงตารางเส้นทางในรูปแบบตัวเลขเต็ม โดย ```route -n```
![Alt text](https://media.geeksforgeeks.org/wp-content/uploads/20200512153837/To-display-routing-table-in-full-numeric-form.png)
source : https://www.geeksforgeeks.org/route-command-in-linux-with-examples/

จะแสดงเส้นทางทั้งหมดที่กำหนดค่าในระบบ 
U หมายถึงเส้นทาง 'up' และ 
G บ่งบอกว่านั่นคือ Gateway

## อภิปรายในเรื่องที่น่าสนใจ เช่น ข้อควรระวังในการใช้งาน, Bug, หรือช่องโหว่ ฯลฯ

## อื่นๆที่น่าสนใจ

### Reference 
https://www.howtouselinux.com/post/linux-command-get-network-gateway
