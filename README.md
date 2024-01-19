# -To-predict-weather-parameter-monitoring-system-with-live-feed-on-the-cloud-iot-
to predict the current  air quality  , temperature quality  ,humidity quality .
#include <DHT.h>
#define DHTPIN            2         // Pin which is connected to the DHT sensor.
#define DHTTYPE           DHT11     // DHT 11 
DHT dht(DHTPIN, DHTTYPE);
int cnt;
int t;
int h;
int mq=0;
void setup() 
{
 Serial.begin(9600); 
 dht.begin();
  }

void loop() 
{
  h = dht.readHumidity();
  t = dht.readTemperature();
  mq=analogRead(A0);

cnt=cnt+1;
delay(1000);

if(cnt>=10)
{
Serial.print("*");
Serial.print(t);
Serial.print(",");
Serial.print(h);
Serial.print(",");
Serial.print(mq);
Serial.println("#");
cnt=0;  
}
}
