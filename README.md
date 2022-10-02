# WatermelonTheBest
## DAB_CODE
locate_bus_code.ipynb : Time Matrix <br>
init_vrp : 초기 경로 설정 <br>
boundary : 바운더리 설정 <br>
new_vrp : 노드 추가 시 신규 경로 설정 <br>
near_bus : 사용자에게 가까운 버스정류장 추천 <br>

------------------------
1. locate all : 걸린시간 매트릭스
2. cvrp : 경로계산 알고리즘
3. cvrp_with_addperson : 수정경로 알고리즘

## 가정
버스 정류장을 기준으로 승차 및 하차 </br>
<br>

## STEP1. 초기 경로 설정
버스 정류장을 기반으로 Matrix 구성</br>
OR-TOOLS를 사용해서 초기 경로 설정 </br>
초기 경로를 기반으로 탑승 가능한 boundary 설정(거리 기반)</br>
- boundary의 경우에는 차량이 5분 동안 운행 가능한 거리를 기준으로 산정 </br
<br>

## STEP2. 사용자 입장
if 가장 가까운 boundary 내 버스 정류장을 노드에 새로 추가했을 때 초기 경로의 10분 이상<br>
- 현재 배정 가능한 차량X <br>

else
- 사용자의 위치에서 가장 가까운 boundary내 버스 정류장 안내</br>
- 버스 정류장까지 도보 이동 방법 + 차량이 도착하기까지 예상 시간 안내</br>
- 사용자가 탑승을 수락한다면 해당 버스 정류장이 새로운 node로 공급자에게 전달</br>
<br>

## STEP3. 공급자(운전 기사) 입장
초기 경로를 TMAP 혹은 카카오 내비에 입력 후 운행시작 <br>
STEP2에서 노드가 추가되면 (현재 차량의 위치 + 기존 경로 + 새로운 노드)를 통해 Matrix 구성<br>
STEP1과 마찬가지로 OR-TOOLS를 사용해서 새로운 경로 설정 <br>