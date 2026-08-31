# Atividade 1 - Criar um programa que crie uma lista de 10 numeros inteiros; solicite valores ao usuário; exiba todos os números; calcule a soma e a média;

#Lista para 10 elementos:
numeros = []
for i in range(10):
  numero = int(input(f"Digite 10 números inteiros {i + 1}º:  "))
  numeros.append(numero)
print("\nOs números informados foram: ")
for numero in numeros:
  print(numero)

# Calculando a soma:
soma = sum(numeros)

# Calculando a média:
media = soma / len(numeros)

# Resultado:
print(f"A soma dos números digitados é {soma}")
print(f"A média dos números digitados é {media:.2f}")

# Desafio: Além disso, encontre o menor valor, o maior valor e a quantidade de números pares.

# Maior e menor:
maior = max(numeros)
menor = min(numeros)

# Pares
pares = 0
for j in numeros:
  if j % 2 == 0:
    pares += 1

print("O maior número digitado foi:", maior)
print("O menor número digitado foi:", menor)
print("A quantidade de pares é:", pares)


# Atividade 2 - Crie uma matriz [3x3], solicite valores ao usuário e exiba a matriz; calcule a soma de todos os elementos; 
# calcule a soma da diagonal principal e encontre o maior elemento.

matriz = []

# Laço para linhas (i = linha)
for i in range(3):
  linha = []

# Laço para colunas (j = coluna)
  for j in range(3):
    valor = int(input(f"Digite o número para a posição [{i}][{j}] "))
    linha.append(valor)             # Adiciona os números digitados na linha
  matriz.append(linha)              # Adicona cada linha na matriz

  # 1 - Exibir a matriz
print("\nExibindo a matriz [3x3] original:")
for i in range(3):                  #laço de repetição para linhas
  for j in range(3):                #laço de repetição para colunas
    print(matriz[i][j], end= "  ")  #end com dois espaços dentro é para os números não ficarem colados e demonstrar realmente as linhas e colunas.
  print()

  # 2 - Para calcular a soma da matriz
soma = 0

for i in range(3):
    for j in range(3):
        soma += matriz[i][j]

  # 3 - Para calcular a soma da diagonal principal
soma_diagonal = 0
for i in range(3):
  soma_diagonal += matriz[i][i]

  # 4 - Para calcular o maior elemento
maior = matriz [0][0]
for i in range(3):
  for j in range(3):
    if matriz[i][j] > maior:
      maior = matriz[i][j]

# 5 - Apresentando o resultado 
print("\nA soma de todos os elementos da matriz é:", soma)
print("A soma da diagonal principal é:", soma_diagonal)
print("O maior elemento da matriz é:", maior)
