 

# TPC6

## Autor
- Nome: Hiuany Drummond
- ID: A115794
- Foto: <img width="1536" height="1024" alt="938bca37-1e4f-42d0-b5d2-975408df7609" src="https://github.com/user-attachments/assets/04117539-1bf6-4d1d-9629-edc1061ee7fb" />
## Resumo
Criar um programa que aparece no output um menu com varias opções, e depois executa de acordo com a escolha do utilizador. 


```python

tabMeteo1 = [((2022, 1, 20), 2, 16, 0),
             ((2022, 1, 21), 1, 13, 0.2),
             ((2022, 1, 22), 7, 17, 0.01)]

menu = ["1-Mostrar tabela", "2 - Adicionar registo", "3 - Temperatura média de cada dia", "4 - Guardar tabela em ficheiro", "5 - Carregar tabela de ficheiro", 
        "6 - Temperatura mínima mais baixa", "7 - Amplitude térmica de cada dia", 
        " 8 - Dia com maior precipitação", "9 - Dias chuvosos", "10 - Maior período consecutivo sem chuva", "11 - Desenhar gráficos",
        "12 - Carregar tabela de exemplo (tabMeteo1)", " 0 - Sair"]

tabela = []
opcao = -1

while opcao != 0:
    print(menu)
    opcao = int(input("Opção: "))

    if opcao == 0:
        print("Adeus!")

    elif opcao == 1:
        if len(tabela) == 0:
            print("A tabela está vazia.")
        else:
            print("Data, TMin, TMax, Precip.")
            for (ano, mes, dia), tmin, tmax, p in tabela:
                print(f"{ano}-{mes:02d}-{dia:02d}   {tmin:>6}  {tmax:>6}  {p:>8}")

    elif opcao == 2:
        ano = int(input("Ano: "))
        mes = int(input("Mês: "))
        dia = int(input("Dia: "))
        tmin = float(input("Temperatura mínima: "))
        tmax = float(input("Temperatura máxima: "))
        prec = float(input("Precipitação: "))
        tabela.append(((ano, mes, dia), tmin, tmax, prec))
        print("Registo adicionado.")

    elif opcao == 3:
        res= []
        for (ano, mes, dia), tmin, tmax, p in tabela:
            media = (tmin + tmax) / 2
            res.append((data,media))
        return res
    print(medias(tabMeteo1))
    
    
    elif opcao == 4:
        fnome = input("Nome do ficheiro: ")
        file = open(fnome, "w")
        for (ano, mes, dia), tmin, tmax, p in tabela:
            file.write(f"{ano}-{mes}-{dia}|{tmin}|{tmax}|{p}\n")
        file.close()
        print("Tabela guardada em", fnome)

    elif opcao == 5:
        res=[]
        file = open(fnome, "r")
            for line in file:
                data, tmin, tmax, p = line.strip().split("|")
                ano, mes, dia = data.split("-"))
            file.close()
            print(len(tabela), "registos carregados.")
        else:
            print("Ficheiro não encontrado.")

    elif opcao == 6:
        if len(tabela) == 0:
            print("A tabela está vazia.")
        else:
            minima = tabela[0][1]
            for data, tmin, tmax, p in tabela:
                if tmin < minima:
                    minima = tmin
            print("Mínima mais baixa:", minima, "ºC")

    elif opcao == 7:
        for (ano, mes, dia), tmin, tmax, p in tabela:
            print(f"{ano}-{mes:02d}-{dia:02d}: {tmax - tmin:.1f} ºC")

    elif opcao == 8:
        if len(tabela) == 0:
            print("A tabela está vazia.")
        else:
            max_data = tabela[0][0]
            max_prec = tabela[0][3]
            for data, tmin, tmax, p in tabela:
                if p > max_prec:
                    max_data = data
                    max_prec = p
            ano, mes, dia = max_data
            print(f"Maior precipitação: {max_prec} no dia {ano}-{mes:02d}-{dia:02d}")

    elif opcao == 9:
        limite = float(input("Limite p: "))
        encontrou = False
        for (ano, mes, dia), tmin, tmax, p in tabela:
            if p > limite:
                print(f"{ano}-{mes:02d}-{dia:02d}: {p}")
                encontrou = True
        if not encontrou:
            print("Nenhum dia acima desse limite.")

    elif opcao == 10:
        limite = float(input("Limite p: "))
        maior = 0
        atual = 0
        for data, tmin, tmax, p in tabela:
            if p < limite:
                atual = atual + 1
                if atual > maior:
                    maior = atual
            else:
                atual = 0
        print("Maior período consecutivo:", maior, "dias")

    elif opcao == 11:
        if len(tabela) == 0:
            print("A tabela está vazia.")
        else:
            x = [f"{d[0]}-{d[1]:02d}-{d[2]:02d}" for d, *_ in tabela]
            y_min = [tmin for _, tmin, _, _ in tabela]
            y_max = [tmax for _, _, tmax, _ in tabela]
            y_prec = [p for _, _, _, p in tabela]

            fig, (ax1, ax2) = plt.subplots(2, 1, sharex=True, figsize=(9, 7))
            ax1.plot(x, y_min, marker="o", label="Temp. mínima")
            ax1.plot(x, y_max, marker="o", label="Temp. máxima")
            ax1.set_ylabel("Temperatura (ºC)")
            ax1.legend()
            ax1.grid(True)
            ax2.bar(x, y_prec)
            ax2.set_ylabel("Precipitação (mm)")
            ax2.set_xlabel("Data")
            ax2.grid(True)
            plt.setp(ax2.get_xticklabels(), rotation=45, ha="right")
            fig.tight_layout()
            plt.show()

    elif opcao == 12:
        tabela = list(tabMeteo1)
        print("Tabela de exemplo carregada.")

    else:
        print("Opção inválida.")

```
