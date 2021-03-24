# การทดลองที่ 4 เรื่อง การเขียนโปรแกรมอินพุทสัญญาณดิจิทัล
## วัตถุประสงค์
    1.เพื่อเรียนรู้การเขียนโปรแกรมเพื่ออินพุทสัญญาณดิจิทัล

## อุปกรณ์ที่ใช้
    1.ไมโครคอนโทรเลอร์ ESP01
    2.อุปกรณ์ต่อ USB to Serial
    3.คอมพิวเตอร์
    4.หลอด LED
    5.อแดปเตอร์ที่ต่อสายแยกพอร์ท

## การศึกษาข้อมูลเบื้องต้น
1.04 run example 4  https://youtu.be/nFqoZT26U5k                                                                                                                             
2.src codeของโปรแกรมที่ 4 input-port  https://github.com/choompol-boonmee/lab63b/tree/master/examples/04_Input-Port/src                                                   
3.platformio  https://github.com/choompol-boonmee/lab63b/blob/master/examples/04_Input-Port/platformio.ini

## วิธีการทำการทดลอง
    1.ต่ออแดปเตอร์เข้ากับ serial และต่อไมโครคอนโทรเลอร์เข้ากับอเเดปเตอร์ เพื่อใช้งาน 2 port ได้พร้อมกัน
    
![image](https://user-images.githubusercontent.com/80879475/112243675-90531a80-8c80-11eb-9a68-74005a5009db.jpg)     
      
    2.เปิด command prompt
    3.เปิดโปรแกรมตัวอย่างที่ 4
      >cd ../04_input-port
      >1s
      >pwd
      >vi src/main.cpp

![image](https://user-images.githubusercontent.com/80879475/112243668-8e895700-8c80-11eb-875a-bc7fdd7cd843.jpg)

      ตัวอย่างโปรแกรมที่ 4 
      (1)ส่วน set up คือการ 
         port 0 = input = สีขาว
         port 2 = output = สีเหลือง
      (2)ส่วน loop เป็นคำสั่งอ่านข้อมูลจาก port 0 = สัญญาณดิจิตอล
         ถ้าเป็น 1 (low) ส่งไปport 2 ส่งผลให้ไฟดับ
         ถ้าเป็น 0 (high) ส่งไปport 2 ส่งผลให้ไฟติด
         โดยที่สัญญาณ input จาก port 0 เป็นตัวควบคุม
         
    4.Upload โปรแกรมที่ 4 ลงบนไมโครคอนโทรเลอร์
      >pio run -t upload
      โปรแกรมจะทำการ upload ลงบนไมโครคอนโทรเลอร์ 
      ระหว่างการ upload ต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง)เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป
      
    5.ดูผลลัพธ์ของการรัน
      >pio device monitor

![image](https://user-images.githubusercontent.com/80879475/112244046-3737b680-8c81-11eb-9408-667ca8c7f5d6.jpg)

    6.นำสายไฟสีขาว(port 0)ไปจิ้มที่ 0 v.(เส้นสีดำ)จะให้สัญญาณ input เป็น 0 ไฟติด

![image](https://user-images.githubusercontent.com/80879475/112244149-66e6be80-8c81-11eb-8780-1fca9527b549.jpg)

    7.นำสายไฟสีขาว(port 0)ไปจิ้มที่เส้นสีแดงจะให้สัญญาณ input เป็น 1 ไฟดับ
    
![image](https://user-images.githubusercontent.com/80879475/112244227-8aaa0480-8c81-11eb-9021-3c54902022fb.jpg)

    8.กดปุ่มสีดำ(port 0 = 0) input เป็น 0 ไฟติด

![image](https://user-images.githubusercontent.com/80879475/112244700-2cc9ec80-8c82-11eb-9885-b3e7d4433aaf.jpg)

    9.ปล่อยปุ่มสีดำ input เป็น 1 ไฟดับ

![image](https://user-images.githubusercontent.com/80879475/112244367-c47b0b00-8c81-11eb-9f38-3ba577b1271a.jpg)

    10.เมื่อนำเซ็นเซอร์แสงมาต่อกับเส้นสีแดงและต่อกับ resister(เข้าที่ port 0)และอีกขาต่อที่ ground
       ถ้ามีแสงสว่าง input เป็น 0 ไฟติด
       ถ้าไม่มีแสงสว่าง input เป็น 1 ไฟดับ

![image](https://user-images.githubusercontent.com/80879475/112244420-e2e10680-8c81-11eb-94c1-2d2feb2778e6.jpg)
![image](https://user-images.githubusercontent.com/80879475/112244423-e2e10680-8c81-11eb-93f6-9e906b8102ec.jpg)
![image](https://user-images.githubusercontent.com/80879475/112244418-e1174300-8c81-11eb-8cbb-03b62abeb640.jpg)
      
   
## การบันทึกผลการทดลอง
    จากการรันคำสั่ง
    >pio device monitor
    เมื่อนำสายไฟสีขาว(port 0)ไปจิ้มที่ 0 v.(เส้นสีดำ)จะให้สัญญาณ input เป็น 0 ไฟติด
    และเมื่อนำสายไฟสีขาว(port 0)ไปจิ้มที่เส้นสีแดงจะให้สัญญาณ input เป็น 1 ไฟดับ
    - กดปุ่มสีดำ(port 0 = 0) input เป็น 0 ไฟติด
    - ปล่อยปุ่มสีดำ input เป็น 1 ไฟดับ
    หลังจากที่นำเซ็นเซอร์แสงมาต่อ จะพบว่า
    - ถ้ามีแสงสว่าง input เป็น 0 ไฟติด
    - ถ้าไม่มีแสงสว่าง input เป็น 1 ไฟดับ
    
## อภิปรายผลการทดลอง
    จากทดลองเพื่ออินพุทสัญญาณดิจิทัล ถ้า port 0 สัญญาณ input เป็น 0 จะส่งผลให้ port 2 ไฟติด
    แต่ถ้ port 0 สัญญาณ input เป็น 1 จะส่งผลให้ port 2 ไฟดับ
    หลังจากนำเซ็นเซอร์แสงมาต่อ จะพบว่าถ้ามีแสงสว่าง input เป็น 0 ไฟติด แต่ถ้าไม่มีแสงสว่าง input เป็น 1 ไฟดับ
    
## คำถามหลังการทดลอง
    ทำไมระหว่างการ upload โปรแกรมลงบนไมโครคอนโทรเลอร์จะต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง)?
    คำตอบ  เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป

