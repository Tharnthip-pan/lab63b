# การทดลองที่ 7 เรื่อง การประยุกต์การเขียนโปรแกรม
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

### การประยุก์การเขียนโปรแกรมเพื่อสร้างไวไฟแอคเซสพอยต์ (Wifi AP)

    1.ต่อไมโครคอนโทรเลอร์เข้ากับ serial 
    2.เปิด command prompt
    3.เปิดโปรแกรมตัวอย่างที่ 7.1
      >cd 07_1
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

      ตัวอย่างโปรแกรมที่ 7.1
      (1)ตั้งชื่อไวไฟและรหัสผ่านที่ต้องการ
      (2)ส่วน Setup IPAddress local_ip , IPAddress gateway , IPAddress subnet 
         
    4.Upload โปรแกรมที่ 7.1 ลงบนไมโครคอนโทรเลอร์
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

 1.ต่ออแดปเตอร์เข้ากับ serial และต่อไมโครคอนโทรเลอร์เข้ากับอเเดปเตอร์
    
![image](https://user-images.githubusercontent.com/80879475/112243151-ab715a80-8c7f-11eb-849c-680c14e98a68.jpg)
![image](https://user-images.githubusercontent.com/80879475/112243155-ad3b1e00-8c7f-11eb-979e-c2a1233b6359.jpg)

    2.เปิด command prompt
    3.เปิดโปรแกรมตัวอย่างที่ 7.2
      >cd 07_2
      >vi src/main.cpp
     
```javascript
#include <ESP8266WiFi.h>
//#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "why do u have to use my wifi?";
const char* password = "whyyyyy!";
unsigned char status_led=0;                                      - กำหนดตัวแปรเพื่อรับและเก็บค่าสถานะของหลอด led -

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){
	Serial.begin(250000);                                    - เพิ่มความเร็ว -
	pinMode(0,output);

	WiFi.mode(WIFI_STA);
	WiFi.begin(ssid, password);
	while (WiFi.status() != WL_CONNECTED) {
		delay(1000);                                      - เพิ่มความหน่วงหรือดีเลย์เป็น 1000 ms หรือ 1 วินาที -
		Serial.print(".");
	     
	}
	Serial.print("\n\nIP address: ");
	Serial.println(WiFi.localIP());

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

  Serial.println("========== เริ่มค้นหาไวไฟ ===========");
	int n = WiFi.scanNetworks();
	if(n == 0) {
		Serial.println("========== ปิดจ้าาาปิด ===========");		
		status_led=0;                   			- กำหนดค่าตัวแปร status_led=0 -
		digitalWrite(0, LOW);					
		Serial.println("NO NETWORK FOUND");
	} else {
		Serial.println("========== เปิดดดดดด ===========");	
		status_led=1;                   		        - กำหนดค่าตัวแปร status_led=1 -
		digitalWrite(0, HIGH);				
		for(int i=0; i<n; i++) {
			Serial.print(i + 1);
			Serial.print(": ");
			Serial.print(WiFi.SSID(i));
			Serial.print(" (");
			Serial.print(WiFi.RSSI(i));
			Serial.println(")");
			int w = i*500
			delay(w);		- กำหนดให้ความหน่วงหรือดีเลย์เพิ่มขึ้นตามจำนวนไวไฟที่พบ -
		}
	}
	Serial.println("NOW! FOUND %w NETWORK",n);		- แสดงจำนวนไวไฟที่ค้นหาเจอ -
  
  delay(1000)                                                   - เพิ่มความหน่วงหรือดีเลย์เป็น 1000 ms หรือ 1 วินาที -
  Serial.println("\n\n\n");
}

© 2021 GitHub, Inc.
```


    4.Upload โปรแกรมที่ 7.2 ลงบนไมโครคอนโทรเลอร์
      >pio run -t upload
      โปรแกรมจะทำการ upload ลงบนไมโครคอนโทรเลอร์ 
      ระหว่างการ upload ต้องกดคำสั่ง upload+reset (ปุ่มสีดำ+สีแดง)เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป
      
    5.รันคำสั่ง
      >pio device monitor
      
## การบันทึกผลการทดลอง
### การประยุก์การเขียนโปรแกรมเพื่อสร้างไวไฟแอคเซสพอยต์ (Wifi AP)
    หลังจากรันคำสั่ง 
    >pio device monitor
    จนแสดงผลว่า ver started ถ้า code ถูกต้องจะสามารถนำโทรศัพท์มือถือมาเช็คไวไฟและทำการเชื่อมต่อสามารถทำได้
### การเขียนโปรแกรมค้นหาไวไฟและเชื่อมต่อไวไฟพร้อมสัญญาณไฟ
    หลังจากรันคำสั่ง 
    >pio device monitor
    ถ้า code ถูกต้องจะสามารถค้นหาไวไฟและเชื่อมต่อไวไฟได้พร้อมกับมีสัญญาณไฟกระพริบเมื่อค้นหาไวไฟและเชื่อมต่อไวไฟได้สำเร็จ
   
## อภิปรายผลการทดลอง
### การประยุก์การเขียนโปรแกรมเพื่อสร้างไวไฟแอคเซสพอยต์ (Wifi AP)
    หลังจากรันคำสั่ง 
    >pio device monitor
    จนแสดงผลว่า ver started ถ้า code ถูกต้องจะสามารถนำโทรศัพท์มือถือมาเช็คไวไฟและทำการเชื่อมต่อสามารถทำได้
### การเขียนโปรแกรมค้นหาไวไฟและเชื่อมต่อไวไฟพร้อมสัญญาณไฟ
    หลังจากรันคำสั่ง 
    >pio device monitor
    ถ้า code ถูกต้องจะสามารถค้นหาไวไฟและเชื่อมต่อไวไฟได้พร้อมกับมีสัญญาณไฟกระพริบเมื่อค้นหาไวไฟและเชื่อมต่อไวไฟได้สำเร็จ
    
## คำถามหลังการทดลอง
    ถ้าเราต้องการดูรายละเอียดของ platformio ต้องรันคำสั่งใด?
    คำตอบ เปิด command prompt และรันคำสั่ง vi platformio.ini
