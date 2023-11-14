<div align="center">
  <h1>🌳 토이프로젝트<br><br>
  ⚡ 포켓몬스터 밸런스 분석</h1>
</div>

<h4> 💭 Language : Python <br><br>
     📝 Library : Pandas, Numpy, Matplotlib, seaborn <br><br>
     🛠  Tool : Google Colab <br><br>
     📅 진행기간 : 2022.01.17 ~ 2022.01.31</h4>
     
### 👨‍👦‍👦 팀원소개
<table>
<tbody>
  <tr>
    <td align="left"><img src="" width="20px;" alt=""/><br /><b>팀원 : 이희구</b></a><br /></td>
   <tr/>
</tbody>
</table>
<br>

# 🔎 기술통계
* 데이터 세트를 로드하여 기술통계를 통해 누락된 값 확인
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

# 🔎 가설 설정
* 가설 : 3세대에서 4세대로 넘어오면서 포획 난이도가 어려워졌을 것이다.

<br><br>

# 🔎 가설 검증
* 가설 : 3세대에서 4세대로 넘어오면서 포획 난이도가 어려워졌을 것이다.
* Welch's t-test를 통하여 3세대와 4세대의 유의 변수를 도출
* p_value(≓0.0396) < a(=0.05)으로 인한 가설 채택 → 3세대와 4세대의 포획 확률에는 유의한 차이가 있다.

<br><br>

# 📊 EDA (탐색적 데이터 분석)
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
<br>

### 4-B) 세대에 따른 기본 유형의 차이
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/e8e2ce2a-129c-4423-84a8-e51fde62c8ef></h3>

* 1세대: 암흑, 강철, 비행 그리고 2세대에는 용, 비행같은 타입이 존재하지 않음
* 비행은 5,6 세대에서만 기본 유형으로 존재한다.
* 1세대에는 독, 3세대에는 강철, 5세대에는 어둠과 사이킥, 6세대에는 페어리 타입이 유난히 많다.
<br>

## 5) 가장 잡기 쉬운 포켓몬스터 세대
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/edd8af1b-784e-4b76-8306-8beba9e9fc65></h3>

* 3세대가 가장 포획하기 쉬운 포켓몬이며, 4세대가 가장 어렵다.
* 전설의 포켓몬은 6세대부터 잡기가 더 쉽다.
<br>

## 6) 가장 잡기 쉬운 포켓몬스터
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/19efde61-eeaa-4f05-a142-e79f75b2503d></h3>

* 페어리 타입이 가장 잡기 쉬운 포켓몬이며, 드래곤이 가장 어렵다.
* 잡기 가장 쉬운 전설의 포켓몬은 풀과 벌레 타입이다.
<br>

## 7) 포켓몬은 보통 몇 가지 능력을 가지고 있는가
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/fa3f8dc7-751e-4aa3-bc8f-c24369f0e32d></h3>

* 비전설의 포켓몬의 가장 일반적인 능력 개수는 3개이며, 대부분의 전설의 포켓몬은 1개의 능력만 가지고 있다.
<br>

## 8) 피지컬이 좋은 포켓몬스터는?
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/77fa5f99-2f23-4d2d-904a-802962adc481></h3>

* 가장 키가 큰 포켓몬 5개 중 2개는 전설의 포켓몬이며, 무거운 포켓몬 5개 중 4개는 전설의 포켓몬이다.
* 셀레스틸라는 몸무게와 키 모두 top5안에 드는 유일한 포켓몬이다.
<br>

## 9) BMI가 가장 높은 포켓몬스터 / BMI가 가장 낮은 포켓몬스터
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/48a6ae87-ed98-4bcc-91bc-95f74bf17877></h3>

* BMI가 가장 높은 포켓몬스터는 Cosmoem이다.
* Haunter와 진화 이전 Gastly가 가장 낮으며, Dratini와 진화버전 Gragonair가 그 뒤를 잇는다.
<br>

## 10) 최고 세대
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/7789826e-a908-49b3-a404-84ce4099e2c3></h3>

* 일반 포켓몬 중에서는 4세대에 최고의 능력치를 가진 포켓몬이 있고, 전설의 포켓몬 중에서는 3세대에 최고의 능력치를 가진 포켓몬이 있다.
<br>

## 11) 속성별 상관관계
### 11-A) 일반 포켓몬스터
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/ec624a17-70eb-4498-93f7-3cd75429ecea></h3>

