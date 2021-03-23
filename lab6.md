# การทดลองที่ 6 เรื่อง การเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP)
## วัตถุประสงค์
    1.เพื่อเรียนรู้การเขียนโปรแกรมเพื่อสร้างไวไฟแอคเซสพอยต์ (Wifi AP)
## อุปกรณ์ที่ใช้
    1.ไมโครคอนโทรเลอร์ ESP01
    2.อุปกรณ์ต่อ USB to Serial
    3.คอมพิวเตอร์
    4.อุปกรณ์ในการทดสอบเชื่อมไวไฟ เช่น โทรศัพท์มือถือ
## การศึกษาข้อมูลเบื้องต้น
    1.[06 run wiri AP](https://youtu.be/T26DVHePlTs)
    2.[src codeของโปรแกรมที่ 6 Wifi-AP-Web-Server](https://github.com/choompol-boonmee/lab63b/blob/master/examples/06_Wifi-AP-Web-Server/src/main.cpp)
    3.[platformio](https://github.com/choompol-boonmee/lab63b/blob/master/examples/06_Wifi-AP-Web-Server/platformio.ini)
## วิธีการทำการทดลอง
    1.ต่อไมโครคอนโทรเลอร์เข้ากับ serial 
    2.เปิด command prompt
    3.เปิดโปรแกรมตัวอย่างที่ 6
      >cd 06_Wifi-AP-Web-Server
      >pwd
      >vi src/main.cpp

      ตัวอย่างโปรแกรมที่ 6
      (1)ตั้งชื่อไวไฟและรหัสผ่านที่ต้องการ
      (2)ส่วน Setup IPAddress local_ip , IPAddress gateway , IPAddress subnet 
         
  
    4.Upload โปรแกรมที่ 6 ลงบนไมโครคอนโทรเลอร์
      >pio run -t upload
      โปรแกรมจะทำการ upload ลงบนไมโครคอนโทรเลอร์ 
      
      ระหว่างการ upload ต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง)เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป
    5.นำโทรศัพท์มือถือมาเช็คไวไฟ
   
   
## การบันทึกผลการทดลอง
## อภิปรายผลการทดลอง
## คำถามหลังการทดลอง

