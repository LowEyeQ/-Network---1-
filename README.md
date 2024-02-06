# Network
## Introduction to Network
เนื้อหาหัวข้อเกี่ยวกับเรื่อง "Network" ใน Linux ซึ่งเป็นหัวข้อที่น่าสนใจและมีความสำคัญในการทำงานกับระบบปฏิบัติการ Linux ที่มีบทบาทสำคัญในการเชื่อมต่อและการจัดการเครือข่ายของระบบคอมพิวเตอร์ของเราทุกคน

ในรายงานนี้, จะอธิบายเกี่ยวกับวิธีการกำหนดค่าและจัดการที่อยู่ IP ในระบบ Linux, การกำหนดเส้นทางของข้อมูลในเครือข่าย,การทำความเข้าใจเกี่ยวกับตัวแทนของการเชื่อมต่อเครือข่ายบน Linux, การใช้คำสั่งที่เกี่ยวข้องกับเครือข่าย และเรื่องอื่นๆที่เกี่ยวข้อง 

หวังว่ารายงานนี้จะเป็นแหล่งข้อมูลที่เต็มไปด้วยความรู้และเพิ่มความเข้าใจให้สามารถนำไปใช้ในการทำงานกับเครือข่ายในระบบ Linux ของคุณ

## Overview
Computer networking เป็นการทำให้คอมพิวเตอร์สื่อสารกัน และการจัดการเครือข่ายของระบบคอมพิวเตอร์ ในหัวข้อนี้จะมองดูระบบเครือข่าย Ethernet กับ Linux จากองค์ประกอบต่างๆ ที่ทำให้มันทำงาน: Interface Devices, LAN Card, Wireless Adaptor, Aircard Adaptor, IP Setup, Routing, Gateway และ DNS

## Key Subcomponent of Focus
- [Interface Devices](https://github.com/LowEyeQ/Network-1/tree/main/088%20Interface%20Devices%20(Purin%20(%E2%80%A2%CB%8B%20_%20%CB%8A%E2%80%A2))) : ดูข้อมูลและสามารถตรวจสอบ network interfaces รวมทั้งดูเอกสารคำสั่งและความช่วยเหลือ
- [LAN Card](https://github.com/LowEyeQ/Network-1/tree/main/017%20LAN%20Card%20(KanphitchaNeamsri)) : การ์ดเครือข่ายที่ใช้เทคโนโลยีอีเธอร์เน็ต (Ethernet) ในการเชื่อมต่อกับเครือข่ายท้องถิ่น (LAN)
- [Wireless Adaptor](https://github.com/LowEyeQ/Network-1/tree/main/086%20Wireless%20Adaptor%20(bncnkktn)) : 
- [Aircard Adaptor](https://github.com/LowEyeQ/Network-1/tree/main/050%20Aircard%20Adaptor%20(Chalisa%20Suntithanyachok)) : 
- [IP Setup](https://github.com/LowEyeQ/Network-1/tree/main/037%20IP%20Setup%20(LowEyeQ)) : 
- [Routing](https://github.com/LowEyeQ/Network-1/tree/main/033%20Routing%20(J-Jindamanee)) : 
- [Gateway](https://github.com/LowEyeQ/Network-1/tree/main/057%20Gateway%20(Titaree-Ravi)) : ตัวกลางที่เชื่อมต่อระบบเครือข่ายภายในเครื่อง Linux กับเครือข่ายภายนอก โดยทำหน้าที่เป็นตัวกลางในการส่งข้อมูล และสามารถอนุญาตให้คอมพิวเตอร์ในเครือข่ายท้องถิ่นเข้าถึงทรัพยากรบนอินเทอร์เน็ตได้
- [DNS](https://github.com/LowEyeQ/Network-1/tree/main/088%20DNS%20Purin%20((%E2%80%A2%CB%8B%20_%20%CB%8A%E2%80%A2))) : ระบบที่ใช้แปลงชื่อโดเมนเป็นที่อยู่ IP และช่วยให้ระบบเครือข่ายทำงานได้อย่างมีประสิทธิภาพและเป็นระบบ

## สิ่งที่เหมือนหรือใกล้เคียงกัน
สิ่งที่ 8 Key Subcomponent of Focus มีเหมือนหรือใกล้เคียงกันบน Linux คือการแสดงข้อมูล และกำหนดค่าเครือข่าย

##Reference
- https://www.oreilly.com/library/view/linux-networking-cookbook/9780596102487/ch01.html
