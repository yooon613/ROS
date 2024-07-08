# ROS


## 1. 실행환경 
- Ubuntu 20.04 LTS, ROS1-noetic
  
## 2. Hardware 스펙
model : turtlebot3 waffle_pi
Size (L x W x H) : 281mm x 306mm x 141mm
Weight : 1.8kg
SBC (Single Board Computers) : 라즈베리파이
LDS(Laser Distance Sensor) : 360 Laser Distance Sensor LDS-02
IMU센서 : 3축 자이로 센서, 3축 가속도 센서, 3축 지자계 센서, 라즈베리 파이 카메라, 360도 LiDAR

![Screenshot from 2024-07-08 16-43-14](https://github.com/yooon613/ROS/assets/124541123/40377f1a-ab2e-4eb1-985d-76f6c1cef767)

## 3. install
+ remote PC</br>
    + ROS 1 [Link](https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/)를 통해 설치한다.

    + 원격 PC에 ROS 설치</br>
    <pre>
        <code>
        $ sudo apt update
        $ sudo apt upgrade
        $ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh
        $ chmod 755 ./install_ros_noetic.sh 
        $ bash ./install_ros_noetic.sh
        </code>
    </pre>
    + 종속 ROS 패키지 설치</br>
    <pre>
        <code>
        $ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
        ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
        ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
        ros-noetic-rosserial-python ros-noetic-rosserial-client \
        ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
        ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
        ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
        ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
        </code>
    </pre>
    + 종속 ROS 패키지 설치</br>
    <pre>
        <code>
        $ sudo apt install ros-noetic-dynamixel-sdk
        $ sudo apt install ros-noetic-turtlebot3-msgs
        $ sudo apt install ros-noetic-turtlebot3
        </code>
        
## 3. SLAM
SLAM (Simultaneous Localization and Mapping)은 로봇이 주변 환경의 지도를 생성하면서 동시에 자신의 위치를 추정하는 기술
-> 이를 통해 로봇은 이전에 방문하지 않은 환경에서도 자율적으로 이동가능

SLAM의 주요 구성요소 2가지

로컬라이제이션 (Localization):
로봇이 현재 자신의 위치를 추정하는 과정
센서 데이터(예: 라이다, 카메라, IMU 등)를 사용하여 주변 환경과의 관계를 파악

맵핑 (Mapping):
로봇의 주변 환경에 대한 지도를 생성하는 과정
센서 데이터를 바탕으로 환경의 구조를 파악하고 이를 지도로 표현

## 4. Navigation
내비게이션은 로봇이 주어진 환경 내에서 출발지점에서 목표지점으로 안전하게 이동하는 과정
이를 위해 로봇은 주어진 환경의 맵, 그리고 다양한 센서 정보를 활용
맵은 이전 SLAM(Simultaneous Localization and Mapping) 과정에서 생성되며, 로봇의 현재 위치와 목표 위치를 기반으로 이동 경로를 계획
