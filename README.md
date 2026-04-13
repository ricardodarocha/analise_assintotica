# Análise assintótica

## LISTA 01/01 

>(resolução abaixo)

1. Explique, com suas próprias palavras, o que é um algoritmo. Em seguida, apresente um exemplo simples do cotidiano que possa ser descrito como um algoritmo.

2. Considere dois algoritmos que resolvem corretamente o mesmo problema. Explique por que, mesmo ambos sendo corretos, um pode ser considerado melhor que o outro.

3. Considere o pseudocódigo abaixo:

soma ← 0
para i ← 1 até n faça
    soma ← soma + i
fim-para

a) Quantas vezes a instrução soma ← soma + i é executada?
b) Qual é o custo do algoritmo em função de n?

 

4. Dois algoritmos A e B possuem custos dados por:

A(n) = 3n + 10

B(n) = n²

a) Qual algoritmo é mais eficiente para valores pequenos de n?
b) Qual algoritmo é mais eficiente para valores grandes de n? Justifique.

5. Explique por que a eficiência deve ser considerada ainda na fase de projeto do algoritmo, e não apenas após sua implementação.
 
>RESOLUÇÃO
## 1. O que é um algoritmo?

Um algoritmo é uma sequência finita, bem definida e ordenada de instruções que, quando executadas, resolvem um problema ou realizam uma tarefa.

Em outras palavras, trata-se de um procedimento passo a passo que transforma uma entrada em uma saída desejada.

### Exemplo do cotidiano

Um exemplo simples é uma receita de café:

1. Aquecer a água
2. Colocar o pó de café no filtro
3. Despejar a água quente sobre o pó
4. Aguardar a filtragem
5. Servir o café

Esse processo é um algoritmo, pois segue uma sequência lógica para atingir um objetivo.

---

## 2. Comparação entre algoritmos corretos

Mesmo que dois algoritmos resolvam corretamente o mesmo problema, um pode ser considerado melhor que o outro devido à sua eficiência.

Os principais critérios são:

* **Tempo de execução** (complexidade temporal)
* **Uso de memória** (complexidade espacial)

Por exemplo, um algoritmo com custo:

$$
O(n)
$$

é mais eficiente do que outro com custo:

$$
O(n^2)
$$

para valores grandes de ( n ), pois cresce mais lentamente.

---

## 3. Análise do pseudocódigo

### Pseudocódigo

```
soma ← 0
para i ← 1 até n faça
    soma ← soma + i
fim-para
```

### a) Número de execuções

A instrução:

```
soma ← soma + i
```

é executada exatamente:

$$
n
$$

vezes.

---

### b) Custo do algoritmo

O custo total é proporcional ao número de iterações do laço:

$$
T(n) = n
$$

Logo, a complexidade do algoritmo é:

$$
O(n)
$$

---

## 4. Comparação de algoritmos

Dadas as funções:

$$
A(n) = 3n + 10
$$

$$
B(n) = n^2
$$

---

### a) Valores pequenos de ( n )

Para valores pequenos de ( n ), o algoritmo ( B(n) ) pode ser mais eficiente, pois:

* ( $n^2$ ) ainda é pequeno
* constantes como ( 10 ) têm maior impacto relativo

---

### b) Valores grandes de ( n )

Para valores grandes de ( n ), o algoritmo ( A(n) ) é mais eficiente, pois:

$$
3n + 10 \in O(n)
$$

enquanto:

$$
n^2 \in O(n^2)
$$

Como:

$$
\lim_{n \to \infty} \frac{n^2}{n} = \infty
$$

o crescimento de ( B(n) ) é muito maior.

---

## 5. Importância da eficiência no projeto

A eficiência deve ser considerada ainda na fase de projeto porque:

* Define a **escalabilidade** do sistema
* Evita retrabalho após implementação
* Reduz custos computacionais (tempo e memória)
* Garante viabilidade para grandes volumes de dados

Corrigir ineficiências depois de implementar pode ser mais caro e complexo do que projetar corretamente desde o início.
 

## LISTA  XX
## Exercício 1. Provar que $( f(n) \in O(n^2) )$

Queremos mostrar que existem constantes $( c > 0 ) e ( n_0 \in \mathbb{N} )$ tais que:

$$
\forall n \ge n_0,\quad f(n) \le c \cdot g(n)
$$

Onde:

$$
f(n) = \frac{3}{2}n^2 + \frac{7}{2}n - 4,\quad g(n) = n^2
$$

Para ( $n \ge 1$ ), temos:

$$
n \le n^2
$$

Logo:

$$
\frac{7}{2}n \le \frac{7}{2}n^2
$$

Então:

$$
f(n) \le \frac{3}{2}n^2 + \frac{7}{2}n^2 = 5n^2
$$

Portanto, tomando:

* ( $c = 5$ )
* ( $n_0 = 1$ )

Concluímos:

$$
f(n) \in O(n^2)
$$

