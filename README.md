# apple

기반 환경 = 구글 코랩(google colab)
사용 라이브러리 = LabelEncoder, train_test_split, mean_squared_error, r2_score, confusion_matrix, numpy, pandas, seaborn, matplotlib, matplotlib.pyplot, LinearRegression, os 등

# 라벨링 데이터(json data)

1) 파일 통합 및 csv형태로 변환

2) 데이터 전처리(불필요한 열 제거, 중복행 제거, 결측값 제거, 인덱스 재정렬, 라벨 인코딩, 원핫인코딩)

 2-1) 불필요 특징 제거 = 이름, 제작자, 제작버전, 제작년도, 데이터셋 타입, 이미지데이터 폴더경로, 라벨링 데이터 폴더경로, 저작권정보, 라이센스 고유번호, 라이센스 이름 등)
 
 2-2) 필요 특징 추출 = 수집정보, 이미지 데이터 정보, 어노테이션 정보(segmentation 좌표, 어노테이션 면적, bounding box 정보, 사과 당도 품질 클래스(A,B,C) 등)
 
 2-3) 추출 데이터 데이터프레임 형태로 변환 및 통합

3) 모델 선택 및 모델 제작

 3-1) 사과 품종별 데이터 불러오기 및 하나의 데이터프레임으로 통합
 
 3-2) 불필요 특징 제거 = 구분, 데이터셋 타입, 촬영농가위치, 파괴당도, 촬영각도, 라이센스 고유번호, 원천데이터, 이미지 이름, 이미지 세로크기, 가로크기 등
 
 3-3) 결측값 행 제거(약 5%로 확인되어 결측값을 대체가 아닌 제거 실시
 
 3-4) 원핫인코딩(사전 훈련용 검증용 데이터 통합후 원핫인코딩 진행 / 사과종류, 사진촬영일시, 일출시간, 일몰시간)
 
 3-5) 통합 데이터 분리(훈련용, 검증용)
 
 3-6) 목표값 라벨인코딩(당도등급 = A, B, C -> 숫자 0,1,2) # 목표값은 상하관계가 존재하기 때문에 원핫인코딩이 아닌 라벨인코딩 실시

4) 성능확인

 4-1) 성능확인 = 정확도, 평균 제곱오차, 결정계수, 혼동행렬
 
 4-2) 모델 저장


# 이미지 데이터(image data)

1)데이터 전처리

 1-1) MASK R-CNN활용 사과 이미지 분류할 가중치 생성(이미지 + 라벨링 데이터)
 
 1-2)MASK R-CNN활용 이미지별 좌표 추출
 
 1-3)추출한 이미지 좌표 통합
 
 1-4)환경데이터 전처리

2) 모델 선택 및 모델 제작
 
 2-1) 불러온 환경데이터 추가적인 데이터 전처리(불필요 특징제거, img_file_name기준 재정렬)
 
 2-2) 환경데이터와 추출한 이미지좌표 통합(기준 = img_file_name)
 
 2-3) 필요없는 특징 제거 = 타입, 농가위치, 당도, 이미지 가로크기, 세로크기 등
 
 2-4) 데이터 통합 후 원핫 인코딩 실시(segmentation 좌표)
 
 2-5) 통합 데이터 훈련용과 검증용으로 분리 및 목표값 분리
 
 2-6) 목표값 라벨 인코딩(사과 당도 등급)
 
 2-7) 모델 선택 및 모델 제작

3) 성능확인
 
 3-1) 성능확인 = 평균제곱오차, 정확도, 혼동행렬 등
