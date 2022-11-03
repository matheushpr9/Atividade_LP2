# Numpy básico

Numpy é a abreviação de Numerical Python e é um dos pacotes mais importantes para processamento numérico em Python. Numpy oferece a base para a maioria dos pacotes de aplicações científicas que utilizem dados numéricos em Python (estruturas de dados e algoritmos).

 Pode-se destacar os seguintes recursos que o pacote Numpy contém:
-  Um poderoso objeto array multidimensional;
- Funções matemáticas sofisticadas para operações com arrays sem a necessidade de utilização de laços *for*;
- Recursos de algebra linear e geração de números aleatórios

Além de seus óbvios usos científicos, o pacote NumPy também é muito utilizado em análise de dados como um eficiente contêiner multidimensional de dados genéricos para transporte entre diversos algoritmos e bibliotecas em Python.

Instalação: https://scipy.org/install.html
Documentação:  https://numpy.org/doc/1.16/

Outros pacotes
Existem diversos pacotes Python disponíveis para download na internet. Cada pacote tem como objetivo a solução de determinado tipo de problema e para isso são desenvolvidos novos tipos, funções e métodos.

Alguns pacotes são bastante utilizados em um contexto de ciência de dados como por exemplo:
- Numpy
- Pandas
- Scikit-learn
- Matplotlib
Alguns pacotes não são distribuídos com a instalação default do Python. Neste caso devemos instalar os pacotes que necessitamos em nosso sistema para podermos utilizar suas funcionalidades.


## Criando arrays Numpy

A biblioteca Numpy, nos disponibiliza uma função semelhante ao range, mas diferente do range, ele cria um arry do numpy.

### Obs:
diferente das listas em Python, os arrays do numpy, só suportam um mesmo tipo de dados, por array.

No Python:
```
import numpy

numpy.arange(10)
```
ou
```
import numpy as np

np.arange(10)
```

Além disso, o Python nos posiblita pegar apenas a função desejada, para não sobrecarregarmos a memória, importando funções que não iremos utilizar.
No Python:
```
from numpy import arange
arange(10)
```

A partir de listas
No Python:
```
import numpy as np

km = np.array([1000, 290, 2300, 4987])
```

A partir de dados externo
No Python:
```
import numpy as np

km = np.loadtxt(fname = r'C:\Users\matheus.ptasinski\Desktop\Alura\Formação - Python para Data Science\python-data-science-aula-1-inicio\Python_Data_Science\Numpy\data\carros-km.txt', dtype = int)
```

Arrays de multipla-dimensões
A biblioteca Numpy nos da a possiblidade  de trabalhar comn arrays de multipla-dimensões.
Nesse modulo vamos nos limitar aos arrays de 2 dimensões, as matrizes ou tabelas.

No python:
```
import numpy as np

dados = [ 
    ['Rodas de liga', 'Travas elétricas', 'Piloto automático', 'Bancos de couro', 'Ar condicionado', 'Sensor de estacionamento', 'Sensor crepuscular', 'Sensor de chuva'],
    ['Central multimídia', 'Teto panorâmico', 'Freios ABS', '4 X 4', 'Painel digital', 'Piloto automático', 'Bancos de couro', 'Câmera de estacionamento'],
    ['Piloto automático', 'Controle de estabilidade', 'Sensor crepuscular', 'Freios ABS', 'Câmbio automático', 'Bancos de couro', 'Central multimídia', 'Vidros elétricos']
]

acessorios = np.array(dados)

print(acessorios)


acessorios.shape


#3 linhas e 8 colunas
```

Mas, porque utilizar os arrays numpy, ao invés das listas do Python?
Comparando desempenho com a listas.
No Python:
```
import numpy as np
np_array = np.arange(1000000)

%time for _ in range(100): np_array*=2
```
ou
```
py_list = list(range(1000000))
%time for _ in range(100): pylist =[x*2 for x in py_list]
```

Após executar os dois códigos, chegamos a conclusão que o numpy é muita maiseficiente em processamento de dados que o próprio Python.
Enquanto o Python demora 14 segundos para fazer uma operação, o Numpy faz a mesma  


Operações aritméticas com arrays Numpy


Operações entre arrays e constantes

Com listas do Python:
```
km = [44410., 5712., 37123., 0., 25757.]
anos = [2003, 1991, 1990, 2019, 2006]

idades = 2019 - anos
print(idades)
```
Nos é retornados um erro.

Já com arrays Numpy:
```
km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])

idades = 2019 - anos
print(idades)
```

Nos é retornado o seguinte array 
```
[2003 1991 1990 2019 2006]
```

Operações entre arrays 

No Python:
```
import numpy as np

km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])



idades = 2019 - anos

km_media_ano = km/anos

print(km_media_ano)
```

