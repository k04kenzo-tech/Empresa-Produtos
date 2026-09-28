import os

class Produtos:

    #O correto é __init__, com dois "_" antes e depois.
    def _init_(self, nome, valor, quantidade):
        self.nomeproduto = nome
        self.valorproduto = valor
        self.quantidadeproduto = quantidade


class SistemaCadastroProduto:

    # ERRO: o correto é __init__, com dois "_" antes e depois.
    def _init_(self):

        # TROQUE AQUI:
        # O arquivo vai ser criado na mesma pasta do programa.
        self.arquivo = "produtos.txt"

    def cadastrarproduto(self):

        print("\n===== CADASTRAR PRODUTO =====\n")

        while True:

            while True:
        #Está entrando números no nome, arrume
                nomeproduto = input("Digite o nome do produto: ").strip()

                if nomeproduto == "":
                    print("\nNome inválido\n")
                else:
                    break

            while True:

                try:

                    #Troque "a valor" por "o valor".
                    valorproduto = float(input("\nDigite a valor do produto: "))

                    if valorproduto < 0:
                        print("\nValor inválido")
                    else:
                        break

                except ValueError:
                    print("\nDigite apenas números")

            while True:

                try:

                    quantidadeproduto = int(
                        input("\nDigite a quantidade de produtos: ")
                    )

                    if quantidadeproduto < 0:
                        print("\nQuantidade inválida")
                    else:
                        break

                except ValueError:
                    print("\nDigite apenas números")

            produto = Produtos(nomeproduto, valorproduto, quantidadeproduto)

            with open(self.arquivo, "a", encoding="utf-8") as arquivo:

                arquivo.write(
                    f"Produto: {produto.nomeproduto} | "
                    f"Valor: R$ {produto.valorproduto:.2f} | "
                    f"Estoque: {produto.quantidadeproduto} |\n"
                )

            print("\nProduto cadastrado com sucesso!\n")

            break


SCP = SistemaCadastroProduto()

SCP.cadastrarproduto()
