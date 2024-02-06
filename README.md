# Network
## บทคัดย่อ
เนื้อหาหัวข้อเกี่ยวกับเรื่อง "Network" ใน Linux ซึ่งเป็นหัวข้อที่น่าสนใจและมีความสำคัญในการทำงานกับระบบปฏิบัติการ Linux ที่มีบทบาทสำคัญในการเชื่อมต่อและการจัดการเครือข่ายของระบบคอมพิวเตอร์ของเราทุกคน

ในรายงานนี้, จะอธิบายเกี่ยวกับวิธีการกำหนดค่าและจัดการที่อยู่ IP ในระบบ Linux, การกำหนดเส้นทางของข้อมูลในเครือข่าย,การทำความเข้าใจเกี่ยวกับตัวแทนของการเชื่อมต่อเครือข่ายบน Linux, การใช้คำสั่งที่เกี่ยวข้องกับเครือข่าย และเรื่องอื่นๆที่เกี่ยวข้อง 

หวังว่ารายงานนี้จะเป็นแหล่งข้อมูลที่เต็มไปด้วยความรู้และเพิ่มความเข้าใจให้สามารถนำไปใช้ในการทำงานกับเครือข่ายในระบบ Linux ของคุณ

## Overview
Computer networking เป็นการทำให้คอมพิวเตอร์สื่อสารกัน และการจัดการเครือข่ายของระบบคอมพิวเตอร์ ในหัวข้อนี้จะมองดูระบบเครือข่าย Ethernet กับ Linux จากองค์ประกอบต่างๆ ที่ทำให้มันทำงาน: Interface Devices, LAN Card, Wireless Adaptor, Aircard Adaptor, IP Setup, Routing, Gateway และ DNS

## Key Subcomponent of Focus
- [Interface Devices](https://github.com/LowEyeQ/Network-1/tree/main/088%20Interface%20Devices%20(Purin%20(%E2%80%A2%CB%8B%20_%20%CB%8A%E2%80%A2))) : ดูข้อมูลและสามารถตรวจสอบ network interfaces รวมทั้งดูเอกสารคำสั่งและความช่วยเหลือ
- [LAN Card](https://github.com/LowEyeQ/Network-1/tree/main/017%20LAN%20Card%20(KanphitchaNeamsri)) : ตัวกลางในการเชื่อมต่อระหว่างคอมพิวเตอร์ที่ใช้ Linux กับเครือข่ายข้อมูล ช่วยให้คอมพิวเตอร์สามารถระบุตัวตนและติดต่อสื่อสารกับอุปกรณ์อื่นๆ บนเครือข่ายได้
- [Wireless Adaptor](https://github.com/LowEyeQ/Network-1/tree/main/086%20Wireless%20Adaptor%20(bncnkktn)) : อุปกรณ์ที่ใช้สำหรับเชื่อมต่อกับเครือข่ายแบบไร้สาย หรือทำให้คอมพิวเตอร์สามารถรับสัญญาณ WiFi ได้
- [Aircard Adaptor](https://github.com/LowEyeQ/Network-1/tree/main/050%20Aircard%20Adaptor%20(Chalisa%20Suntithanyachok)) : 
- [IP Setup](https://github.com/LowEyeQ/Network-1/tree/main/037%20IP%20Setup%20(LowEyeQ)) : เครื่องมือสำคัญสำหรับการกำหนดค่าเครือข่าย ช่วยให้ผู้ใช้สามารถกำหนดค่าต่างๆ เช่น IP address, subnet mask, และค่าอื่นๆ ที่จำเป็นสำหรับการเชื่อมต่อกับเครือข่าย
- [Routing](https://github.com/LowEyeQ/Network-1/tree/main/033%20Routing%20(J-Jindamanee)) : กระบวนการของการเลือกเส้นทางในเครือข่ายต่างๆ เพื่อส่งข้อมูลจากแหล่งต้นทางไปยังปลายทาง
- [Gateway](https://github.com/LowEyeQ/Network-1/tree/main/057%20Gateway%20(Titaree-Ravi)) : ตัวกลางที่เชื่อมต่อระบบเครือข่ายภายในเครื่อง Linux กับเครือข่ายภายนอก โดยทำหน้าที่เป็นตัวกลางในการส่งข้อมูล และสามารถอนุญาตให้คอมพิวเตอร์ในเครือข่ายท้องถิ่นเข้าถึงทรัพยากรบนอินเทอร์เน็ตได้
- [DNS](https://github.com/LowEyeQ/Network-1/tree/main/088%20DNS%20Purin%20((%E2%80%A2%CB%8B%20_%20%CB%8A%E2%80%A2))) : ระบบที่ใช้แปลงชื่อโดเมนเป็นที่อยู่ IP และช่วยให้ระบบเครือข่ายทำงานได้อย่างมีประสิทธิภาพและเป็นระบบ

## สิ่งที่เหมือนหรือใกล้เคียงกัน
สิ่งที่ 8 Key Subcomponent of Focus มีเหมือนหรือใกล้เคียงกันบน Linux คือการแสดงข้อมูล และกำหนดค่าเครือข่าย

## Member
| **รหัสนักศึกษา** | **ชื่อ-นามสกุล** | **รูป** | 
| :-------- | :------- |  :------- | 
|**65070017**| นางสาว กานต์พิชชา  เนียมศรี | ![Alt text]() |
|**65070033**| นางสาว จินดามณี  จิรสรวงเกษม | ![Alt text]() |
|**65070037**| นาย จิรัฎฐวัฒน์  อัศวโกศลปภา | ![Alt text]() |
|**65070050**| นางสาว ชาลิสา  สันติธัญญาโชค | ![Alt text]() |
|**65070057**| นางสาว ฐิตารีย์  รวิชุติวรรณ | ![Alt text](https://scontent.fbkk6-1.fna.fbcdn.net/v/t39.30808-6/426103768_1104010290723274_1652347665402036447_n.jpg?_nc_cat=108&ccb=1-7&_nc_sid=dd5e9f&_nc_eui2=AeEmwNUX42ryFwTYwfF-P1awuXhelb9J4q-5eF6Vv0nir-WYgsfpeDQsX26H3F7A9ieGZtsy4_UttulrTU2lJaqB&_nc_ohc=jv42dy3hIdoAX_n120k&_nc_ht=scontent.fbkk6-1.fna&cb_e2o_trans=t&oh=00_AfBVDx9MnrB9q7ORkbXCPLSA7aq3WBOCfUaBn0EOWsUeSQ&oe=65C7DADD) |
|**65070086**| นางสาว ณิชนันท์  กิมเกถนอม | ![Alt text]() |
|**65070088**| นางสาว ปุรินปรัชญ์  อาษานอก | ![Alt text]() |

## Reference
- https://www.oreilly.com/library/view/linux-networking-cookbook/9780596102487/ch01.html
