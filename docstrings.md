## **Макет Sphynx**

Общий макет этой строки документации показан ниже.

```python
"""< Summary. >

:param <variable_name>: <variable_description>, defaults to <default_value>
:type <variable_name>: <variable_type>(, optional)
<other parameters and types>:raises <error_type>: <error_description>
<other exceptions>:rtype: <return_type>
:return: <return_description>
"""
```

# Docstrings  

## **Синтаксис Sphinx**

В Sphinx используется такой же, как и в большинстве языков программирования синтаксис: `keyword(reserved word)`. Наиболее важные ключевые слова:

- `param` и `type`: значение параметра и тип его переменной;
- `return` и `rtype`: возвращаемое значение и его тип;
- `:raises`: описывает любые ошибки, которые возникают в коде;
- `.. seealso::`: информация для дальнейшего чтения;
- `.. notes::`: добавление заметки;
- `.. warning::`: добавление предупреждения.

Пример:

```python

def multiply(a, b, c=0):
    """Return sum of multiplication of all arguments.
 
    :param a: arg1
    :type a: int
    :param b: arg2
    :type b: int
    :param c: arg3, defaults to 0
    :type c: int, optional

    :raises ValueError: if arg1 is equal to arg2
    
    :rtype: int
    :return: multiplication of all arguments 
    """
    if a == b:
        raise ValueError('arg1 must not be equal to arg2')

    return a*b*c
```
