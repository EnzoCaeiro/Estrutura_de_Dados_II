# Atividade Avaliativa 02: Algoritmos de Ordenação e Busca

## PARTE 1 – PESQUISA: BUBBLE SORT E QUICK SORT

### BUBBLE SORT

* **Como o algoritmo funciona:** Ele percorre a lista da esquerda para a direita múltiplas vezes, comparando pares de elementos adjacentes (vizinhos) ao longo do caminho.
* **Sua lógica de ordenação:** Se o elemento atual for maior que o próximo, eles trocam de posição. Assim, a cada passagem, o maior elemento restante "flutua" para o final da lista, até que nenhuma troca seja mais necessária.
* **Complexidade no melhor caso:** $O(n)$ ocorre quando a lista já está ordenada.
* **Complexidade no caso médio:** $O(n^2)$ ocorre quando os elementos estão misturados aleatoriamente.
* **Complexidade no pior caso:** $O(n^2)$ ocorre quando a lista está em ordem inversamente classificada, do maior para o menor.
* **Vantagens:** É um algoritmo estável (não altera a ordem de elementos iguais), opera no próprio local da memória (in-place) e possui uma lógica muito fácil de entender e codificar.
* **Limitações:** É extremamente lento e ineficiente. O número de operações cresce muito rápido à medida que o tamanho da lista aumenta.
* **Situações em que seu uso é adequado:** É ótimo para fins didáticos (ensinar lógica de programação), ou para ordenar listas muito pequenas que já estejam quase totalmente ordenadas.
* **Situações em que seu uso não é recomendado:** Em aplicações reais de software, sistemas de produção ou qualquer cenário com médio ou grande volume de dados.

### QUICK SORT

* **Como o algoritmo funciona:** Ele utiliza a estratégia de "dividir para conquistar", separando o problema principal em problemas menores de forma recursiva.
* **Sua lógica de ordenação:** O algoritmo escolhe um elemento da lista para ser o "pivô". Ele então particiona os dados, colocando todos os valores menores que o pivô à esquerda dele e os maiores à direita. O processo é repetido nas sub-listas da esquerda e da direita até que tudo esteja ordenado.
* **Complexidade no melhor caso:** $O(n \log n)$ ocorre quando o pivô sempre consegue dividir a lista em duas metades perfeitamente iguais.
* **Complexidade no caso médio:** $O(n \log n)$ ocorre na maioria dos casos práticos com elementos aleatórios.
* **Complexidade no pior caso:** $O(n^2)$ ocorre se o pivô escolhido for sempre o pior possível, como escolher o primeiro elemento em uma lista que já está ordenada.
* **Vantagens:** É um dos algoritmos de ordenação mais rápidos na prática. Lida muito bem com a memória cache do processador e também opera in-place, sem exigir muita memória extra.
* **Limitações:** Geralmente é instável (pode trocar a ordem de valores iguais). Além disso, sua implementação é um pouco mais complexa e o desempenho pode cair drasticamente em listas específicas se o pivô for mal escolhido.
* **Situações em que seu uso é adequado:** É o padrão ouro para a maioria das aplicações do mundo real. Excelente para bancos de dados, bibliotecas padrão de linguagens de programação e grandes volumes de dados na memória.
* **Situações em que seu uso não é recomendado:** Quando é estritamente necessário um algoritmo de ordenação estável (onde elementos iguais devem manter a ordem original) ou em sistemas de tempo real super críticos onde o risco do pior caso ($O(n^2)$) não pode existir de forma alguma.

### Tabela Comparativa

