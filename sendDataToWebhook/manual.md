# Description  
Edubot ( ESP32 ) 에서 발생하는 Data를 아래 그림 처럼 IFTTT의 WebHook 으로 보내고 이를 IFTTT 프로그램을 통해 https://io.adafruit.com/ 사이트로 보내는 예제 입니다.   
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/sendDataToWebhook/picture/pic1.png?raw=true" width="70%" height="70%">  

# 실행 순서 
## Step 1 IFTTT Program 만들기   
1. https://ifttt.com/discover 사이트에 접속해 계정만들고 로그인 
2. MyApplets -> New Applet -> this Click 하여 IFTTT 프로그램이 시작하는 트리거 이벤트 만들기   

<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/sendDataToWebhook/picture/pic3.png?raw=true" width="70%" height="70%">  


3. webhook -> Receive a web request 를 클릭하여 Event Name 에 test 적기   
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/sendDataToWebhook/picture/pic4.png?raw=true" width="70%" height="70%">  

4. that Click 하여 트리거 이벤트 ( this ) 발생시 어떠한 동작을 취할지 정하기   
   여기서는 adafruit 을 이용해 해당 사이트에 데이타를 적는 동작을 that으로 설정했습니다.  
   adafruit 사이트 설정은 아래 Option 부분에 설명 되어있습니다.  

<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/sendDataToWebhook/picture/pic2.png?raw=true" width="50%" height="50%">  

## Step 2. 에듀봇에 example -> IFTTT -> sendDataToWebhook.ino 예제를 설치 한다.     
이때 아래 항목을 자신에게 맞게 수정해서 설치한다.  
```bash
const char* ssid     = "U+NetB277";  // 공유기의 이름 
const char* password = "32F2021315";  // 공유기의 비밀번호 
#define IFTTT_KEY   "32F8881888zR-432F8881888ae5wLyD32F8881888Fcn" // 자신의 WebHook Key 
char * MakerIFTTT_Event = "test";  //webhook에서 설정한 Event Name 과 동일해야 함 
```
자신의 WebHook Key 는  https://ifttt.com/maker_webhooks  사이트에서 Document 클릭하면  
Your key is: 32F8881888zR-432F8881888ae5wLyD32F8881888Fcn  라고 자신의 webhook Key를 볼수 있다.  

## Step 2. 실행
1. 에듀봇 전원을 키면 IFTTT Site나 ,   adafruit site 에서 data 가 날라오는지 확인이 되어야 한다.   
2. IFTTT Site 측 확인은 https://ifttt.com/activity 여기에서 할수 있다. 만일 Edubot쪽은 데이타 전송 OK 뜨는데    
https://ifttt.com/activity  여기서 데이타 확인이 되지 않는다면 해당 Applet을 Click 해서 check now를 해서 해당 Applet이 정상동작 하고 있는지 확인해 본다.   
3. adafruit site 확인은 https://io.adafruit.com/ 사이트 접속   Feeds -> Edubot_Control 하면 전송된 data를 볼수 있어야 한다.   



## Option  Adafruit IO 사이트 설정하는 방법

1.https://io.adafruit.com/  사이트 진입 / 로그인   
2.Feeds 항목 클릭해서 Edubot_Control 를 feed 항목에 추가   
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/sendDataToWebhook/picture/pic8.png?raw=true" width="100%" height="100%">  
3.Feeds > Edubot_Control 에서 받은 데이타 19e60707 내용을 볼수 있음.
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/sendDataToWebhook/picture/pic7.png?raw=true" width="100%" height="100%">  




