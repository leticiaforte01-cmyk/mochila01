
🎒 Problema da Mochila 0-1 (Knapsack)

Este projeto implementa uma solução em Python para o problema clássico da mochila 0-1, utilizando programação dinâmica. O objetivo é selecionar os itens com maior valor possível sem ultrapassar a capacidade da mochila.


📌 Objetivo

Dado um conjunto de itens com seus respectivos pesos e valores, e uma capacidade máxima da mochila, o algoritmo determina a melhor combinação de itens para maximizar o valor total transportado.


🧠 Como funciona

Cada item pode ser incluído (1) ou excluído (0).

O algoritmo constrói uma matriz de decisões, onde cada célula representa o valor máximo possível com os primeiros i itens e capacidade w.

A escolha é entre levar o item atual ou pular para o próximo.


🛠️ Tecnologias utilizadas
Linguagem: Python 3

Paradigma: Programação dinâmica


📥 Instalação e execução

Acesse o código: https://colab.research.google.com/drive/1-hjuyxdF23aZXdwsSCC-wbBpQ4R_vf0h?ts=68d32abf


🧩 Passo a passo explicativo do código

Este projeto resolve o Problema da Mochila 0-1 usando programação dinâmica. Abaixo está a explicação detalhada do código:

def mochila_01(peso, valor, capacidade):

🔹 Define a função mochila_01, que recebe:

peso: lista com os pesos dos itens.

valor: lista com os valores dos itens.

capacidade: capacidade máxima da mochila.

    n = len(valor)
    
🔹 Calcula o número de itens disponíveis.

    matriz = [[0 for x in range(capacidade + 1)] for x in range(n + 1)]
    
🔹 Cria uma matriz de decisões com n+1 linhas e capacidade+1 colunas.

Cada célula matriz[i][w] representa o valor máximo possível usando os primeiros i itens com capacidade w.

    for i in range(1, n + 1):
        for w in range(1, capacidade + 1):
        
🔹 Percorre cada item (i) e cada capacidade possível (w), começando do 1 (porque a linha 0 representa o caso sem itens).

            if peso[i - 1] <= w:
            
🔹 Verifica se o item atual cabe na mochila com a capacidade w.

                matriz[i][w] = max(valor[i - 1] + matriz[i - 1][w - peso[i - 1]], matriz[i - 1][w])

🔹 Se couber, calcula o máximo entre duas opções:

1. Levar o item: soma o valor do item atual com o melhor valor possível para o espaço restante.

2. Não levar: mantém o valor anterior.

            else:
                matriz[i][w] = matriz[i - 1][w]

🔹 Se o item não couber, apenas copia o valor anterior (sem incluir o item).

    return matriz[n][capacidade]

🔹 Retorna o valor máximo possível que pode ser carregado com todos os itens e a capacidade total da mochila.






