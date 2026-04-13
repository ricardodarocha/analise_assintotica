# Análise assintótica

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
