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