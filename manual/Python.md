#формирование списка по условию 1
d2= []  
for i in d:
  try:
    if (i["p"] < 9):
      d2.append(i)
  except KeyError:
    d2.append(i)
#формирование списка по условию 2
for i in vid: 
  if ("universities") in i:
    if (i["universities"] != []):
      mas.append(i)
    elif ("occupation") in i:
      if (i["occupation"] != []):
        mas.append(i)
  elif ("occupation") in i:
    if (i["occupation"] != []):
        mas.append(i)
        
#Генерация списка по условию 1
p = [i for i in d if i["id"] != []] 
#Обработка списка (удаление словарей) (способ 1)
for k in d: 
  if "p" in k:
    del k["p"]
#Обработка списка (удаление словарей) (способ 1)
for k in d: 
  k.pop("p", None)
#конвертация текста в число
a = int('1') 
#Перебор дат
from datetime import timedelta, date 
def daterange(start_date, end_date):
    for n in range(int ((end_date - start_date).days)):
        yield start_date + timedelta(n)
mas = []
start_date = date(2015, 1, 1)
end_date = date(2015, 6, 2)
for single_date in daterange(start_date, end_date):
    d = single_date.strftime("%d")
    m = single_date.strftime("%m")
    mas.append(d+m)

# создание колоды карт при помощи генератора списков масти
suits = "HDCS" # масти
ranks = "23456789TJQKA" # ранги
deck = [r+s for r in ranks for s in suits] # генерируем колоду

#исключающая итерация — например, вывести элементы 1-го списка, которых нет во 2-м списке:
for item in set(L).difference(L2)
lst.insert(0,'vocal') # добавление ключа vocal в первой позиции списка lst
lst.extend([3,4]) #добавление элементов
lst.index('guitar') #определение индекса [] ключа guitar в списке lst
lst.remove(100) #удаление 100 из списка lst
del d[n] #удаленние n-го элемента списка d
len(lst) #кол-во элементов в списке

# слияние списков (https://habr.com/ru/post/63539/)
a= [{"id":50, "universities": [], "au":41},{"id":84, "universities": [], "occupation": [], "au":41},{"id":53, "occupation": [], "au":41},{"id":55, "au":41},{"id":1709967, "universities": [{"city": 1, "id":55}]}]
for k in a:      #Обработка списка (удаление вложенных списков) (способ 1)
  try:
    if (k['universities'] == []):
      pass
    else:
      id = (k['universities'][0]['id'])
      (k['universities'][0]).clear()
      (k['universities'])=id
  except KeyError:
    pass
print(a)

#удаление словаря по признаку ключа.
d = {'myArray': [{'name': 'good', 'value': '1'}, {'name': 'bad', 'value': '2'}]} 
d=[x for x in d['myArray'] if x['name'] != 'bad'] # Вариант А
for a in d['myArray']: # Вариант Б
  if (a['name'] == u'bad'):
    d['myArray'].remove(a)
print(d)

##Кортежи
points={'a':(3,4), 'b':(1,2), 'c':(5,5), 'd':(3,3)}
points2={k: v for k, v in points.items() if v[0] < 5 and v[1] < 5}
points2=dict((k, v) for (k, v) in points.items() if v[0] < 5 and v[1] < 5)
points2=dict((k, v) for k, v in points.items() if all(x < 5 for x in v))
points2=dict(filter(lambda x: (x[1][0], x[1][1]) < (5, 5), points.items()))

#ввод данных с консоли
h = int(input()) 
#пересечение двух списков
list_a = [1, 2, 3, 4]
list_b = [2, 3, 4, 5]
print(set(list_a) & set(list_b)) #способ 1
print([a for a in list_a for b in list_b if a == b])  #способ 2
#фильтрация по списку индикаторов
d = [{"a":1, "b":457}, {"a":2, "b":47}]
a = [0, 1]
filtered_list = [i for (i, v) in zip(d, a) if v]
print (filtered_list)
# фильтр по признаку равенства
def filter_list(list, key, value, limit=None):
    return [i for i in list if i[key] == value]
    
#Извлечение данных из словаря
a = {100: "one", 23: "two", 3: "three"}
if 23 in a:
  print (a[23])
    
#Вывод значения по умолчанию для отсутствующего ключа словаря
d = {'a':1, 'b':2}
print(d.get('c'))
print(d.get('c', 3))

