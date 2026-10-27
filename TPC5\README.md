# TPC5

## Autor
- Nome: Hiuany Drummond
- ID: A115794
- Foto: <img width="1536" height="1024" alt="938bca37-1e4f-42d0-b5d2-975408df7609" src="https://github.com/user-attachments/assets/04117539-1bf6-4d1d-9629-edc1061ee7fb" />
## Resumo
Criar um programa que aparece no output um menu com varias opções, e depois executa de acordo com a escolha do utilizador. 

```python
aluno = (nome, id, [notaTPC, notaProj, notaTeste])
turma = []

def mostrar_menu():
    menu = ["1: Criar uma turma", "2: Inserir um aluno na turma", "3: Listar a turma",
            "4: Consultar um aluno por id", "8: Guardar a turma em ficheiro",
            "9: Carregar uma turma dum ficheiro", "0: Sair da aplicação"]
    for linha in menu:
        print(linha)
numero = -1
while numero != 0:
    mostrar_menu()
    numero = int(input("Escolha uma das opções existentes: "))

    if numero == 1:
        turma = []
        print("Turma criada")
    elif numero == 2:
        nome = input("Nome: ")
        id = int(input("Id: "))
        notaTPC = int(input("notaTPC: "))
        notaProj = int(input("notaProj: "))
        notaTeste = int(input("notaTeste: "))
        aluno = (nome, id, [notaTPC, notaProj, notaTeste])
        turma.insert(0, aluno)
        print("Operação completa")
    elif numero == 3:
        for aluno in turma:
            print(aluno[0], aluno[1], aluno[2][0], aluno[2][1], aluno[2][2])
    elif numero == 4:
        id = int(input("id: "))
        encontrado = False
        for aluno in turma:
            if aluno[1] == id:
                print(aluno)
                encontrado = True
        if encontrado == False:
            print("O aluno nao existe")
    elif numero == 8:
        with open("turma.txt", "w") as f:
            f.write(str(turma))
        print("Turma guardada")
    elif numero == 9:
        with open("turma.txt", "r") as f:
            texto = f.read()
        turma = ast.literal_eval(texto)
        print("Turma carregada")
    elif numero == 0:
        print("Sair da aplicação")

```
