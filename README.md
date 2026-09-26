# IMPORTA A BIBLIOTECA MATPLOTLIB PARA CRIAR O GRÁFICO
```python
import matplotlib.pyplot as plt
```

# CLASSE QUE REPRESENTA UM LIVRO
```python
class Livro:
    # MÉTODO CONSTRUTOR DA CLASSE
    def __init__(self, titulo, autor, genero, quantidade):
        self.titulo = titulo
        self.autor = autor
        self.genero = genero
        self.quantidade = quantidade
```

# LISTA QUE ARMAZENARÁ TODOS OS LIVROS CADASTRADOS
```python
livros = []
```

# FUNÇÃO RESPONSÁVEL POR CADASTRAR UM NOVO LIVRO
```python
def cadastrar_livro():
    titulo = input("Digite o título do livro: ")
    autor = input("Digite o autor: ")
    genero = input("Digite o gênero: ")
    quantidade = int(input("Digite a quantidade disponível: "))

    livro = Livro(titulo, autor, genero, quantidade)
    livros.append(livro)

    print("Livro cadastrado com sucesso!")
```

# FUNÇÃO RESPONSÁVEL POR LISTAR TODOS OS LIVROS CADASTRADOS
```python
def listar_livros():
    if len(livros) == 0:
        print("Nenhum livro cadastrado.")
        return

    print("--- LIVROS CADASTRADOS ---")

    for livro in livros:
        print(f"Título: {livro.titulo}")
        print(f"Autor: {livro.autor}")
        print(f"Gênero: {livro.genero}")
        print(f"Quantidade disponível: {livro.quantidade}")
        print("--------------------------")
```

# FUNÇÃO RESPONSÁVEL POR BUSCAR UM LIVRO PELO TÍTULO
```python
def buscar_livro():
    titulo_busca = input("Digite o título do livro que deseja buscar: ")

    encontrado = False

    for livro in livros:
        if livro.titulo.lower() == titulo_busca.lower():
            print("--- LIVRO ENCONTRADO ---")
            print(f"Título: {livro.titulo}")
            print(f"Autor: {livro.autor}")
            print(f"Gênero: {livro.genero}")
            print(f"Quantidade disponível: {livro.quantidade}")

            encontrado = True
            break
```
# CASO NENHUM LIVRO SEJA ENCONTRADO
   ```python
    if not encontrado:
        print("Livro não encontrado.")
```

# FUNÇÃO RESPONSÁVEL POR GERAR O GRÁFICO
```python
def gerar_grafico():
    generos = {}

    for livro in livros:
        if livro.genero in generos:
            generos[livro.genero] += livro.quantidade
        else:
            generos[livro.genero] = livro.quantidade

    if len(generos) == 0:
        print("Nenhum livro cadastrado para gerar o gráfico.")
        return

    plt.bar(generos.keys(), generos.values())

    plt.title("Quantidade de livros por gênero")
    plt.xlabel("Gênero")
    plt.ylabel("Quantidade de livros")

    plt.show()
```

# MENU PRINCIPAL DO SISTEMA
```python
while True:
    print("===== BIBLIOTECA =====")
    print("1 - Cadastrar livro")
    print("2 - Listar livros")
    print("3 - Buscar livro")
    print("4 - Gerar gráfico")
    print("5 - Sair")

    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        cadastrar_livro()

    elif opcao == "2":
        listar_livros()

    elif opcao == "3":
        buscar_livro()

    elif opcao == "4":
        gerar_grafico()

    elif opcao == "5":
        print("Sistema encerrado.")
        break

    # CASO O USUÁRIO DIGITE UMA OPÇÃO INEXISTENTE
    else:
        print("Opção inválida.")
```
