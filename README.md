# roboarmardu
#its a code describing the working of robo arm 
#include <Servo.h>

Servo xservo; Servo yservo; Servo hservo; Servo gservo; 

int ypos = 90;
int xpos = 90;
int hpos = 90;
int gpos = 90;

void setup() {
 
  xservo.attach(9);
  yservo.attach(10);
  hservo.attach(11);
  gservo.attach(12);
  Serial.begin(9600);
}

void loop()
{ 
  int sensorValue1 = analogRead(A0);
  int sensorValue2 = analogRead(A1);
  int sensorValue3 = analogRead(A2);
   int sensorValue4 = analogRead(A3);
    int sensorValue5 = analogRead(A4);
     int sensorValue6 = analogRead(A5);

  Serial.print(sensorValue1);
  Serial.print("       ");
  Serial.print(sensorValue2);
  Serial.print("       ");
  Serial.print(sensorValue3);
  Serial.print("       ");
   Serial.print(sensorValue4);
  Serial.print("       ");
   Serial.print(sensorValue5);
  Serial.print("       ");
   Serial.print(sensorValue6);
  Serial.print("       ");
  Serial.println();
 if(sensorValue1 > 1000 && sensorValue2 > 1000 && sensorValue3 < 600)
    {  
      Serial.println("left1");
       if(xpos<180)
     xpos += 3;
      xservo.write(xpos);
    }  
else if(sensorValue1 > 1000 && sensorValue2 < 100 && sensorValue3 < 600)
    { 
      Serial.println("right1");
      if(xpos>0)
     xpos -= 3;
      xservo.write(xpos);
    }  
 else if(sensorValue1 > 1000 && sensorValue2 < 600 && sensorValue3 > 1000)
    { 
      Serial.println("up1");
       if(ypos<180)
     ypos += 2;
      yservo.write(ypos);
    }  
 else if(sensorValue1 > 400 && sensorValue2 < 600 && sensorValue3 < 100)
{ 
      Serial.println("down1");
      if(ypos>0)
     ypos -= 2;
      yservo.write(ypos);
    }  
 if(sensorValue4 > 1000 && sensorValue5 < 600 && sensorValue6 > 1000)
    { 
      Serial.println("up2");
             if(hpos<180)
     hpos += 6;
      hservo.write(hpos);
    }  
 else if(sensorValue4 < 100 && sensorValue5 < 600 && sensorValue6 > 1000)
    { 
      Serial.println("dwn2");
      if(hpos>0)
     hpos -= 6;
      hservo.write(hpos);
    }   
     
 else if(sensorValue4 < 600 && sensorValue5 < 100 && sensorValue6 > 1000)
    { 
      Serial.println("right2"); 
       if(gpos<180)
     gpos += 3;
      gservo.write(gpos);
    }  
    
 else if(sensorValue4 < 600 && sensorValue5 > 1000 && sensorValue6 > 1000)
    {  
      Serial.println("left2");
      if(gpos>0)
     gpos -= 3;
      gservo.write(gpos);
    }     
    delay(150);        
}
