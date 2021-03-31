# Test code

## สร้างไวไฟ

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

## เชื่อมไวไฟ+ไฟกระพริบ

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
	Serial.begin(250000);
	pinMode(0,output);

	WiFi.mode(WIFI_STA);
	WiFi.begin(ssid, password);
	while (WiFi.status() != WL_CONNECTED) {
		delay(1000);
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
//lab6
  server.handleClient();
  //lab2
  Serial.println("========== Start Scan Wifi ===========");
	int n = WiFi.scanNetworks();
	if(n == 0) {
		Serial.println("========== OFF ===========");		//lab3
		status_led=0;                   			//กำหนดค่า ตัวแปรใน status_led=0
		digitalWrite(0, LOW);					//lab3
		Serial.println("NO NETWORK FOUND");
	} else {
		Serial.println("========== ON ===========");	//lab3
		status_led=1;                   		//กำหนดค่า ตัวแปรใน status_led=1
		digitalWrite(0, HIGH);				//lab3
		for(int i=0; i<n; i++) {
			Serial.print(i + 1);
			Serial.print(": ");
			Serial.print(WiFi.SSID(i));
			Serial.print(" (");
			Serial.print(WiFi.RSSI(i));
			Serial.println(")");
			int w = i*500
			delay(w);		//กำหนดให้ความหน่วงเพิ่มขึ้นตามจำนวนไวไฟที่พบ
		}
	}
	Serial.println("NOW! FOUND %w NETWORK",n);		//บอกจำนวนไวไฟที่เจอรอบสถานที่นั้น
  
  delay(1000)
  Serial.println("\n\n\n");
}

© 2021 GitHub, Inc.
```
  server.handleClient();
}

© 2021 GitHub, Inc.
```
