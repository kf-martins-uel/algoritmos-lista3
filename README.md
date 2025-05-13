# Lista de Exercícios 3 - Algoritmos

- Curso: Ciência de Dados e IA
- Professor: Anderson
- Aluno: Kauã Felipe Martins
- Data: 13/05/2025

---

## Exercício 1

Escreva um programa que leia n números reais e calcule o desvio padrão destes valores. O desvio padrão é dado pela seguinte equação: $s = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (x_i - \overline{x})^2}$, onde $n$ é a quantidade de números, $x_i$ é o i-ésimo valor e $\overline{x}$ é a média dos valores.

- Código do programa:

```python
print("Digite um conujunto de valores reais separados por espaço (enter para terminar)")
n = [float(i) for i in input().split()]
s = (sum([(i-sum(n)/len(n))**2 for i in n])/(len(n)-1))**(1/2)
print(f"O desvio padrão do conjunto é: {s: .2f}")
```

- Saída:

```plaintext
Digite um conujunto de valores reais separados por espaço (enter para terminar)
10 5
O desvio padrão do conjunto é:  3.54
```

---

## Exercício 2

Mostre o que o programa abaixo irá imprimir caso seja executado (execute o programa a mão, sem usar o interpretador Python).

```python
v1 = []
v2 = []
n = 123456789  
while n != 0:
    v1 . append ( n % 10)
    n = n // 10
    v2 . append (1)

for a in v1 [: -1]:
    print (a , end = ", ")
print ( v1 [ -1])

for a in v2 [: -1]:
    print (a , end = ", ")
print ( v2 [ -1])

for i in range (len ( v1 ) ) :
    for j in range ( v1 [ i ]) :
        v2 [ i ] = 2 * v2 [ i ]

for a in v2 :
    print (a , end = ", ")
print (1)
```

- Duas listas (v1 e v2) vazias
- Uma variável n com valor de 123456789
- Primeiro while:
  - Enquanto n for difernete de zero, adicionar na lista v1 o resto de da divisão de n po 10 (Um valor entre 0 e 9)
    - 123456789 % 10 = 9
  - n passa a ser o valor inteiro de n dividido por 10
    - 123456789 / 10 = 12345678.9
    - 123456789 // 10 = 12345678
  - adiciona 1 em v2 em todas iterações
- Primeiro for iterando sobre de v1 menos o último elemento:
  - imprimir na tela cada valor separado por vírgulas
- Imprimir o último elemento de v1
- Segundo for iterado em v2 menos o último elemento:
  - Sabendo que a lista dois inteira possui apenas 1, imprimá 8 vezes o número 1, separado por vírgulas
- Imprimir o último valor de v2, que é 1
- Terceiro for iterado em i em um intervalo no tamanho de v1 (v1 tem 9 de tamanho, for ira de 0 até 8):
  - Outro for iterando em j de em um intervalo no tamanho do elemento i de v1:
    - Elemento i de v2 = 2 * elemento i de v2
      - Primeira vez, i = 0, j de 0 até 8 (9 vezes):
        - v2[0] = 1*2 = 2
        - v2[0] = 2*2 = 4
        - v2[0] = 4*2 = 8
        - ...
        - v2[0] = 256*2 = 512
      - Segunda vez, i = 1, j de 0 até 7 (8 vezes):
        - v2[1] = 2*2 = 4
        - ...
        - v2[1] = 128*2 = 256
    - O que acontece: Todos elemento são múltiplicado por 2 uma x quantidade de vezes no qual x é igual ao elemento i de v1. Ou seja, estamos falando de 2^v1[i], em que i vai de 9 até 1. Por fim, quando chegar no último elemento de v1 que é 1, o range(1) é igual à 0 e for não itera em 0, fazendo com que o último elemento de v2 continue sendo 2.
- Último for:
  - Imprimir todos elementos de v2
- Imprimir 1
- saída esperada:

```plaintext
9, 8, 7, 6, 5, 4, 3, 2, 1
1, 1, 1, 1, 1, 1, 1, 1, 1
512, 256, 128, 64, 32, 16, 8, 4, 2, 1
```

---

## Exercício 3

