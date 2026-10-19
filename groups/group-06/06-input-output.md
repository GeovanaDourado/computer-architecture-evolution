# 6. Input and Output

## 6.1 Input Devices

## 6.2 Output Devices

## 6.3 Communication Interfaces

## 6.4 Peripheral Devices

## 6.5 Examples

## 6.6 Historical Evolution

How did I/O change over time?

## 6.7 Modern Comparison

A diferença central em relação ao I/O (Input and Output) é que a Arquitetura de Harvard clássica mantém barramentos totalmente independentes para instruções e dados, garantindo que o acesso a periféricos (via barramento de dados) nunca dispute caminho com a busca de instruções. Já a Arquitetura Harvard moderna (modificada) preserva a separação apenas no nível de cache e trata o I/O quase sempre como memória mapeada dentro do espaço de dados, compartilhando o barramento de memória principal. Assim, ambos os modelos oferecem bom desempenho para I/O, mas a Harvard clássica é mais “pura” na separação física, enquanto a moderna privilegia a flexibilidade e a compatibilidade com sistemas operacionais e carregamento dinâmico de programas.

