# -------------------------------------------------------------------------------------------------------------------------------------- #
# Na implementação do sistema de trigem anterior eu observei um erro que não poderia ser resolvido usando uma única fila em que se       #
# manipulasse as duas pontas (começo e final da fila). O problema é que os pacientes prioritários sempre seriam inseridos no começo      #
# da fila, na frente de outros pacientes prioritários anteriormente cadastrados, uma vez que eu só posso manipular o inicio, sendo       # 
# impossível inserir um paciente no meio da fila.                                                                                        #
# Para resolver esse problema, eu implementei uma outra lógica, utilizando duas filas. Uma para pacientes normais, outra para prioridade.#
# Dessa forma, os pacientes prioritários são atendidos na frente dos pacientes normais, repeitando a ordem em que foram cadastrados.     #
# Nesse sistema, os pacientes normais só serão atendidos depois que a lista de paciente prioritários estiver vazia.                      #
# -------------------------------------------------------------------------------------------------------------------------------------- #

from collections import deque

class TriagemHospitalar:
    def __init__(self):
        # Filas separadas para preservar a ordem de chegada (FIFO) de cada grupo
        self.fila_prioritaria = deque()
        self.fila_padrao = deque()

    def adicionar_paciente(self, nome, prioritario=False):
        if prioritario:
            self.fila_prioritaria.append(nome)
            print(f"-> Paciente prioritário '{nome}' adicionado com sucesso.")
        else:
            self.fila_padrao.append(nome)
            print(f"-> Paciente '{nome}' (fluxo padrão) adicionado com sucesso.")

    def chamar_proximo_paciente(self):
        # Regra de negócio: atende prioritários primeiro
        if self.fila_prioritaria:
            proximo = self.fila_prioritaria.popleft()
            print(f"-> CHAMANDO PARA ATENDIMENTO: [PRIORITÁRIO] {proximo}")
            return proximo
        elif self.fila_padrao:
            proximo = self.fila_padrao.popleft()
            print(f"-> CHAMANDO PARA ATENDIMENTO: [PADRÃO] {proximo}")
            return proximo
        else:
            print("-> Nenhum paciente aguardando nas filas.")
            return None

    def exibir_filas(self):
        print("\n--- ESTADO ATUAL DAS FILAS ---")
        
        # Exibindo a Fila Prioritária
        print(f" Prioritários ({len(self.fila_prioritaria)}):", end=" ")
        if self.fila_prioritaria:
            print(" -> ".join(self.fila_prioritaria))
        else:
            print("[Vazia]")

        # Exibindo a Fila Padrão
        print(f" Padrão       ({len(self.fila_padrao)}):", end=" ")
        if self.fila_padrao:
            print(" -> ".join(self.fila_padrao))
        else:
            print("[Vazia]")
        print("-" * 30 + "\n")


# -- Menu para cadastrar pacientes --
hospital = TriagemHospitalar()

while True:
    print("--- GERENCIAMENTO DE TRIAGEM HOSPITALAR ---")
    print("1 - Cadastrar novo paciente")
    print("2 - Chamar próximo paciente")
    print("3 - Sair")
    
    opcao = input("Escolha a opção desejada: ")

    if opcao == "1":
        nome = input("Nome do paciente: ")
        if not nome:
            print("O nome do paciente não pode ser vazio!\n")
            continue

        print("\nClassificação do Paciente:")
        print(" [S] Sim - Prioritário")
        print(" [N] Não - Padrão")
        prioridade_resp = input("O paciente é prioritário? (S/N): ")
        
        prioridade = (prioridade_resp == "S")
        hospital.adicionar_paciente(nome, prioritario=prioridade)
        hospital.exibir_filas()

    elif opcao == "2":
        hospital.chamar_proximo_paciente()
        hospital.exibir_filas()

    elif opcao == "3":
        print("Programa encerrado com sucesso")
        break

    else:
        print("Opção inválida! Tente novamente.\n")
