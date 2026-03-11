# 시작 전 

- 실습은 노트북 파일을 사용합니다. 사용하는 IDE에 맞춰 확장 프로그램을 설치하시거나 주피터랩 혹은 주피터 노트북을 설치해주시면 감사하겠습니다.
- 노트북을 실행하기 위해서 주피터 커널 또한 준비해주셔야 합니다.
```
# 가상환경을 사용할 경우
# $ conda activate carla가상환경이름
$ pip install ipykernel
$ python -m ipykernel install --user --name carla_env --display-name "carla_0.9.14"
```

# CARLA 서버 설치

본 워크숍에서는 0.9.14 버전을 사용합니다.
운영 체제에 맞춰 파일을 다운 받아 주세요.

[CARLA_0.9.14 다운로드](https://github.com/carla-simulator/carla/releases/tag/0.9.14/)

CARLA 서버를 직접 실행하기 위해서는 다음의 사양을 체크해주세요.

- 운영 체제 : 윈도우 10, 11 / 우분투 20.04, 22.04 
- RTX2070 이상의 GPU 혹은 8GB 이상의 VRAM을 가진 GPU
- 20GB 이상의 디스크 공간
- CARLA는 기본적으로 2000번과 2001 포트를 사용하므로, 해당 포트가 방화벽이나 다른 프로그램에 의해 차단되지 않도록 해주세요 .
- Python 3.7
- PIP 20.3 이상

# CARLA 서버 실행
```
# carla 설치 폴더로 이동
$ ./CarlaUE4.sh
```


# CALRLA 클라이언트 라이브러리 설치
wheel 파일 직접 설치

```
# 우분투
cd /PythonAPI/carla/dist/
pip install carla-0.9.14-cp37-cp37m-manylinux_2_27_x86_64.whl

# libomp5 오류 발생 시
# sudo apt-get install libomp5
```

```
# 윈도우

```

# 서버 사양이 안 되시는 분들을 위한 CARLA 서버 접속
python3 manual_control.py --host 'IP주소' --res 400x300
조작법 안내

# CARLA 서버 제어
client , world 내용
 1. carla.Client
서버의 world를 조정하거나 객체를 생성하고 이들을 다루기 위해선 carla.Client 객체를 생성해야 합니다.
주요 생성자는 다음과 같습니다. init(host=127.0.0.1, port=2000). 기본적으로 로컬 호스트와 2000번 포트에 연결하도록 설정이 되어있습니다.

host : Carla 시뮬레이터 서버가 작동하고 있는 host의 IP.
port : Carla 시뮬레이터 서버가 작동하고 있는 host의 TCP 포트.

 2. map 설정
Carla는 다양한 시나리오를 고려할 수 있도록 잘 구축된 몇 개의 맵들을 제공합니다.
설치 파일의 크기를 위해 일부 맵은 추가 Asset으로 제공하며, 서버 파일과 마찬가지로 Carla 깃허브 저장소에서 다운받을 수 있습니다.

Carla 시뮬레이터 서버의 맵을 변경하기 위해선 carla.Client.load_world('맵이름') 메서드를 사용합니다.
사용 가능한 맵 목록을 알고 싶다면 carla.Client.get.available_maps() 메서드를 사용합니다.

비오는 상황 같이 기후적 시나리오도 고려할 수 있도록 날씨의 변경도 가능한데, 이 또한 Client 객체를 사용하여 가능합니다.


`client = carla.Client('IP주소', 2000)`

# CARLA의 Actor와 Blueprint
시뮬레이션 내에서 역할을 수행하는 모든 것들은 carla.Actor로 정의됩니다. 차량뿐만 아니라 보행자, 신호등, 차량의 센서, 표지판 마저 모두 Actor에 속합니다.
그러나 이들 객체를 직접 생성하는 것은 아니며, blueprint를 활용하여 Actor를 생성합니다.
blueprint는 Carla에서 정의해둔, 말 그대로 블루 프린트 입니다. 각 blueprint는 시뮬레이션에서 표현될 그래픽 요소와, 해당 객체의 적절한 기능.. 예를 들어 차량이라면 차량 센서, 깜빡이, 쓰로틀링 및 스티어링과 같은 속성들을 사전 정의해둡니다.
이러한 blueprint는 blueprint library에서 조회할 수 있습니다.

블루 프린트는 

# Actor 생성

Actor의 생성은 World 객체를 통해 수행할 수 있습니다.



# Actor 제어 : Vehicle Controller

# Vehicle Controller 기반 제어 

# Waypoint 기반 제어