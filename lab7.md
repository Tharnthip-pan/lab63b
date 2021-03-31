# การทดลองที่ 7 เรื่อง การประยุกต์โปรแกรม
## วัตถุประสงค์
    1.เพื่อเรียนรู้การเขียนโปรแกรมเพื่อใช้รันบนไมโครคอนโทรเลอร์
    2.เพื่อเรียนรู้การนำโปรแกรมไปประยุกต์
    
## อุปกรณ์ที่ใช้
    1.ไมโครคอนโทรเลอร์ ESP01
    2.อุปกรณ์ต่อ USB to Serial
    3.คอมพิวเตอร์
    4.หลอด led
    5.อแดปเตอร์ที่ต่อสายแยกพอร์ท
    
## การศึกษาข้อมูลเบื้องต้น
1.02 run example 2  https://youtu.be/yBjab0UNuB8                                                                                                                               
2.src codeของโปรแกรมที่ 2 scan-wifi  https://github.com/choompol-boonmee/lab63b/blob/master/examples/02_Scan-Wifi/src/main.cpp   
3.1.03 run example 3  https://youtu.be/CCnN1WJsXQY                                                                                                                                                                                                                                                  
4.src codeของโปรแกรมที่ 3 output-port  https://github.com/choompol-boonmee/lab63b/tree/master/examples/03_Output-Port/src  
5.05 run wifi  https://youtu.be/VX-QNQcO-b4                                                                                                                                   
6.src codeของโปรแกรมที่ 5 Wifi-Web-Server  https://github.com/choompol-boonmee/lab63b/blob/master/examples/05_Wifi-Web-Server/src/main.cpp      
7.06 run wiri AP  https://youtu.be/T26DVHePlTs                                                                                                                                 
8.src codeของโปรแกรมที่ 6 Wifi-AP-Web-Server  https://github.com/choompol-boonmee/lab63b/blob/master/examples/06_Wifi-AP-Web-Server/src/main.cpp      

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


## การบันทึกผลการทดลอง
    หลังจากที่รันคำสั่งเพื่อดูรายละเอียดของ platformio
       >vi platformio.ini
    ทำให้รายละเอียด เช่น 
    platform : espressif8266
    board : esp01_1m
    framework : arduino
    port ที่ใช้ติดต่อ : COM3
    และหลังจากที่ใช้คำสั่งเพื่อดูผลลัพธ์ของการรันของไมโครคอนโทรเลอร์
       >pio device monitor
    จะพบว่าตัว count จะเพิ่มขึ้นทีละ 1 และแสดงผลทุกๆ 1 วินาที
   
## อภิปรายผลการทดลอง
    จากการทดลองรันคำสั่งเพื่อดูรายละเอียดของ platformio จะสามารถเก็นรายละเอียดของ platformio ได้และจากการรันคำสั่งเพื่อดูผลลัพธ์ของการรัน
    ของไมโครคอนโทรเลอร์ก็พบว่าไมโครคอนโทรเลอร์ที่ลงโปรแกรมที่ 1 serial-monitor สามารถใช้งานได้จริงและดูได้จากการบันทึกผลการทดลอง
    
## คำถามหลังการทดลอง
    ถ้าเราต้องการดูรายละเอียดของ platformio ต้องรันคำสั่งใด?
    คำตอบ เปิด command prompt และรันคำสั่ง vi platformio.ini
