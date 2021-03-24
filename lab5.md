# การทดลองที่ 5 เรื่อง การเขียนโปรแกรมเชื่อมต่อไวไฟและเว็บเซอร์เวอร์
## วัตถุประสงค์
    1.เพื่อเรียนรู้การเขียนโปรแกรมเพื่อเชื่อมต่อไวไฟและเว็บเซอร์เวอร์
## อุปกรณ์ที่ใช้
    1.ไมโครคอนโทรเลอร์ ESP01
    2.อุปกรณ์ต่อ USB to Serial
    3.คอมพิวเตอร์
## การศึกษาข้อมูลเบื้องต้น
1.05 run wifi  https://youtu.be/VX-QNQcO-b4                                                                                                                                   
2.src codeของโปรแกรมที่ 5 Wifi-Web-Server  https://github.com/choompol-boonmee/lab63b/blob/master/examples/05_Wifi-Web-Server/src/main.cpp                                       
3.platformio  https://github.com/choompol-boonmee/lab63b/blob/master/examples/05_Wifi-Web-Server/platformio.ini                                                             
## วิธีการทำการทดลอง
    1.ต่อไมโครคอนโทรเลอร์เข้ากับ serial 
    2.เปิด command prompt
    3.เปิดโปรแกรมตัวอย่างที่ 5
      >cd 05_Wifi-Web-Server
      >1s
      >vi src/main.cpp

![image](https://user-images.githubusercontent.com/80879475/112244897-84685800-8c82-11eb-9324-25c82914e42c.jpg)

      ตัวอย่างโปรแกรมที่ 5
      (1)ระบุชื่อไวไฟและรหัสผ่านที่ต้องการเชื่อมต่อ
      (2)ส่วน Setup ให้เชื่อมต่อกับไวไฟที่เราระบุไว้และ setup webserver ให้ทำการเเสดงผล hello count โดย count จะเพิ่มขึ้นทีละ 1 ไปเรื่อยๆ
         
    4.Upload โปรแกรมที่ 5 ลงบนไมโครคอนโทรเลอร์
      >pio run -t upload
      โปรแกรมจะทำการ upload ลงบนไมโครคอนโทรเลอร์     
      ระหว่างการ upload ต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง) เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป
      
![image](https://user-images.githubusercontent.com/80879475/112245283-21c38c00-8c83-11eb-9b4a-9a4cf5326071.jpg)
![image](https://user-images.githubusercontent.com/80879475/112245272-1f613200-8c83-11eb-80c1-d164fc4f9f3b.jpg)
![image](https://user-images.githubusercontent.com/80879475/112245282-212af580-8c83-11eb-90dc-5fa6275a9c36.jpg)

    5.ดูผลลัพธ์ของการรัน จะได้ ip address
      >pio device monitor
    6.ทำการ copy ip address ไปเปิดบน Browser 
   
## การบันทึกผลการทดลอง
    หลังจากที่รันคำสั่งเพื่อให้ได้ ip address ออกมาโดยใช้คำสั่ง 
    >pio device monitor
    และเมื่อทำการcopy ip address ไปเปิดบน Browser ก็จะเเสดงผล hello 1 โดย count จะเปลี่ยนไปเรื่อยๆ 
## อภิปรายผลการทดลอง
    จากการทดลองเพื่อให้ไมโครคอนโทรเลอร์เชื่อมต่อไวไฟและเว็บเซอร์เวอร์สามารถทำงานได้จริง
## คำถามหลังการทดลอง
    ทำไมระหว่างการ upload โปรแกรมลงบนไมโครคอนโทรเลอร์จะต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง)?
    คำตอบ  เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป
