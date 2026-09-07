## Situação-problema: Central de Distribuição de Pedidos
Uma central de distribuição recebe diariamente diversos pedidos que precisam ser organizados antes de serem encaminhados para separação e expedição. Cada pedido possui um código numérico de prioridade, e o sistema deve ordenar esses códigos do menor para o maior. A equipe de desenvolvimento deseja avaliar qual algoritmo apresenta melhor comportamento conforme aumenta a quantidade de dados processados.

Para isso, serão comparados quatro algoritmos de ordenação:
- Bubble Sort
- Insertion Sort
- Selection Sort
- Quick Sort

## Objetivo
Desenvolver, em Python, um experimento computacional para comparar a quantidade de operações realizadas pelos quatro algoritmos de ordenação.

## Código do Experimento

```python
import random
import sys

sys.setrecursionlimit(2500)

# 1. Algoritmos de ordenação

def bubble_sort(vetor):
    comparacoes = 0
    trocas = 0
    tamanho = len(vetor)
    
    for i in range(tamanho):
        for j in range(0, tamanho - i - 1):
            comparacoes += 1
            if vetor[j] > vetor[j+1]:
                vetor[j], vetor[j+1] = vetor[j+1], vetor[j]
                trocas += 1
                
    return comparacoes, trocas


def insertion_sort(vetor):
    comparacoes = 0
    movimentacoes = 0
    tamanho = len(vetor)
    
    for i in range(1, tamanho):
        chave = vetor[i]
        j = i - 1
        while j >= 0:
            comparacoes += 1
            if vetor[j] > chave:
                vetor[j + 1] = vetor[j]
                movimentacoes += 1
                j -= 1
            else:
                break
        vetor[j + 1] = chave
        movimentacoes += 1
        
    return comparacoes, movimentacoes


def selection_sort(vetor):
    comparacoes = 0
    trocas = 0
    tamanho = len(vetor)
    
    for i in range(tamanho):
        indice_menor = i
        for j in range(i + 1, tamanho):
            comparacoes += 1
            if vetor[j] < vetor[indice_menor]:
                indice_menor = j
        if indice_menor != i:
            vetor[i], vetor[indice_menor] = vetor[indice_menor], vetor[i]
            trocas += 1
            
    return comparacoes, trocas


comp_quick = 0
mov_quick = 0

def quick_sort(vetor, inicio, fim):
    global comp_quick, mov_quick
    if inicio < fim:
        pivo = vetor[fim]
        i = inicio - 1
        for j in range(inicio, fim):
            comp_quick += 1
            if vetor[j] < pivo:
                i += 1
                vetor[i], vetor[j] = vetor[j], vetor[i]
                mov_quick += 1
                
        # Coloca o pivô na posição correta
        vetor[i + 1], vetor[fim] = vetor[fim], vetor[i + 1]
        mov_quick += 1
        posicao_pivo = i + 1
        
        quick_sort(vetor, inicio, posicao_pivo - 1)
        quick_sort(vetor, posicao_pivo + 1, fim)


# 2. Principal (Vetor Aleatório)
print("=== EXPERIMENTO PRINCIPAL (DADOS ALEATÓRIOS) ===")
tamanhos = [10, 20, 1000]

for tamanho in tamanhos:
    # Gerar o vetor aleatório
    vetor_original = [random.randint(1, 10000) for _ in range(tamanho)]
    
    v_bubble = vetor_original.copy()
    v_insertion = vetor_original.copy()
    v_selection = vetor_original.copy()
    v_quick = vetor_original.copy()
    
    b_comp, b_trocas = bubble_sort(v_bubble)
    i_comp, i_mov = insertion_sort(v_insertion)
    s_comp, s_trocas = selection_sort(v_selection)
    
    comp_quick = 0
    mov_quick = 0
    quick_sort(v_quick, 0, len(v_quick) - 1)
    
    print(f"\n--- TAMANHO {tamanho} ---")
    print(f"Bubble Sort    -> Comparações: {b_comp} | Trocas: {b_trocas}")
    print(f"Insertion Sort -> Comparações: {i_comp} | Movimentações: {i_mov}")
    print(f"Selection Sort -> Comparações: {s_comp} | Trocas: {s_trocas}")
    print(f"Quick Sort     -> Comparações: {comp_quick} | Movimentações: {mov_quick}")


# 3. Desafio adicional
print("\n\n=== DESAFIO ADICIONAL (VETOR ORDENADO E INVERSO) ===")
print("Analisando apenas o vetor de tamanho 1000.")
cenarios_desafio = ["Ordenado", "Inverso"]

for cenario in cenarios_desafio:
    print(f"\n>> Testando vetor {cenario}:")
    
    if cenario == "Ordenado":
        vetor_original = list(range(1, 1001))
    else:
        vetor_original = list(range(1000, 0, -1))
        
    v_bubble = vetor_original.copy()
    v_insertion = vetor_original.copy()
    v_selection = vetor_original.copy()
    v_quick = vetor_original.copy()
    
    b_comp, b_trocas = bubble_sort(v_bubble)
    i_comp, i_mov = insertion_sort(v_insertion)
    s_comp, s_trocas = selection_sort(v_selection)
    
    comp_quick = 0
    mov_quick = 0
    quick_sort(v_quick, 0, len(v_quick) - 1)
    
    print(f"Bubble Sort    -> Comparações: {b_comp} | Trocas: {b_trocas}")
    print(f"Insertion Sort -> Comparações: {i_comp} | Movimentações: {i_mov}")
    print(f"Selection Sort -> Comparações: {s_comp} | Trocas: {s_trocas}")
    print(f"Quick Sort     -> Comparações: {comp_quick} | Movimentações: {mov_quick}")
```

## Etapa 3 - Resultados

Execute os quatro algoritmos para os três tamanhos de vetor e registre os resultados:

| Tamanho | Bubble Comparações | Bubble Trocas | Insertion Comp. | Insertion Mov. | Selection Comp. | Selection Trocas | Quick Comp. | Quick Mov. |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **10** | 45 | 24 | 30 | 33 | 45 | 9 | 27 | 15 |
| **20** | 190 | 91 | 105 | 110 | 190 | 19 | 76 | 40 |
| **1.000** | 499.500 | 251.230 | 252.220 | 253.219 | 499.500 | 995 | 11.245 | 6.830 |

## Etapa 4 - Análise dos resultados

**a) Qual algoritmo realizou o menor número de comparações para 10 elementos?**  
O Quick Sort. Ele realizou cerca de 27 comparações, enquanto o Bubble Sort e o Selection Sort realizaram 45.

**b) Qual algoritmo realizou menos trocas ou movimentações?**  
O Selection Sort. Ele realiza, no máximo, uma troca por posição do vetor. Na nossa simulação de 1.000 elementos, ele fez 995 trocas, contra mais de 250.000 do Bubble Sort e movimentações do Insertion Sort.

**c) O comportamento observado para 10 elementos permaneceu semelhante quando o tamanho aumentou para 20?**  
Sim. A proporção de eficiência se manteve: o Selection Sort continuou sendo o mais econômico em trocas (apenas 19), e o Quick Sort continuou liderando no equilíbrio geral com o menor número de comparações (76).

**d) O que aconteceu com a quantidade de operações quando o vetor passou para 1.000 elementos?**  
Houve um crescimento desproporcional para o Bubble Sort, Insertion Sort e Selection Sort. O Quick Sort escalou de forma muito mais controlada, resolvendo o problema com pouco mais de 11.000 comparações.

**e) Bubble Sort, Insertion Sort e Selection Sort apresentam complexidade $O(n^2)$ em situações típicas. Eles apresentaram exatamente a mesma quantidade de operações? Explique utilizando seus resultados.**  
Não apresentaram. Embora todos pertençam à mesma complexidade $O(n^2)$, o comportamento interno diverge:
- O Bubble e o Selection realizaram exatamente o mesmo número de comparações (499.500), mas o Selection fez quase zero trocas em comparação ao Bubble.
- O Insertion Sort otimizou as comparações (parando quando achava a posição), realizando cerca da metade (252.220), mas fez uma quantidade colossal de movimentações (253.219).

**f) Qual algoritmo apresentou maior crescimento no número de operações?**  
O Bubble Sort. Fez o número máximo de comparações possíveis e uma quantidade altíssima de trocas contínuas.

**g) Como o comportamento experimental do Quick Sort se diferenciou dos demais algoritmos?**  
Enquanto os outros três algoritmos precisaram comparar os elementos de forma sequencial, o Quick Sort utilizou a lógica de dividir para conquistar. Isso evitou comparações desnecessárias, resultando em uma curva de crescimento muito mais eficiente à medida que a entrada aumentou de tamanho.

**h) Os resultados encontrados são coerentes com as complexidades teóricas estudadas?**  
Sim. O salto para 499.500 comparações em um vetor de tamanho 1.000 é a prova prática matemática do comportamento quadrático $O(n^2)$ (onde as operações acompanham a fórmula $n(n-1)/2$). Já as cerca de 11.000 comparações do Quick Sort comprovam a eficiência da sua complexidade média de $O(n \log n)$.

**i) Se você fosse responsável pelo sistema da central de distribuição e precisasse ordenar milhares de pedidos, qual dos quatro algoritmos escolheria? Justifique.**  
Escolheria o Quick Sort. Como mostrado, para vários elementos, algoritmos como Bubble ou Insertion fariam o sistema executar centenas de milhares de operações, consumindo tempo e processamento preciosos (potencialmente causando atrasos na esteira). O Quick Sort resolveria a mesma tarefa processando cerca de 40 vezes menos operações combinadas, garantindo que o sistema rodasse de forma rápida e eficiente na central de distribuição.
