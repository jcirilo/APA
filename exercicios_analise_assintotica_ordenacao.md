# Análise assintótica em algorítimos de ordenação

## 1. Insertion Sort

![Insertion sort gif](https://markbowman.org/LCC/SortInsertion.gif)

Animação por [Mark M Bowman](https://markbowman.org/LCC)

### 1.1. Pseudocódigo

```py
InsertionSort(A, n)
1. pivo ← null
2. for i ← 1 to n – 1:
3.      pivo ← A[i]
4.      j ← i - 1
5.      while j ≥ 0 and A[j] > pivo:
6.          A[j+1] ← A[j]
7.          j ← j - 1
8.      A[j+1] ← pivo
9. return A
```

### 1.2. Pior caso

O array está ordenado ao contrário

#### 1.2.1. Contagem de passos

```py
InsertionSort(A, n)                     #   op  exec                                    op * exec
1. pivo ← null                          #   1   1                                       1
2. for i ← 1 to n – 1:                  #   2   n-1                                     2(n-1)
3.      pivo ← A[i]                     #   2   n-1                                     2(n-1)
4.      j ← i - 1                       #   2   n-1                                     2(n-1)
5.      while j ≥ 0 and A[j] > pivo:    #   4   (n-1)(1+n-1)/2 => (n-1)n/2 => n^2-n/2   4(n^2-n/2)
6.          A[j+1] ← A[j]               #   4   (n-1)(1+n-1)/2                          4(n^2-n/2)
7.          j ← j - 1                   #   2   (n-1)(1+n-1)/2                          2(n^2-n/2)
8.      A[j+1] ← pivo                   #   3   n-1                                     3(n-1)
9. return A                             #   1   1                                       1
```

É possível identificar que o padrão de iteração na linha 5 é de uma **progressão aritimética** $S_n=\frac{n \times (a_1+a_n)}{2}$

#### 1.2.2. Polinômio

$T_p(n) = \frac{10(n^2-n)}{2} + 9(n-1) + 1 + 1$

$T_p(n) = \frac{10n^2-10n}{2} + 9n-9+2$

$T_p(n) = 5n^2-5n + 9n-7$

$T_p(n) = 5n^2 + 4n-7$

### 1.3. Melhor caso

No melhor caso o vetor de entrada já está ordenado.

#### 1.3.1 Contagem de passos

```py
InsertionSort(A, n)                     #   op  exec    op * exec
1. pivo ← null                          #   1   1       1
2. for i ← 1 to n – 1:                  #   2   n-1     2(n-1)
3.      pivo ← A[i]                     #   2   n-1     2(n-1)
4.      j ← i - 1                       #   2   n-1     2(n-1)
5.      while j ≥ 0 and A[j] > pivo:    #   4   n-1     4(n-1)
6.          A[j+1] ← A[j]               #   4   0       0
7.          j ← j - 1                   #   2   0       0
8.      A[j+1] ← pivo                   #   3   n-1     3(n-1)
9. return A                             #   1   1       1
```

#### 1.3.2. Polinômio

$T_m(n) = 13(n-1) + 1 + 1$

$T_m(n) = 13n-13 + 2$

$T_m(n) = 13n - 11$

## 2. Selection Sort

![Selection Sort](https://markbowman.org/LCC/SortSelection.gif)

Animação por [Mark M Bowman](https://markbowman.org/LCC)

### 2.1. Pseudocódigo

```py
SelectionSort(A, n)
1. for i ← 0 to n – 2:
2.      i_min ← i
3.      for j ← i+1 to n – 1:
4.          if A[j] < A[i_min]:
5.              i_min ← j
6.      if A[i] ≠ A[i_min]:
7.          temp ← A[i]
8.          A[i] ← A[i_min]
9.          A[i_min] ← temp
10.return A
```

### 2.2. Pior Caso

Digamos que as condicionais da linha 4 e 5 sempre serão verdadeiras.

#### 2.2.1. Contagem de passos

```py
SelectionSort(A, n)                 #   op  exec            op * exec
1. for i ← 0 to n – 2:              #   2   n-1             2(n-1)
2.      i_min ← i                   #   1   n-1             1(n-1)
3.      for j ← i+1 to n – 1:       #   3   (n-1)(n-1+1)/2  3(n^2-n/2)
4.          if A[j] < A[i_min]:     #   3   (n-1)(n-1+1)/2  3(n^2-n/2)
5.              i_min ← j           #   1   (n-1)(n-1+1)/2  1(n^2-n/2)
6.      if A[i] ≠ A[i_min]:         #   3   n-1             3(n-1)
7.          temp ← A[i]             #   2   n-1             2(n-1)
8.          A[i] ← A[i_min]         #   3   n-1             3(n-1)
9.          A[i_min] ← temp         #   2   n-1             2(n-1)
10.return A                         #   1   1               1
```

#### 2.2.2. Polinômio

$T_p(n) = \frac{7(n^2-n)}{2} + 13(n-1) + 1$

$T_p(n) = \frac{7n^2-7n}{2} + 13n-13 + 1$

$T_p(n) = \frac{7n^2-7n}{2} + 13n-12$

$T_p(n) = 3.5n^2-3.5n + 13n-12$

$T_p(n) = 3.5n^2-9.5n-12$

### 2.3. Melhor Caso

O vetor já está ordenado.

#### 2.3.1. Contagem de passos

```py
SelectionSort(A, n)                 #   op  exec            op * exec
1. for i ← 0 to n – 2:              #   2   n-1             2(n-1)
2.      i_min ← i                   #   1   n-1             1(n-1)
3.      for j ← i+1 to n – 1:       #   3   (n-1)(n-1+1)/2  3(n^2-n/2)
4.          if A[j] < A[i_min]:     #   3   (n-1)(n-1+1)/2  3(n^2-n/2)
5.              i_min ← j           #   1   0               0
6.      if A[i] ≠ A[i_min]:         #   3   n-1             3(n-1)
7.          temp ← A[i]             #   2   0               0
8.          A[i] ← A[i_min]         #   3   0               0
9.          A[i_min] ← temp         #   2   0               0
10.return A                         #   1   1               1
```

#### 2.3.2. Polinômio

$T_m(n) = \frac{6(n^2-n)}{2} + 6(n-1) + 1$

$T_m(n) = \frac{6n^2-6n}{2} + 6n-6 + 1$

$T_m(n) = 3n^2-3n + 6n-5$

$T_m(n) = 3n^2+3n-5$
