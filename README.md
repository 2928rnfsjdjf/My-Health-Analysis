# 🏃‍♂️ 비만도와 운동량 상관관계 분석<br>
이 프로젝트는 ADsP 공부 내용을 바탕으로 비만도와 운동량의 관계를 분석한 기록입니다.<br>
kaggle의 [Estimation of Obesity Levels Based On Eating Habit] 데이터를 사용했습니다.<br>
1. kaggle에서 데이터를 다운로드해서 구글코랩으로 한번 돌려보겠습니다.<br>
2. from google.colab import files<br>
uploaded = files.upload() 이걸로 csv 파일을 넣습니다.<br>
3. import pandas as pd<br>
df = pd.read_csv('/content/ObesityDataSet_raw_and_data_sinthetic.csv')<br>
이걸로 df(dataframe, 데이터프레임)인 불러온 .csv 파일을 df라고 이름 붙여줍니다.<br>
4. df.info()를 통해서 Non-Null Count, Dtype, Memory Usage 정도 가볍게 파악해줍니다.<br>
``` <class 'pandas.core.frame.DataFrame'>
RangeIndex: 2572 entries, 0 to 2571
Data columns (total 17 columns):
 #   Column                          Non-Null Count  Dtype  
---  ------                          --------------  -----  
 0   Gender                          2572 non-null   object 
 1   Age                             2572 non-null   float64
 2   Height                          2572 non-null   float64
 3   Weight                          2572 non-null   float64
 4   family_history_with_overweight  2572 non-null   object 
 5   FAVC                            2572 non-null   object 
 6   FCVC                            2572 non-null   float64
 7   NCP                             2572 non-null   float64
 8   CAEC                            2572 non-null   object 
 9   SMOKE                           2572 non-null   object 
 10  CH2O                            2572 non-null   float64
 11  SCC                             2572 non-null   object 
 12  FAF                             2572 non-null   float64
 13  TUE                             2572 non-null   float64
 14  CALC                            2572 non-null   object 
 15  MTRANS                          2572 non-null   object 
 16  NObeyesdad                      2572 non-null   object 
dtypes: float64(8), object(9)
memory usage: 341.7+ KB
```
5. df.isnull().sum()를 통해서 결측치가 있는지 확인합니다<br>
<img width="278" height="606" alt="image" src="https://github.com/user-attachments/assets/550dc606-b0c6-48ec-aa43-a7cdc76964c0" />



### 가설 설정<br>
* 귀무가설($H_0$) : 운동량(X)와 BMI(Y)의 관계는 독립관계이다(유의마한 관계가 없다.)<br>
* 대립가설($H_1$) : 독립변수 X와 종속변수 Y는 연관이 있을 것이다(유의미한 관계가 있다.)<br>
### 상관 분석<br>
* 상관계수($r$): 독립변수와 종속변수의 관계가 얼마나 밀접한가?(-1~+1)<br>
* 산점도: 상관 분석을 그래프로 시각화<br>
### 회귀 분석<br>
* 결정계수($R^2$): 독립변수가 종속변수에 끼치는 영향력의 설명력이 얼마나 있는가?(0~1)<br>
### 가설 검정(T or Z)<br>
* **t-test**: 독립변수에 따른 종속변수의 차이가 있는지 확인<br>
(표본이 작으면 t, 많으면 z 이지만, 보통 t를 많이 사용하므로 t검정을 이용.)
