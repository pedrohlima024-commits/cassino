# cassino
# just some tests of what i've learned on these days of python, nothing too elaborated but i think i'm getting better
# yall can translate it (:

import random

import time

import os

from colorama import Fore, Style, init


init()

# Listas
opcoes_roleta = ["Preto", "Vermelho", "Azul", "Amarelo"]
numbers = list(range(1, 10))

# Roleta
def RoletaPY(opcoes):
    print(f"Aposte em uma Cor: {Fore.BLACK}Preto{Style.RESET_ALL}, {Fore.RED}Vermelho{Style.RESET_ALL}, {Fore.BLUE}Azul{Style.RESET_ALL} ou {Fore.YELLOW}Amarelo{Style.RESET_ALL}")
    aposta = input("Sua Escolha: ").capitalize()
    valor_aposta = int(input("Valor da aposta: R$ "))
    for i in range(20):
        os.system("cls")
        print("Girando a Roleta...")
        Resultado = random.choice(opcoes)
        print("👉", Resultado)
        time.sleep(0.1 + i * 0.01)
    if aposta == Resultado:
        print("Você ganhou!")
        print(f"Sua aposta foi multiplicada por 5! {valor_aposta} x 5 = {valor_aposta * 5}")
    else:
        print("Você perdeu!")

# PPT
def PPT():
    opcoes = ["Pedra", "Papel", "Tesoura"]
    regras = {
        "Pedra": "Tesoura",
        "Tesoura": "Papel",
        "Papel": "Pedra"
    }

    while True:
        usuario = input("Pedra, Papel ou Tesoura? ").capitalize()
        print(f"Aposte em uma Cor: {Fore.BLACK}Preto{Style.RESET_ALL}, {Fore.RED}Vermelho{Style.RESET_ALL}, {Fore.BLUE}Azul{Style.RESET_ALL} ou {Fore.YELLOW}Amarelo{Style.RESET_ALL}")
        aposta = input("Sua aposta: ")
        if usuario not in opcoes:
            print("Opção inválida!\n")
            continue

        escolha = random.choice(opcoes)
        print(f"Minha escolha foi {escolha}")

        if usuario == escolha:
            print("Deu empate!\n")
        elif regras[usuario] == escolha:
            print("Você ganhou!\n")
            print(f"Sua aposta foi multiplicada por 5! {aposta} x 5 = {aposta * 5}")       
        else:
            print("Perdeu!\n")

        sair = input("Quer jogar de novo? (s/n): ").lower()
        if sair != "s":
            break

def AdivinhaPY(numbers):
    
    while True:
        computador = random.choice(numbers)
        print(Fore.RED + f"\nIntruções:" + Style.RESET_ALL + f"\nDigite um número de 1 a 10.\nSe adivinhar o número que a máquina escolheu,\nVocê {Fore.GREEN}ganha!{Style.RESET_ALL}")
        usuario2 = int(input(f"\nEscolha um número: "))
        aposta = float(input("Sua aposta: "))
        if usuario2 == computador:
            print(f"Você Ganhou!")
            print(f"Sua aposta foi multiplicada por 5! {aposta} x 5 = {aposta * 5}")
        else:
            print(f"Errou!")
        jogar_novamente = input("Quer jogar de novo? (s/n): ").lower()
        if jogar_novamente != "s":
            break

def main():
    # Introdução
    print(f"Bem vindo à loteria do {Fore.BLUE}Python{Style.RESET_ALL}!\n")
    time.sleep(2)

    # Menu
    print(Fore.RED + f"\nJogos:"+ Style.RESET_ALL)
    print("RoletaPY [1]")
    print("Pedra, Papel e Tesoura [2]")
    print("AdivinhaPY [3]\n")

    tipos = input(f"Digite o número da aposta que deseja: ")

    # Controle do menu
    if tipos == "1":
        print(f"\nVocê escolheu RoletaPY!\n")
        print(f"Carregando...\n")
        time.sleep(2)
        RoletaPY(opcoes_roleta)
    elif tipos == "2":
        print("Você escolheu Pedra, Papel e Tesoura!\n")
        print(f"Carregando...\n")
        time.sleep(2)
        PPT()
    elif tipos == "3":
        print("Você escolheu AdivinhaPY!\n")
        print(f"Carregando...\n")
        time.sleep(2)
        AdivinhaPY(numbers)
    else:
        print("Opção inválida!")

if __name__ == "__main__":
    main()



