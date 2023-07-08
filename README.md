<div align="center">
  <h1>🌳 토이프로젝트<br><br>
  ⚡ 포켓몬스터 밸런스 분석</h1>
</div>

<h4> 💭 Language : Python <br><br>
     📝 Library : Pandas, Numpy, Matplotlib, seaborn <br><br>
     🛠  Tool : Google Colab <br><br>
     📅 진행기간 : 2023.03.23 ~ 2023.06.07</h4>
     
### 👨‍👦‍👦 팀원소개
<table>
<tbody>
  <tr>
    <td align="left"><img src="" width="20px;" alt=""/><br /><b>팀원 : 이희구</b></a><br /></td>
   <tr/>
</tbody>
</table>
<br>

# 💡 분석 기획
* 포켓몬스터의 능력치 밸런스 분석<br>
* 포켓몬스터의 일반적인 능력 유형 조합 분석<br>
* 전설 포켓몬스터의 일반적인 능력 유형 조합 분석<br>
* 세대에 따른 기본 유형의 차이 분석<br>
* 가장 잡기 쉬운 포켓몬스터 및 세대 분석<br>
* 포켓몬스터가 가진 능력 개수 분석<br>
* 포켓몬스터의 BMI 분석<br>
* 가장 좋은 유형의 포켓몬스터 분석<br>
* 최고의 포켓몬스터 분석<br><br>
<br>

# 🔎 데이터 전처리
|전처리|방법|
|------|:-------------:|
|불필요한 컬럼 삭제|분석에 불필요한 컬럼들은 전부 삭제|
|값 대체|'Is_Legendary'컬럼 값 0은 "Non-legendary", 1은 "Legendary"로 대체|
|컬럼 결합|'Type1' 컬럼과 'Type2' 컬럼을 단일 유형으로 결합|
|형태 변환|능력 컬럼의 값을 리스트 형태로 변환|
|컬럼 생성|포켓몬스터별 능력의 개수 컬럼 생성|
|컬럼 생성|BMI 컬럼 생성|
|Nan값 대체|포획률의 30 (Meteorite)255 (Core) 값 Nan으로 변경|

<br><br>

# 📊 EDA(탐색적 데이터 분석)
## 1) 세대별 포켓몬 수
<h3 align="center"><img src= "https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/7791f49f-38f5-4f6a-a2b3-937814d21e9e"></h3>

* 홀수 세대는 짝수 세대에 비해 더 많은 포켓몬이 존재
<br>


## 2) 가장 흔한 유형
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/f84f8f58-23d1-49e6-a218-d35d2695f293></h3>

* 물 -> 노멀 -> 풀 ... 의 순으로 타입이 많다.

<br>

## 3) 보조 타입 여부
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/43d0fa9a-7fc3-4833-85de-59e5a95c5209></h3>

* 포켓몬의 거의 절반이 보조 유형이 없다.
<br>

## 4) 타입별 유형1과 유형2 비교
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/aaff2034-3f86-4086-a08b-1d4d48741285></h3><br>

### 4-A) 가장 일반적인 유형 조합 / 전설 포켓몬의 가장 일반적인 유형
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/c5e27e8c-ec27-4984-8b2d-205030678f80></h3>

* 첫 번째: 일반 + 비행 / 두 번째: 풀 + 독 / 세 번째: 벌레 + 비행
* 전설의 포켓몬의 가장 일반적인 유형은 Psychic

### 4-B) 세대에 따른 기본 유형의 차이
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/e8e2ce2a-129c-4423-84a8-e51fde62c8ef></h3>

* 1세대: 암흑, 강철, 비행 그리고 2세대에는 용, 비행같은 타입이 존재하지 않음
* 비행은 5,6 세대에서만 기본 유형으로 존재한다.
* 1세대에는 독, 3세대에는 강철, 5세대에는 어둠과 사이킥, 6세대에는 페어리 타입이 유난히 많다.
<br>