* 일반 포켓몬에 대해
>* hp와 sp_attack, sp_defense와 attack 사이에는 양의 관계가 있다. 하지만 방어와는 낮은 상관관계를 보여주고있다. 방어가 높은 포켓몬이 더 높은 hp를 가질것이라 생각하였지만 그게 아니었다.
>* attack은 defense와 가장 밀접한 관계가 있다.
>* Defense는 sp_defense와 가장 강한 관계가 있다.
>* Speed는 defense와 매우 약한 음의 관계가 있다.
<br>

### 11-B) 전설 포켓몬스터
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/5aeb433e-2d40-4f4f-921d-07e149646bbb></h3>

* 전설의 포켓몬에 대해
>* 전설의 포켓몬은 attack과 sp_defense, 방어와 sp_attack의 관계가 음의 관계로 바뀐다. 또한 attack과 speed가 양의 관계로, defense와 speed의 관계가 음의 관계로 더 강해졌다.
>* 즉, 공격수 타입의 전설의 포켓몬은 공격력과 스피드가 더 빨라졌고 수비수 타입의 전설의 포켓몬은 방어를 높이고 스피드를 낮추며 밸런스를 조절하였다.
>* 그렇다면, 공격적인 전설의 포켓몬은 밸런스가 매우 붕괴된게 아닌가..? 공격과 스피드를 둘다 줬으니!!
<br>

## 12) 가장 좋은 유형은?
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/5dace01c-195c-4c01-9177-5992ddcae1c6></h3>

* 일반 포켓몬:
>* Top 5 types - attack: fighting, dragon, ground, dark, steel
>* Top 5 types - sp_attack: psychic, electric, fairy, fire, ghost
>* Top 5 types - defense: steel, rock, ground, ghost, ice
>* Top 5 types - sp_defense: steel, fairy, ghost, psychic, dragon
>* Top 5 types - hp: fairy, normal, fighting, ice, ground
>* Top 5 types - speed: flying, electric, fire, dark, dragon
>* Top 5 types - base_total: ghost, steel, fighting, fairy and ice
* <strong>불, 어둠, 용 타입의 포켓몬은 attack, sp_attack, speed가 top5에 들기 때문에 공격위주의 포켓몬이다.</strong>
* <strong> 요정, 얼음, 땅 타입의 포켓몬은 defense, sp_defense, hp가 top5에 들기 때문에 방어위주의 포켓몬이다.</strong>
<br>

* 전설의 포켓몬:
>* Top 5 types - attack: ground, bug, fairy, normal, dragon
>* Top 5 types - sp_attack: dragon, dark, fairy, ground, electric
>* Top 5 types - defense: ground, steel, normal, dragon, ghost
>* Top 5 types - sp_defense: ice, water, normal, psychic, rock
>* Top 5 types - hp: ghost, dark, fairy, normal, dragon
>* Top 5 types - speed: flying, normal, grass, rock, electric
>* Top 5 types - base_total: dragon, ground, fairy, ghost, normal
* <strong>일반, 전기 타입의 포켓몬이 공격하기 좋은 포켓몬</strong>
* <strong>고스트, 노멀, 드래곤이 방어하기 좋은 포켓몬</strong>
<br>

## 13) 유형 효율성 분석
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/8bbfb770-d5f8-483a-b251-15407eb52747></h3>

* 전기는 땅 타입에 약하고, 노말은 격투 타입에 약하다는 것을 강조하기 한다. 신기하게도 유령은 유령끼리 약하고 비행은 얼음에 극도로 약하다는 인사이트를 도출했다.
<br>

## 14) 최고의 포켓몬스터는?
<h3 align="center"><img src= https://github.com/LHG-Git/Pokemon_Balance_Analysis/assets/100845169/b0bacd85-0ab5-48ef-88f6-fb355a95b01b></h3>

* 뮤츠와 레쿠자가 가장 좋은 포켓몬으로 선정되었다.
<br>

## 📄 분석결과 요약
* 물타입의 포켓몬이 가장 많고, 그 다음이 노멀과 풀이다.

* 3세대가 가장 잡기 쉬운 포켓몬이며, 4세대는 가장 어렵다.
  
* 전설의 포켓몬은 6세대로 진입하면서 부터 포획하기가 조금 더 수월해졌다.
  
* 페어리 타입은 가장 잡기 쉬운 포켓몬이고, 드래곤이 가장 어렵다.
  
* 잡기 쉬운 전설의 포켓몬은 풀가 벌레 타입이다.
  
* 4세대에는 최고의 일반 포켓몬이 있고, 3세대에는 최고의 전설에 포켓몬이 있다.
  
* 1~7세대 통틀어 뮤츠와 레쿠자가 최고의 포켓몬이다.





