```python
# Importa a biblioteca Matplotlib para criar o gráfico
import matplotlib.pyplot as plt


# Classe que representa um livro
class Livro:
    # Método construtor da classe
    def __init__(self, titulo, autor, genero, quantidade):
        self.titulo = titulo
        self.autor = autor
        self.genero = genero
        self.quantidade = quantidade


# Lista que armazenará todos os livros cadastrados
livros = []


# Função responsável por cadastrar um novo livro
def cadastrar_livro():
    titulo = input("Digite o título do livro: ")
    autor = input("Digite o autor: ")
    genero = input("Digite o gênero: ")
    quantidade = int(input("Digite a quantidade disponível: "))

    livro = Livro(titulo, autor, genero, quantidade)
    livros.append(livro)

    print("Livro cadastrado com sucesso!")


# Função responsável por listar todos os livros cadastrados
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


# Função responsável por buscar um livro pelo título
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

    if not encontrado:
        print("Livro não encontrado.")


# Função responsável por gerar o gráfico
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


# Menu principal do sistema
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

    else:
        print("Opção inválida.")
```
