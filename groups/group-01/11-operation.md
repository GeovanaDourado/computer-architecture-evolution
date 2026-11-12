# 11. Operation

## 11.1 Input
- Quais são as informações introduzidas no sistema 

## 11.2 Configuration
- Como o sistema está configurado nessa operação

## 11.3 Components
- Quais componentes participam da operação

## 11.4 Routing
- Como as informações circulam pelo sistema durante a operação

## 11.5 Operations
- Quais operações são realizadas durante a operação principal

Durante a operação principal (computing run ou main operation), o ENIAC executava o algoritmo previamente cablado por meio da propagação sincronizada de pulsos elétricos pelas unidades funcionais ativas. Como a máquina não possuía uma memória central para buscar instruções sequencialmente, a operação principal consiste em uma reação em cadeia controlada, na qual cada módulo recebe um pulso de ativação, realiza sua tarefa dentro do ritmo fixo de 200 microssegundos (1 tempo de adição da Cycling Unit) e emite um sinal de conclusão para engatilhar a etapa seguinte.

 As operações realizadas durante o ciclo ativo dividem-se em cinco frentes principais:

### 11.5.1 Operações Aritméticas Básicas e Compostas

Os módulos matemáticos atuam diretamente sobre palavras decimais de 10 dígitos com sinal:

#### 11.5.1.1 Adição e Subtração 

Executadas pelos 20 Acumuladores em exatamente 1 tempo de adição (200 µs). A soma ocorre pelo avanço direto dos anéis de flip-flops (com propagação de carry na janela de 70 µs), enquanto a subtração é realizada pela adição do complemento de 10, utilizando as saídas complementares (S) e o pulso 1'P 

#### 11.5.1.2 Multiplicação

Realizada pelo High-Speed Multiplier em conjunto com acumuladores de apoio. Utilizando sua matriz física de resistores (tabuada eletrônica), a unidade gera produtos parciais de dezenas e unidades que são somados posteriormente, consumindo em torno de 14 tempos de adição (2,8 ms) para operandos de 10 dígitos.

#### 11.5.1.3 Divisão e Extração de Raiz Quadrada

Executadas de forma iterativa pelo Divider & Square-Rooter sobre um conjunto de cinco acumuladores acoplados. Por meio de subtrações e adições sucessivas com testes de sinal e deslocamentos de casa decimal (shifts), essas operações demandam entre 125 e 140 tempos de adição (cerca de 25 a 28 ms) [6, 8].

### 11.5.2 Consulta de Tabelas e Injeção de Constantes

Para alimentar as equações com valores pré-definidos sem precisar calculá-los em tempo real se usava:

#### 11.5.2.1 Leitura de Tabelas de Funções (Function Tables)

O sistema envia um argumento de dois dígitos para uma tabela configurada manualmente via chaves rotativas, recuperando valores de funções complexas ou empíricas (como senos, cossenos ou coeficientes balísticos) em 1 tempo de adição.

#### 11.5.2.2 Transmissão de Constantes (Constant Transmitter)

Libera parâmetros fixos ou dados lidos previamente dos cartões de entrada diretamente para os barramentos de dígitos nos momentos exigidos pelo fluxo do algoritmo.

### 11.5.3 Transferência de Dados e Limpeza de Registradores

A movimentação interna de operandos ocorre em paralelo em todas as 10 casas decimais simultaneamente,assim era necessário que houvesse:

#### 11.5.3.1 Transmissão Não-Destrutiva

O acumulador transmissor recebe o trem de pulsos 10P, girando seus anéis decádicos por uma volta completa de 10 passos. Isso envia o número pelas Digit Trunks sem apagar o valor originalmente armazenado.

#### 11.5.3.2 Limpeza (Clear)

Caso o algoritmo precise reutilizar um acumulador para um novo cálculo na iteração seguinte, a chave de controle local aciona a rotina de limpeza ao final do ciclo de 200 µs, zerando os flip-flops.

### 11.5.4 Controle de Fluxo, Loops e Ramificação Condicional

O sequenciamento lógico do programa é gerenciado dinamicamente durante a execução sem intervenção humana utilizando de lógicas como:

#### 11.5.4.1 Controle de Iterações (Loops)

O Master Programmer utiliza seus counters (contadores de década) e steppers (seletores de etapas) para repetir blocos inteiros de operações um número pré-determinado de vezes, redirecionando os pulsos de programa de volta ao início da sub-rotina até atingir a contagem configurada.

