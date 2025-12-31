# Exercícios de Arrays

## Two Pointer

É uma técnica para resolução de algoritmos que são usados em cima de arrays ou strings, então essa solução consiste em conter dois ponteiros um inicializando no início e outro no final, sendo assim fica com uma melhor performance por conta que não precisa alocar um espaço na memória para armazenar algum valor, por conta que utilizando os ponteiros podemos saber exatamente o ponto que estamos dentro do array.

Desafio: Dada uma string 's' deve ser invertido a ordem das letras.
Exemplo: 
 -> Entrada: "Let's take LeetCode contest"
 -> Saída  : "s'teL ekat edoCteeL tsetnoc"

Solução em Python:

```python
class Solution:
  def reverseWords_manual(s):
    res = ""
    l, r = 0, 0

    while r <= len(s):
      if s[r] != ' ':
        r += 1
      else:
        res += s[l:r+1][::-1]

        r += 1
        l = r

    res += ' '
    res += s[l:r+2][::-1]

    return res[1:]
```

## Binary Search

Para a binary search funcionar ela precisa primeiramente dos itens ordenados e a complexidade computacional é O(Log n) e espacial O(1) por conta que não vai ser preciso adicionar mais espaço na memória, ela funciona o ponteiro apontando para o indice do meio do array, sendo assim digamos que estamos procurando o valor 4, e temos um array ordenado do 1 ao 10, sendo assim o indice do meio é o 5 (podendo ser o 4 sem problema, dependendo da implementação) então ele começa e pergunta se o 5 é maior que o 4, e realmente é, então ele "ignora" os indices depois do 5 então fica o 5 posições e o ponteiro vai para o meio novamente que no caso é o 3, então verifica se o 3 é meio que o 4 e então é menor, então "ignora" os anteriores então sobra o 4, achando o resultado, por isso que a complexidade computacional é de O(Log n), por conta que mesmo que o array dobrar o seu tamanho a complexidade será linear, digamos que começamos com um array de 10 posições então ficaria:

- Log2(10) = 2,321
- Log2(20) = 3,321
- Log2(40) = 4,321

```python
def binary_search(nums, n):
    lo, hi, steps = 0, len(nums), 0
  
    while lo <= hi:
      steps += 1
      mid = int((lo+hi)/2)

      if nums[mid] == n:
          print(f"***** steps: {steps}")
          return mid
      elif nums[mid] < n: 
          lo = mid + 1
      else:
          hi = mid

    return -1

a = [x for x in range(1, 6)]
b = [x for x in range(1, 11)]
c = [x for x in range(1, 21)]
d = [x for x in range(1, 41)]

binary_search(a, 4)
binary_search(b, 4)
binary_search(c, 4)
binary_search(d, 4)
```

## Sliding Window

Esse problema é bem comum que se diz respeito a solução do problema ser um sub-array, tamanho de um sub-array, sub-string ou tamanho de uma sub-string que preenche certa condição. Por exemplo, encontrar um maior sub-sting que as letras não se repetem em pelo menos duas vezes.

```python
def max_sub_string_that_repeat_max_twice(s):
  l, r = 0, 0
  _max = 1
  counter = {}

  counter[s[0]] = 1

  while r < len(s) - 1:
    r += 1

    if counter.get(s[r]):
      counter[s[r]] += 1
    else:
      counter[s[r]] = 1

    while counter[s[r]] == 3:
      counter[s[l]] -= 1
      l += 1

    _max = max(_max, r - l + 1)

  return _max

a = 'bcbbbcbad'

print(max_sub_string_that_repeat_max_twice(a))
```

## Exponential Search

Em resumo o Exponential Search nada mais é que a implementação de uma Binary Search, porém ele é recomendado para quando o array tem várias posições, e que precise ter um filtro para melhorar a implementação do Binary Search, então ele fica meio que responsável por melhorar o array para então iniciar o algoritmo de Binary Search, então como o próprio nome já diz ele vai aumentando exponencialmente um ponteiro até identificar que o valor que está no ponteiro é maior que o valor buscado, por exemplo, digamos que temos o seguinte caso:

Caso: temos um array ordenado do 1 até o 200 mil, e queremos encontrar o número 289, sendo assim com o Exponential Search ele pode iniciar na posição 0 do array e verifica se o valor que está lá é maior que o valor buscado, se não for ele pega a posição do ponteiro e realiza a exponenciação dele multiplicando por 2 então ele vai fazendo isso até buscar o número maior e quando encontrado encontraria ali um sub-array onde não precisaria percorrer os 200 mil registros.

Exemplo: Array de 1 ... 200 mil

0 * 2 = 2 e não é maior que 289
2 * 2 = 4 e não é maior que 289
4 * 2 = 8 e não é maior que 289
8 * 2 = 16 e não é maior que 289
16 * 2 = 32 e não é maior que 289
32 * 2 = 64 e não é maior que 289
64 * 2 = 128 e não é maior que 289
128 * 2 = 256 e não é maior que 289
256 * 2 = 512 e é maior que 289

então em fez que a Binary Search buscar o valor 289 em um array de 1 à 289 ele busca somente do 256 à 512 e assim ele pode melhorar a busca.

Só que para utilizar o Exponential Search com o Binary Search será necessário fazer uma simples mudança na lógica criada na seção de Binary Search.

```python
def binary_search_for_exponential_search(nums, n, lo, hi):
    steps = 0

    while lo <= hi:
      steps += 1
      mid = int((lo+hi)/2)

      if nums[mid] == n:
        print(f"***** steps: {steps}")
        return mid
      elif nums[mid] < n: 
        lo = mid + 1
      else:
        hi = mid

    return -1

def exponential_search(arr, target):
  if arr[0] == target:
    return 0

  n = len(arr)
  i = 1

  while i < n and arr[i] < target:
    i *= 2

  if arr[i] == target:
    return i

  return binary_search_for_exponential_search(arr, target, i//2, min(i, n-1))

arr = [x for x in range(1, 41)]
target = 32
result = exponential_search(arr, target)

print(f'Element found at index {result}')
```