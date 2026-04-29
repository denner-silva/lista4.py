import random
from util import inputint, inputfloat
'''
Lista de Exercícios referentes a coleções e arquivos em python
'''

#1. Faça um programa que armazene 15 números inteiros em uma lista e depois
#permita que o usuário digite um número inteiro para ser buscado na lista, se
#for encontrado o programa deve imprimir a posição desse número na lista, caso
#contrário, deve imprimir a mensagem: "Nao encontrado!".

def q1() -> None:
    numeros: list = [random.randrange(200) for _ in range(15)]
    #forma extensa da linha anterior:
    #for _ in range(15):
    #    numeros.append(random.randrange(200))
    print(numeros)
    numero: int = inputint('Digite o número a ser localizado na lista: ')
    try:
        posicao: int = numeros.index(numero)
    except ValueError:
        print('Número não encontrado!')
    else:
        print(f'Número localizado na posição: {posicao}')

#2. Faça um programa que armazene 10 letras em uma lista e imprima uma listagem
#numerada. (ASCII 65-90)

def q2() -> None:
    letras: list = [chr(random.randrange(65,91)) for _ in range(10)]
    # tipo enumerate cria automaticamente um contador para os elementos da lista começando em 0
    for posicao, letra in enumerate(letras):
        print(f'[{posicao}]: {letra}')


#2.1 Faça um programa que peça ao usuário para informar a qtde de caracteres
# para a geração de uma senha aleatória. Ao final o programa deve exibir a
# senha sugerida. (ASCII 40-126)

def q2.1 -> None:
    tamanho_senha: str = inputint('informe a qtde de caracteres para senha (4-32): ', min=4, max=32)
    
#3. Construa uma programa que armazene 15 números em uma lista e imprima
#uma listagem numerada contendo o número e uma das mensagens: par ou ímpar.
def q3() -> None
numeros? list = [random.randrange(200) for _ in range(15)]
for posição, numero in enumerate(numeros):
    print(f'[{str (posição):<2}]: {str(numero):>3} ({"par" if numero%2==0 else "IMPAR"})')


#4. Faça um programa que armazene 8 números em uma lista e imprima todos os
#números. Ao final, imprima o total de números múltiplos de seis.

def q4() -> None:
    numeros: list = [random.randrange(100) for _ in range(8)]
    multiplos_seis = 0
    for posicao, numero in enumerate(numeros):
        if numero % 6 == 0: multiplos_seis += 1
        print(f'[{str(posicao):<2}]: {str(numero):>3}')
    print(f'\nTotal de múltiplos de seis: {multiplos_seis}')


#5. Faça um programa que armazene as notas das provas 1 e 2 de 15 alunos. Calcule
#e armazene a média arredondada. Armazene também a situação do aluno: 1-
#Aprovado ou 2-Reprovado. Ao final o programa deve imprimir uma listagem
#contendo as notas, a média e a situação de cada aluno em formato tabulado.
#Utilize quantas listas forem necessárias para armazenar os dados.

def q5() -> None:
    notas1: list = [random.randint(0, 10) for _ in range(15)]
    notas2: list = [random.randint(0, 10) for _ in range(15)]
    medias: list = [round((n1 + n2) / 2) for n1, n2 in zip(notas1, notas2)]
    situacao: list = ["Aprovado" if m >= 6 else "Reprovado" for m in medias]
    print(f'{"ID":<4} {"N1":<4} {"N2":<4} {"MÉDIA":<6} {"SITUAÇÃO"}')
    for i, (n1, n2, m, s) in enumerate(zip(notas1, notas2, medias, situacao)):
       print(f'[{i:<2}]: {n1:<4} {n2:<4} {m:<6} {s}')

#6. Construa um programa que permita armazenar o salário de 20 pessoas. Calcular
#e armazenar o novo salário sabendo-se que o reajuste foi de 8%. Imprimir uma
#listagem numerada com o salário e o novo salário. Declare quantas listas forem
#necessárias.

def q6() -> None:
    salarios: list = [round(random.uniform(1500, 5000), 2) for _ in range(20)]
    novos_salarios: list = [round(s * 1.08, 2) for s in salarios]
    for i, (velho, novo) in enumerate(zip(salarios, novos_salarios)):
        print(f'[{i+1:<2}]: Antigo: R$ {velho:>8.2f} | Novo: R$ {novo:>8.2f}')

#7. Crie um programa que leia o preço de compra e o preço de venda de 100 mercadorias
#(utilize listas). Ao final, o programa deverá imprimir quantas mercadorias
#proporcionam:
#• lucro < 10%
#• 10% <= lucro <= 20%
#• lucro > 20%

