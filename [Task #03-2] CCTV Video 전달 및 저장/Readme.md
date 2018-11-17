![Architecture](./images/task3-2.png)
<br>분산된 CCTV 단말들로 부터의 중앙 관제센터로의 영상 전달 및 저장 구성도
<br><br>


* 분산된 CCTV 단말들에서 중앙 관제센터로의 영상 전달 및 저장 기능 설계 및 구축
  - 총 8개의 분산된 CCTV 단말기들로부터 스트리밍 데이터를 저장하기 위하여 SmartX Playground에서의 IoT-Cloud를 활용하여 DataLake 및 중앙 관제센터 기능을 수행하는 사이트(GIST)에 전송 한다. 
  - 총 8개로 분산된 CCTV 단말기의 정보를 수집하기 위하여 CCTV 단말기들을 운영하는 사이트(Campus Site# 1, Campus Site# 2)의 컴퍼스 환경에 맞게 배치하고 SmartX Playground를 이용하여 DataLake 및 중앙 관제센터 스트리밍 데이터를 전송한다. 
  - 총 8개의 CCTV 단말기들은 KOREN 상에 있는 클라우드/네트워크 자원을 SmartX Open Platform, SDN/SDI API를 활용하여 Smart Campus Safety 서비스 테스트베드를 구축한다.
  - Campus Site# 1의 CCTV 4개 채널과 Campus Site# 2의 CCTV 4개 채널로 총 8개 CCTV 채널을 구성하고 안정적인 스트리밍 전송을 위하여 SmartX Playground의 워크프로우를 이용하여 관제센터로 전송한다.  
  -  Campus Site# 1과 Campus Site# 2에서 설치되어 인증 받은 CCTV 단말기로부터 미디어 스트리밍 데이터를 전달 받은 뒤, Apache Kafka로 구성된 메시지 브로커를 이용하여 스트리밍 정보를 수집한다. Kafka는 실시간으로 수집되는 다양한 종류의 데이터에 대해 Pub/sub 방식으로 메시지 전달이 가능하지만 이를 영구적으로 저장하기에는 적합하지 않기 때문에, MariaDB등을 통해 저장한다. 또한 향후 CCTV 영상에 대한 Deep Learning기반의 프레임 분석 및 처리 등을 고려한 별도의 저장 작업을 진행한다. 실시간 데이터 처리를 위해서는 인-메모리 기반 프로세싱 엔진인 Apache Spark를 활용한다. 
  - Campus Site# 1과 Campus Site# 2사이트에는 Type O SD-Access Box를 배치하고, SmartX Open Platform은 SDN/SDI API를 이용해 해당 Type O Box를 포함한 클라우드/네트워크 슬라이스를 구성한다. 
  - 총 8개로 분산된 CCTV 단말기들을 보다 효과적으로 활용하기 위하여 CCTV 단말기를 오픈소스 하드웨어인 라즈베리 파이 등을 통해 CCTV 단말의 고정형 모듈로 구성한다. 
  - Campus Site# 1 4채널과 Campus Site# 2 4채널로 분산된 총 8개의 CCTV 단말기들로 분산된 CCTV 단말기는 CCTV 단말기 내에 구성된 Apache Flume과 Fluentd등을 활용하여 스트리밍 데이터를 취합되고, 이를 Type O SD-Access Box를 통해 데이터 레이크(Type S, Type C)로 전달한다. 
  - 총 8개로 분산된 CCTV 단말기와 Type O Box간의 통신은 유선 통신 또는 WiFi 무선통신을 이용한다. 