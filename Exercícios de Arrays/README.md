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

