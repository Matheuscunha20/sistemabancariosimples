﻿# sistemabancariosimples
class Banco:
    def __init__(self):
        self.saldo = 0.0
        self.transacoes = []

    def depositar(self, valor):
        if valor > 0:
            self.saldo += valor
            self.transacoes.append(f"Depósito: R${valor:.2f}")
            print(f"Depósito de R${valor:.2f} realizado com sucesso.")
        else:
            print("Valor inválido para depósito. Insira um valor positivo.")

    def sacar(self, valor):
        if valor > self.saldo:
            print("Saldo insuficiente para realizar o saque.")
        elif valor > 500:
            print("O valor máximo para saque é R$500.")
        elif valor > 0:
            self.saldo -= valor
            self.transacoes.append(f"Saque: R${valor:.2f}")
            print(f"Saque de R${valor:.2f} realizado com sucesso.")
        else:
            print("Valor inválido para saque. Insira um valor positivo.")

    def extrato(self):
        print("\n--- Extrato ---")
        if not self.transacoes:
            print("Nenhuma transação realizada.")
        else:
            for transacao in self.transacoes:
                print(transacao)
        print(f"Saldo atual: R${self.saldo:.2f}")
        print("----------------\n")

# Exemplo de uso
banco = Banco()

# Realizando operações
banco.depositar(1500.45)
banco.sacar(200)
banco.sacar(600)
banco.extrato()