def q7() -> None:
    compra: list = [random.randint(10, 100) for _ in range(100)]
    venda: list = [round(c * random.uniform(1.05, 1.30), 2) for c in compra]
    l1, l2, l3 = 0, 0, 0
    for c, v in zip(compra, venda):
        lucro = (v - c) / c
        if lucro < 0.10: l1 += 1
        elif lucro <= 0.20: l2 += 1
        else: l3 += 1
    print(f'Lucro < 10%: {l1}\n10% <= Lucro <= 20%: {l2}\nLucro > 20%: {l3}')

#8. Construa um programa que armazene o código, a quantidade, o valor de compra
#e o valor de venda de 30 produtos. A listagem pode ser de todos os produtos ou
#somente de um ao se digitar o código. Utilize dicionário como estrutura de dados.

def q8() -> None:
    produtos = {i: {"qtd": random.randint(1, 50), "compra": 10.0, "venda": 15.0} for i in range(1, 31)}
    # Exemplo de listagem de todos
    for cod, dados in produtos.items():
        print(f'Cód: {cod:<2} | Qtd: {dados["qtd"]:<3} | Venda: R${dados["venda"]}')
        
#9. Faça um programa que leia dois conjuntos de números inteiros, tendo
#cada um 10 elementos. Ao final o programa deve listar os elementos comuns aos
#conjuntos.

def q9() -> None:
    conj1 = [random.randint(1, 20) for _ in range(10)]
    conj2 = [random.randint(1, 20) for _ in range(10)]
    comuns = list(set(conj1) & set(conj2))
    print(f'Conj 1: {conj1}\nConj 2: {conj2}\nComuns: {comuns}')
    
#10. Faça um programa que leia uma lista com 10 elementos e obtenha outra lista resultado
#cujos valores são os fatoriais da lista original.
#Imprimir o maior e o menor, sem ordenar, o percentual de números pares e a
#média dos elementos da lista.

def q10() -> None:
    # Cria lista original e a lista de fatoriais
    lista: list = [random.randint(1, 10) for _ in range(10)]
    fatoriais: list = [math.factorial(n) for n in lista]
    for i, (orig, fat) in enumerate(zip(lista, fatoriais)):
        print(f'[{i:<2}]: Número: {orig:>2} | Fatorial: {fat}')

#11. Imprimir o maior e o menor, sem ordenar, o percentual de números pares e a
#média dos elementos da lista.

def q11() -> None:
    numeros: list = [random.randint(1, 100) for _ in range(20)]
    maior = max(numeros)
    menor = min(numeros)
    media = sum(numeros) / len(numeros)
    pares = len([n for n in numeros if n % 2 == 0])
    perc_pares = (pares / len(numeros)) * 100
    for i, n in enumerate(numeros):
        print(f'[{i:<2}]: {n:>3}')
    print(f'\nMaior: {maior} | Menor: {menor}')
    print(f'Média: {media:.2f} | % Pares: {perc_pares}%')

#12. Crie um programa para gerenciar um sistema de reservas de mesas em uma casa
#de espetáculo. A casa possui 30 mesas de 5 lugares cada. O programa deverá
#permitir que o usuário escolha o código de uma mesa (1 a 30) e forneça a
#quantidade de lugares desejados. O programa deverá informar se foi possível
#realizar a reserva e atualizar a reserva. Se não for possível, o programa deverá
#emitir uma mensagem. O programa deve terminar quando o usuário digitar
#o código 0 (zero) para uma mesa ou quando todos os 150 lugares estiverem
#ocupados.

def q12() -> None:
    mesas = [5] * 30  # 30 mesas com 5 lugares cada
    total_lugares = 150
    while total_lugares > 0:
        cod = int(input("Código da mesa (1-30) ou 0 para sair: "))
        if cod == 0: break
        lugares_desejados = int(input(f"Quantos lugares deseja na mesa {cod}? "))
        if cod < 1 or cod > 30:
            print("Mesa inválida!")
        elif mesas[cod-1] >= lugares_desejados:
            mesas[cod-1] -= lugares_desejados
            total_lugares -= lugares_desejados
            print(f"Reserva confirmada! Restam {mesas[cod-1]} lugares nesta mesa.")
        else:
            print(f"Não foi possível. Esta mesa só tem {mesas[cod-1]} lugares.")
    print("Sistema encerrado ou lotação esgotada.")

#13. Construa um programa que realize as reservas de passagens áreas de uma companhia.
#O programa deve permitir cadastrar o número de 10 voos e definir a
#quantidade de lugares disponíveis para cada um. Após o cadastro, leia vários
#pedidos de reserva, constituídos do número da carteira de identidade do cliente e
#do número do voo desejado. Para cada cliente, verificar se há possibilidade no
#voo desejado. Em caso afirmativo, imprimir o número da identidade do cliente e
#o número do voo, atualizando o número de lugares disponíveis. Caso contrário,
#avisar ao cliente a inexistência de lugares. A leitura do número 0 (zero) para o voo
#desejado indica o término da leitura de reservas.

