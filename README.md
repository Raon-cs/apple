## :apple: 리미트리스

---

### 사과 당도 품질 데이터를 활용한 사과 분류 인공지능 서비스


## 👩‍👩‍👧‍👧 역할

---

`팀장`
<br/>
`데이터 수집 및 전처리` : 불필요 특성 제거, 중복행 및 결측값 제거, 인덱스 재정렬, 라벨 인코딩, 원핫 인코딩 등
<br/>
`모델 제작` : 환경데이터 활용 예측모델, 이미지 활용 예측 모델

## 🔗 프로젝트 개요

---

### 💡 기획 배경

- 정책적 배경 : 귀농정착 지원사업(3년간 월 최대 백만원 지원) , 로컬푸드 활성화 정책(지역 먹거리 선순환 체계)
- 사회적 배경 : 농촌에 대한 인식변화, 농촌정착지원사업의 정책 성과 등이 반영되며 농촌에 대한 긍정적 이미지 구축, 장년층의 은퇴 후 귀농 생활 증가
- 경제적 배경 : 귀농 인구의 증가 및 인식의 변화에 따른 고급 과일 선호도 증가 추세
- 사회 트렌드 : 개인의 건강, 환경 오염, 동물 윤리 등 다양한 이유로 증가 추세에 있는 국내외 채식자 수, 소비자는 비싸더라도 당도가 높아 만족감을 줄 수 있는 과일을 선호함
- 기술적 배경 : AI허브 등 대량의 데이터를 가공해서 제공하는 사이트의 수가 증가하면서, 필요한 데이터에 접근하여 활용하는 것이 비교적 쉬워짐

### 📅 프로젝트 진행 기간

2022.08.09 ~ 2022.08.31

## 🖇️ 주요 내용

---

### 📝 기존 측정 기술
- 롯데마트 AI 선별 시스템
    - 근적외선으로 과일을 촬영해 대량의 화상 데이터를 얻어 딥러닝으로 분석
    - 과일의 당도, 중량, 수분함량, 후숙도 등의 파악이 간으
    - 일부 과일에만 사용 중
    - 개별 농장에서의 활용은 제한됨
- 비파괴 당도 선별기
    - 근적외선을 과일에 조사 후 반사되는 빛을 분석하여 당도를 측정하는 방식
    - 사과의 수가 많을 수록 조사가 제한적이며 정밀한 파악이 어려움
    - 기계 1대당 300만원 정도로 가격대가 높음
- 파괴 당도 선별기
    - 착즙하여 얻은 과즙을 당도계 센서에 떨어드려 당도를 측정하는 방식
    - 모든 과일에 대하여 측정하는 것은 사실상 불가능하므로, 표본으로 고른 일부 과일만 측정 가능


### 📝 서비스 소개

- 새로운 서비스의 필요성 : 기본 방식의 한계 극복, 농장에서 개별적으로 사용가능, 기존 방식보다 낮은 비용

- 서비스의 달성 목표 : 사용자가 직접 사과의 당도를 `빠르고 정확하게 측정`해 등급을 알려주는 서비스

- 기존 시장과의 차별성 : 여러 사람들이 이용가능, 더 정밀한 파악, 소요시간 적음, 과일에 직접 접촉할 필요 없음

- 기대효과 : 사과 분류에 사용되는 인적/물적 자원 낭비 최소화, 사과 분류 기술의 범용성 확대, 추후 사과를 원하는 당도로 기르기 위한 농업의 보조 역할

- 목표 달성 전략
    - 데이터 구축 : AI허브 데이터 활용(전북 장수 사과 당도 품질 데이터)
        * https://aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&aihubDataSe=realm&dataSetSn=490
    - 데이터 전처리 및 인공지능 모델 개발 : 사과 영상 데이터 및 환경 센서 데이터 등 수집한 학습용  데이터들 전처리, 사과 품종별 테스트용 모델 학습
    - 인공지능 모델 성능 향상 : 테스트용 모델의 예측값의 여러가지 지표 향상(정확도, 정밀도 등), 테스트용 모델의 목표 수준 달성도 측정, 학습데이터를 활용하여 인공지능 모델별 성능 확인 및 개선


