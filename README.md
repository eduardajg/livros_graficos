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
    # Solicita os dados do livro ao usuário
    titulo = input("Digite o título do livro: ")
    autor = input("Digite o autor: ")
    genero = input("Digite o gênero: ")
    quantidade = int(input("Digite a quantidade disponível: "))

    # Cria um objeto da classe Livro
    livro = Livro(titulo, autor, genero, quantidade)

    # Adiciona o livro à lista
    livros.append(livro)

    print("Livro cadastrado com sucesso!")


# Função responsável por listar todos os livros cadastrados
def listar_livros():
    # Verifica se a lista está vazia
    if len(livros) == 0:
        print("Nenhum livro cadastrado.")
        return

    print("--- LIVROS CADASTRADOS ---")

    # Percorre todos os livros da lista
    for livro in livros:
        print(f"Título: {livro.titulo}")
        print(f"Autor: {livro.autor}")
        print(f"Gênero: {livro.genero}")
        print(f"Quantidade disponível: {livro.quantidade}")
        print("--------------------------")


# Função responsável por buscar um livro pelo título
def buscar_livro():
    titulo_busca = input("Digite o título do livro que deseja buscar: ")

    # Variável utilizada para verificar se o livro foi encontrado
    encontrado = False

    # Percorre a lista procurando pelo título
    for livro in livros:
        if livro.titulo.lower() == titulo_busca.lower():
            print("--- LIVRO ENCONTRADO ---")
            print(f"Título: {livro.titulo}")
            print(f"Autor: {livro.autor}")
            print(f"Gênero: {livro.genero}")
            print(f"Quantidade disponível: {livro.quantidade}")

            encontrado = True
            break

    # Caso nenhum livro seja encontrado
    if not encontrado:
        print("Livro não encontrado.")


# Função responsável por gerar o gráfico
def gerar_grafico():
    # Dicionário que armazenará a quantidade de livros por gênero
    generos = {}

    # Percorre todos os livros cadastrados
    for livro in livros:

        # Se o gênero já estiver no dicionário,
        # soma a quantidade do novo livro
        if livro.genero in generos:
            generos[livro.genero] += livro.quantidade

        # Caso seja um gênero novo, cria uma nova entrada
        else:
            generos[livro.genero] = livro.quantidade

    # Verifica se existem livros cadastrados
    if len(generos) == 0:
        print("Nenhum livro cadastrado para gerar o gráfico.")
        return

    # Cria o gráfico de barras
    plt.bar(generos.keys(), generos.values())

    # Define o título e os nomes dos eixos
    plt.title("Quantidade de livros por gênero")
    plt.xlabel("Gênero")
    plt.ylabel("Quantidade de livros")

    # Exibe o gráfico
    plt.show()


# Menu principal do sistema
while True:
    print("===== BIBLIOTECA =====")
    print("1 - Cadastrar livro")
    print("2 - Listar livros")
    print("3 - Buscar livro")
    print("4 - Gerar gráfico")
    print("5 - Sair")

    # Solicita ao usuário uma opção
    opcao = input("Escolha uma opção: ")

    # Executa a função correspondente à opção escolhida
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

    # Caso o usuário digite uma opção inexistente
    else:
        print("Opção inválida.")
