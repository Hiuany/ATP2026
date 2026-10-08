# TPC3 

## Autor
- Nome: Hiuany Drummond
- ID: A115794
- Foto: <img width="1536" height="1024" alt="938bca37-1e4f-42d0-b5d2-975408df7609" src="https://github.com/user-attachments/assets/04117539-1bf6-4d1d-9629-edc1061ee7fb" />

## Resumo
Criar um jogo entre o computador e o jogaor. Cada um joga um número, quem no fim tiver o número final em que a soma for 100, ganha o jogo. Precisamos de 2 modalidade, uma em que o computador começa, e outra em que o oponente começa. 


```python
chaves = [1,12,23,34,45,56,67,78,89,100]
import random 
def computador_comeca():
    total=1
        print("O computador jogou 1")
        while total<100:
            oponente=int(input("Escreva um número de 1 a 10:"))
            total=total+oponente
            resposta=11-oponente
            total=total+resposta
            print("O computador jogou", resposta)
            print("Total:", total)
    if total==100:
        print("O computador ganhou")


def oponente_comeca():
    total = 0
    while total < 100:
        oponente= int(input("Escreva um número de 1 a 10: "))
        total = total + oponente
        if total == 100:
            print("Ganhaste!")
        else:
            if total in chaves:
                computador = random.randint(1,10)
                total=total+computador
                print(f"O computador jogou {computador} e Total={total}")
            elif total not in chaves: 
               computador= 11-oponente
               total=total+computador
                print(f"O computador jogou {computador} e Total={total}")
             if total=100
                print("O computador ganhou!")

#Menu

print("1- O computador começa")
print("2- O oponente começa")
menu=input("Escolha uma modalidade:")
if menu=="1":
    computador_comeca()
 else:
    oponente_comeca()
```
