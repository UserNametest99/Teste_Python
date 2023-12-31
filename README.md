import random
import tkinter as tk
from tkinter import simpledialog, messagebox

class IAsimples:
    def __init__(self):
        self.numero = random.randint(1, 100)

    def advinhar(self, tentativa):
        if tentativa == self.numero:
            return "Acertou!"
        elif tentativa < self.numero:
            return "Tente um número mais alto"
        elif tentativa > self.numero:
            return "Tente um número mais baixo"
        else:
            return None

def configurar_cores(widget):
    widget.configure(bg="purple", fg="white")

# Função para exibir o resultado final
def mostrar_resultado(resultado, contagem):
    messagebox.showinfo("Parabéns!", f"{resultado}\nVocê acertou em {contagem} tentativas!")

# Função principal do jogo
def jogar_jogo():
    IAbot = IAsimples()
    contagem = 0

    while True:
        tentativa = simpledialog.askinteger("Adivinhação", "Digite seu número da sorte:")
        if tentativa is None:
            # Usuário clicou em Cancelar, encerrar o jogo
            break

        contagem += 1
        resultado = IAbot.advinhar(tentativa)
        messagebox.showinfo("Resultado", resultado)

        if resultado == "Acertou!":
            mostrar_resultado(resultado, contagem)
            break

# Criar a janela principal
janela = tk.Tk()
janela.title("Jogo de Adivinhação")
janela.configure(bg="black")

# Botão para iniciar o jogo
botao_iniciar = tk.Button(janela, text="Iniciar Jogo", command=jogar_jogo)
configurar_cores(botao_iniciar)
botao_iniciar.pack(pady=20)

# Botão para fechar o aplicativo
botao_fechar = tk.Button(janela, text="Fechar", command=janela.quit)
configurar_cores(botao_fechar)
botao_fechar.pack()

# Iniciar o loop principal da janela
janela.mainloop()