def q13() -> None:
    # Cadastro de 10 voos
    voos = {random.randint(100, 999): random.randint(1, 50) for _ in range(10)}
    print(f"Voos disponíveis (Voo: Vagas): {voos}")
    while True:
        num_voo = int(input("\nNúmero do voo desejado (ou 0 para encerrar): "))
        if num_voo == 0: break
        identidade = input("Número da identidade do cliente: ")
        if num_voo in voos:
            if voos[num_voo] > 0:
                voos[num_voo] -= 1
                print(f"Reserva confirmada! ID: {identidade} | Voo: {num_voo}")
            else:
                print("Inexistência de lugares neste voo.")
        else:
            print("Voo não encontrado.")

#14. Faça um programa que armazene 50 números inteiros em uma lista. O programa
#deve gerar e imprimir uma segunda lista em que cada elemento é o quadrado do
#elemento da primeira lista.

def q14() -> None:
    lista1 = [random.randint(1, 20) for _ in range(50)]
    lista2 = [n**2 for n in lista1]
    for i, (n, q) in enumerate(zip(lista1, lista2)):
        print(f'[{i:<2}]: {n:>3}² = {q:>4}')

#15. Faça um programa que leia e armazene vários números, até digitar o número
#0. Imprimir quantos números iguais ao último número foram lidos. O limite de
#números é 100.

def q15() -> None:
    numeros = []
    while len(numeros) < 100:
        n = int(input("Digite um número (0 para sair): "))
        if n == 0: break
        numeros.append(n)
    if numeros:
        ultimo = numeros[-1]
        iguais_ao_ultimo = numeros.count(ultimo)
        print(f"O último número lido foi {ultimo}.")
        print(f"Ele apareceu {iguais_ao_ultimo} vezes na lista.")

#16. Crie um programa para ler um conjunto de 100 números reais e informe:
#• quantos números lidos são iguais a 30
#• quantos são maior que a média
#• quantos são iguais a média

def q16() -> None:
    # Gera 100 números reais (decimais) entre 10 e 50
    numeros: list = [round(random.uniform(10, 50), 2) for _ in range(100)]
    media = sum(numeros) / len(numeros)
    iguais_30 = numeros.count(30.0)
    maior_media = len([n for n in numeros if n > media])
    igual_media = len([n for n in numeros if n == media])
    print(f'Média dos números: {media:.2f}')
    print(f'Quantidade igual a 30: {iguais_30}')
    print(f'Quantidade maior que a média: {maior_media}')
    print(f'Quantidade igual à média: {igual_media}')

#17. Faça um programa que leia um conjunto de 30 valores inteiros, armazene-os em
#uma lista e os imprima ao contrário da ordem de leitura.

def q17() -> None:
    valores = [random.randint(1, 100) for _ in range(30)]
    print(f'Original: {valores}')
    print(f'Invertida: {valores[::-1]}')

#18. Faça um programa que permita entrar com 20 valores numéricos,
# em que podem existir vários elementos repetidos. Gere
#uma lista ordenada que terá apenas os elementos não repetidos.

def q18() -> None:
    valores = [random.randint(1, 15) for _ in range(20)]
    unica_ordenada = sorted(list(set(valores)))
    print(f'Original: {valores}')
    print(f'Únicos e Ordenados: {unica_ordenada}')

#19. Suponha uma estrutura de 30 elementos contendo: código e telefone. Faça
#um programa que permita buscar pelo código e imprimir o telefone.

def q19() -> None:
    # Cria uma estrutura com 30 elementos (Código: Telefone)
    # Simulando telefones aleatórios para preencher a lista
    agenda = {i + 100: f'9{random.randint(8000, 9999)}-{random.randint(1000, 9999)}' for i in range(30)}
    print("--- BUSCA DE TELEFONE ---")
    busca_cod = int(input("Digite o código para buscar (100 a 129): "))
    if busca_cod in agenda:
        print(f'Código: {busca_cod} | Telefone: {agenda[busca_cod]}')
    else:
        print("Código não encontrado na base de dados.")

#20. Faça um programa que leia a matrícula e a média de 100 alunos. Ordene da maior
#para a menor nota e imprima uma relação contendo todas as matrículas e médias.

def q20() -> None:
    alunos = [{"mat": i+100, "nota": round(random.uniform(0, 10), 1)} for i in range(100)]
    alunos_ordenados = sorted(alunos, key=lambda x: x['nota'], reverse=True)
    print(f'{"MATRÍCULA":<12} {"MÉDIA":<5}')
    for aluno in alunos_ordenados:
        print(f'{aluno["mat"]:<12} {aluno["nota"]:<5}')

questao = int(input('Questão a ser executada: '))
eval(f'q{questao}()')
