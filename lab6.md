# การทดลองที่ 6 เรื่อง การเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP)
## วัตถุประสงค์
    1.เพื่อเรียนรู้การเขียนโปรแกรมเพื่อสร้างไวไฟแอคเซสพอยต์ (Wifi AP)
## อุปกรณ์ที่ใช้
    1.ไมโครคอนโทรเลอร์ ESP01
    2.อุปกรณ์ต่อ USB to Serial
    3.คอมพิวเตอร์
    4.อุปกรณ์ในการทดสอบเชื่อมไวไฟ เช่น โทรศัพท์มือถือ
## การศึกษาข้อมูลเบื้องต้น
1.06 run wiri AP  https://youtu.be/T26DVHePlTs                                                                                                                                 
2.src codeของโปรแกรมที่ 6 Wifi-AP-Web-Server  https://github.com/choompol-boonmee/lab63b/blob/master/examples/06_Wifi-AP-Web-Server/src/main.cpp                                 
3.platformio  https://github.com/choompol-boonmee/lab63b/blob/master/examples/06_Wifi-AP-Web-Server/platformio.ini
## วิธีการทำการทดลอง
    1.ต่อไมโครคอนโทรเลอร์เข้ากับ serial 
    2.เปิด command prompt
    3.เปิดโปรแกรมตัวอย่างที่ 6
      >cd 06_Wifi-AP-Web-Server
      >pwd
      >vi src/main.cpp

![image](https://user-images.githubusercontent.com/80879475/112245483-8b439a80-8c83-11eb-895c-b71bd85e4214.jpg)
![image](https://user-images.githubusercontent.com/80879475/112245712-fc834d80-8c83-11eb-9884-81cd845de58d.jpg)
![image](https://user-images.githubusercontent.com/80879475/112245717-fee5a780-8c83-11eb-8e2a-1ab5e42f52c1.jpg)

      ตัวอย่างโปรแกรมที่ 6
      (1)ตั้งชื่อไวไฟและรหัสผ่านที่ต้องการ
      (2)ส่วน Setup IPAddress local_ip , IPAddress gateway , IPAddress subnet 
         
    4.Upload โปรแกรมที่ 6 ลงบนไมโครคอนโทรเลอร์
      >pio run -t upload
      โปรแกรมจะทำการ upload ลงบนไมโครคอนโทรเลอร์ 
      ระหว่างการ upload ต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง)เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป
      
    5.รันคำสั่ง
      >pio device monitor
      จนแสดงผลว่า ver started

![image](https://user-images.githubusercontent.com/80879475/112245820-39e7db00-8c84-11eb-84f3-c9a21711df0f.jpg)

    6.นำโทรศัพท์มือถือมาเช็คไวไฟ
   
![image](https://user-images.githubusercontent.com/80879475/112245984-8c28fc00-8c84-11eb-8072-9a1a88f69898.jpg)
   
## การบันทึกผลการทดลอง
    หลังจากรันคำสั่ง 
    >pio device monitor
    จนแสดงผลว่า ver started หลังจากนั้นนำโทรศัพท์มือถือมาเช็คไวไฟและทำการเชื่อมต่อสามารถทำได้
    
## อภิปรายผลการทดลอง
    จากการทดลองเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP) ลงบนไมโครคอนโทรเลอร์สามารถทำงานได้จริง

## คำถามหลังการทดลอง
    ทำไมระหว่างการ upload โปรแกรมลงบนไมโครคอนโทรเลอร์จะต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง)?
    คำตอบ  เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป

