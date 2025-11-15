# Estrutura de Dados

## Big-O Notation
Fala sobre escalabilidade, e não necessariamente perfomance. Normalmente temos que considerar o caso mais pessimista quando for feito a análise.

### -> Complexidade Temporal
É sobre o tempo que uma função irá precisar para executar.

### -> Complexidade Espacial
É sobre a quantidade de valores serão armazenados na memória.

### -> Principais Big-O (lista do melhor para pior)
- 1 - O(1)

- 2 - O(Log N)
 -> Exemplo de algoritmo: "Binary Search"
 -> Toda vez que aumentamos o input exponencialmente o tempo de execução aumenta linearmente

- 3 - O(N)

- 4 - O(N Log N)
 -> Todos algoritmos de sorting (busca {"quicksort", "mergesort"}) são, com excesão do "Bubblesort"

- 5 - O(N²)
 -> For dentro de For, por exemplo
**Não são tanto utilizados:**

- 6 - O(2^N)

- 7 - O(raiz de N)

- 8 - O(N!)

## Array

O array é um espaço contínuo em memória que pode ser interpretado que contêm vários elementos.

Exemplo de como o array se comporta dentro da memória:

digamos que criei um array de 4 posições, sendo assim o array que criei irá procurar um espaço na memória onde ela consiga colocar seus valores um ao lado do outro.

Digamos que a memória atual está assim:

| Col 1 | Col 2 | Col 3 |Col 4 | Col 5 | Col 6 |
| :---: | :---: | :---: |:---: | :---: | :---: |
| - | x | - | x | - | - |
| - | x | - | x | x | - |
| - | - | - | - | x | x |
| x | x | x | x | - | - |

Então na criação ele vai popular o local que tem disponível 4 posições que ficaria assim
(a letra A representa nosso array)

| Col 1 | Col 2 | Col 3 |Col 4 | Col 5 | Col 6 |
| :---: | :---: | :---: |:---: | :---: | :---: |
| - | x | - | x | - | - |
| - | x | - | x | x | - |
| A | A | A | A | x | x |
| x | x | x | x | - | - |

E se o array mudar de tamanho e não tendo espaço para aumentar o seu tamanho no mesmo local onde ele está, então ele deve procurar outro local para ocupar de acordo com o novo tamanho atribuído, sendo assim algumas linguagens de programação não permite manipular o tamanho do array após o mesmo já ter sido criado.

## Linked List

É um objeto um pouco diferente do array por conta que os valores contidos dentro dele não está obrigatóriamente em um espaço um ao lado do outro.

A estrutura da Linked List consiste em cada índice ter um valor e a posição do próximo item, e tem o caso de os items que ligações tanto para frente quanto para trás ter os apontamentos para ambos os lados (índice anterior e próximo) e que no caso a estrutura se chamaria Doubly Linked List:

Essa estutura seria um exemplo de uma Singly Linked List, onde o índice [4] não apontaria para o seu anterior por exemplo:

[1] -> [2] -> [3] -> [4] -> [5]

Neste exemplo (apesar de não ter um desenho tão legal) há uma estrutura de Doubly Linked List onde o índice [4] por exemplo consegue apontar tanto para o anterio quando para o próximo.

[1] -> <- [2] -> <- [3] -> <- [4] -> [5]

## Queue

A Queue segue o conceito de fila ou FIFO (First In First Out), e sempre em sua estrutura armazena o primeiro índice e o último índice (HEAD e TAIL), então ele armazena esses índices para caso precise fazer uma adição de um novo elemento ele adicionaria ao final da "fila" e caso seja necessário uma remoção ele remove o primeiro índice. Lembrando que a Queue utiliza a estrutura do Singly Linked List e caso para a utilização da **Dequeue** seria necessário a utilização da Doubly Linked List, pois neste caso poderíamos adicionar ou remover uma posição em qualquer dois lados.

Exemplo com Python
```python
from queue import Queue
from collections import dequeue

q = Queue()

q.put(1)
q.put(2)
q.put(3)
q.put(4)
q.put(5)

print(q.get()) # 1
print(q.get()) # 2
print(q.get()) # 3
print(q.get()) # 4
print(q.get()) # 5
```

OBS: No final das contas a Queue em Python implementa a Dequeue.