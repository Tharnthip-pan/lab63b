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
      
    4.

      ตัวอย่างโปรแกรมที่ 1 มี 2 ส่วน
      (1)ส่วน set up เป็นคำสั่งรัน 1 ครั้งและ set serial port ที่ความเร็ว 115200
      (2)ส่วน loop เป็นคำสั่งรันวนลูป เพิ่มตัวแปร count ไปเรื่อยๆและแสดงผลตัวแปร count ออกมาและหน่วงเวลา 1 วินาที
      
    4.รันคำสั่งเพื่อดูรายละเอียดของ platformio
      >vi platformio.ini
    5.Upload โปรแกรมที่ 1 ลงบนไมโครคอนโทรเลอร์
      >pio run -t upload
      โปรแกรมจะทำการ upload ลงบนไมโครคอนโทรเลอร์ 
      
      ระหว่างการ upload ต้องกดคำสั่ง reset (ปุ่มสีดำ+สีแดง)เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป
    6.ดูผลลัพธ์ของการรัน
      >pio device monitor
## การบันทึกผลการทดลอง
## อภิปรายผลการทดลอง
## คำถามหลังการทดลอง
