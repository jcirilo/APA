# APA

Repositório para o curso de Análise e Projeto de Algorítmos 2024.2 da @UFPB

## Índices

1. [Análise Assintótica - Exercicios](#análise-assintótica---exercicios)
   1. [Busca Sequencial](#1-busca-sequencial)
   1. [Conta Ocorrências](#2-conta-ocorrências)
   1. [Maior Elemento](#3-maior-elemento)
   1. [Fibonacci Iterativo](#4-fibonacci-iterativo)
   1. [Insertion Sort](#5-insertion-sort)
   1. [Selection Sort](#6-selection-sort)

## Análise Assintótica - Exercicios

### Consderações

Para as análises considerarei como operações básicas:

- Expressões de avaliação
- Atribuições de valores a variáveis
- Indexação de um array
- Retorno de funções

---

### 1. Busca Sequencial

#### 1.1. Pseudocódigo

```py
buscaSequencial(x, A)
1. i = 0
2. while i <= n and A[i] != x:
3.   i = i+1
4. if i > n:
5.   return -1
6. return i
```

#### 1.2. Pior caso

No pior caso o elemento buscado não está no array

##### 1.2.1. Contagem de passos

```py
buscaSequencial(x, A)           #   op  exec    op * exec
1. i = 0                        #   1   1       1
2. while i <= n and A[i] != x:  #   4   n       4n
3.   i = i+1                    #   2   n       2n
4. if i > n:                    #   1   1       1
5.   return -1                  #   1   1       1
6. return i                     #   1   0       0
```

##### 1.2.2. Polinômio

$T_p(n) = 4n + 2n + 1 + 1 + 1 + 0$

$T_p(n) = 6n + 3$

#### 1.3. Melhor caso

No melhor caso o elemento que buscamos está no primeiro índice do array de entrada.

##### 1.3.1. Contagem de passos

```py
buscaSequencial(x, A)           #   op  exec    op * exec
1. i = 0                        #   1   1       1
2. while i <= n and A[i] != x:  #   4   1       4
3.   i = i+1                    #   2   0       0
4. if i > n:                    #   1   1       1
5.   return -1                  #   1   0       0
6. return i                     #   1   1       1
```

##### 1.3.2. Polinômio

$T_m(n) = 1 + 4 + 1 + 1$

$T_m(n) = 7$

---

### 2. Conta Ocorrências

#### 2.1. Pseudocódigo

```py
contaOcorrencias(x, A, n)
1.  cont = 0
2.  for i = 0 to n-1:
3.      if A[i] == x:
4.          cont++
5.  return cont
```

#### 2.2. Pior caso

No pior caso, todos os elementos do array são iguais a x.

##### 2.2.1. Contagem de passso

```py
contaOcorrencias(x, A, n)   #   op  exec    op * exec
1.  cont = 0                #   1   1       1
2.  for i = 0 to n-1:       #   3   n       3n
3.      if A[i] == x:       #   2   n       2n
4.          cont++          #   1   n       n
5.  return cont             #   1   1       1
```

##### 2.2.2. Polinômio

$T_p(n) = 3n+2n+n+1+1$

$T_p(n) = 6n+2$

#### 2.3. Melhor caso

No melhor caso o elemento que queremos contar não está no array.

##### 2.3.1. Contagem de passos

```py
contaOcorrencias(x, A, n)   #   op  exec    op * exec
1.  cont = 0                #   1   1       1
2.  for i = 0 to n-1:       #   3   n       3n
3.      if A[i] == x:       #   2   n       2n
4.          cont++          #   1   0       0
5.  return cont             #   1   1       1
```

##### 2.3.2. Polinômio

$T_m(n)=3n+2n+1+1$

$T_m(n)=5n+2$

---

### 3. Maior Elemento

#### 3.1. Pseudocódigo

```py
ArrayMax(A, n)
1. currentMax = A[0]
2.  for i = 1 to n − 1:
3.      if A[i] > currentMax:
4.          currentMax = A[i]
5.      i++
6. return currentMax
```

#### 3.2. Pior caso

No pior caso o maior elemento está no final do array.

##### 3.2.1. Contagem de Passso

```py
ArrayMax(A, n)                      #   op  exec    op * exec
1. currentMax = A[0]                #   2   1       2
2.  for i = 1 to n − 1:             #   2   n-1     2n-2
3.      if A[i] > currentMax:       #   2   n-1     2n-2
4.          currentMax = A[i]       #   2   n-1     2n-2
5.      i++                         #   1   n-1     n-1
6. return currentMax                #   1   1       1
```

##### 3.2.2. Polinômio

$T_p(n) =2n+2n+2n+n+2+1-2-2-2-1$

$T_p(n) =7n+3-7$

$T_p(n) =7n-4$

#### 3.3. Melhor caso

No melhor caso o maior elemento é o primeiro ou todos são iguais.

##### 3.3.1. Contagem de passos

```py
ArrayMax(A, n)                      #   op  exec    op * exec
1. currentMax = A[0]                #   2   1       2
2.  for i = 1 to n − 1:             #   2   n-1     2n-2
3.      if A[i] > currentMax:       #   2   n-1     2n-2
4.          currentMax = A[i]       #   2   0       0
5.      i++                         #   1   n-1     n-1
6. return currentMax                #   1   1       1
```

##### 3.3.2. Polinômio

$T_m(n) =2n+2n+n+2+1-2-2-1$

$T_m(n) =5n+3-5$

$T_m(n) =5n-2$

---

### 4. Fibonacci Iterativo

#### 4.1. Pseudocódigo

```py
fibonacci2(n)
1. if n = 0
2.      return 0
3. crie um vetor f[0...n]
4. f[0] = 0
5. f[1] = 1
6. for i = 2...n:
7.      f[i] = f[i-1] + f[i-2]
8. return f[n]
```

#### 4.2. Pior caso

No pior caso, n > 0

##### 4.2.1. Contagem de passos

```py
fibonacci2(n)                       #   op  exec    op * exec
1. if n = 0                         #   1   1       1   
2.      return 0                    #   1   0       0
3. crie um vetor f[0...n]           #   n   1       n
4. f[0] = 0                         #   2   1       2
5. f[1] = 1                         #   2   1       2
6. for i = 2...n:                   #   2   n-2     2n-4
7.      f[i] = f[i-1] + f[i-2]      #   7   n-2     7n-14
8. return f[n]                      #   2   1       2
```

##### 4.2.2. Polinômio

$T_p(n) = 7n+2n+n+1+0+2+2+2-4-14$

$T_p(n) = 10n+7-18$

$T_p(n) = 10n-11$

#### 4.3. Melhor caso

No melhor caso, n = 0

##### 4.3.1. Contagem de passos

```py
fibonacci2(n)                       #   op  exec    op * exec
1. if n = 0                         #   1   1       1   
2.      return 0                    #   1   1       1
3. crie um vetor f[0...n]           #   n   0       0
4. f[0] = 0                         #   2   0       0
5. f[1] = 1                         #   2   0       0
6. for i = 2...n:                   #   2   0       0
7.      f[i] = f[i-1] + f[i-2]      #   7   0       0
8. return f[n]                      #   2   0       0
```

##### 4.3.2. Polinômio

$T_m(n) = 1+1$

$T_m(n) = 2$

---

### 5. Insertion Sort

![Insertion sort gif](https://markbowman.org/LCC/SortInsertion.gif)

Animação por [Mark M Bowman](https://markbowman.org/LCC)

#### 5.1. Pseudocódigo

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

#### 5.2. Pior caso

O array está ordenado ao contrário

##### 5.2.1. Contagem de passos

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

##### 5.2.2. Polinômio

$T_p(n) = \frac{10(n^2-n)}{2} + 9(n-1) + 1 + 1$

$T_p(n) = \frac{10n^2-10n}{2} + 9n-9+2$

$T_p(n) = 5n^2-5n + 9n-7$

$T_p(n) = 5n^2 + 4n-7$

#### 5.3. Melhor caso

No melhor caso o vetor de entrada já está ordenado.

##### 5.3.1 Contagem de passos

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

##### 5.3.2. Polinômio

$T_m(n) = 13(n-1) + 1 + 1$

$T_m(n) = 13n-13 + 2$

$T_m(n) = 13n - 11$

---

### 6. Selection Sort

![Selection Sort](https://markbowman.org/LCC/SortSelection.gif)

Animação por [Mark M Bowman](https://markbowman.org/LCC)

#### 6.1. Pseudocódigo

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

#### 6.2. Pior Caso

Digamos que as condicionais da linha 4 e 5 sempre serão verdadeiras.

##### 6.2.1. Contagem de passos

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

##### 6.2.2. Polinômio

$T_p(n) = \frac{7(n^2-n)}{2} + 13(n-1) + 1$

$T_p(n) = \frac{7n^2-7n}{2} + 13n-13 + 1$

$T_p(n) = \frac{7n^2-7n}{2} + 13n-12$

$T_p(n) = 3.5n^2-3.5n + 13n-12$

$T_p(n) = 3.5n^2-9.5n-12$

#### 6.3. Melhor Caso

O vetor já está ordenado.

##### 6.3.1. Contagem de passos

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

##### 6.3.2. Polinômio

$T_m(n) = \frac{6(n^2-n)}{2} + 6(n-1) + 1$

$T_m(n) = \frac{6n^2-6n}{2} + 6n-6 + 1$

$T_m(n) = 3n^2-3n + 6n-5$

$T_m(n) = 3n^2+3n-5$