| Característica | Bubble Sort | Quick Sort |
| :--- | :--- | :--- |
| **Princípio de funcionamento** | Compara elementos adjacentes e os troca de posição, fazendo os maiores valores "flutuarem" para o final. | "Dividir para conquistar". Escolhe um pivô, particiona a lista em menores e maiores que ele, e aplica recursão. |
| **Melhor caso** | $O(n)$ | $O(n \log n)$ |
| **Caso médio** | $O(n^2)$ | $O(n \log n)$ |
| **Pior caso** | $O(n^2)$ | $O(n^2)$ |
| **Uso de memória** | Mínimo / $O(1)$. Opera in-place (no próprio local). | Baixo / Opera in-place, mas consome espaço na pilha de recursão (em média $O(\log n)$). |
| **Vantagem principal** | Lógica extremamente simples de implementar e algoritmo estável. | Muito rápido na prática para grandes conjuntos de dados. |
| **Limitação principal** | Totalmente ineficiente para volumes médios ou grandes de dados. | Algoritmo instável e pode sofrer queda drástica de desempenho se o pivô for mal escolhido. |
| **Aplicação recomendada** | Fins puramente didáticos ou listas minúsculas quase ordenadas. | Padrão para uso geral na indústria, bibliotecas nativas e grandes coleções de dados. |

---

## PARTE 2 – EXPERIMENTO DE ORDENAÇÃO

### Código em Python
```python
import random

tamanhos = [10, 20, 1000]

for tamanho in tamanhos:
    # Dados
    dados_originais = [random.randint(1, 10000) for _ in range(tamanho)]
    lista_bubble = dados_originais.copy()
    lista_quick = dados_originais.copy()

    # Bubble Sort
    comp_bubble = 0
    trocas_bubble = 0
    n = len(lista_bubble)
    
    for i in range(n):
        for j in range(0, n - i - 1):
            comp_bubble += 1
            if lista_bubble[j] > lista_bubble[j + 1]:
                lista_bubble[j], lista_bubble[j + 1] = lista_bubble[j + 1], lista_bubble[j]
                trocas_bubble += 1

    # Quick Sort
    comp_quick = 0
    mov_quick = 0

    def quick_sort(lista, inicio, fim):
        global comp_quick, mov_quick
        if inicio < fim:
            pivo = lista[fim]
            i = inicio - 1
            for j in range(inicio, fim):
                comp_quick += 1
                if lista[j] <= pivo:
                    i += 1
                    lista[i], lista[j] = lista[j], lista[i]
                    mov_quick += 1
            
            lista[i + 1], lista[fim] = lista[fim], lista[i + 1]
            mov_quick += 1
            p = i + 1
            
            quick_sort(lista, inicio, p - 1)
            quick_sort(lista, p + 1, fim)

    quick_sort(lista_quick, 0, len(lista_quick) - 1)

    # Resultados
    print(f"--- TAMANHO: {tamanho} ---")
    print(f"Bubble Sort -> Comparações: {comp_bubble} | Trocas: {trocas_bubble}")
    print(f"Quick Sort -> Comparações: {comp_quick} | Movimentações: {mov_quick}\n")
```

### Resultados Obtidos

| Tamanho do Array | Bubble Sort - Comparações | Bubble Sort - Trocas | Quick Sort - Comparações | Quick Sort - Movimentações |
| :--- | :--- | :--- | :--- | :--- |
| **10** | 45 | 22 | 25 | 12 |
| **20** | 190 | 95 | 74 | 35 |
| **1.000** | 499.500 | 251.300 | 10.970 | 6.500 |

### Respostas

**a) Qual algoritmo realizou menos operações para 10 elementos?**  
O Quicksort realizou menos operações.

**b) O comportamento permaneceu igual para 20 elementos?**  
Sim. A vantagem do Quick Sort se manteve, e a distância entre a quantidade de operações realizadas por cada um começou a ficar maior. O Bubble Sort realizou exatamente 190 comparações, enquanto o Quick Sort permaneceu ainda menor.

**c) O que aconteceu quando o tamanho aumentou para 1.000 elementos?**  
A diferença se tornou ainda maior. O Bubble Sort realizou 499.500 comparações e milhares de trocas, demonstrando grande lentidão. O Quick Sort, por outro lado, resolveu o problema com pouco mais de 10.970 comparações.

**d) Qual algoritmo apresentou maior crescimento da quantidade de operações?**  
O Bubble Sort. À medida que o tamanho da lista aumentou de 10 para 1000 (100 vezes maior), o número de comparações do Bubble Sort aumentou de 45 para 499.500 (mais de 11.000 vezes maior).

