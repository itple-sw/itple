# turtle 사용법 배우기
## turtle 사용법
* ```import turtle as t```로 모듈을 가져옵니다.
* turtle을 t로 줄여서 사용하면 좋습니다.
* t.Turtle() : turtle 객체를 만듭니다.
* t.bgcolor("색깔") : 배경 색깔을 정합니다.
* t.color("색깔") : 펜색깔을 정합니다.
* t.speed(숫자) : 펜이 움직이는 속도를 정합니다.
* t.penup() : 펜을 들어서 그리는 것을 멈춥니다.
* t.pendown() : 펜을 내려서 그립니다.
* t.forward(숫자) : 입력한 숫자만큼 앞으로 갑니다.
* t.left(숫자) : 입력한 숫자만큼 왼쪽으로 회전합니다.
* t.right(숫자) : 입력한 숫자만큼 오른쪽으로 회전합니다.
* t.circle(숫자) : 입력한 숫자크기로 원을 그립니다.
* t.goto(x좌표, y좌표) : 입력한 좌표로 이동합니다.

## 4각형 그리기
![image](https://user-images.githubusercontent.com/76088532/145509000-cf8f7e68-9bbd-4733-8976-3214dd153e85.png)
* 반복문을 사용해서 코딩할 수 있습니다.
```python
import turtle as t

t.Turtle()
t.bgcolor("black")
t.color("yellow")
t.speed(50)

for i in range(4):
    t.forward(100)
    t.left(90)
```

## n각형 그리기
* 360/각의 수만큼 회전합니다.
```python
for i in range(angle):
    t.forward(length)
    t.left(360/angle)
```    
* n각형을 연속해서 그립니다.
* 이중 for문을 사용합니다.

![image](https://user-images.githubusercontent.com/76088532/145509610-e7630b87-2be6-42ee-86fa-86fd74806144.png)
```python
import turtle as t

t.Turtle()
t.bgcolor("black")
t.color("yellow")
t.speed(50)

angle = 3
for i in range(4):
    for j in range(angle):
        t.forward(100)
        t.left(360/angle)
    angle = angle+1
```
## 여러 모양의 그림 그리기

![image](https://user-images.githubusercontent.com/76088532/145509713-dcf86009-3d9e-4624-a629-a30221fd0b49.png)

![image](https://user-images.githubusercontent.com/76088532/145509782-39a529be-b7ce-4ecc-a998-a5a94f674347.png)
```python
import turtle as t

t.Turtle()
t.bgcolor("black")
t.color("yellow")
t.speed(10)

length = 2
for i in range(100):
    t.forward(length)
    t.left(89)
    length += 2
```

# turtle로 다양한 그림 그리기
## 회전하는 삼각형 그리기

![image](https://user-images.githubusercontent.com/76088532/145509972-d4aefcd1-a2b9-4d54-9e9c-89bba6c4ddae.png)

## 같은 면은 색깔이 같도록 삼각형 그리기
* 나머지를 사용합니다.
* a % b는 a를 b로 나눈 나머지입니다.
* 나머지는 계속 반복됩니다.
* 예를 3으로 나누면 1,2,0,1,2,0.. 이렇게 나머지가 반복됩니다.

![image](https://user-images.githubusercontent.com/76088532/145510166-657e9e36-04fe-4b48-b60b-600d599f2005.png)
```python
import turtle as t

t.Turtle()
t.bgcolor("black")
t.color("yellow")
t.speed(10)

length = 2
for i in range(100):
    if i % 3 == 0:
        t.color("yellow")
    elif i % 3 == 1:
        t.color("blue")
    elif i % 3 == 2:
        t.color("red")
    t.forward(length)
    t.left(119)
    length += 4
```

## 거미줄 그리기
* 반복문을 잘 사용합니다.

![image](https://user-images.githubusercontent.com/76088532/145510266-4cc4fbdd-16f6-46fa-8af6-5239c4410afe.png)

# 재귀함수로 멋진 그림 그리기
## 재귀함수 이해하기
* 자기 자신을 호출하는 함수입니다.
* 멈추는 코드가 없으면 계속 반복합니다.
```python
from time import sleep

def recursion():
	print("재귀함수입니다.")
	sleep(0.01)
	recursion()
	
recursion()
```	

## 나무 모양 그리기 1
```python
import turtle as t

t.Turtle()
t.bgcolor("black") 
t.color("yellow")
t.speed(100)

def draw_tree(length):
    if length > 1:
        t.forward(length)
        t.right(45)
        draw_tree(length/2)
        t.left(90)
        draw_tree(length/2)
        t.left(135)
        t.forward(length)
        t.left(180)

t.left(90)
draw_tree(100)
```

## 나무 모양 그리기 2
* 나뭇가지 색깔과 나뭇잎 색깔을 칠합니다.
* 나뭇가지 사이의 각도를 다르게 합니다.
```python
import turtle as t

t.Turtle()
t.bgcolor("white") 
t.color("#89600F")
t.speed(100)

def draw_tree(length):
    if length > 1:
        if length < 2:
            t.color("#0BA916")
        else:
            t.color("#89600F")
        t.forward(length)
        t.right(30)
        draw_tree(length/1.5)
        t.left(60)
        draw_tree(length/1.5)
        t.left(150)
        t.forward(length)
        t.left(180)
        t.color("#89600F")

t.left(90)
draw_tree(100)
```

## 사이핀스키 삼각형 그리기
* 일정 길이 이하면 삼각형을 그립니다.
* 일정 길이를 넘으면 재귀함수로 삼각형을 그립니다.
```python
import turtle as t

t.Turtle()
t.bgcolor("black") 
t.color("yellow")
t.speed(100)

def draw_triangle(length):
    if length > 10:
        draw_triangle(length/2)
        t.forward(length/2)
        draw_triangle(length/2)
        t.left(120)
        t.forward(length/2)
        t.right(120)
        draw_triangle(length/2)
        t.right(120)
        t.forward(length/2)
        t.left(120)
    else:
        for i in range(3):
            t.forward(length)
            t.left(120)
            
draw_triangle(100)
```

# 파이썬과 드론의 만남
## pip로 e_drone 패키지 설치하기
### PIP 이해하기
* PIP (Pip Installs Pakares)는 패키지 설치 매니저입니다. 
* 터미널에서 간단한 명령어로 다양한 SW, 라이브러리 등을 쉽게 설치하고 업데이트 할 수 있습니다.
* 파이썬으로 드론을 조종하려면, 드론 하드웨어를 지원하는 모듈이나 패키지 등을 설치해야 합니다.
* pip install 패키지 이름으로 설치하면 됩니다

### e_drone 설치하기
* 우리가 설치할 패키지는 e_drone입니다.
* 윈도우키+R키를 눌러 실행창이 나오면 cmd명령(명령 프롬프트)을 입력합니다.
* 명령 프롬프트에서 pip 명령어로 e_drone 라이브러리를 설치합니다.
``` 
pip install e_drone
```

* pip 버전이 이전 버전이어서 안되는 경우가 있습니다. 
* python -m pip install --upgrade pip 입력하면 pip가 업그레이드됩니다.
```
python -m pip install --upgrade pip
```

* 라이브러리를 최신 버전으로 유지해 주어야 가장 최신 만들어진 함수까지 모두 사용할 수 있습니다. 
* pip install --upgrade e_drone 입력하여 업그레이드합니다
```
pip install --upgrade e_drone
```

## 드라이버 설치하기
* ‘드라이버(Driver)’란 ‘컴퓨터와 연결된 특정 장치와 통신하여 이를 제어하는 역할을 하는 프로그램’을 말합니다. 
* 보통 ‘장치 드라이버’라고 하는데 ‘장치(Device)’란 컴퓨터에 연결된 주변기기들을 의미합니다.
* 이런 각각의 하드웨어 장치를 제어하는 기능을 가진 프로그램이 바로 드라이버입니다.
* 컴퓨터 운영체제가 Windows 10인 경우 컨트롤러와 컴퓨터를 USB로 연결하면 자동으로 컨트롤러 USB 드라이버가 자동 설치됩니다. 
* 하지만 Windows 7과 Windows 8에서는 드라이버를 수동으로 설치해야 합니다. 
* 로보링크 ‘교육·기술지원 웹사이트’ < www.robolinksw.com >로 가서 USB Helper Download를 클릭하여 다운로드 합니다. 
* 압축 파일을 풀고 드라이버 설치 프로그램을 실행합니다.

## 장치관리자에서 포트 번호확인하기
* 장치관리자에서 포트 번호를 확인합니다.

## e_drone 패키지 설치되었는지 확인하기
* C:\Users\USER\AppData\Roaming\Python\Python39\site-packages와 같이 site-packages폴더에 들어가면 설치된 라이브러리를 확인할 수 있습니다.
* import를 했을 때 이상이 없으면 패키지가 잘 설치된 것입니다.
```python
from e_drone.drone import *
from e_drone.protocol import *
```

## PyPI 사이트에서 관련 함수 찾아보기
* < https://pypi.org/ >에 들어갑니다.
* 검색창에 'e_drone' 을 검색합니다.
* e_drone 라이브러리 관련 함수 사용법을 확인합니다.
* [Documents for E-Drone python library](http://dev.byrobot.co.kr/documents/kr/products/e_drone/library/python/e_drone/)

## 로보링크 깃북에서 관련 함수 찾아보기
* [로보링크 깃북 사이트 바로가기](https://robolink.gitbook.io/manual/codrone_lib/codrone_python_main)


## 파이썬 드론 코드 예제 실행해보기
* 여러 예제 중에 원하는 것을 선택해서 실행해봅니다.
* 기본적인 파이썬 드론 코드를 이해합니다.
* ```__name__```은 파이썬 내장변수입니다.
* ```__name__```에는 파일이름 또는 모듈이름이 들어갑니다.
* ```if __name__ == '__main__':```는 모듈로 가져온 것이 아니라 해당 코드를 직접 실행했을 때를 말합니다.
1. 관리자 권한으로 파이썬 IDLE를 실행합니다.
2. test1.py를 만들고 ```print(__name__)```를 입력하고 실행합니다. ```__main__```이라고 나옵니다.
3. test2.py를 만들고 ```print(__name__)```를 입력합니다. 
4. test1.py에서 ```import test2```를 입력하고 실행합니다. ```test2```라고 나옵니다.

* ```if __name__ == '__main__':```를 입력하지 않으면 해당 모듈을 import 했을 때 코드가 실행됩니다.
* drone = Drone()으로 드론 객체를 만듭니다.
* drone.open('com3')과 같이 포트번호를 입력합니다.

# 파이썬으로 드론 LED 제어하기
## LED 계속 색깔 바꾸기
* random 모듈을 사용합니다.
* ```random.randint(최소, 최대)```로 최소값과 최대값 사이에 있는 정수를 랜덤으로 고릅니다.
* Drone 객체를 만들 때 True를 넣으면 통신 상태 등을 확인할 수 있습니다.
* True를 넣지 않아도 됩니다.
```python
import random
from time import sleep
from e_drone.drone import *
from e_drone.protocol import *

if __name__ == '__main__':
    drone = Drone(True, True, True, True, True)
    drone.open("com3")
    while True:
        drone.sendLightDefaultColor(LightModeDrone.BodyDimming, 1, 255, 0, 0)
        sleep(2)
        drone.sendLightDefaultColor(LightModeDrone.BodyDimming, 1, 0, 255, 0)
        sleep(2)
        drone.sendLightDefaultColor(LightModeDrone.BodyDimming, 1, 0, 0, 255)
        sleep(2)
    drone.close()
```

## LED 색깔 랜덤으로 바꾸기
* ```convertByteArrayToString```는 특정 함수들은 타입의 포맷이 정해져 있어서 타입의 형을 변환하는 함수를 사용합니다.
* 문자열 포매팅을 합니다.
```python
import random
from time import sleep
from e_drone.drone import *
from e_drone.protocol import *

if __name__ == '__main__':
    drone = Drone(True, True, True, True, True)
    drone.open("com3")
    for i in range(0, 10, 1):
        r = int(random.randint(0, 255))
        g = int(random.randint(0, 255))
        b = int(random.randint(0, 255))
        dataArray = drone.sendLightDefaultColor(LightModeDrone.BodyDimming, 1, r, g, b)
        print(" {0} / {1}".format(i, convertByteArrayToString(dataArray)))
        sleep(2)
    drone.close()
```

# 파이썬으로 드론 움직이기
## 드론 초기화하기
* drone.sendClearBias()로 초기화합니다.
```python
from time import sleep
from e_drone.drone import *
from e_drone.protocol import *

def eventTrim(trim):
    print("{0}, {1}, {2}, {3}".format(trim.roll, trim.pitch, trim.yaw, trim.throttle))

def eventMotion(motion):
    print("eventMotion()")
    print("- Accel: {0}, {1}, {2}".format(motion.accelX, motion.accelY, motion.accelZ))
    print("- Gyro: {0}, {1}, {2}".format(motion.gyroRoll, motion.gyroPitch, motion.gyroYaw))  

if __name__ == '__main__':
    drone = Drone()
    drone.open("com3")
    drone.setEventHandler(DataType.Trim, eventTrim)
    drone.setEventHandler(DataType.Motion, eventMotion)
    drone.sendClearBias()
    sleep(0.1)
    drone.sendRequest(DeviceType.Drone, DataType.Trim)
    sleep(0.1)
    drone.sendRequest(DeviceType.Drone, DataType.Motion)
    sleep(0.1)
    drone.close()
```

## 드론 트림만 초기화하기
* drone.sendClearTrim()로 트림만 초기화합니다.
```python
from time import sleep
from e_drone.drone import *
from e_drone.protocol import *

def eventTrim(trim):
    print("{0}, {1}, {2}, {3}".format(trim.roll, trim.pitch, trim.yaw, trim.throttle))

if __name__ == '__main__':
    drone = Drone()
    drone.open("com3")
    drone.setEventHandler(DataType.Trim, eventTrim)
    drone.sendClearTrim()
    sleep(0.1)
    drone.sendRequest(DeviceType.Drone, DataType.Trim)
    sleep(0.1)
    i = 0
    while i < 5 :
        i += 1
        drone.sendRequest(DeviceType.Drone, DataType.Trim)
        sleep(0.1)
    drone.close()
```

## 이륙과 착륙하기
* drone.sendTakeOff()로 이륙합니다.
* 이륙이 안 되면 sleep() 함수로 조금 기다리도록 합니다.
* drone.sendLanding()로 착륙합니다.
* drone.sendControlWhile(롤, 피치, 요우, 쓰로틀, 밀리초)로 움직입니다.
* -100 부터 100 사이의 값을 넣어서 움직입니다.
* 움직이다가 방향을 바꿀 때는 drone.sendControlWhile(0, 0, 0, 0, 밀리초)로 조금 멈췄다가 움직입니다.
```python
from time import sleep
from e_drone.drone import *
from e_drone.protocol import *

if __name__ == '__main__':
    drone = Drone()
    drone.open("com3")
    sleep(2)
    print("TakeOff")
    drone.sendTakeOff()
    sleep(2)
    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 5000)
    print("Go Stop")
    drone.sendControlWhile(0, 0, 0, 0, 1000)
    print("Landing")
    drone.sendLanding()
    sleep(0.01)
    drone.sendLanding()
    sleep(0.01)
    drone.close()
```

## 미세조정하기
* drone.sendTrim(롤, 피치, 요우, 쓰로틀)로 미세조정을 합니다.
* -200 부터 200 사이의 값을 넣어서 미세조정을 합니다.
```python
from time import sleep
from e_drone.drone import *
from e_drone.protocol import *

def eventTrim(trim):
    print("{0}, {1}, {2}, {3}".format(trim.roll, trim.pitch, trim.yaw, trim.throttle))

if __name__ == '__main__':
    drone = Drone()
    drone.open("com3")
    drone.setEventHandler(DataType.Trim, eventTrim)
    drone.sendTrim(0, 0, 0, 0)
    sleep(0.1)
    drone.sendRequest(DeviceType.Drone, DataType.Trim)
    sleep(2)
    print("TakeOff")
    drone.sendTakeOff()
    sleep(2)
    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 5000)
    print("Go Stop")
    drone.sendControlWhile(0, 0, 0, 0, 1000)
    print("Landing")
    drone.sendLanding()
    sleep(0.01)
    drone.sendLanding()
    sleep(0.01)
    drone.close()
```

## 앞으로 움직이기
```python
from time import sleep
from e_drone.drone import *
from e_drone.protocol import *

if __name__ == '__main__':
    drone = Drone()
    drone.open("com3")
    sleep(2)
    print("TakeOff")
    drone.sendTakeOff()
    sleep(2)
    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 5000)
    print("Go Start")
    drone.sendControlWhile(0, 50, 0, 0, 2000)
    print("Go Stop")
    drone.sendControlWhile(0, 0, 0, 0, 1000)
    print("Landing")
    drone.sendLanding()
    sleep(0.01)
    drone.sendLanding()
    sleep(0.01)
    drone.close()
```

#  여러가지 패턴으로 비행하기
## 플립(공중회전)
* drone.sendFlightEvent(FlightEvent.종류)로 공중회전을 할 수 있습니다.
* 공중회전을 할 때는 드론 위쪽 공간이 충분하게 있어야 합니다.
```python
from time import sleep
from e_drone.drone import *
from e_drone.protocol import *

if __name__ == '__main__':
    drone = Drone()
    drone.open("com3")
    sleep(2)
    print("TakeOff")
    drone.sendTakeOff()
    sleep(2)
    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 3000)
    print("Flip")
    drone.sendFlightEvent(FlightEvent.FlipLeft)
    sleep(1)
    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 3000)
    print("Landing")
    drone.sendLanding()
    sleep(0.01)
    drone.sendLanding()
    sleep(0.01)
    drone.close()
```

## 사각 패턴비행
* 움직이다가 방향을 바꿀 때는 drone.sendControlWhile(0, 0, 0, 0, 밀리초)로 조금 멈췄다가 움직입니다.
```python
from time import sleep
from e_drone.drone import *
from e_drone.protocol import *

if __name__ == '__main__':
    drone = Drone()
    drone.open("com3")
    print("TakeOff")
    drone.sendTakeOff()
    sleep(0.01)
    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 4000)
    print("Go Start")
    drone.sendControlWhile( 0, 50, 0, 0, 1000)
    drone.sendControlWhile(0, 0, 0, 0, 1000)
    drone.sendControlWhile( 50, 0, 0, 0, 1000)
    drone.sendControlWhile(0, 0, 0, 0, 1000)
    drone.sendControlWhile( 0, -50, 0, 0, 1000)
    drone.sendControlWhile(0, 0, 0, 0, 1000)
    drone.sendControlWhile( -50, 0, 0, 0, 1000)
    drone.sendControlWhile(0, 0, 0, 0, 1000)
    print("Go Stop")
    print("Landing")
    drone.sendLanding()
    sleep(0.01)
    drone.sendLanding()
    sleep(0.01)
    drone.close()
```

## 원 패턴비행
* 피치 또는 롤과 요우로 원 비행을 할 수 있습니다.
```python
from time import sleep
from e_drone.drone import *
from e_drone.protocol import *

if __name__ == '__main__':
    drone = Drone()
    drone.open("com3")
    print("TakeOff")
    drone.sendTakeOff()
    sleep(0.01)
    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 4000)
    print("Go Start")
    drone.sendControlWhile( 50, 0, -50, 0, 4000)
    print("Go Stop")
    drone.sendControlWhile(0, 0, 0, 0, 1000)
    print("Landing")
    drone.sendLanding()
    sleep(0.01)
    drone.sendLanding()
    sleep(0.01)
    drone.close()
```

## 회오리 비행
* 원이 점점 커지도록 코딩을 합니다.
* 변수와 반복문을 사용하면 쉽게 회오리 비행 코딩을 할 수 있습니다.
* 요우 값은 점점 작아지고 롤 또는 피치 값은 점점 커지도록 코딩을 합니다.