#Поиск наиболее часто-встречающегося значения списка
a = [1, 2, 3, 1, 2, 3, 2, 2, 4, 5, 1]
print(max(set(a), key=a.count))
#Поиск наиболее часто-встречающегося значения списка (с указанием кол-ва повторений)
import collections
a = [1, 2, 3, 1, 2, 3, 2, 2, 4, 5, 1]
cnt = Counter(a)
print(cnt.most_common(3))
>[(2, 4), (1, 3), (3, 2)]

#создание словаря из двух списков:
dict(zip([1, 2, 3, 4], ['a', 'b', 'c', 'd']))
> {1: 'a', 2: 'b', 3: 'c', 4: 'd'}

#объединить словари
x = {'a':1, 'b': 2}
y = {'b':10, 'c': 11}
z = {**x, **y}

#Объединить два списка словарей (без объединения ключей)
lst1 = [{"id": 1, "x": "one"},{"id": 2}]
lst2 = [{"id": 2, "x": "two"}, {"id": 3, "x": "three"}]
result = {x['id']:x for x in lst2 + lst1}.values() 
#Способ 2
for i in d: #очистка
        if all(k["id"] != i["id"] for k in база): 
            база.append(i)

#Объединить два списка словарей (c объединением ключей)
l1 = [{"index":1, "b":2}, {"index":2, "b":3}, {"index":3, "green":"eggs"}]
l2 = [{"index":1, "c":4}, {"index":2, "c":5}] 
l3=[dict(sum([z.items() for z in z2],[])) for z2 in [[x3 for x3 in l1+l2 if x3['index']==key] for key in set([x1['index'] for x1 in l1]+[x2['index'] for x2 in l2])]]
>[{'index': 1, 'b': 2, 'c': 4}, {'index': 2, 'b': 3, 'c': 5}, {'index': 3, 'green': 'eggs'}]

#объединить одинаковые по длине списки в словарь
students = ["Peter", "Julia", "Alex"]
marks = [84, 65, 77]
dictionary = dict(zip(students, marks))
print(dictionary) # {'Peter': 84, 'Julia': 65, 'Alex': 77}
#выдать одинаковые по длине списки попарно
countries = ['France', 'Germany', 'Canada']
capitals = ['Paris', 'Berlin', 'Ottawa']
for country, capital in zip(countries,capitals):
    print(country, capital) # France Paris 
                              Germany Berlin
                              Canada Ottawa
#перебор возможных матчей между командами
import itertools
friends = ['Team 1', 'Team 2', 'Team 3', 'Team 4']
list(itertools.combinations(friends, r=2)) # [('Team 1', 'Team 2'),      ('Team 1', 'Team 3'),  ('Team 1', 'Team 4'),  ('Team 2', 'Team 3'),  ('Team 2', 'Team 4'),  ('Team 3', 'Team 4')]

#посчитать количество повторяющихся значений в списке
import collections
count = collections.Counter(['a','b','c','d','b','c','d','b'])
print(count) # Counter({'b': 3, 'c': 2, 'd': 2, 'a': 1}) 

#Циклы по спискам с индексами
colors = ['red', 'green', 'blue', 'yellow']
for i, color in enumerate(colors):
    print(i, '-->', color)

# Циклы по двум спискам
names = ['raymond', 'rachel', 'matthew']
colors = ['red', 'green', 'blue', 'yellow']
for name, color in zip(names, colors):
    print(name, '-->', color)

«Изучаем Python» Марка Лутца
Бизли «Python книга рецептов»
#https://pandas.pydata.org/pandas-docs/stable/ — сводные таблицы и таблицы  (http://qaru.site/questions/1682110/merge-two-lists-of-dicts-of-different-lengths-using-a-single-key-in-python)

# перемножение по словарю
from collections import ChainMap
fruits_prices = {"apple": 0.80, "grape": 0.40, "orange": 0.50}
veggies_prices = {"tomato": 1.20, "pepper": 1.30, "onion": 1.25}
prices = ChainMap(fruits_prices, veggies_prices)
order = {"apple": 4, "tomato": 8, "orange": 4}
for product, units in order.items():
  price = prices[product]
  subtotal = units * price
  print(f"{product:6}: ${price:.2f} × {units} = ${subtotal:.2f}")

>apple : $0.80 × 4 = $3.20
>tomato: $1.20 × 8 = $9.60
>orange: $0.50 × 4 = $2.00
