# การทดลองที่ 1 เรื่อง การเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์
## วัตถุประสงค์
    1.เพื่อเรียนรู้การเขียนโปรแกรมเพื่อใช้รันบนไมโครคอนโทรเลอร์
    2.เพื่อทราบรายละเอียดของ platformio
    3.เพื่อทราบรายละเอียดของตัวอย่างโปรแกรม
## อุปกรณ์ที่ใช้
    1.ไมโครคอนโทรเลอร์ ESP01
    2.อุปกรณ์ต่อ USB to Serial
    3.คอมพิวเตอร์
## การศึกษาข้อมูลเบื้องต้น
    1.[01 run example 1](https://youtu.be/NLIUsWLEpmg)
    2.[src codeของโปรแกรมที่ 1 serial-monitor](https://github.com/choompol-boonmee/lab63b/blob/master/examples/01_Serial-Monitor/src/main.cpp)
    3.[platformio](https://github.com/choompol-boonmee/lab63b/blob/master/examples/01_Serial-Monitor/platformio.ini)
## วิธีการทำการทดลอง
    1.ต่อไมโครคอนโทรเลอร์เข้ากับ serial
    2.เปิด command prompt
    3.เปิดโฟลเดอร์ซึ่งมีโปรแกรมตัวอย่าง 9 โปรแกรม
      >cd pattani
    4.เปิดโปรแกรมตัวอย่างที่ 1 
      >cd 01_serial_monitor
      >vi src/main.cpp

      ตัวอย่างโปรแกรมที่ 1 มี 2 ส่วน
      (1)ส่วน set up เป็นคำสั่งรัน 1 ครั้งและ set serial port ที่ความเร็ว 115200
      (2)ส่วน loop เป็นคำสั่งรันวนลูป เพิ่มตัวแปร count ไปเรื่อยๆและแสดงผลตัวแปร count ออกมาและหน่วงเวลา 1 วินาที
      
    4.รันคำสั่งเพื่อดูรายละเอียดของ platformio
      >vi platformio.ini
    5.Upload โปรแกรมที่ 1 ลงบนไมโครคอนโทรเลอร์
      >pio run -t upload
      โปรแกรมจะทำการ upload ลงบนไมโครคอนโทรเลอร์ 
      
      ระหว่างการ upload ต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง)เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป
    6.ดูผลลัพธ์ของการรัน
      >pio device monitor
## การบันทึกผลการทดลอง
## อภิปรายผลการทดลอง
## คำถามหลังการทดลอง
