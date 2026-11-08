# TPC8

## Autor
- Nome: Hiuany Drummond
- ID: A115794
- Foto: <img width="1536" height="1024" alt="938bca37-1e4f-42d0-b5d2-975408df7609" src="https://github.com/user-attachments/assets/04117539-1bf6-4d1d-9629-edc1061ee7fb" />
## Resumo: definir quatro funções sobre strings e números: contar quantas vezes uma substring aparece sem sobreposição, calcular o produto dos 3 menores inteiros de uma lista, reduzir um número a um só dígito somando repetidamente os seus dígitos, e encontrar o índice da primeira ocorrência de uma string dentro de outra.

```python


# a) Número de vezes que subs aparece em s, sem sobreposição
def strCount(s, subs):
    res = 0
    i = 0
    while i <= len(s) - len(subs):
        if s[i:i + len(subs)] == subs:
            res = res + 1
            i = i + len(subs)  # salta a substring encontrada (sem sobreposição)
        else:
            i = i + 1
    return res

print(strCount("catcowcat", "cat"))  # 2
print(strCount("catcowcat", "cow"))  # 1
print(strCount("catcowcat", "dog"))  # 0


# b) Menor produto possível multiplicando 3 inteiros da lista (os 3 menores)
def produtoM3(lista):
    menores = sorted(lista)[:3]
    return menores[0] * menores[1] * menores[2]

print(produtoM3([12, 3, 7, 10, 12, 8, 9]))  


# c) Soma repetida dos dígitos até restar apenas um dígito
def reduxInt(n):
    while n >= 10:
        soma = 0
        for d in str(n):
            soma = soma + int(d)
        n = soma
    return n

print(reduxInt(38))   
print(reduxInt(777))  


# d) Índice da primeira ocorrência de s2 em s1, ou -1
def myIndexOf(s1, s2):
    for i in range(len(s1) - len(s2) + 1):
        if s1[i:i + len(s2)] == s2:
            return i
    return -1

print(myIndexOf("Hoje está um belo dia de sol!", "belo"))   
print(myIndexOf("Hoje está um belo dia de sol!", "chuva"))  
```