**e) Os resultados experimentais são coerentes com as complexidades teóricas estudadas?**  
Sim. O Bubble Sort tem complexidade de tempo $O(N^2)$ no pior caso e no caso médio. O Quick Sort tem complexidade de tempo média de $O(N \log N)$. Isso significa que ele escala de forma muito mais suave e eficiente à medida que a entrada cresce.

**f) Em qual situação você escolheria Bubble Sort?**  
Usaria para fins educacionais por conta da complexidade menor e para listas menores. O Bubble para o mundo corporativo é muito ineficiente comparado aos outros algoritmos.

**g) Em qual situação você escolheria Quick Sort?**  
Usaria para listas enormes e menor uso da RAM, além do tempo de carregamento ser infinitamente mais rápido.

---

## PARTE 3 – INVESTIGAÇÃO DE BUSCA EM MATRIZES

### Código em Python
```python
import random

tamanhos = [(2, 2), (10, 10), (100, 100)]

for linhas, colunas in tamanhos:
    # CRIANDO A MATRIZ COM VALORES ALEATÓRIOS
    matriz = []
    for i in range(linhas):
        linha = []
        for j in range(colunas):
            linha.append(random.randint(1, 10000))
        matriz.append(linha)

    total_elementos = linhas * colunas
    print(f"--- MATRIZ {linhas}x{colunas} ({total_elementos} elementos) ---")
    
    alvo_inicio = matriz[0][0]
    alvo_fim = matriz[linhas-1][colunas-1]
    alvo_inexistente = -1

    testes = [
        ("Busca no início", alvo_inicio),
        ("Busca no final", alvo_fim),
        ("Valor inexistente", alvo_inexistente)
    ]

    # Execução
    for cenario, alvo in testes:
        comparacoes = 0
        encontrado = False
        linha_encontrada = -1
        coluna_encontrada = -1

        # Lógica da Busca Sequencial com loops aninhados
        for i in range(linhas):
            for j in range(colunas):
                comparacoes += 1
                if matriz[i][j] == alvo:
                    encontrado = True
                    linha_encontrada = i
                    coluna_encontrada = j
                    break
            if encontrado:
                break

        # Resultados
        if encontrado:
            print(f"{cenario}: Valor {alvo} encontrado na linha {linha_encontrada}, coluna {coluna_encontrada} | Comparações: {comparacoes}")
        else:
            print(f"{cenario}: Valor {alvo} NÃO encontrado | Comparações: {comparacoes}")
    print()
```

### Resultados Obtidos

| Matriz | N° de elementos | Busca no início | Busca no final | Valor inexistente |
| :--- | :--- | :--- | :--- | :--- |
| **2 x 2** | 4 | 1 | 4 | 4 |
| **10 x 10** | 100 | 1 | 100 | 100 |
| **100 x 100** | 10.000 | 1 | 10.000 | 10.000 |

### Respostas

**a) Por que encontrar um elemento no início exige menos operações?**  
Porque a busca sequencial verifica os elementos de forma linear, um por um, a partir da primeira posição (linha 0, coluna 0). Se o elemento procurado for logo o primeiro, o algoritmo o encontra imediatamente, interrompe a busca e realiza apenas 1 comparação.

**b) O que acontece quando o elemento procurado não existe?**  
O algoritmo é forçado a percorrer e verificar todos os elementos da matriz para ter certeza de que o valor realmente não está lá. Isso resulta no número máximo de operações possíveis para o tamanho daquela estrutura.

**c) Qual é o pior caso da busca sequencial?**  
Quando o elemento procurado está na última posição da matriz ou quando o elemento não existe na matriz. Em ambos os cenários, o algoritmo precisa percorrer todos os itens, realizando o número máximo de comparações.

**d) Como o aumento das dimensões da matriz influencia a quantidade de operações?**  
O aumento das dimensões aumenta o limite máximo de operações de forma diretamente proporcional ao número total de elementos. Se a matriz passa de 100 elementos para 10.000 elementos (aumentou 100 vezes), o número máximo de operações no pior caso também aumentará 100 vezes. É um crescimento linear em relação à área da matriz.

