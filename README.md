# 🍅 Sparta_coding

## 2021.06.07
  * sparta_coding data analysis week 01 complete

## 1주차 과제 (피자 데이터)
## Q1. 피자를 가장 많이 시켜먹는 요일은 언제인가요?
```
import pandas as pd
import matplotlib.pyplot as plt

pizza_data = pd.read_csv('./data/pizza_09.csv')
pizza_calls_data = pizza_data.groupby('요일')['통화건수'].sum()

weeks = ['월', '화', '수', '목', '금', '토', '일']
sorted_pizza_calls_data = pizza_calls_data.sort_values(ascending=True).reindex(weeks)
```

## graph
```
plt.figure(figsize=(10,5))
plt.bar(sorted_pizza_calls_data.index, sorted_pizza_calls_data)
plt.title('요일별 피자 총 주문 수')
plt.xlabel('요일')
plt.ylabel('주문 수')
plt.show()

print('피자를 가장 많이 시켜먹는 요일 : 일요일')
```


![1](https://user-images.githubusercontent.com/47622991/121136646-d88ddc00-c870-11eb-842e-fbfd2985fd83.PNG)



## Q2. 피자를 가장 많이 시켜먹는 구는 어디인가요?
```
pizza_calls_data_for_place = pizza_data.groupby('발신지_구')['통화건수'].sum()
sorted_pizza_calls_data_for_place = pizza_calls_data_for_place.sort_values(ascending=True)
```

## graph
```
plt.figure(figsize=(10,5))
plt.bar(sorted_pizza_calls_data_for_place.index, sorted_pizza_calls_data_for_place)
plt.title('구별 피자 총 주문 수')
plt.xlabel('서울특별시 구')
plt.ylabel('주문 수')
plt.xticks(rotation=45)
plt.show()

print('피자를 가장 많이 시켜먹는 구 : 강서구')
```


![2](https://user-images.githubusercontent.com/47622991/121136641-d75caf00-c870-11eb-9fba-d2aefed11838.PNG)



## 바 그래프 2개 그리기
## 요일별 치킨 및 피자 총 주문 수
```
chicken07 = pd.read_csv('./data/chicken_07.csv')
chicken08 = pd.read_csv('./data/chicken_08.csv')
chicken09 = pd.read_csv('./data/chicken_09.csv')
chicken_data = pd.concat([chicken07, chicken08, chicken09])
sum_of_calls_by_week = chicken_data.groupby('요일')['통화건수'].sum().reindex(weeks)
sorted_sum_of_calls_by_week = sum_of_calls_by_week.sort_values(ascending=True)

plt.bar(sorted_sum_of_calls_by_week.index, sorted_sum_of_calls_by_week)
plt.bar(pizza_calls_data.index, pizza_calls_data)
plt.title('요일별 치킨 및 피자 총 주문 수')
plt.xlabel('요일')
plt.ylabel('주문 수')
plt.legend(['치킨 주문 수','피자 주문 수'])
plt.show()
```


![3](https://user-images.githubusercontent.com/47622991/121136644-d88ddc00-c870-11eb-9236-0d082eaa5580.PNG)





----------------

## 2주차 과제
### 4월 강남구의 유동인구를 분석해봅시다.
### Q1. 4월의 유동인구가 가장 많은 구는 어디일까요? (bar)

```
import pandas as pd
import matplotlib.pyplot as plt

population_of_April = pd.read_csv('./data/population04.csv')
population_of_July = pd.read_csv('./data/population07.csv')

population_by_gu_of_April = population_of_April.groupby('군구')['유동인구수'].sum()
sorted_population_by_gu_of_April = population_by_gu_of_April.sort_values(ascending=True)

plt.figure(figsize=(10,5))
plt.bar(sorted_population_by_gu_of_April.index,sorted_population_by_gu_of_April)
plt.title('서울특별시 구별 4월 유동인구 수')
plt.xlabel('군구')
plt.ylabel('유동인구수')
plt.xticks(rotation = 90)
plt.show()

print('4월의 유동인구가 가장 많은 구 : 강남구')
```

![1](https://user-images.githubusercontent.com/47622991/121793535-03927a00-cc3b-11eb-8e1c-5af6ae8ec303.png)



### Q2. 4월과 7월의 강남구의 일별 유동인구는 어떤가요? (line)

```
population_kangnam_of_April = population_of_April[population_of_April['군구'] == '강남구']
population_kangnam_of_April = population_kangnam_of_April.groupby('일자')['유동인구수'].sum()

population_kangnam_of_July = population_of_July[population_of_July['군구'] == '강남구']
population_kangnam_of_July = population_kangnam_of_July.groupby('일자')['유동인구수'].sum()

date_of_April = []
date_of_July = []
for day in population_kangnam_of_April.index:
    date_of_April.append(str(day))
    
for day in population_kangnam_of_July.index:
    date_of_July.append(str(day))

plt.figure(figsize=(20,5))    
plt.plot(date_of_April, population_kangnam_of_April, label = '2020년 4월')
plt.plot(date_of_July, population_kangnam_of_July, label = '2020년 7월')

plt.title('2020년 4월 및 7월의 서울특별시 강남구 일별 유동인구 수')
plt.xlabel('날짜')
plt.ylabel('유동인구 수')
plt.xticks(rotation = 90)
plt.legend()
plt.show()
```


![2](https://user-images.githubusercontent.com/47622991/121793539-08efc480-cc3b-11eb-9ec0-cb60a862a2b2.png)
