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
    6.รีเลย์
    
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

### การประยุกต์การเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP)

    1.ต่อไมโครคอนโทรเลอร์เข้ากับ serial 
    2.เปิด command prompt
    3.เปิดโปรแกรมตัวอย่างที่ 6
      >cd 06_Wifi-AP-Web-Server
      >pwd
      >vi src/main.cpp


```javascript
#include <ESP8266WiFi.h>
//#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "why do u have to use my wifi?";          - กำหนด ssid หรือชื่อไวไฟ -
const char* password = "whyyyyy!";                           - กำหนดรหัสผ่าน -

IPAddress local_ip(192, 168, 1, 1);                          - กำหนด IPAddress local_ip -
IPAddress gateway(192, 168, 1, 1);                           - กำหนด IPAddress gateway -
IPAddress subnet(255, 255, 255, 0);                          - กำหนด IPAddress subnet -

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){ 
	Serial.begin(250000);                                      - เพิ่มความเร็ว -

	WiFi.softAP(ssid, password);
	WiFi.softAPConfig(local_ip, gateway, subnet);
	delay(1000);                                               - เพิ่มดีเลย์หรือความหน่วงเวลา 1000 ms หรือ 1 วินาที -

	server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");
	});

	server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain", msg);
	});

	server.begin();
	Serial.println("HTTP server started");
}

void loop(void){
  server.handleClient();
}

© 2021 GitHub, Inc.
```

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
   
### การเขียนโปรแกรมค้นหาไวไฟและเชื่อมต่อไวไฟพร้อมสัญญาณไฟ


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
