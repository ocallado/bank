
# PROJETO BANKPY ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)


Este projeto foi um desafio proposto pelo curso Python AI Backend Developer da DIO. 
A premissa do projeto seria montar um sistema bancário simples utilizando os conhecimentos adquiridos em:

|CONHECIMENTOS ADQUIRIDOS|
|------------------------|
|Tipos de Operadores com Python|
|Estruturas condicionais e de repetição|
|Manipulação de Strings|


## 
## O código

### Menu
``` 
menu = """
SEJA BEM VINDO AO BANKPY

Selecione a opção desejada abaixo:

[1] Depositar
[2] Sacar
[3] Extrato
[0] Sair

```

### Movimentação
```
=> """

saldo = 0
limite = 150000
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3
```
Nas Variáveis de movimentação inserimos as regras:

|REGRA|FUNÇÃO|
|------|-----|
|LIMITE_SAQUES = 3 | o usuário só poderá efetuar 3 saques por dia|
|numero_saques = 0 | quantos saques o usuário fez |
|limite = 150000 | o usuário pode sacar até 150.000 por dia |
|saldo = 0 | saldo do usuário |
|extrato ="" | Variável que irá apresentar a movimentação |


### Opções
Logo após inserimos a variável "opção" que é uma repetição da variável "menu"
```
while True:

    opcao = input(menu)
```

#### Depósito

Ao selecionar a opção [1] o usuário precisa inserir o valor de depósito

```
if opcao == "1":
        valor = float(input("Informe o valor do depósito: "))
```

Quando o Valor de depósito for maior que "0" o sistema irá somar esse valor com a variável "saldo" e também irá acrescentar essa movimentação da variável "extrato", apresentando "Deposito: R$ 00,00". A variável valor é do tipo flutuante e utilizamos o método {valor:.2f} para inserir apenas duas casas decimais.

Em caso do usuário inserir um valor de depósito menor que "0", apresentará a mensagem de erro: "Operação falhou! Valor informado é inválido."

```
if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Operação falhou! O valor informado é inválido.")
```

#### Saque

Agora acrescentamos um elif dentro de "opção" para quando o usuário selecionar a opção [2] Sacar.

```
elif opcao == "2":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES
```

Aqui inserimos um input do tipo flutuantes solicitando que o usuário digite o valor que deseja sacar.

```
valor = float(input("Informe o valor do saque: "))
```

Logo após, precisamos fazer as seguintes verificações:
- O usuário tem saldo suficiente?

```
excedeu_saldo = valor > saldo
```

- O usuário excedeu o valor de saque permitido?

```
excedeu_limite = valor > limite
```

- O usuário excedeu o número de saques permitidos?
```
excedeu_saques = numero_saques >= LIMITE_SAQUES
```

Ainda dentro desse elif colocamos as condições:

```
if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")

```

Caso exceda limite, saque ou saldo, a operação irá falhar!

E se o usuário inserir um valor maior que "0", o sistema irá subtrair do saldo o valor inserido, também vai inserir a transação na variável "extrato" (Saque: R$ -00,00).

```
elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ -{valor:.2f}\n"
            numero_saques += 1

```

No caso do usuário inserir um valor menor que "0" aparecerá a mensagem de erro.

```
else:
            print("Operação falhou! O valor informado é inválido.")
```

#### Extrato

Na opção [3] aparecerão todas as movimentações feitas além de inserir o saldo restante na conta!

```
 elif opcao == "3":
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")
```

#### Sair

Caso o usuário selecione a opção [0] o sistema executará a função "break" e vai encerrar a aplicação.

```
 elif opcao == "0":
        print("Obrigado por ser nosso cliente. VOLTE SEMPRE!")

        break
```

### Mensagem de erro

Se o usuário não inserir uma opção válida, o sistema exibirá a seguinte mensagem de erro:

```
else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")
```

## RESUMO

Este sistema foi desenvolvido pensando em simular um sistema bancário simples, onde temos operações de saque, depósitos e exibição da movimentação por meio do extrato. 
