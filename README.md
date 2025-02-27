menu = """

[D] Depositar
[S] Sacar
[E] Extrato
[x] Sair

=> """

saldo = 0
limite = 500
extrato = ""
quantidade_saques = 0
LIMITE_SAQUE = 3

while True:
    opcao = input(menu).upper()

    if opcao == "D":
        valor = float(input("Valor do depósito: "))

        if valor > 0 and valor <= 500:
            saldo += valor
            extrato += f"+ R$ {valor:.2f}\n"
        
        else:
            print("Valor inválido!")

    elif opcao == "S":
        if quantidade_saques < LIMITE_SAQUE:
            valor = float(input("Valor do saque: "))

            if 0 < valor <= saldo + limite:
                saldo -= valor
                extrato += f"- R$ {valor:.2f}\n"
                quantidade_saques += 1
            
            else:
                print("Saldo insuficiente!")

        else:
            print("Limite de saques atingido!")

    elif opcao == "E":
        print(f"Saldo: R$ {saldo:.2f}")
        print("Extrato:")
        print(extrato) 

    elif opcao == "X":
        break

    else:
        print("Opção inválida!")
