# 6. Operações de E/S (Entradas e Saídas)

## 6.1 Escopo da entrada e relação com Harvard
A Arquitetura de Harvard é um modelo de organização de computadores caracterizado pela separação entre as instruções de um programa e os dados utilizados durante sua execução. Essa separação permite que instruções e dados sejam armazenados em estruturas distintas e, nas implementações modernas, tenham caminhos de acesso independentes. Para compreender sua origem histórica, é importante conhecer o computador Harvard Mark I, desenvolvido por Howard Aiken em colaboração com a IBM e instalado na Universidade Harvard em 1944. O Mark I utilizava mecanismos físicos diferentes para fornecer instruções e dados à máquina. As instruções eram lidas por meio de uma fita de papel perfurada, enquanto os dados podiam ser introduzidos por cartões perfurados, fitas específicas ou interruptores para a configuração de valores numéricos. Dessa forma, a separação entre instruções e dados não dependia simplesmente dos periféricos de entrada, mas da maneira como a máquina organizava e processava cada tipo de informação. É importante destacar que a denominação Arquitetura de Harvard foi consolidada posteriormente e que a classificação histórica do Mark I como exemplo dessa arquitetura é discutida por pesquisadores.

## 6.2 Entrada do programa
No contexto da Arquitetura de Harvard, a entrada do programa corresponde ao processo de fornecer à máquina as instruções que determinam quais operações devem ser executadas e em que sequência. No Harvard Mark I, esse processo começava com a preparação do programa pelos programadores, que precisavam transformar um problema matemático em uma sequência de instruções compatíveis com as operações da máquina. Depois, essas instruções eram codificadas em uma fita de papel perfurada. O mecanismo de controle de sequência realizava a leitura da fita, uma linha de cada vez, e acionava a operação correspondente. Após executar uma instrução, o sistema avançava para a seguinte, respeitando a sequência estabelecida. Diferentemente dos computadores modernos que armazenam programas em memórias eletrônicas, o Mark I recebia suas instruções por meio desse suporte físico externo. A fita podia ser preparada, corrigida e reutilizada, e sequências de instruções podiam ser armazenadas para resolver outros problemas. Esse método demonstra como as instruções eram representadas e fornecidas separadamente dos dados utilizados nos cálculos.

## 6.3 Interfaces de Comunicação

## 6.4 Dispositivos Periféricos

## 6.5 Exemplos

## 6.6 Histórico de Evolução

Como as E/S mudaram durante o tempo?

## 6.7 Comparação Moderna

A diferença central em relação a E/S é que a Arquitetura de Harvard clássica mantém barramentos totalmente independentes para instruções e dados, garantindo que o acesso a periféricos (via barramento de dados) nunca dispute caminho com a busca de instruções. Já a Arquitetura Harvard moderna (modificada) preserva a separação apenas no nível de cache e trata a E/S quase sempre como memória mapeada dentro do espaço de dados, compartilhando o barramento de memória principal. Assim, ambos os modelos oferecem bom desempenho para E/S, mas a Harvard clássica é mais “pura” na separação física, enquanto a moderna privilegia a flexibilidade e a compatibilidade com sistemas operacionais e carregamento dinâmico de programas.