#### 11.5.4.2 Ramificação Condicional (Conditional Branching): 

O fluxo de execução pode alterar sua rota lógica testando se o sinal é positivo negativo, ou mesmo usando o valor de um dígito específico em um acumulador, desviando o pulso de programa para caminhos físicos distintos conforme o resultado parcial obtido.

### 11.5.5 Sincronização de Paralelismo (Dummy Programs)

Como o ENIAC permite executar múltiplas operações simultaneamente em painéis distintos, tarefas de durações diferentes precisam ser realinhadas antes que seus resultados sejam combinados. Para isso, acumuladores ociosos são acionados como programas fictícios (Dummy Programs), consumindo ciclos em branco para reter o pulso de uma operação rápida (como uma adição de 1 ciclo) até que uma operação lenta (como uma raiz quadrada de 140 ciclos) seja concluída.

## 11.6 Output
A saída do ENIAC, ou Output, é a informação gerada pelo computador sendo transmitida para o usuário. Nos computadores modernos, o Output pode ser feito pelo monitor ou por uma impressora, por exemplo. Já no ENIAC, a saída era feita de maneira física, por cartões perfurados.

O processo do ENIAC era dividido em 3 etapas:
1. Processamento de informações, onde o computador realizava as operações matemáticas.
2. Registro físico, onde a informação era repassada para a Punch Card Machine, que perfurava os cartões para representar os valores numéricos.
3. Apresentação dos resultados, onde uma tabuladora lia o cartão perfurado de saída e traduzia os valores em papel.

> Obs.: Esse processo dividido em 3 etapas era importante, pois permitia que o ENIAC continuasse processando informações e executando operações enquanto registrava a saída (output) de outros dados.

### 11.6.1 Cartões Perfurados
Os cartões perfurados eram feitos de papel-cartão rígido com 80 colunas. Cada coluna continha 12 posições de perfuração e as linhas eram nomeadas em:
12, 11, 0, 1, 2, 3, 4, 5, 6, 7, 8 e 9

Assim, se fôssemos representar o valor 415, utilizaríamos 3 colunas com perfurações nas linhas 4, 1 e 5, respectivamente. 

Ademais, não era o próprio ENIAC que perfurava os cartões de saída, mas sim o equipamento de perfuração de cartões da IBM, conhecido como Summary Punch.

O passo a passo da impressão da saída era a seguinte:
1. O ENIAC realizava a operação e guardava os resultados nos acumuladores.
2. Uma unidade chamada Printer recebia a informação dos resultados que serão enviados para a saída.
3. A Printer enviava esses dados para um relés eletromecânico que armazenava os dados e enviava os sinais para a IBM Summary Punch.
4. A IBM Summary Punch fazia as perfurações no cartão, com os dados que a foram enviados.
5. O cartão era enviado para a pilha de saída, onde era lido, armazenado ou recolocado à entrada (input) do ENIAC para dar início à novas operações.

> Obs.: A Printer, apesar de ser traduzida "impressora", não imprimia nada. Essa unidade, na verdade, preparava os dados para saída e controlava o equipamento externo de perfuração.

### 11.6.2 Principais limitações
Como limitações da saída do ENIAC, podemos citar diversos fatores, tais quais:
1. Velocidade eletromecânica. Apesar do processamento do ENIAC ser extremamente rápido, a perfuração dos cartões era muito mais lenta.
2. Capacidade de armazenamento. Os cartões continham número limitado de valores que podiam armazenar, gerando diversas pilhas de cartões para algumas operações.
3. Dependência de equipamentos externos. A impressão dos resultados exigia uma máquina tabuladora separada.
4. Organização manual. Devido à saída física, é necessário o manejo de pilhas de cartões perfurados, o transporte e a organização em ordem adequada.
5. Ausência de visualização moderna, como um monitor ou tela, que mostrasse o resultado imediatamente.

> Obs.: Enquanto o ENIAC conseguia executar 5.000 adições por segundo, a perfuradora registrava aproximadamente 100 cartões por minuto, sendo cerca de 1,67 cartões por segundo. 
> Vale citar que um cartão não equivale à uma adição, mas ainda assim a discrepância segue sendo muito grande.

![Mulher inserindo cartões em uma leitora de cartões perfurados](./images/photos/inserting-cards-in-card-reader.jpg)
- Como o resultado é produzido