**e) Qual a complexidade da busca sequencial em uma matriz com m linhas e n colunas?**  
A complexidade de tempo no pior caso é de $O(m \times n)$, pois o algoritmo precisa visitar, no limite, cada célula de cada linha e de cada coluna. Se chamarmos o total de elementos da matriz de $N$ (onde $N = m \times n$), podemos simplificar a representação da complexidade para $O(N)$, indicando que o tempo de execução cresce linearmente em relação ao volume total de dados.

---

## PARTE 4 – HANDS ON 1: INVESTIGAÇÃO DO ARRAY

### Código em Python
```python
print("PROGRAMA DE ANÁLISE DE TEMPERATURAS")
temperaturas = []
print("\nENTRADA DE DADOS")

for i in range(10):
    while True:
        try:
            valor = float(input(f"Digite a temperatura do indice {i}: "))
            temperaturas.append(valor)
            break
        except ValueError:
            print("Erro! Digite um número válido.")

print("\nTEMPERATURAS ARMAZENADAS")
print("Índice | Temperatura")
print("-" * 25)

for i in range(10):
    print(f"  {i:2d}   | {temperaturas[i]:.1f} °C")

soma = 0
maior = temperaturas[0]
menor = temperaturas[0]
indice_maior = 0
indice_menor = 0

for i in range(10):
    soma += temperaturas[i]
    if temperaturas[i] > maior:
        maior = temperaturas[i]
        indice_maior = i
    if temperaturas[i] < menor:
        menor = temperaturas[i]
        indice_menor = i

media = soma / 10
acima_media = 0

for i in range(10):
    if temperaturas[i] > media:
        acima_media += 1

print("\nRESULTADOS DA ANÁLISE")
print(f"Média das temperaturas: {media:.2f}°C")
print(f"Maior temperatura: {maior:.1f}°C (índice {indice_maior})")
print(f"Menor temperatura: {menor:.1f}°C (índice {indice_menor})")
print(f"Valores acima da média: {acima_media}")
```

### Respostas

**Qual a complexidade do algoritmo desenvolvido?**  
A complexidade do algoritmo é linear, representada pela notação $O(N)$, onde $N$ é o tamanho da estrutura de dados.

**Quantidade de operações?**  
Foram realizadas 30 operações de percurso sobre o array já preenchido. Isso ocorre porque o algoritmo utiliza 3 laços de repetição (`for`) distintos e sequenciais, percorrendo todos os 10 elementos em cada um deles:
1.  10 operações para imprimir a tabela de temperaturas;
2.  10 operações para calcular a soma e encontrar o maior e o menor valor simultaneamente;
3.  10 operações para contar os valores que ficaram acima da média.

---

## PARTE 5 – HANDS ON 2: MATRIZ APLICADA – MONITORAMENTO DE SENSORES

### Código em Python
```python
import random

# Matriz
sensores = []
for i in range(5):
    linha = []
    for j in range(24):
        linha.append(round(random.uniform(15.0, 35.0), 1))
    sensores.append(linha)

soma_geral = 0.0
maior_temp = sensores[0][0]
sensor_maior = 0
hora_maior = 0

print("1. MÉDIA DE CADA SENSOR")
print("-" * 36)
for i in range(5):
    soma_sensor = 0.0
    for j in range(24):
        temp_atual = sensores[i][j]
        soma_sensor += temp_atual
        soma_geral += temp_atual
        
        if temp_atual > maior_temp:
            maior_temp = temp_atual
            sensor_maior = i
            hora_maior = j
            
    print(f"Sensor {i}: {(soma_sensor / 24):.2f} °C")

print("\nRESULTADOS GERAIS")
print("-" * 36)
print(f"2. Maior temperatura registrada: {maior_temp:.1f} °C")
print(f"3. Sensor responsável..........: {sensor_maior}")
print(f"4. Horário da ocorrência.......: {hora_maior}:00")
print(f"5. Média geral do sistema......: {(soma_geral / 120):.2f}°C")

print("\n6. ANÁLISE DE LIMITE")
print("-" * 36)
try:
    limite = float(input("Informe o limite de temperatura (°C): "))
    acima_limite = 0
    for i in range(5):
        for j in range(24):
            if sensores[i][j] > limite:
                acima_limite += 1
    print(f"Quantidade de leituras acima do limite: {acima_limite}")
except ValueError:
    print("Erro: Digite um valor numérico válido.")
```

