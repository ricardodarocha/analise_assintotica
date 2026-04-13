>1.
>Ordene as funções abaixo do menor para o maior crescimento assintótico:  
>
>$n$  
>$n²$  
>$log n$  
>$2ⁿ$  

**resolução**  
$logn<n<n2<2n$
 
---
>2.
>Explique por que, na análise assintótica, constantes e termos de menor ordem são desprezados.

**resolução**  
Constantes multiplicativas não alteram a ordem de crescimento  
Termos de menor grau tornam-se irrelevantes comparados ao termo dominante

---

> 3.
> Determine a notação O para as funções abaixo:  
>
>a) $f(n) = 5n + 20$  
>b) $f(n) = 3n² + 2n + 7$  
>c) $f(n) = log n + 100$  

### 3. Notação O

a) $f(n) = 5n + 20 ⇒ O(n)$  

b) $f(n) = 3n² + 2n + 7⇒ O(n²)$

c) $f(n) = log n + 100⇒ O(log n)$  

---

>4.  
>Explique a diferença entre as notações $O, Ω e Θ$.

### 4. Diferença entre $O$, $Ω$ e $Θ$

**Big-O (O) — limite superior**
$f(n) ∈ O(g(n)) ⇒ f(n) ≤ c · g(n)$  
Interpretação: cresce no máximo como $g(n)$  

**Big-Omega (Ω) — limite inferior**
$f(n) ∈ Ω(g(n)) ⇒ f(n) ≥ c · g(n)$  
Interpretação: cresce pelo menos como $g(n)$  

**Big-Theta (Θ) — limite apertado**
$f(n) ∈ Θ(g(n)) ⇒ c₁g(n) ≤ f(n) ≤ c₂g(n)$  
Interpretação: cresce exatamente como $g(n)$ (mesma ordem)

---

> 5.
> Considere um algoritmo cujo tempo de execução é dado por:  
>   
>Melhor caso: $n$  
>Pior caso: $n²$  
>a) Qual é a notação $O$?  
>b) Qual é a notação $Ω$?  
>c) É possível definir $Θ$? Justifique.

### 5. Melhor caso: n | Pior caso: n²

a) Notação O:
$O(n²)$  
(Big-O considera o pior caso)

b) Notação $Ω$:
$Ω(n)$  
(Big-Omega considera o melhor caso)

c) Existe $Θ$?

Não é possível definir diretamente.

Justificativa:
$Θ$ exige que a função esteja entre dois limites da mesma ordem.

Aqui: $n ≤ T(n) ≤ n²$

Como são ordens diferentes, não há um único crescimento assintótico exato.

6. Explique por que um algoritmo com complexidade $O(n log n)$ é, em geral, preferível a um algoritmo $O(n²)$.

### 6. Por que $O(n log n)$ é melhor que $O(n²)$?

Porque cresce significativamente mais devagar.

n²: crescimento quadrático  
n log n: crescimento linearizado (amenizado)

Exemplo:

$n = 1.000$  
$n log n ≈ 10.000$  
$n² = 1.000.000$  

$n = 1.000.000$  
$n log n ≈ 20.000.000$  
$n² = 1.000.000.000.000$  

Conclusão:
Para entradas grandes, algoritmos $O(n log n)$ são muito mais eficientes.
