# การทดลองที่ 2 เรื่อง การเขียนโปรแกรมค้นหาไวไฟ
## วัตถุประสงค์
    1.เพื่อเรียนรู้การเขียนโปรแกรมค้นหาไวไฟ
    2.เพื่อใช้ไมโครคอนโทรเลอร์ค้นหาไวไฟที่อยู่รอบๆ
## อุปกรณ์ที่ใช้
    1.ไมโครคอนโทรเลอร์ ESP01
    2.อุปกรณ์ต่อ USB to Serial
    3.คอมพิวเตอร์
## การศึกษาข้อมูลเบื้องต้น
1.02 run example 2  https://youtu.be/yBjab0UNuB8                                                                                                                               
2.src codeของโปรแกรมที่ 2 scan-wifi  https://github.com/choompol-boonmee/lab63b/blob/master/examples/02_Scan-Wifi/src/main.cpp                                                   
3.platformio  https://github.com/choompol-boonmee/lab63b/blob/master/examples/02_Scan-Wifi/platformio.ini 
## วิธีการทำการทดลอง
    1.ต่อไมโครคอนโทรเลอร์เข้ากับ serial
    2.เปิด command prompt
    3.เปิดโปรแกรมตัวอย่างที่ 2
      >cd pattani
      >cd 02_scan-wifi
      
![image](https://user-images.githubusercontent.com/80879475/112242431-6dc00200-8c7e-11eb-8307-fb60e83819ad.jpg)

      ตัวอย่างโปรแกรมที่ 2 มี 2 ส่วน
      (1)ส่วน set up เป็นคำสั่งรัน set up wifi
      (2)ส่วน loop เป็นคำสั่งรันวนลูป 
      
    4.Upload โปรแกรมที่ 2 ลงบนไมโครคอนโทรเลอร์
      >pio run -t upload
      โปรแกรมจะทำการ upload ลงบนไมโครคอนโทรเลอร์     
      ระหว่างการ upload ต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง)เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป
      
![image](https://user-images.githubusercontent.com/80879475/112242652-deffb500-8c7e-11eb-8377-d0927c65d4f7.jpg)
![image](https://user-images.githubusercontent.com/80879475/112242655-df984b80-8c7e-11eb-8ac2-8bb23a32c56c.jpg)
![image](https://user-images.githubusercontent.com/80879475/112242647-dd35f180-8c7e-11eb-898f-b7f07d844913.jpg)

    5.ดูผลลัพธ์ของการรัน
      >pio device monitor
![image](https://user-images.githubusercontent.com/80879475/112242800-1d956f80-8c7f-11eb-955b-48af5d0c6173.jpg)

## การบันทึกผลการทดลอง
    หลังจากรันคำสั่งเพื่อใช้ไมโครคอนโทรเลอร์ในการค้นหาไวไฟ
    >pio device monitor
    จะได้ผลการรันโดยคือไมโครคอนโทรเลอร์จะเริ่มค้นหาไวไฟและเเสดงผลออกมาให้เห็นชื่อของไวไฟที่อยู่ใกล้เรา
    
## อภิปรายผลการทดลอง
    จากการทดลองใช้ไมโครคอนโทรเลอร์ในการค้นหาไวไฟสามารถทำได้จริง ซึ่งสามารถดูผลการทดลองได้ตามบันทึกผลการทดลองได้เลย
    
## คำถามหลังการทดลอง
    การสแกนหาไวไฟในแต่ละครั้งมีจำนวนไวไฟที่แสดงผลว่าค้นเจอในเเต่ละครั้งไม่เท่ากันสาเหตุมาจากอะไรได้บ้าง?
    คำตอบ ความเร็วและความแรงของสัญญาณไวไฟนั้นๆและระยะห่างระหว่างไมโครคอนโทรเลอร์ที่ใช้ทดลองกับสัญญาณไวไฟ
