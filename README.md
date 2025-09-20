# Check-Up Guide Robot

This project proposes a ROS2-based autonomous robot designed to guide patients in large-scale medical check-up centers.  
It is currently at the system planning and design stage, with simulation implementation in progress.

## Project Overview

- Goal: Reduce congestion and improve navigation experience in health screening centers
- Functionality:
  - Personalized route guidance via UWB wristbands
  - Real-time screen + voice instructions
  - Autonomous elevator riding and floor transition
  - Sensor fusion-based obstacle avoidance

## Hardware and Design

- MCU: Dual structure (SBC + STM32 or Jetson + MCU)
- Sensors:
  - 2D LiDAR (RPLIDAR S1)
  - Depth camera (Intel RealSense D455)
  - IMU (BNO085)
  - UWB Module (e.g., DWM3000)
  - NFC reader (wristband authentication)
  - Bumper, ultrasonic sensors, wheel encoder
- Display: 25-inch touchscreen + LED direction panel
- Power: DC + wireless charging for wristband

Design Notes:
- Designed for multi-floor indoor environments (~5000㎡)
- Wristband (NFC + UWB) identifies and tracks patient
- UI optimized for elderly and foreign visitors

## Software Components

- ROS2: Navigation2 stack (Nav2) with Cartographer SLAM
- Object Tracking: YOLOv5 + DeepSORT
- Wristband Tracking: UWB distance + Kalman filter
- Elevator Interface: V2I (Vehicle-to-Infrastructure) simulation planned
- Simulation Environment: Gazebo + hospital world map (planned)

## Algorithms Used

| Function               | Algorithm                     |
|------------------------|-------------------------------|
| Mapping & Localization | Cartographer (SLAM)           |
| Global Planning        | A*                            |
| Local Planning         | DWB (Dynamic Window Approach) |
| Object Tracking        | YOLO + DeepSORT               |
| Fail-Safe Navigation   | Predictive UWB dead zone mode |

---

## 건강검진 안내 자율주행 로봇

본 프로젝트는 대형 건강검진센터에서 환자에게 **개인 맞춤형 길 안내**를 제공하는 ROS2 기반 자율주행 로봇 설계안입니다.  
현재는 시스템 기획 단계이며, 시뮬레이션 구현이 진행 중입니다.

### 프로젝트 개요

- 목표: 대기 혼잡 완화 및 고령자·외국인 대상 실내 내비게이션 제공
- 기능:
  - UWB/NFC 팔찌를 통한 환자 식별 및 경로 안내
  - 터치스크린 + 음성으로 시각·청각 동시 안내
  - 엘리베이터 탑승 포함한 경로 자율 주행
  - 센서 융합 기반 장애물 회피

### 하드웨어 및 설계

- MCU 구조: SBC(Master) + MCU(Slave) 또는 Jetson + STM32 구조
- 센서 구성:
  - 2D LiDAR (RPLIDAR S1)
  - 3D 카메라 (RealSense D455)
  - IMU (BNO085)
  - NFC 리더기 (인증)
  - UWB 모듈 (거리 측정)
  - 초음파, 범퍼, 엔코더 등
- 디스플레이: 25인치 터치스크린 + 후면 LED 방향 표시
- 전원: 유선 DC + 손목밴드 무선충전

설계 특징:
- 약 5000㎡ 규모의 다층 실내 환경을 타겟으로 설계
- 팔찌 기반의 사용자 인식 + 추적
- 고령자 및 외국인을 고려한 직관적인 UI 제공

### 소프트웨어 구성

- ROS2: Navigation2 + Cartographer SLAM
- 객체 인식 및 추적: YOLOv5 + DeepSORT
- 손목밴드 위치 추정: UWB 거리 + 칼만 필터
- 엘리베이터 연동: V2I 통신 (시뮬레이션 계획 중)
- 시뮬레이션: Gazebo 기반 병원 환경 구축 예정

### 적용 알고리즘

| 기능                    | 적용 알고리즘                 |
|-------------------------|------------------------------|
| 맵핑 및 위치추정       | Cartographer (SLAM)          |
| 전역 경로 계획         | A*                           |
| 지역 경로 계획         | DWB (Dynamic Window Approach)|
| 객체 추적              | YOLO + DeepSORT              |
| 비가시 영역 대응       | UWB 기반 예측 Fail-safe 주행|

