![Architecture](./images/task3-1.png)
<br>-컨테이너기반 Smart Campus Safety 서비스 워크 플로우 개념 및 Web 기반 UI

* 컨테이너 기반 Smart Campus Safety 서비스 워크플로우 설계
  - Smart Campus Safety 서비스 실증을 위해 분산 CCTV 기기들이 운용되는 사이트와 Control Room 기능을 수행하는 사이트를 고려하여, 각 사이트의 역할에 맞는 요소기능들을 배치하고, 상호 연결되어 동작할 수 있도록 설정해야한다.
  - CCTV기기들이 운용되는 사이트에서는 다양한 종류의 CCTV들이 설치되어 수집되는 영상데이터를 Control Room에 전달하는 서비스가 구성된다. 각 사이트에는 Type O SD-Access Box를 배치하고, KOREN SmartX Open Platform은 해당 Type O Box들을 포함하는 클라우드/네트워크 슬라이스를 구성한다. 영상데이터 수집을 위해 드론 탑재 카메라, IP Camera, 라즈베리 파이 캠, 아두이노 캠과 같은 다양한 종류의 IoT기기를 Type O Box에 연결한다. 해당 기기들에서 수집되는 영상데이터는 RTMP(Real Time Messaging Protocol) 또는 RTSP (Real Time Streaming Protocol)을 통해 Type O Box에서 구성되는 컨테이너 기반의 CCTV관리 프로그램에 전달된다. 이때, 다양한 영상데이터 전송 프로토콜을 다루기 위해 FFMpeg와 같은 프로토콜 및 이미지 컨버터를 활용할 수 있다. 해당 CCTV관리 프로그램은 전달받은 영상데이터를 Control Room에 전달하거나, 개발자 및 사용자들에게 제공한다.
  - Control Room을 운용하는 사이트에서는 통합적인 CCTV관제를 위한 컨테이너 기반의 웹 서비스가 구성된다. 분산된 Type O Box에서 제공되는 영상데이터를 접근하여 표현하기 위한 웹 서비스를 중심으로 Control Room이 운용된다. 제공받은 영상데이터를 이용한 간단한 분석 서비스를 위해 컨테이너 기반의 영상데이터 분석 서비스를 제공할 수 있다.

* Web 기반 Smart Campus Safety 서비스 UI 설계 및 구현
  - Smart Campus Safety CCTV 서비스의 Control Room에서는 분산된 CCTV의 통합 관제를 위한 시각화 및 각 CCTV의 구체적 정보 확인을 위한 시각화가 필요하다. 또한, 간단한 영상 데이터 분석 결과를 확인하기 위한 시각화를 제공할 수도 있다.
  - 통합 관제 시각화를 위해서 분산되어 설치된 다수의 CCTV에서 제공되는 영상데이터를 통합된 UI를 통해 표현한다. VLC 또는 IP Camera viewer등을 활용해 통합된 영상데이터 시각화를 수행하고, 서비스 운용자의 관심영역을 능동적으로 파악하여 시각화하는 기능을 제공할 수 있다.
  - Type O Box에 구성된 CCTV관리 프로그램에서 제공하는 각 CCTV의 통계적 분석 결과 및 움직임 감지와 같은 간단한 영상데이터 분석결과를 표현할 수 있는 시각화 UI를 제공한다.
