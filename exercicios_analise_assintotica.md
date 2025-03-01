# Análise assintótica

## Consderações

Para as análises considerarei como operações básicas:

- Expressões de avaliação
- Atribuições de valores a variáveis
- Indexação de um array
- Retorno de funções

## 1. Busca Sequencial

### 1.1. Pseudocódigo

```py
buscaSequencial(x, A)
1. i = 0
2. while i <= n and A[i] != x:
3.   i = i+1
4. if i > n:
5.   return -1
6. return i
```

### 1.2. Pior caso

No pior caso o elemento buscado não está no array

#### 1.2.1. Contagem de passos

```py
buscaSequencial(x, A)           #   op  exec    op * exec
1. i = 0                        #   1   1       1
2. while i <= n and A[i] != x:  #   4   n       4n
3.   i = i+1                    #   2   n       2n
4. if i > n:                    #   1   1       1
5.   return -1                  #   1   1       1
6. return i                     #   1   0       0
```

#### 1.2.2. Polinômio

$T_p(n) = 4n + 2n + 1 + 1 + 1 + 0$

$T_p(n) = 6n + 3$

### 1.3. Melhor caso

No melhor caso o elemento que buscamos está no primeiro índice do array de entrada.

#### 1.3.1. Contagem de passos

```py
buscaSequencial(x, A)           #   op  exec    op * exec
1. i = 0                        #   1   1       1
2. while i <= n and A[i] != x:  #   4   1       4
3.   i = i+1                    #   2   0       0
4. if i > n:                    #   1   1       1
5.   return -1                  #   1   0       0
6. return i                     #   1   1       1
```

#### 1.3.2. Polinômio

$T_m(n) = 1 + 4 + 1 + 1$

$T_m(n) = 7$

## 2. Conta Ocorrências

### 2.1. Pseudocódigo

```py
contaOcorrencias(x, A, n)
1.  cont = 0
2.  for i = 0 to n-1:
3.      if A[i] == x:
4.          cont++
5.  return cont
```

### 2.2. Pior caso

No pior caso, todos os elementos do array são iguais a x.

#### 2.2.1. Contagem de passso

```py
contaOcorrencias(x, A, n)   #   op  exec    op * exec
1.  cont = 0                #   1   1       1
2.  for i = 0 to n-1:       #   3   n       3n
3.      if A[i] == x:       #   2   n       2n
4.          cont++          #   1   n       n
5.  return cont             #   1   1       1
```

#### 2.2.2. Polinômio

$T_p(n) = 3n+2n+n+1+1$

$T_p(n) = 6n+2$

### 2.3. Melhor caso

No melhor caso o elemento que queremos contar não está no array.

#### 2.3.1. Contagem de passos

```py
contaOcorrencias(x, A, n)   #   op  exec    op * exec
1.  cont = 0                #   1   1       1
2.  for i = 0 to n-1:       #   3   n       3n
3.      if A[i] == x:       #   2   n       2n
4.          cont++          #   1   0       0
5.  return cont             #   1   1       1
```

#### 2.3.2. Polinômio

$T_m(n)=3n+2n+1+1$

$T_m(n)=5n+2$

## 3. Maior Elemento

### 3.1. Pseudocódigo

```py
ArrayMax(A, n)
1. currentMax = A[0]
2.  for i = 1 to n − 1:
3.      if A[i] > currentMax:
4.          currentMax = A[i]
5.      i++
6. return currentMax
```

### 3.2. Pior caso

No pior caso o maior elemento está no final do array.

#### 3.2.1. Contagem de Passso

```py
ArrayMax(A, n)                      #   op  exec    op * exec
1. currentMax = A[0]                #   2   1       2
2.  for i = 1 to n − 1:             #   2   n-1     2n-2
3.      if A[i] > currentMax:       #   2   n-1     2n-2
4.          currentMax = A[i]       #   2   n-1     2n-2
5.      i++                         #   1   n-1     n-1
6. return currentMax                #   1   1       1
```

#### 3.2.2. Polinômio

$T_p(n) =2n+2n+2n+n+2+1-2-2-2-1$

$T_p(n) =7n+3-7$

$T_p(n) =7n-4$

### 3.3. Melhor caso

No melhor caso o maior elemento é o primeiro ou todos são iguais.

#### 3.3.1. Contagem de passos

```py
ArrayMax(A, n)                      #   op  exec    op * exec
1. currentMax = A[0]                #   2   1       2
2.  for i = 1 to n − 1:             #   2   n-1     2n-2
3.      if A[i] > currentMax:       #   2   n-1     2n-2
4.          currentMax = A[i]       #   2   0       0
5.      i++                         #   1   n-1     n-1
6. return currentMax                #   1   1       1
```

#### 3.3.2. Polinômio

$T_m(n) =2n+2n+n+2+1-2-2-1$

$T_m(n) =5n+3-5$

$T_m(n) =5n-2$

## 4. Fibonacci Iterativo

### 4.1. Pseudocódigo

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

### 4.2. Pior caso

No pior caso, n > 0

#### 4.2.1. Contagem de passos

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

#### 4.2.2. Polinômio

$T_p(n) = 7n+2n+n+1+0+2+2+2-4-14$

$T_p(n) = 10n+7-18$

$T_p(n) = 10n-11$

### 4.3. Melhor caso

No melhor caso, n = 0

#### 4.3.1. Contagem de passos

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

#### 4.3.2. Polinômio

$T_m(n) = 1+1$

$T_m(n) = 2$
