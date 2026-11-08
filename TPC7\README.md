# TPC7

## Autor
- Nome: Hiuany Drummond
- ID: A115794
- Foto: <img width="1536" height="1024" alt="938bca37-1e4f-42d0-b5d2-975408df7609" src="https://github.com/user-attachments/assets/04117539-1bf6-4d1d-9629-edc1061ee7fb" />
## Resumo
Criar três listas em compreensão: uma com os elementos não comuns a duas listas, outra com as palavras de um texto com mais de 3 letras, e outra com pares (índice, valor) de uma lista dada.
```python

# a) Lista formada pelos elementos que não são comuns às duas listas
lista1 = [1, 2, 3, 4, 5]
lista2 = [4, 5, 6, 7, 8]
ncomuns = [x for x in lista1 if x not in lista2] + [x for x in lista2 if x not in lista1]
print(ncomuns)  # [1, 2, 3, 6, 7, 8]

# b) Lista formada pelas palavras do texto compostas por mais de 3 letras

lista = [palavra for palavra in texto.split() if len(palavra) > 3]
print(lista)

# c) Lista formada por pares (índice, valor) com os valores da lista dada
lista = ['anaconda', 'burro', 'cavalo', 'macaco']
listaRes = [(i + 1, lista[i]) for i in range(len(lista))]
print(listaRes) 

```
