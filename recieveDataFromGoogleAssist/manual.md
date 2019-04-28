# Description  
휴대폰 Google Assistant 에 입력한 Text를 Edubot LCD 화면에 띄우는 예제 입니다. 전체 Data flow는 아래와 같습니다.    
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/1.jpg?raw=true" width="70%" height="70%">  

동작 영상 -> 클릭하면 유투브 동영상으로 연결 됩니다.  
[![Video Label](http://img.youtube.com/vi/96Q6f7Jycpc/0.jpg)](https://youtu.be/96Q6f7Jycpc?t=0s)   

# 실행 순서 
## Step1. Adafruit IO 웹프로그램 구현 ( Adafruit 계정 필요/무료 )   
1. https://io.adafruit.com/  사이트 진입 / 로그인   
2. 아래 그림처럼 Edubot_Control Feed 제작   
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/2.png?raw=true" width="100%" height="100%">  
3. 해당  IO USER NAME  ,  IO KEY  값은 이후 Step3 에서 진행될 에듀봇 firmware 프로그램에 입력해야 합니다.  
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/3.png?raw=true" width="100%" height="100%"> 
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/13.png?raw=true" width="100%" height="100%"> 

## Step2. IFTTT  웹프로그램 구현 ( 구글계정 필요/무료 )  
1. https://ifttt.com/discover   사이트 가셔서 휴대폰과 동일한 Google 계정으로  로그인   
   -> 나중에 폰의 Google Assistant를 사용할 것이기 때문에   
2. My Apples -> New Applet 클릭하여 새 applet 제작, 트리거가 될 this 값 구글어시스턴스로 설정     
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/4.png?raw=true" width="100%" height="100%">  
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/5.png?raw=true" width="70%" height="70%">  
3. Google Assistant에서 Edubot이라는 단어 이후 입력된 문장은 모조리 io.adafruit.com 사이트를 통해 Edubot firmware 로 보내서 Edubot LCD 에 표시할 것이기 때문에 아래 네개중  3번째 타입 클릭  
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/6.png?raw=true" width="70%" height="70%">  

$ 로 된 부분을  넘긴다는 의미 입니다. 예로 Edubot dance with me , nice ~~  치면   $ 에 해당하는  dance with me , nice ~~ 문구가   
io.adafruit.com 사이트를 통해 Edubot firmware 에서 로그&LCD로 찍힙니다.   
그리고 시작이 Edubot 이 아니더라도  oroca 나 oroca edubot 형태라도 트리거가 발생한다는 내용의 프로그램 입니다.  
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/7.png?raw=true" width="70%" height="70%">  

4. this 트리거 를 설정했으니 that ( 먼 행동을 할까 ) 를 설정 합니다.   
저희는 io.adafruit.com 사이트를 통해 Edubot firmware  로 전달할 것이니까  adafruit 찾아 클릭. 아마 위에서 만든 adafruit 계정 입력하라고 뜰겁니다.  
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/8.png?raw=true" width="70%" height="70%">  
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/9.png?raw=true" width="100%" height="100%">  
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/10.png?raw=true" width="100%" height="100%">  

## Step3. 에듀봇에 example -> IFTTT -> recieveDataFromGoogleAssist.ino 예제를 설치 한다.
1.에듀봇 환결 설정 하시고요.  Board Manager 에서 OROCA Edubot 으로 board 설정된 상태에서 “adafruit mqtt” then a library  를 설치해주세요 .   
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/11.png?raw=true" width="70%" height="70%">  
<img src="https://github.com/hyunoklee/OROCA-EduBot-Manual/blob/master/recieveDataFromGoogleAssist/picture/12.png?raw=true" width="70%" height="70%">  
2.recieveDataFromGoogleAssist.ino 예제에서 아래 항목을 자신에게 맞게 수정해서 설치한다.  

```bash
const char* ssid     = "U+123451315";  // 공유기의 이름 
const char* password = "123451315";  // 공유기의 비밀번호 
```
AIO_KEY 부분은 위의 Step1의 3번에서 나오는 값을 적으시면 됩니다.   
```bash
#define AIO_USERNAME    "boo"  // https://io.adafruit.com  사이트 IO USER NAME
#define AIO_KEY         "123451315123451315121234513153451315123451315" //https://io.adafruit.com  사이트 IO KEY
```
## Step4. 폰의 마켓에서 구글 어시스턴스 앱 다운받아 설치  
폰에 기본 들어있는  G 알록 달록한걸로 하면 안되시고   
마켓에서 Google Assistant 검색하면 동그라미 여러개 나온 어플이 검색됩니다.     
그리고 언어를 영어로 바꿔 주셔야 합니다.   
구글 어시스턴스 실행 -> 나침판 같이 생긴거 클릭 -> 프로필 사진 클릭 -> Setting -> Assitant -> Languages -> English 설정   
하고 나면 아래  Android language settings  라는 항목이 생기는데 이것도 클릭해서 폰전체 언어도 영어로 바꿔 주어야 하더라고요  

## Step5. 실행 
구글 어시스턴스 앱 실행. 
Edubot 안녕하세요  를 구글 어시스턴스에 입력하면 에듀봇 LCD에 안녕하세요라고 보여짐.   
원래는 음석인성으로도 되어야 하지만 해보니 영어발음으로 Edubot 라는 단어를 구글 어시스턴트가 인지하게 하는게 거의 불가능 합니다.   
구글 어시스턴트는 한글을 지원하지만 IFTTT 는 한글을 지원하지 않으므로 트리거가 되는 단어, 여기서는 Edubot을 영어로 해야 합니다.  
## Step6. 디버깅 
2. IFTTT Site 측 확인은 https://ifttt.com/activity 여기에서 할수 있다. 만일   
https://ifttt.com/activity  여기서 데이타 확인이 되지 않는다면 해당 Applet을 Click 해서 check now를 해서 해당 Applet이 정상동작 하고 있는지 확인해 본다.   
3. adafruit site 확인은 https://io.adafruit.com/ 사이트 접속   Feeds -> Edubot_Control 하면 전송된 data를 볼 수 있어야 한다.   

