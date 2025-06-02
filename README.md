# desafio-em-python
Projeto de simulação bancária em Python, fiz com a orientação do professor do curso!



menu = """

[1] Despositar
[2] Sacar
[3] Extrato
[4] Sair

=> """

saldo= 0
limite= 500
extrato= ""
limite_saques = 3

while True:

    opcao = input(menu)


    if opcao == "1":
        valor  = float(input("informe o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("operação falhou! O valor informado é inválido.")

    elif opcao == "2":
        valor = float(input("informe o valor do saque: "))

        excedeu_saldo = valor > saldo
        excedeu_limite = valor > limite
        excedeu_saques = limite_saques

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:
            print("operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número maximo de saques excedido.")

        elif valor > 0:
            saldo -= valor 
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

        else:
            print("operaçao falhou! O valor informado é invalido.")

    elif opcao == "3":
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("===========================================")

    elif opcao == "4":
        break

    else:
        print("Operação invalida, por favor selecione novamente a operação desejada.")

