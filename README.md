# ๐ Sparta_coding

## 2021.06.07
  * sparta_coding data analysis week 01 complete

## 1์ฃผ์ฐจ ๊ณผ์  (ํผ์ ๋ฐ์ดํฐ)
## Q1. ํผ์๋ฅผ ๊ฐ์ฅ ๋ง์ด ์์ผ๋จน๋ ์์ผ์ ์ธ์ ์ธ๊ฐ์?
```
import pandas as pd
import matplotlib.pyplot as plt

pizza_data = pd.read_csv('./data/pizza_09.csv')
pizza_calls_data = pizza_data.groupby('์์ผ')['ํตํ๊ฑด์'].sum()

weeks = ['์', 'ํ', '์', '๋ชฉ', '๊ธ', 'ํ ', '์ผ']
sorted_pizza_calls_data = pizza_calls_data.sort_values(ascending=True).reindex(weeks)
```

## graph
```
plt.figure(figsize=(10,5))
plt.bar(sorted_pizza_calls_data.index, sorted_pizza_calls_data)
plt.title('์์ผ๋ณ ํผ์ ์ด ์ฃผ๋ฌธ ์')
plt.xlabel('์์ผ')
plt.ylabel('์ฃผ๋ฌธ ์')
plt.show()

print('ํผ์๋ฅผ ๊ฐ์ฅ ๋ง์ด ์์ผ๋จน๋ ์์ผ : ์ผ์์ผ')
```


