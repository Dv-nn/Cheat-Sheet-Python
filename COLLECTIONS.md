## Модуль Collections  
Модуль collections содержит специализированные классы контейнеров, альтернативных традиционным dict, list и tuple  
____  
import collections  
____  
**namedtuple()** - с именованным кортежем вы можете получить доступ к элементам непосредственно по их именам     
`movie = namedtuple('movie','genre rating lead_actor')  
ironman = movie(genre='action',rating=8.5,lead_actor='robert downey junior')  
titanic = movie(genre='romance',rating=8,lead_actor='leonardo dicaprio') `  
s2 = s1._asdict() - использовать для создания экземпляра OrderedDict из существующего экземпляра    
s2 = s1._replace(age='14') - изменить значение поля экземпляра    
____  
**Counter()** - посчитать, определить количество вхождений или наиболее (наименее) часто встречающихся элементов    
`Counter('абракадабра') --> Counter({'а': 5, 'б': 2, 'р': 2, 'к': 1, 'д': 1})`  

_Counter.elements()_ - преобразует результаты подсчета в итератор  
`Counter({'like': 2, 'dislike': 3}).elements() --> ['like', 'like', 'dislike', 'dislike', 'dislike'] `  

_Counter.most_common(n)_ - ищет n самых повторяющихся элементов        
`Counter('абракадабра').most_common(3) --> [('а', 5), ('б', 2), ('р', 2)]   # найдет ри самых встречающихся символа  `    
____  
**defaultdict** - не генерирует KeyError при попытке доступа к несуществующему ключу    
____  
**OrderedDict** – это словарь, в котором ключи сохраняют порядок, в котором они вставляются, что означает, что если вы измените значение ключа позже, он не изменит положение ключа    
____  
**deque** – это список, оптимизированный для вставки и удаления элементов      
deq.append("d")    
deq.appendleft("e")    
deq.pop()    
deq.popleft()    
deq.clear()   
____  
**ChainMap** -  используется для объединения нескольких словарей или отображений, возвращает список словарей    
ChainMap(dict1, dict2)      
chain_map.keys()    
chain_map.values()   
chain_map.new_child(dict3) - добавление нового словаря    



