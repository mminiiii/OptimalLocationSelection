# OptimalLocationSelection
2023 1학기 데이터사이언스캡스톤프로젝트 팀 포동포동

## 💻 프로젝트 소개
<서울시 공동육아나눔터 최적 입지 선정>
- 현존 공동육아나눔터의 위치를 고려하여, 서울시 내 공동육아나눔터 추가 입지 제안
- 최소한의 시설물(공동육아나눔터) 설치를 통해 최대의 수요(아동 인구)를 커버할 수 있는 최적 입지 찾기

개발 기간: 23.03.17 ~ 23.06.09

## 🫶 팀 구성 및 역할
- 김보현(팀장): 데이터 수집, 행정동 추출, EDA, 클러스터링 변수 생성, 필터링 수요 기반 입지 선정
- 김민: 데이터 수집, 데이터 전처리, EDA, 클러스터링&필터링, 전체 수요 기반 입지 선정

## 🔍 분석 흐름
1. 데이터 수집
2. 데이터 전처리 (주소 정제 -> 위/경도 변환 -> 행정동 추출, 데이터 병합, 결측치 보간)
3. EDA (변수별 지도 시각화, 공동육아나눔터 현존 행정동의 인사이트 찾기, 상관분석)
4. 행정동 클러스터링을 위한 변수 생성 (전체 데이터를 축소한 PCA의 loading을 가중치로 인구 지수, 예산/복지 지수 생성)
5. 클러스터링 결과를 기반으로 입지 후보 행정동 1차 필터링
6. 수요 정의 (수요 = 반경 2.5km 이내 아동 인구)
7. 전체 행정동의 수요 기반 LSCP 입지 선정
8. 필터링된 행정동만의 수요 기반 LSCP + MCLP 입지 선정
9. 입지 선정 결과 분석

## 👶 분석 결과
#### EDA 인사이트
- 총 생활인구는 서울 중심지에서 높은 반면, 아동 인구는 주거지가 많은 서울 외곽에서 더 높게 나타남
- 20~40대 직장인구는 마포구, 용산구, 서초구, 강남구 등 한강 부근에서 높게 나타남
- 한부모 가정/저소득층은 서울 서부 및 북부의 자치구에서 상대적으로 높게 나타남
- 자치구별 예산과 한부모 가정/저소득층의 수는 0.7 정도의 높은 양의 상관관계를 가짐
- 현존 공동육아나눔터는 복지 제도적 특성이 강함
- 현존 공동육아나눔터는 아동 인구, 신혼부부 인구 등 인구 분포를 고려하지 못한 배치였음

#### 전체 행정동 수요 기반 입지 결과
![화면 캡처 2023-06-14 214348](https://github.com/mminiiii/OptimalLocationSelection/assets/90174257/8534bf33-1daf-47ec-85b0-1684a3b57c92)


#### 필터링 행정동 수요 기반 입지 결과
LSCP의 시설물 설치 개수에 따른 미충족 수요 그래프에서의 elbow point인 4를 최적의 시설물 개수로 보고, n=4인 MCLP 적용

![화면 캡처 2023-06-14 214420](https://github.com/mminiiii/OptimalLocationSelection/assets/90174257/a1db93c6-5ea0-472a-8444-f6ff60422065)