![1](https://user-images.githubusercontent.com/47622991/121136646-d88ddc00-c870-11eb-842e-fbfd2985fd83.PNG)



## Q2. ํผ์๋ฅผ ๊ฐ์ฅ ๋ง์ด ์์ผ๋จน๋ ๊ตฌ๋ ์ด๋์ธ๊ฐ์?
```
pizza_calls_data_for_place = pizza_data.groupby('๋ฐ์ ์ง_๊ตฌ')['ํตํ๊ฑด์'].sum()
sorted_pizza_calls_data_for_place = pizza_calls_data_for_place.sort_values(ascending=True)
```

## graph
```
plt.figure(figsize=(10,5))
plt.bar(sorted_pizza_calls_data_for_place.index, sorted_pizza_calls_data_for_place)
plt.title('๊ตฌ๋ณ ํผ์ ์ด ์ฃผ๋ฌธ ์')
plt.xlabel('์์ธํน๋ณ์ ๊ตฌ')
plt.ylabel('์ฃผ๋ฌธ ์')
plt.xticks(rotation=45)
plt.show()

print('ํผ์๋ฅผ ๊ฐ์ฅ ๋ง์ด ์์ผ๋จน๋ ๊ตฌ : ๊ฐ์๊ตฌ')
```


![2](https://user-images.githubusercontent.com/47622991/121136641-d75caf00-c870-11eb-9fba-d2aefed11838.PNG)



## ๋ฐ ๊ทธ๋ํ 2๊ฐ ๊ทธ๋ฆฌ๊ธฐ
## ์์ผ๋ณ ์นํจ ๋ฐ ํผ์ ์ด ์ฃผ๋ฌธ ์
```
chicken07 = pd.read_csv('./data/chicken_07.csv')
chicken08 = pd.read_csv('./data/chicken_08.csv')
chicken09 = pd.read_csv('./data/chicken_09.csv')
chicken_data = pd.concat([chicken07, chicken08, chicken09])
sum_of_calls_by_week = chicken_data.groupby('์์ผ')['ํตํ๊ฑด์'].sum().reindex(weeks)
sorted_sum_of_calls_by_week = sum_of_calls_by_week.sort_values(ascending=True)

plt.bar(sorted_sum_of_calls_by_week.index, sorted_sum_of_calls_by_week)
plt.bar(pizza_calls_data.index, pizza_calls_data)
plt.title('์์ผ๋ณ ์นํจ ๋ฐ ํผ์ ์ด ์ฃผ๋ฌธ ์')
plt.xlabel('์์ผ')
plt.ylabel('์ฃผ๋ฌธ ์')
plt.legend(['์นํจ ์ฃผ๋ฌธ ์','ํผ์ ์ฃผ๋ฌธ ์'])
plt.show()
```


![3](https://user-images.githubusercontent.com/47622991/121136644-d88ddc00-c870-11eb-9236-0d082eaa5580.PNG)





----------------

## 2์ฃผ์ฐจ ๊ณผ์ 
### 4์ ๊ฐ๋จ๊ตฌ์ ์ ๋์ธ๊ตฌ๋ฅผ ๋ถ์ํด๋ด์๋ค.
### Q1. 4์์ ์ ๋์ธ๊ตฌ๊ฐ ๊ฐ์ฅ ๋ง์ ๊ตฌ๋ ์ด๋์ผ๊น์? (bar)

```
import pandas as pd
import matplotlib.pyplot as plt

population_of_April = pd.read_csv('./data/population04.csv')
population_of_July = pd.read_csv('./data/population07.csv')

population_by_gu_of_April = population_of_April.groupby('๊ตฐ๊ตฌ')['์ ๋์ธ๊ตฌ์'].sum()
sorted_population_by_gu_of_April = population_by_gu_of_April.sort_values(ascending=True)

plt.figure(figsize=(10,5))
plt.bar(sorted_population_by_gu_of_April.index,sorted_population_by_gu_of_April)
plt.title('์์ธํน๋ณ์ ๊ตฌ๋ณ 4์ ์ ๋์ธ๊ตฌ ์')
plt.xlabel('๊ตฐ๊ตฌ')
plt.ylabel('์ ๋์ธ๊ตฌ์')
plt.xticks(rotation = 90)
plt.show()

print('4์์ ์ ๋์ธ๊ตฌ๊ฐ ๊ฐ์ฅ ๋ง์ ๊ตฌ : ๊ฐ๋จ๊ตฌ')
```

![1](https://user-images.githubusercontent.com/47622991/121793535-03927a00-cc3b-11eb-8e1c-5af6ae8ec303.png)
<br>
4์์ ์ ๋์ธ๊ตฌ๊ฐ ๊ฐ์ฅ ๋ง์ ๊ตฌ : ๊ฐ๋จ๊ตฌ


### Q2. 4์๊ณผ 7์์ ๊ฐ๋จ๊ตฌ์ ์ผ๋ณ ์ ๋์ธ๊ตฌ๋ ์ด๋ค๊ฐ์? (line)

```
population_kangnam_of_April = population_of_April[population_of_April['๊ตฐ๊ตฌ'] == '๊ฐ๋จ๊ตฌ']
population_kangnam_of_April = population_kangnam_of_April.groupby('์ผ์')['์ ๋์ธ๊ตฌ์'].sum()

population_kangnam_of_July = population_of_July[population_of_July['๊ตฐ๊ตฌ'] == '๊ฐ๋จ๊ตฌ']
population_kangnam_of_July = population_kangnam_of_July.groupby('์ผ์')['์ ๋์ธ๊ตฌ์'].sum()

date_of_April = []
date_of_July = []
for day in population_kangnam_of_April.index:
    date_of_April.append(str(day))
    
for day in population_kangnam_of_July.index:
    date_of_July.append(str(day))

plt.figure(figsize=(20,5))    
plt.plot(date_of_April, population_kangnam_of_April, label = '2020๋ 4์')
plt.plot(date_of_July, population_kangnam_of_July, label = '2020๋ 7์')

plt.title('2020๋ 4์ ๋ฐ 7์์ ์์ธํน๋ณ์ ๊ฐ๋จ๊ตฌ ์ผ๋ณ ์ ๋์ธ๊ตฌ ์')
plt.xlabel('๋ ์ง')
plt.ylabel('์ ๋์ธ๊ตฌ ์')
plt.xticks(rotation = 90)
plt.legend()
plt.show()
```


![2](https://user-images.githubusercontent.com/47622991/121793539-08efc480-cc3b-11eb-9ec0-cb60a862a2b2.png)




-----------

## 3์ฃผ์ฐจ ๊ณผ์ 

### ๋๋ง์ ์๋ ํด๋ผ์ฐ๋ ๋ง๋ค๊ธฐ
### ์ต์ ๊ณก ๊ฐ์ฌ ์๋ ํด๋ผ์ฐ๋ ๋ง๋๊ธฐ
### ๋ด๊ฐ ์ข์ํ๋ ๊ฐ์ฌ๋ค์ txt ํ์ผ๋ก ์ ์ฅ, ์ํ๋ ์ด๋ฏธ์ง ํ์ผ ์ ์ฅ (week03 dict)

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from PIL import Image
from wordcloud import WordCloud

result = ""

for number in range(1,7):
    index = '{:02}'.format(number)
    filename = 'Sole_' + index + '.txt'
    
    text = open('./data/'+ filename, 'r', encoding='utf-8-sig')
    result += text.read().replace('\n', ' ')
```



### WordCloud    
```
font_path = 'C:\WINDOWS\Fonts\malgun.ttf'
mask = np.array(Image.open('./data/cd.jpg'))
wc = WordCloud(font_path=font_path, background_color='white', mask=mask)
wc.generate(result)

f = plt.figure(figsize=(40,40))
plt.rcParams['font.family'] = 'Malgun Gothic'
plt.imshow(wc, interpolation='bilinear')
plt.title('WordCloud of Sole Musics' , size=40)
plt.axis('off')
plt.show()
f.savefig('./data/SoleWordCloud.png')
```


![SoleWordCloud](https://user-images.githubusercontent.com/47622991/122008629-3d5ab080-cdf4-11eb-80fc-eafa02b48ea4.png)




### ์์์ผ๊ณผ ํ์์ผ์ ์๊ฐ์๋ฃ์๊ฐ ๋น๊ต
```
sparta_data = pd.read_csv('./data/enrolleds_detail.csv')

format = '%Y-%m-%dT%H:%M:%S.%f'
sparta_data['done_date_time'] = pd.to_datetime(sparta_data['done_date'],format=format)
sparta_data['done_date_time_weekday'] = sparta_data['done_date_time'].dt.day_name()
sparta_data['done_date_time_hour'] = sparta_data['done_date_time'].dt.hour

sparta_data_of_monday = sparta_data[sparta_data['done_date_time_weekday'] == 'Monday']
sparta_data_of_monday = sparta_data_of_monday.groupby('done_date_time_hour')['user_id'].count()

sparta_date_of_tuesday = sparta_data[sparta_data['done_date_time_weekday'] == 'Tuesday']
sparta_date_of_tuesday = sparta_date_of_tuesday.groupby('done_date_time_hour')['user_id'].count()

plt.figure(figsize=(10,5))
plt.plot(sparta_data_of_monday.index, sparta_data_of_monday, label = '์์์ผ')
plt.plot(sparta_date_of_tuesday.index, sparta_date_of_tuesday, label = 'ํ์์ผ')
plt.xlabel('์๊ฐ')
plt.ylabel('์๊ฐ์๋ฃ ์')
plt.xticks(np.arange(24))
plt.title('์์์ผ๊ณผ ํ์์ผ์ ์๊ฐ์๋ฃ ์๊ฐ ๋น๊ต')
plt.legend()
plt.show()

print('์์์ผ๊ณผ ํ์์ผ์ ๋น๊ตํ์ ๋, ํ์์ผ 18์์ ๋ง์ผํํ๊ธฐ ๊ฐ์ฅ ์ข๋ค.')
```

![1](https://user-images.githubusercontent.com/47622991/122008567-2d42d100-cdf4-11eb-9a33-42ad544d76d4.png)




---------
## 4์ฃผ์ฐจ ๊ณผ์ 

![heatmap](https://user-images.githubusercontent.com/47622991/123232274-f49da880-d513-11eb-853c-90deae9f95ea.PNG)

![์บก์ฒ](https://user-images.githubusercontent.com/47622991/123233383-fb78eb00-d514-11eb-8dae-c53743914b1d.PNG)

[stocks_report.pdf](https://github.com/seunghy1468/Sparta_coding/files/6707736/stocks_report.pdf)

* ๋ถ์
  * ์นด์นด์ค์ ๋ค์ด๋ฒ๋ ์๋นํ correlation์ด ์กด์ฌํ๋ค.
  * ์์๊ณผ๋ ๋ค๋ฅด๊ฒ ๋ค์ด๋ฒ๋ ์นด์นด์ค๋ฟ๋ง ์๋๋ผ LGํํ๊ณผ์ correlation์ด ์กด์ฌํ๋ค.
  * ์ผ์ฑ์ ์๋ ์นด์นด์ค, ๋ค์ด๋ฒ, ํ๋์๋์ฐจ ๋ฑ ์ฌ๋ฌ ํ์ฌ์์ correlation์ด ์กด์ฌํ๋ค.
  * ํ๋๋ชจ๋น์ค๋ SK์ด๋ธ๋ฒ ์ด์๊ณผ์ correlation์ ๋์ง๋ง, LGํํ๊ณผ์ correlation์ ๋ฎ๋ค.
  * SK์ด๋ธ๋ฒ ์ด์์ ํ๋๋ชจ๋น์ค์ ํ๋์๋์ฐจ ๋ชจ๋ correlation์ด ๋๋ค.
  * LGํํ์ SK์ด๋ธ๋ฒ ์ด์๊ณผ์ correlation์ด ์นด์นด์ค, ๋ค์ด๋ฒ, ์ผ์ฑ์ ์ ๋ฑ์ ๋นํด ๋ฎ๋ค.