### Respostas

**Por que são necessários loops aninhados?**  
Uma matriz é uma estrutura de dados bidimensional (composta de linhas e colunas). Um único loop só consegue percorrer uma dimensão (como uma lista simples). Para visitar todos os dados, usamos o loop externo para fixar uma linha e o loop interno para iterar por todas as colunas daquela linha. Assim que as colunas acabam, o loop externo avança para a próxima linha, repetindo o processo até esgotar a matriz.

**Qual o papel dos índices `[i][j]`?**  
Eles funcionam exatamente como um sistema de coordenadas cartesianas (x, y) mapeando um endereço na memória.
*   O índice `i` (controlado pelo loop externo) representa a coordenada da linha, ou seja, qual sensor estamos lendo (de 0 a 4).
*   O índice `j` (controlado pelo loop interno) representa a coordenada da coluna, ou seja, qual horário estamos lendo (de 0 a 23).
Juntos, `[i][j]` garantem o acesso a uma posição única e específica do arranjo.

**Quantas posições da matriz são percorridas?**  
São 120 posições. O código acessa cada elemento uma única vez no percurso principal e mais uma vez no percurso de verificação do limite.

**Qual a relação entre o número de linhas, colunas e quantidade de operações?**  
A relação é de multiplicação direta. O bloco de código que fica dentro do loop mais interno será executado o número de vezes equivalente ao total de linhas multiplicado pelo total de colunas.

---

## PARTE 6 – ANÁLISE E CONCLUSÃO

**1. O aumento do tamanho da estrutura de dados influencia a quantidade de operações?**  
Sim, de forma direta. A quantidade de dados de entrada é o que define o esforço do processador. Nos experimentos realizados, ficou claro que aumentar o tamanho da estrutura (seja um vetor ou uma matriz) exige que o sistema realize muito mais repetições para terminar a tarefa. Em uma busca sequencial, por exemplo, esse crescimento é estritamente proporcional: se a quantidade de dados aumenta cem vezes, o limite de operações também aumenta cem vezes. Esse comportamento é classificado com a complexidade linear $O(N)$.

**2. Bubble Sort e Quick Sort crescem da mesma maneira quando o número de elementos aumenta?**  
Não, eles lidam com o aumento de dados de formas completamente diferentes. 
O Bubble Sort possui uma complexidade quadrática, representada por $O(N^2)$. Isso significa que o número de operações cresce de forma drástica e ineficiente; ao aumentar a lista para 1.000 elementos, ele precisou fazer quase meio milhão de comparações. 
Já o Quick Sort possui uma complexidade otimizada de $O(N \log N)$. Ele divide o problema em partes menores (particionamento), fazendo com que a quantidade de operações cresça de maneira muito mais suave. Para os mesmos 1.000 elementos, ele resolveu o problema fazendo apenas cerca de 10 mil comparações. A diferença de desempenho entre os dois se torna gigantesca à medida que os dados aumentam.

**3. Por que analisar somente o resultado final da ordenação não é suficiente para comparar algoritmos?**  
Porque o resultado final comprova apenas que o algoritmo funciona, mas esconde o custo real para a máquina. Tanto o Bubble Sort quanto o Quick Sort vão entregar exatamente a mesma lista ordenada no final, o que os faz parecerem iguais caso olhemos apenas a saída.
No entanto, comparar algoritmos exige medir a eficiência e a escalabilidade. É fundamental saber quanto tempo o processador gastou e se o programa daria conta de processar milhões de registros em um sistema real sem travar. Avaliar apenas o resultado ignora o desempenho e o consumo de recursos do sistema.
