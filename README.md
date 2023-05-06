# Fire-Alarm-System-Project-by-Interfacing-Arduino-with-Temperature-
Materials Used:

Arduino Uno board
MQ-2 gas sensor
Jumper wires
Wi-Fi module (ESP8266)
Breadboard

STEP--
1.Create a new circuit in Tinkercad, and add an Arduino Uno board, a MQ-2 gas sensor, a Wi-Fi module, and a breadboard to the circuit.

2.Connect the VCC pin of the MQ-2 gas sensor to the 5V pin of the Arduino Uno board, the GND pin of the MQ-2 gas sensor to the GND pin of the Arduino Uno board, and the A0 pin of the MQ-2 gas sensor to the A0 pin of the Arduino Uno board.

3.Connect the TX pin of the Wi-Fi module to the RX pin of the Arduino Uno board, and the RX pin of the Wi-Fi module to the TX pin of the Arduino Uno board.

4.In the Tinkercad Code Editor, write the code to read the gas sensor data and send it to a cloud platform.
5.Replace "your-cloud-platform.com" with the URL of your cloud platform, and modify "insert_data.php" according to your cloud platform's API.

6.Upload the code to the Arduino Uno board in Tinkercad.

7.Open the Serial Monitor to see the gas sensor data.

8.Check your cloud platform to see if the data is successfully sent.

Circuit Diagram
<img width="747" alt="image" src="https://user-images.githubusercontent.com/125742021/236607302-c3f247e4-42e4-4c29-a5c7-f6e445d284b1.png">
CODE--


float temp;
float vout;
float vout1;
int LED=13;
int gasSensor;
int piezo=7;

void setup()
{
  pinMode(A0,INPUT);
  pinMode(A1,INPUT);
  pinMode(LED,OUTPUT);
  pinMode(piezo,OUTPUT);
  Serial.begin(9600);
}

void loop()
{
  vout=analogRead(A1);
  vout1=(vout/1023)*5000;
  temp=(vout1-500)/10;
  gasSensor=analogRead(A0);
  if(temp>=80)
  {
    digitalWrite(LED,HIGH);
  }
  else
  {
    digitalWrite(LED,LOW);
  }
  if(gasSensor>=100)
  {
    digitalWrite(piezo,HIGH);
  }
  else
  {
    digitalWrite(piezo,LOW);
  }
  Serial.print("Temperature = ");
  Serial.print(temp);
  Serial.print("°C");
  Serial.print("\t");
  Serial.print("Gas Sensor = ");
  Serial.print(gasSensor);
  Serial.println();
  delay(1000);
} 
