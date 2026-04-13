## LISTA 01/01 
>1.  
>Explique, com suas próprias palavras, o que é um algoritmo. Em seguida, apresente um exemplo simples do cotidiano que possa ser descrito como um algoritmo.

>2.  
>Considere dois algoritmos que resolvem corretamente o mesmo problema. Explique por que, mesmo ambos sendo corretos, um pode ser considerado melhor que o outro.

>3.  
>Considere o pseudocódigo abaixo:
>```
>soma ← 0
>para i ← 1 até n faça
>    soma ← soma + i
>fim-para
>```
>
>a) Quantas vezes a instrução soma ← soma + i é executada?  
>b) Qual é o custo do algoritmo em função de n?

>4.  
>Dois algoritmos A e B possuem custos dados por:
>A(n) = 3n + 10
>B(n) = n²>
>a) Qual algoritmo é mais eficiente para valores pequenos de n?
>b) Qual algoritmo é mais eficiente para valores grandes de n? Justifique.

>5.  
>Explique por que a eficiência deve ser considerada ainda na fase de projeto do algoritmo, e não apenas após sua implementação.
 
# RESOLUÇÃO lista 01-01

## 1. O que é um algoritmo?

> Um algoritmo é uma sequência finita, bem definida e ordenada de instruções que, quando executadas, resolvem um problema ou realizam uma tarefa.  
> Em outras palavras, trata-se de um procedimento passo a passo que transforma uma entrada em uma saída desejada.

### Exemplo do cotidiano

>Um exemplo simples é uma receita de café:  
>1. Aquecer a água  
>2. Colocar o pó de café no filtro  
>3. Despejar a água quente sobre o pó  
>4. Aguardar a filtragem  
>5. Servir o café  
>Esse processo é um algoritmo, pois segue uma sequência lógica para atingir um objetivo.

---

## 2. Comparação entre algoritmos corretos

>Mesmo que dois algoritmos resolvam corretamente o mesmo problema, um pode ser considerado melhor que o outro devido à sua eficiência.
>
>Os principais critérios são:
>
>* **Tempo de execução** (complexidade temporal)
>* **Uso de memória** (complexidade espacial)
>
>Por exemplo, um algoritmo com custo:
>
>$$
>O(n)
>$$
>
>é mais eficiente do que outro com custo:
>
>$$
>O(n^2)
>$$
>
>para valores grandes de ( n ), pois cresce mais lentamente.

---

## 3. Análise do pseudocódigo

>### Pseudocódigo
>
>```
>soma ← 0
>para i ← 1 até n faça
>    soma ← soma + i
>fim-para
>```
>
>### a) Número de execuções
>
> A instrução: `soma ← soma + i` é executada exatamente: $n$ vezes.
>
>---
>
>### b) Custo do algoritmo
>
>O custo total é proporcional ao número de iterações do laço: $T(n) = n$ Logo, a complexidade do algoritmo é: $O(n)$
>
---

## 4. Comparação de algoritmos

>Dadas as funções:
>$A(n) = 3n + 10$  
>$B(n) = n^2$  
>
>### a) Valores pequenos de ( n )
>
>Para valores pequenos de ( n ), o algoritmo ( B(n) ) pode ser mais eficiente, pois:
>
>* ( $n^2$ ) ainda é pequeno
>* constantes como ( 10 ) têm maior impacto relativo
>
>---
>### b) Valores grandes de ( n )
>Para valores grandes de ( n ), o algoritmo ( A(n) ) é mais eficiente, pois:
>
>$
>3n + 10 \in O(n)
>$
>
>enquanto:
>$n^2 \in O(n^2)$
>
>Como:
>$\lim_{n \to \infty} \frac{n^2}{n} = \infty$
>
>o crescimento de ( B(n) ) é muito maior.
---

## 5. Importância da eficiência no projeto

A eficiência deve ser considerada ainda na fase de projeto porque:

* Define a **escalabilidade** do sistema
* Evita retrabalho após implementação
* Reduz custos computacionais (tempo e memória)
* Garante viabilidade para grandes volumes de dados

Corrigir ineficiências depois de implementar pode ser mais caro e complexo do que projetar corretamente desde o início.
 