Escreva um programa que leia duas sequências de n e m valores inteiros, onde n ≤ m, e imprima quantas vezes a primeira sequência ocorre na segunda.  
Exemplo:  
Primeira sequência: 1 0 1  
Segunda sequência: 1 1 0 1 0 1 0 0 1 1 0 1 0  
Resultado: 3

- Código do programa:

```python
n = [int(i) for i in input().split()]
m = [int(i) for i in input().split()]
seq = 0
for i in range(len(m)-len(n)+1):
    if m[i:i+len(n)] == n:
        seq+=1
print(seq)
```

- Saída:

```plaintext
1 2 3
1 2 3 1 2 3 3 4 1 2 3
3
```

---

## Exercício 4

Faça um programa que leia dois conjuntos de números inteiros distintos e imprima a interseção destes dois conjuntos (os números presentes em ambos os conjuntos).  
Exemplo:  
Primeiro conjunto: 1 2 3 4 5  
Segundo conjunto: 2 5 7 1 9 18  
Resultado: 1 2 5

- Código do programa, solução 1:

```python
n = set([int(i) for i in input().split()])
m = set([int(i) for i in input().split()])

print(n.intersection(m))
```

- Saída:

```plaintext
1 2 3 4 5
4 5 6 7 8
{4, 5}
```

- Código do programa, solução 2:

```python
# Usar set apenas para garantir que não tenha valores iguais repetidos
# Se não teria mais um passo para fazer remover os repetidos
n = list(set([int(i) for i in input().split()]))
m = list(set([int(i) for i in input().split()]))
res = []
for i in range(min(len(n), len(m))):
    if n > m:
        if n[i] in m:
            res.append(n[i])
    else:
        if m[i] in n:
            res.append(m[i])
for i in res:
    print(i, end=' ')
```

- Saída:

```plaintext
1 2 3 4 5
4 5 6 7 8
4 5
```

---

## Exercício 5

Faça um programa que leia dois conjuntos de números inteiros distintos e imprima a união destes conjuntos (os números presentes em pelo menos um dos conjuntos).  
Exemplo:  
Primeira conjunto: 1 2 3 4 5  
Segundo conjunto: 2 5 7 1 9 18  
Resultado: 1 2 3 4 5 7 9

- Código do programa:

```python
n = set([int(i) for i in input().split()])
m = set([int(i) for i in input().split()])
print(n.union(m))
```

- Saída:

```plaintext
1 2 3 4
1 4 5 6
{1, 2, 3, 4, 5, 6}
```

---

## Exercício 6

Faça um programa que leia duas sequências de números inteiros ordenados e imprima uma sequência com os números ordenados das duas sequências anteriores. Você não deve usar o método sort.  
Exemplo:
Primeira sequência: 1 3 5 5 7 9 10  
Segunda sequência: 2 2 4 6 8 8 10  
Resultado: 1 2 2 3 4 5 5 6 7 8 8 9 10 10  

- Código do programa:

- Solução supondo que as listas realmente estarão ordenadas:

```python
s1 = [int(i) for i in input().split()]
s2 = [int(i) for i in input().split()]

res = []
i, j = 0, 0

while i < len(s1) and j < len(s2):
    if s1[i] < s2[j]:
        res.append(s1[i])
        i += 1
    else:
        res.append(s2[j])
        j += 1

res.extend(s1[i:])
res.extend(s2[j:])

print(res)
```

- Saída:

```plaintext
1 1 1 2 2 3 4 5 5 6
3 3 3 4 4 5
[1, 1, 1, 2, 2, 3, 3, 3, 3, 4, 4, 4, 5, 5, 5, 6]
```

- Solução supondo que as listas não estarão ordenadas:

```python
s1 = [int(i) for i in input().split()]
s2 = [int(i) for i in input().split()]

res = s1+s2

for i in range(len(res)):
    for j in range(i, len(res)-1):
        if res[i] > res[j]:
            res[i], res[j] = res[j], res[i]

print(res)
```

- Saída:

```plaintext
1 3 5 5 7 9 10 
2 2 4 6 8 8 10 
[1, 2, 2, 3, 4, 5, 5, 6, 7, 8, 8, 9, 10, 10]
```

---

## Exercício 7