Operações com arrays de duas dimensões
No python:
```
import numpy as np

km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])

dados = np.array([km, anos])

km_media = dados[0] / dados[1] 
```




Seleção com arrays

A seleção em arrays se assemelha muito com a seleção de listas.
Mas com algumas pequenas implementações, por exemplo:
No Python, tanto esse código:
```
import numpy as np

km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])

dados = np.array([km, anos])

print(dados[1][2])
```
Quanto este:
```
import numpy as np
km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])
dados = np.array([km, anos])
print(dados[1,2])
```

Extra1:
```
import numpy as np
km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])
dados = np.array([km, anos])
print(dados[:,1:4])
```

Extra1:
```
import numpy as np
km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])
dados = np.array([km, anos])

media = dados[:,1:4][0]/dados[:,1:4][1]

print(media)
```

Isso ocorre apenas com arrays Numpy e não ocorre com listas

Outra maneira interessante de percorrer um array é com pulos, como podemos ver a seguir:
No Python:
```
import numpy as np

lista = np.arange(10)

print(lista[0:8:2])
```

Nesse caso, o código nos retorna uma lista, com os itens que estão entre o index 0 e 7,  começando no index 0 e indo / pulando 2 em 2


Indexação com array booleano

Uma outra funcionalidade muito interessante é que podemos filtrar nossos arrays de uma maneira bem simples 

No Python:
```
import numpy as np

lista = np.arange(10)

print(lista > 5)

print(lista[lista > 5])
```
ou 
```
import numpy as np
km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])
dados = np.array([km, anos])

print(dados[1][dados[1]>2000])
```


Atributos e métodos do Numpy


Atributos
Agora vamos pincelar alguns dos atributos mais importantes do Numpy, mas caso deseje, pode consultar todos nesse link

ndarray.shape
Retorna uma tupla com as dimeções do array.
No Python:
```
import numpy as np

km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])
dados = np.array([km, anos])

print(dados.shape)# 2 linhas e 5 colunas
```

ndarray.ndim
Retorna o número de dimensões do array
No Python:
```
import numpy as np

km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])
dados = np.array([km, anos])

print(dados.ndim)# 2 dimenções
```

ndarray.size
Retorna o número de elementos de um array
No Python:
```
import numpy as np

km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])
dados = np.array([km, anos])

print(dados.size)# 10 itens
```

ndarray.dtype
Retorna o tipo de dados dos elementos do array
No Python:
```
import numpy as np



km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])


dados = np.array([km, anos])



print(dados.dtype)#float64
```

ndarray.T
Retorna o array transposto, isto é, converte linhas em colunas e vice versa.
No Python:
```
import numpy as np

km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])

dados = np.array([km, anos])

print(dados.T)#
# [[44410.  5712. 37123.     0. 25757.]
#  [ 2003.  1991.  1990.  2019.  2006.]]
# [[44410.  2003.]
#  [ 5712.  1991.]
#  [37123.  1990.]
#  [    0.  2019.]
#  [25757.  2006.]]
```
ou:
```
import numpy as np

km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])

dados = np.array([km, anos])

print(dados.transpose())#
# [[44410.  5712. 37123.     0. 25757.]
#  [ 2003.  1991.  1990.  2019.  2006.]]
# [[44410.  2003.]
#  [ 5712.  1991.]
#  [37123.  1990.]
#  [    0.  2019.]
#  [25757.  2006.]]
```
Métodos
Agora vamos pincelar alguns dos atributos mais importantes do Numpy, mas caso deseje, pode consultar todos nesse link

ndarray.tolist()
Retorna o array como uma lista Python
No Python:
```
import numpy as np

km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])

dados = np.array([km, anos])

print(dados.tolist())#[[44410.0, 5712.0, 37123.0, 0.0, 25757.0], [2003.0, 1991.0, 1990.0, 2019.0, 2006.0]]
```

ndarray.reshape(shape[,order])
Retorna um array que contém os mesmos dados com uma nova forma.
No Python:
```
import numpy as np

lista = np.arange(10)

print(lista)
print(lista.reshape((5,2)))# retorna um array com os mesmos dados mas de uma forma diferente
```
ou:
```
import numpy as np

lista = np.arange(10)

print(lista)
print(lista.reshape((5,2), order='F'))# retorna um array com os mesmos dados mas de uma forma diferente
```

ndarray.resize(newshape[,refcheck])
Altera a forma e o tamanho do array.
No Python:
```
import numpy as np



km = np.array([44410., 5712., 37123., 0., 25757.])
anos = np.array([2003, 1991, 1990, 2019, 2006])



dados = np.array([km, anos])

dados_new = dados.copy()

dados_new.resize((3,5), refcheck = False)

print(dados_new)

dados_new[2] = dados_new[0]/dados_new[1]

print(dados_new)
```