# 📄 Modeling
## 1) 군집화
<h3 align="center"><img src= https://github.com/LHG-Git/project/assets/100845169/e22674c7-b20e-4298-b8bc-b7b9f2f4583a></h3>

* 최적의 k값 도출을 위해 <strong>실루엣 계수</strong>를 사용<br> 
* 이때 실루엣 계수 평균만을 고려하지 않았고 figure5를 통해 도출된 인사이트를 함께 고려<br>
* 그 결과 cluster별 실루엣 계수 평균이 가장 높지는 않지만, 실루엣 계수의 너비가 비교적 균일한 지점에서 <strong>최적의 k(k=6)값을 도출</strong><br><br>

<h3 align="center"><img src= https://github.com/LHG-Git/project/assets/100845169/909e7b1d-0b40-4745-abc5-f3652ef06a84></h3>

* 최적의 K값을 통해 위치별 군집화 결과, figure 5에서 인천 부근의 서해에 위치한 관측치와, 부산 부근의 남해에 위치한 관측치에서 화학적 산소농도 수치가 높게 기록
<br>

## 2) 모델 성능 지표 선정
* 성능 지표의 경우 본 프로젝트의 주제 자체가 ‘해양정보를 활용한 해양오염 예측’이기 때문에, 모델의 설명력을 나타내는 R2값 보다 실제 예측 오차의 크기인 MAE가 본 프로젝트와 맞는 지표라고 생각하여, <strong>MAE값을 기준으로 최종 모델을 선정</strong>
<br>

## 3) 최종 모델 선정
<h3 align="center"><img src= https://github.com/LHG-Git/project/assets/100845169/da4b5525-0513-4615-a954-9778eadeda55></h3>

* 최종 예측결과 전체 모델에서 훈련세트에 <strong>약간의 과적합 존재</strong><br>
* <strong>CatBoost모델의 MAE값이 가장 준수</strong>
* 해양오염 예측에 사용될 모델을 <strong>CatBoostRegressor로 선정</strong>
<br>

## 4) 하이퍼파라미터 튜닝
* CatBoostRegressor모델의 특성상 하이퍼파라미터 튜닝을 진행하여도 모델 성능 개선에 크게 영향을 미치지 않음
* 오히려 파라미터의 default값으로 모델 예측을 수행하였을 때, 성능이 가장 높게 측정됨
<br>

## 5) K-Fold 교차검증
* 최종 선정된 모델(CatBoostRegressor)의 경우 train과 text의 성능 지표에서 약간의 과적합이 발생
* 과적합을 방지하기 위해 valid data를 생성
* 해당 데이터셋을 이용하여 가장 흔하게 사용되는 <strong>K-Fold 교차검증을 진행</strong>
* <strong>K값은 5로 지정</strong>하였으며, 모델 진행시에 골고루 데이터의 특성을 반영하기 위하여 <strong>shuffle을 진행</strong>
<br>

## 6) 모델평가 및 검증
<h3 align="center"><img src= https://github.com/LHG-Git/project/assets/100845169/1f3ca8e2-9710-404d-9425-d9a9d3f64cdf></h3>

* <strong>하이퍼파라미터 튜닝 및 K-Fold교차검증을 통하여 모델 성능 최적화를 진행하여 과적합 개선</strong>

* 그 결과 이전의 결과에서 보다 <strong>과적합이 많이 개선</strong>되었음을 확인하였고 <strong>모델의 성능 또한 향상됨</strong>

* 성능 지표의 경우 본 프로젝트의 주제가 ‘해양정보를 활용한 해양오염 예측’ 이기 때문에, 모델의 설명력을 나타내는 R2값 보다 실제 예측 오차의 크기인 MAE가 본 프로젝트와 맞는 지표라고 판단

* <strong>최종 모델링 결과 약 MAE = 0.076으로 실제값과 약 0.076이 차이가 나는 모델 완성</strong>

* 최근 10년동안 국내 연안의 화학적 산소농도가 연평균 1.13~1.82mg/L인 것을 고려했을 때, 꽤 정확도가 높은 모델이라고 설명할 수 있음



