import tkinter as tk
from tkinter import ttk

class ContadorPontosJiuJitsu:
    def __init__(self, root):
        self.root = root
        self.root.title("Contador de Pontos - Jiu-Jitsu")

        self.pontuacao_azul = 0
        self.pontuacao_branco = 0
        self.tempo_luta = 0
        self.tempo_restante = 0
        self.em_andamento = False

        # Rótulos e Exibição de Pontuação
        tk.Label(root, text="Pontos Azul:").grid(row=0, column=0)
        self.exibicao_azul = tk.Entry(root, font=("Helvetica", 24), state="readonly")
        self.exibicao_azul.grid(row=0, column=1)

        tk.Label(root, text="Pontos Branco:").grid(row=1, column=0)
        self.exibicao_branco = tk.Entry(root, font=("Helvetica", 24), state="readonly")
        self.exibicao_branco.grid(row=1, column=1)

        # Botões para adicionar pontos
        tk.Button(root, text="+2 Queda", command=lambda: self.adicionar_ponto("azul", 2)).grid(row=2, column=0)
        tk.Button(root, text="+3 Passagem de Guarda", command=lambda: self.adicionar_ponto("azul", 3)).grid(row=2, column=1)
        tk.Button(root, text="+4 Montada", command=lambda: self.adicionar_ponto("azul", 4)).grid(row=2, column=2)

        tk.Button(root, text="+2 Queda", command=lambda: self.adicionar_ponto("branco", 2)).grid(row=3, column=0)
        tk.Button(root, text="+3 Passagem de Guarda", command=lambda: self.adicionar_ponto("branco", 3)).grid(row=3, column=1)
        tk.Button(root, text="+4 Montada", command=lambda: self.adicionar_ponto("branco", 4)).grid(row=3, column=2)

        # Configuração do Cronômetro
        tk.Label(root, text="Cronômetro:").grid(row=4, column=0)
        self.tempo_combate = ttk.Combobox(root, values=['3', '4', '5', '6'], state="readonly")
        self.tempo_combate.set('3')
        self.tempo_combate.grid(row=4, column=1)

        tk.Button(root, text="Iniciar/Parar", command=self.iniciar_parar_luta).grid(row=4, column=2)

        # Atualização inicial da exibição de pontuação
        self.atualizar_exibicao_pontuacao()

    def adicionar_ponto(self, lutador, pontos):
        if lutador == "azul":
            self.pontuacao_azul += pontos
        elif lutador == "branco":
            self.pontuacao_branco += pontos

        self.atualizar_exibicao_pontuacao()

    def atualizar_exibicao_pontuacao(self):
        self.exibicao_azul.config(state="normal")
        self.exibicao_azul.delete(0, tk.END)
        self.exibicao_azul.insert(0, str(self.pontuacao_azul))
        self.exibicao_azul.config(state="readonly")

        self.exibicao_branco.config(state="normal")
        self.exibicao_branco.delete(0, tk.END)
        self.exibicao_branco.insert(0, str(self.pontuacao_branco))
        self.exibicao_branco.config(state="readonly")

    def iniciar_parar_luta(self):
        if not self.em_andamento:
            self.tempo_luta = int(self.tempo_combate.get()) * 60
            self.tempo_restante = self.tempo_luta
            self.em_andamento = True
            self.atualizar_cronometro()
        else:
            self.em_andamento = False

    def atualizar_cronometro(self):
        if self.em_andamento and self.tempo_restante > 0:
            minutos, segundos = divmod(self.tempo_restante, 60)
            tempo_formatado = "{:02d}:{:02d}".format(minutos, segundos)
            self.root.title(f"Contador de Pontos - Jiu-Jitsu ({tempo_formatado})")
            self.tempo_restante -= 1
            self.root.after(1000, self.atualizar_cronometro)
        elif self.tempo_restante == 0:
            self.em_andamento = False
            self.root.title("Contador de Pontos - Jiu-Jitsu")

if __name__ == "__main__":
    root = tk.Tk()
    app = ContadorPontosJiuJitsu(root)
    root.mainloop()
