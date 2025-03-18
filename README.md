# Menu de opções
print("""
Escolha uma das opções:
[d] Depositar
[s] Sacar
[e] Ver Extrato
[q] Sair
""")

# Variáveis iniciais
saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:
    opcao = input("Digite a opção desejada: ").lower()

    if opcao == "d":
        valor = float(input("Quanto você deseja depositar? R$ "))
        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"
            print(f"Depósito de R$ {valor:.2f} realizado!")
        else:
            print("Valor inválido!")

    elif opcao == "s":
        valor = float(input("Quanto você deseja sacar? R$ "))
        if valor > saldo:
            print("Você não tem saldo suficiente!")
        elif valor > limite:
            print(f"O valor do saque excede o limite de R$ {limite:.2f}.")
        elif numero_saques >= LIMITE_SAQUES:
            print(f"Você já fez o número máximo de saques ({LIMITE_SAQUES}) hoje!")
        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1
            print(f"Saque de R$ {valor:.2f} realizado!")
        else:
            print("Valor inválido!")

    elif opcao == "e":
        print("\n================ EXTRATO ================")
        if extrato == "":
            print("Nenhuma movimentação realizada.")
        else:
            print(extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao == "q":
        print("Saindo... Até logo!")
        break

    else:
        print("Opção inválida! Escolha novamente.")
