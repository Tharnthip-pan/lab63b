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
1.01 run example 1 https://youtu.be/NLIUsWLEpmg                                                                                                                               
2.src codeของโปรแกรมที่ 1 serial-monitor https://github.com/choompol-boonmee/lab63b/blob/master/examples/01_Serial-Monitor/src/main.cpp                                         
3.platformio https://github.com/choompol-boonmee/lab63b/blob/master/examples/01_Serial-Monitor/platformio.ini

## วิธีการทำการทดลอง

    1.ต่อไมโครคอนโทรเลอร์เข้ากับ serial
    
![image](https://user-images.githubusercontent.com/80879475/112241058-1ae54b00-8c7c-11eb-839a-ae2bf9ed776b.jpg)
![image](https://user-images.githubusercontent.com/80879475/112241060-1b7de180-8c7c-11eb-9d2b-bc1dc93bafe9.jpg)
![image](https://user-images.githubusercontent.com/80879475/112241052-191b8780-8c7c-11eb-9011-468a60235599.jpg)      
                                                         
    2.เปิด command prompt                                                                                                                                                       
    3.เปิดโฟลเดอร์ซึ่งมีโปรแกรมตัวอย่าง 9 โปรแกรม
      >cd pattani 

![image](https://user-images.githubusercontent.com/80879475/112241282-87604a00-8c7c-11eb-8722-b50cd9adf8c6.jpg)

    4.เปิดโปรแกรมตัวอย่างที่ 1 
      >cd 01_serial_monitor
      >vi src/main.cpp

![image](https://user-images.githubusercontent.com/80879475/112241376-b5458e80-8c7c-11eb-81e6-c69790d7f03d.jpg)

      ตัวอย่างโปรแกรมที่ 1 มี 2 ส่วน                                                                                                                                                 
      (1)ส่วน setup เป็นคำสั่งรัน 1 ครั้งและ set serial port ที่ความเร็ว 115200                                                                                                           
      (2)ส่วน loop เป็นคำสั่งรันวนลูป เพิ่มตัวแปร count ไปเรื่อยๆและแสดงผลตัวแปร count ออกมาและหน่วงเวลา 1 วินาที                                                                             
    4.รันคำสั่งเพื่อดูรายละเอียดของ platformio
      >vi platformio.ini            
                                                                                                                                           
![image](https://user-images.githubusercontent.com/80879475/112241548-09507300-8c7d-11eb-94b5-82e39549f44d.jpg)
![image](https://user-images.githubusercontent.com/80879475/112241541-06ee1900-8c7d-11eb-92b9-9d5c3c3faf8e.jpg)
![image](https://user-images.githubusercontent.com/80879475/112241546-08b7dc80-8c7d-11eb-8c28-293b5056d4b4.jpg)

    5.Upload โปรแกรมที่ 1 ลงบนไมโครคอนโทรเลอร์
      >pio run -t upload
      โปรแกรมจะทำการ upload ลงบนไมโครคอนโทรเลอร์ 
      ระหว่างการ upload ต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง)เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป

![image](https://user-images.githubusercontent.com/80879475/112241869-57657680-8c7d-11eb-8e26-f0b41453f496.jpg)
![image](https://user-images.githubusercontent.com/80879475/112241866-559bb300-8c7d-11eb-96a5-662ec7aebf3e.jpg)
![image](https://user-images.githubusercontent.com/80879475/112241868-56cce000-8c7d-11eb-98e9-1f9c5b7334fd.jpg)

    6.ดูผลลัพธ์ของการรัน
      >pio device monitor

![image](https://user-images.githubusercontent.com/80879475/112241963-87ad1500-8c7d-11eb-9d43-486090a9b789.jpg)

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