### 단계별 기본 설명

#### 라벨링 데이터(json data)

##### 1. 파일 통합 및 csv형태로 변환

##### 2. 데이터 전처리(불필요한 열 제거, 중복행 제거, 결측값 제거, 인덱스 재정렬, 라벨 인코딩, 원핫인코딩)

 2-1) 불필요 특징 제거 = 이름, 제작자, 제작버전, 제작년도, 데이터셋 타입, 이미지데이터 폴더경로, 라벨링 데이터 폴더경로, 저작권정보, 라이센스 고유번호, 라이센스 이름 등)
 
 2-2) 필요 특징 추출 = 수집정보, 이미지 데이터 정보, 어노테이션 정보(segmentation 좌표, 어노테이션 면적, bounding box 정보, 사과 당도 품질 클래스(A,B,C) 등)
 
 2-3) 추출 데이터 데이터프레임 형태로 변환 및 통합

##### 3. 모델 선택 및 모델 제작

 3-1) 사과 품종별 데이터 불러오기 및 하나의 데이터프레임으로 통합
 
 3-2) 불필요 특징 제거 = 구분, 데이터셋 타입, 촬영농가위치, 파괴당도, 촬영각도, 라이센스 고유번호, 원천데이터, 이미지 이름, 이미지 세로크기, 가로크기 등
 
 3-3) 결측값 행 제거(약 5%로 확인되어 결측값을 대체가 아닌 제거 실시
 
 3-4) 원핫인코딩(사전 훈련용 검증용 데이터 통합후 원핫인코딩 진행 / 사과종류, 사진촬영일시, 일출시간, 일몰시간)
 
 3-5) 통합 데이터 분리(훈련용, 검증용)
 
 3-6) 목표값 라벨인코딩(당도등급 = A, B, C -> 숫자 0,1,2) # 목표값은 상하관계가 존재하기 때문에 원핫인코딩이 아닌 라벨인코딩 실시

##### 4. 성능확인

 4-1) 성능확인 = 정확도, 평균 제곱오차, 결정계수, 혼동행렬
 
 4-2) 모델 저장


#### 이미지 데이터(image data)

##### 1. 데이터 전처리

 1-1) MASK R-CNN활용 사과 이미지 분류할 가중치 생성(이미지 + 라벨링 데이터)
 
 1-2)MASK R-CNN활용 이미지별 좌표 추출
 
 1-3)추출한 이미지 좌표 통합
 
 1-4)환경데이터 전처리

##### 2. 모델 선택 및 모델 제작
 
 2-1) 불러온 환경데이터 추가적인 데이터 전처리(불필요 특징제거, img_file_name기준 재정렬)
 
 2-2) 환경데이터와 추출한 이미지좌표 통합(기준 = img_file_name)
 
 2-3) 필요없는 특징 제거 = 타입, 농가위치, 당도, 이미지 가로크기, 세로크기 등
 
 2-4) 데이터 통합 후 원핫 인코딩 실시(segmentation 좌표)
 
 2-5) 통합 데이터 훈련용과 검증용으로 분리 및 목표값 분리
 
 2-6) 목표값 라벨 인코딩(사과 당도 등급)
 
 2-7) 모델 선택 및 모델 제작

##### 3. 성능확인
 
 3-1) 성능확인 = 평균제곱오차, 정확도, 혼동행렬 등
 
 3-2) 환경데이터모델 = 정확도  0.95
 
 3-3) 이미지 데이터 모델 = 정확도 0.39

 3-4) 통합(환경+이미지) 데이터 모델 = 0.44

### :calendar: 개발일정
![개발일정](https://github.com/Raon-cs/pig/assets/108639467/68e5df2f-ef06-4cbc-925e-341b17af00c9)


### ⚒️ 협업 환경

---

### Cooperation & Communication & Library

- Colab
- Goolgle drive
- Slack
- Mask-RCNN
- LabelEncoder
- train_test_split
- mean_squared_error
- r2_score
- confusion_matrix
- numpy
- pandas
- seaborn
- matplotlib
- matplotlib.pyplot
- LinearRegression