---

# 2. Verificação de pares

## (a) ( $f(n) = 25n ), ( g(n) = n^3$ )

Para ( $n \ge 1$ ):

$$
25n \le 25n^3
$$

Logo:

* ( $c = 25$ )
* ( $n_0 = 1$ )

$$
25n \in O(n^3)
$$

---

## (b) ( $f(n) = 10n^2 ), ( g(n) = 2^n$ )

Sabemos que exponenciais dominam polinômios.

Para ( $n \ge 5$ ):

$$
10n^2 \le 2^n
$$

Logo:

* ( $c = 1$ )
* ( $n_0 = 5$ )

$$
10n^2 \in O(2^n)
$$

---

# 3. Provar que ( $f(n) \in O(n^3)$ )

$$
f(n) = 3n^3 + 2n^2
$$

Para ( $n \ge 1$ ):

$$
2n^2 \le 2n^3
$$

Logo:

$$
f(n) \le 3n^3 + 2n^3 = 5n^3
$$

Portanto:

* ( $c = 5$ )
* ( $n_0 = 1$ )

$$
f(n) \in O(n^3)
$$

---

# 4. Transitividade da notação ( O )

Suponha:

$$
f(n) \in O(g(n)) \quad \text{e} \quad g(n) \in O(h(n))
$$

Então existem constantes:

$$
c_1, c_2 > 0,\quad n_1, n_2
$$

tais que:

$$
f(n) \le c_1 g(n), \quad \forall n \ge n_1
$$

$$
g(n) \le c_2 h(n), \quad \forall n \ge n_2
$$

Para ( $n \ge \max(n_1, n_2)$ ):

$$
f(n) \le c_1 g(n) \le c_1 c_2 h(n)
$$

Logo:

$$
f(n) \in O(h(n))
$$

---

# 5. Se ( $f(n) \in O(n) ), então ( f(n)^2 \in O(n^2)$ )

Se:

$$
f(n) \le c n
$$

Então:

$$
f(n)^2 \le (c n)^2 = c^2 n^2
$$

Logo:

* ( $c' = c^2$ )

$$
f(n)^2 \in O(n^2)
$$
 
----

```lean
import Mathlib.Data.Real.Basic
import Mathlib.Tactic

open Asymptotics

-- Definição de O-grande
def bigO (f g : ℕ → ℝ) :=
  ∃ c > 0, ∃ n0, ∀ n ≥ n0, f n ≤ c * g n

-- 1)
--/
--Provar que f(n) \in O(n^2)  
--/--
theorem ex1 :
  bigO (fun n => (3/2 : ℝ)*n^2 + (7/2 : ℝ)*n - 4)
       (fun n => (n:ℝ)^2) :=
by
  use 5
  constructor
  · norm_num
  use 1
  intro n hn
  have h1 : (n:ℝ) ≤ n^2 := by
    have := hn
    nlinarith
  have : (3/2)*n^2 + (7/2)*n - 4 ≤ 5*n^2 := by
    nlinarith
  simpa using this

-- 2a)
theorem ex2a :
  bigO (fun n => (25:ℝ)*n) (fun n => (n:ℝ)^3) :=
by
  use 25
  constructor
  · norm_num
  use 1
  intro n hn
  have : (n:ℝ) ≤ n^3 := by
    nlinarith
  nlinarith

-- 3)
theorem ex3 :
  bigO (fun n => (3:ℝ)*n^3 + 2*n^2)
       (fun n => (n:ℝ)^3) :=
by
  use 5
  constructor
  · norm_num
  use 1
  intro n hn
  have : (n:ℝ)^2 ≤ n^3 := by
    nlinarith
  nlinarith

-- 4) Transitividade
theorem bigO_trans {f g h : ℕ → ℝ} :
  bigO f g → bigO g h → bigO f h :=
by
  intro hfg hgh
  rcases hfg with ⟨c1, hc1, n1, h1⟩
  rcases hgh with ⟨c2, hc2, n2, h2⟩
  use c1 * c2
  constructor
  · positivity
  use max n1 n2
  intro n hn
  have hn1 : n ≥ n1 := le_of_max_le_left hn
  have hn2 : n ≥ n2 := le_of_max_le_right hn
  have hf := h1 n hn1
  have hg := h2 n hn2
  have : f n ≤ c1 * (c2 * h n) := by
    nlinarith
  ring_nf at this
  exact this

-- 5)
theorem square_bigO {f : ℕ → ℝ} :
  bigO f (fun n => (n:ℝ)) →
  bigO (fun n => (f n)^2) (fun n => (n:ℝ)^2) :=
by
  intro hf
  rcases hf with ⟨c, hc, n0, h⟩
  use c^2
  constructor
  · positivity
  use n0
  intro n hn
  have hf := h n hn
  have : (f n)^2 ≤ (c*n)^2 := by
    have := hf
    nlinarith
  ring_nf at this
  exact this
```