Faça um programa que calcule o produto interno de dois vetores u e v de mesmo tamanho n. O programa deve ler primeiramente o valor de n e em seguida deve ler duas sequências de mesmo tamanho de números reais e salvar cada sequência em uma lista. O programa deve então calcular e imprimir o produto interno dos vetores lidos.  

- Código do programa:

```python
v, u = [],[]
n = int(input())
# v = [int(i) for i in input().split()]
# u = [int(i) for i in input().split()]
# if len(v) > n or len(u) > n:
#     print(f'Tamanho das listas diferente de {n}')
#     exit(1)
i=0
while i<n:
    v.append(int(input()))
    i+=1
i=0
while i<n:
    u.append(int(input()))
    i+=1

print([v[i]*u[i] for i in range(n)])
```

- Saída:

```plaintext
3
2
2
2
1
2
3
[2, 4, 6] 
```

---

## Exercício 8

Escreva um programa que leia uma sequência de números inteiros e os salve em uma lista. Em seguida o programa deve ler um outro número inteiro C. O programa deve então encontrar dois números de posições distintas da lista cuja multiplicação seja C e imprimí-los. Caso não existam tais números, o programa deve imprimir uma mensagem correspondente.  
Exemplo:  
Lista = [2, 4, 5, 10, 7]  
C = 35  
Resultado: 5 e 7  
Lista = [2, 4, 5, 10, 7]  
C = 25  
Resultado: não existem tais números  

- Código do programa:

```python
lista = [int(i) for i in input().split()]
c = int(input())
res = {}

for i in lista:
    target = c / i
    if target in lista and target not in res:
        res[i] = int(target)
        print(f'{i} e {res[i]}')
if not res:
    print('não existem tais números')
```

- Saída 1:

```plaintext
2 4 5 10 7
20
2 e 10
4 e 5
```

- Saída 2:

```plaintext
4 2 1
9
não existem tais números
```

---

## Exercício 9

Escreva um programa que leia uma sequência de n números inteiros positivos maiores que
1 e os salve em uma lista v.  
O programa deve então imprimir um quadrado de n linhas por n colunas onde em cada posição (i, j), com i, j ∈ {0, . . . , n − 1}, deste quadrado deverá ser impresso 1 caso os números v[i] e v[j] sejam coprimos, e 0 caso contrário.  
Os pares de números v[i] e v[j] são coprimos se não há nenhum divisor d > 1 que seja
comum a ambos. Por exemplo 15 e 8 são coprimos, pois os divisores de 8, que são 2, 4 e 8,
não são divisores de 15. Abaixo temos um exemplo de execução do programa para n = 6
e v = [2, 3, 4, 5, 6, 7].  

|          | v[0] | v[1] | v[2] | v[3] | v[4] | v[5] |
|----------|------|------|------|------|------|------|
| **v[0]** | 0    | 1    | 0    | 1    | 0    | 1    |
| **v[1]** | 1    | 0    | 1    | 1    | 0    | 1    |
| **v[2]** | 0    | 1    | 0    | 1    | 0    | 1    |
| **v[3]** | 1    | 1    | 1    | 0    | 1    | 1    |
| **v[4]** | 0    | 0    | 0    | 1    | 0    | 1    |
| **v[5]** | 1    | 1    | 1    | 1    | 1    | 0    |  

Note no exemplo que v[0] = 2 é coprimo de v[1] = 3, v[3] = 5 e v[5] = 7.  

- Código do programa:

```python
v = [int(i) for i in input().split()]
coprimos: dict[int, list[int]] = {}

for i in v:
    for j in v:
        a, b = i, j
        while b != 0:
            a, b = b, a%b
        if a == 1:
            coprimos[i] = coprimos.get(i, []) + [1]
        else:
            coprimos[i] = coprimos.get(i, []) + [0]

print(f'{'':^5}', end=' ')
for i in range(len(v)):
    print(f'{f'v[{i}]':^5}', end='  ')
print()
for i, values in enumerate(v):
    print(f'v[{i}]', end='  ')
    for valor in coprimos[values]:
        print(f'{valor:^5}', end='  ')
    print()
```

- Saída:

```plaintext
4 5 8 15

      v[0]   v[1]   v[2]   v[3]   
v[0]    0      1      0      1    
v[1]    1      0      1      0    
v[2]    0      1      0      1    
v[3]    1      0      1      0   
```

---
