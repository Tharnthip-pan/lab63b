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
  server.handleClient();
}

© 2021 GitHub, Inc.
```
