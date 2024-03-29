## ITERTOOLS    
  Стандартная библиотека функций языка Python дает возможность программисту создавать определенные последовательности объектов и всячески ими манипулировать.   
При помощи простых итераций, действующих в цикле, можно наполнять массивы неким содержимым, а пользуясь генераторами списков – задавать более сложные условия для их формирования.  
____  
import itertools *  
from itertools import product  
____  
1 - с помощью этих методов можно генерировать объекты или совершать определенные действия неограниченное количество раз  
2 -  функции, позволяющие комбинировать различные значения, меняя местами их составляющие  
3 - для управления данными в списке или любой другой последовательности значений,  умеют автоматически удалять отдельные элементы, не удовлетворяющие заданных программистом условий  
4 - их применение иногда также бывает очень полезным для решения многих довольно специфических задач, часто они становятся актуальны в паре с другими итераторами
____  
| Название | Назначение | Результат |  
|----------------|---------------|----------------|    
|-------- 1 --------|---------------|----------------|   
| count | Итерация с заданным шагом без ограничений | count(10) --> 10 11 12 13 14 ... |  
| cycle | Итерация с повторением без ограничений | cycle('ABCD') --> A B C D A B C D ... |  
| repeat | Итерация с повторением заданное количество раз | repeat(10, 3) --> 10 10 10 |  
|-------- 2 --------|---------------|----------------|    
| combinations | Комбинация всех возможных значений без повторяющихся элементов | list(combinations('DOG', 2)) --> [('D', 'O'), ('D', 'G'), ('O', 'G')] |  
| combinations_with_replacement | Комбинация всех возможных значений с повторяющимися элементами | combinations_with_replacement('DOG', 2) --> [(DD, DO), (DG, OO), ...] |  
| permutations | Комбинация с перестановкой всех возможных значений | permutations('DOG', 2) --> [(DO, DG), (OD, OG)...] |  
| product | product	Комбинация, полученная из всех возможных значений вложенных списков | list(product([1, 2], repeat=2)) --> [(1, 1), (1, 2), (2, 1), (2, 2)] | 
|-------- 3 --------|---------------|-----------------|    
| filterfalse | Все элементы, для которых функция возвращает ложь | list(filterfalse(lambda i: i == 0, [1, 2, 3, 0, 4, 5, 1])) --> [1, 2, 3, 4, 5, 1] |  
| dropwhile | Все элементы, начиная с того, для которого функция вернет ложь | dropwhile(lambda x: x<5, [1,4,6,4,1]) --> 6 4 1 |  
| takewhile | Все элементы, до тех пор, пока функция не вернет истину | takewhile(lambda x: x<5, [1,4,6,4,1]) --> 1 4 |  
| compress | Удаление элементов, для которых было передано значение ложь | list(compress('CAT', [True, False, True])) --> ['C', 'T'] |  
|-------- 4 --------|---------------|----------------|      
| chain | Поочередное объединение списков при помощи итераторов | chain('ABC', 'DEF') --> A B C D E F |  
| chain.from_terable | Аналогично chain, но аргумент — список, в который вложены объединяемые списки | (chain.from_iterable(['ABC', 'DEF']) --> A B C D E F |  
| islice | Получение среза, благодаря указанному количеству элементов [start:stop:step] | islice('ABCDEFG', 2, None) --> C D E F G |  
| zip_longest | Объединение нескольких итераций с повышением размера до максимального | list(zip_longest('DOG', [0, 1, 2, 3], fillvalue = ' ')) --> [('D', 0), ('O', 1), ('G', 2), (' ', 3)] |  
| tee | Возвращает n независимых итераторов из одного итерируемого объекта | tee([1, 2, 3], 3) --> [1, 2, 3] [1, 2, 3] [1, 2, 3] |  
| groupby | Группировка элементов последовательности по некоторым ключевым значениям | groupby(iterable,key=None) |  
| accumulate | Каждый элемент результирующей последовательности равен сумме текущего и всех предыдущих исходной последовательности | accumulate([1,2,3,4,5]) --> 1 3 6 10 15 |  
| starmap | Первый аргумент — это функция. Второй аргумент — это с писок параметров, подаваемых на функцию | starmap(pow, [(2,5), (3,2), (10,3)]) --> 32 9 1000 |  
|----------------|---------------|----------------|    
____  
![]() 
