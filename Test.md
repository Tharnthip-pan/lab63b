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
	delay(1000);                                               - ดีเลย์หรือความหน่วงเวลา 1000 ms หรือ 1 วินาที -

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

## ค้นหาไวไฟ+เชื่อมไวไฟ

```javascript
#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	WiFi.mode(WIFI_STA);
	WiFi.disconnect();
	delay(100);
	Serial.println("\n\n\n");
}

void loop()
{
	Serial.println("========== เริ่มต้นแสกนหา Wifi ===========");
	int n = WiFi.scanNetworks();
	if(n == 0) {
		Serial.println("NO NETWORK FOUND");
	} else {
		for(int i=0; i<n; i++) {
			Serial.print(i + 1);
			Serial.print(": ");
			Serial.print(WiFi.SSID(i));
			Serial.print(" (");
			Serial.print(WiFi.RSSI(i));
			Serial.println(")");
			delay(10);
		}
	}
	Serial.println("\n\n");
}

© 2021 GitHub, Inc.
```
