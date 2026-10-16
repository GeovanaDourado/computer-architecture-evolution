# 6. Data Flow and Access

## 6.1 Data Origins
- De onde vinham os operandos (transmissor de constante ou cálculo anterior)

## 6.2 Data Movement Process
- Como um número percorria o caminho da Unidade A até a Unidade B por meio de bandejas de dígitos

## 6.3 Intermediate Results

A retenção de resultados parciais ocorria diretamente nos Acumuladores, eliminando o roteamento constante de dados para a memória externa. Ao finalizar uma etapa matemática, como uma adição ou a recepção de um produto parcial de um multiplicador, o valor recém-calculado permanecia gravado eletricamente no próprio hardware sem depender de ciclos de processamento contínuos.

### 6.3.1 Vacuum Triodes
Para compreender como um valor era mantido eletricamente, é necessário analisar o funcionamento do tríodo, a válvula termiônica básica do sistema. Um tríodo consiste em um tubo de vidro selado a vácuo contendo quatro componentes internos principais:

1. Filamento: Uma resistência elétrica que se aquece com a passagem de corrente, funcionando de maneira semelhante ao filamento de uma lâmpada incandescente.
2. Cátodo: Um pequeno cilindro metálico posicionado ao redor do filamento. Quando aquecido, o metal do cátodo libera elétrons livres no vácuo, um fenômeno físico chamado emissão termiônica. Como os elétrons possuem carga elétrica negativa, eles formam uma nuvem ao redor do cilindro.
3. Placa (Ânodo): Uma lâmina de metal posicionada na extremidade oposta do tubo, polarizada com alta tensão elétrica positiva. Pela lei da atração eletrostática, cargas opostas se atraem: a placa positiva atrai os elétrons negativos emitidos pelo cátodo, criando um fluxo contínuo de corrente elétrica através do vácuo.
4. Grade de Controle: Uma malha fina de fios metálicos posicionada fisicamente entre o cátodo e a placa, por onde os elétrons precisam passar.

A grade de controle funciona como uma comporta eletrônica para o fluxo de elétrons, operada pela variação de sua voltagem entre dois estados:

- Estado de Corte: Quando uma tensão fortemente negativa é aplicada à grade, sua carga repele os elétrons que tentam sair do cátodo (pois cargas iguais se repelem). O fluxo de partículas é fisicamente bloqueado antes de atingir a placa. Dessa forma a válvula entra em estado de corte, onde nenhuma corrente elétrica circula pelo circuito da placa.
- Estado de Saturação: Quando a tensão da grade é elevada (tornando-se nula ou positiva em relação ao cátodo), a barreira de repulsão desaparece. Os elétrons atravessam livremente as aberturas da grade e colidem em alta velocidade contra a placa. A válvula entra em estado de condução/saturação, onde a corrente elétrica flui livremente pelo circuito.

A válvula 6SN7, amplamente empregada no ENIAC, era um duplo-tríodo, ou seja, ela agrupava dois desses conjuntos completos de cátodo, grade e placa dentro de um único invólucro de vidro.

### 6.3.2 Bistable Circuits
O armazenamento de um estado elétrico dependia da união de dois tríodos em um circuito biestável, também conhecido como gatilho Eccles-Jordan ou flip-flop. Esse circuito foi projetado para possuir dois estados estáveis de repouso, utilizando a técnica de realimentação por acoplamento cruzado.

No circuito biestável, a placa do primeiro tríodo (Tríodo A) é ligada diretamente à grade de controle do segundo tríodo (Tríodo B) através de uma rede de resistores. De forma idêntica e cruzada, a placa do Tríodo B é ligada de volta à grade de controle do Tríodo A. Esse circuito opera em um equilíbrio auto-sustentável baseado na queda de tensão elétrica:

Quando uma corrente elétrica passa por um resistor ligado à placa de um tríodo em condução, ocorre uma queda abrupta na voltagem dessa placa (a tensão cai para um nível baixo). Se o Tríodo A entra em condução (saturação), a baixa tensão de sua placa é conduzida diretamente para a grade do Tríodo B. Essa baixa voltagem empurra a grade do Tríodo B para um potencial altamente negativo, forçando o Tríodo B a entrar em corte (bloqueando sua condução de elétrons). Como o Tríodo B não conduz corrente, não há queda de tensão em sua placa. A placa do Tríodo B permanece com sua voltagem máxima positiva. Essa alta tensão da placa de B é conduzida de volta para a grade do Tríodo A, mantendo a grade de A positiva e sustentando a condução de elétrons em A.

Os dois tubos travam-se mutuamente nesse estado. O Tríodo A permanece indefinidamente em condução contínua e o Tríodo B permanece indefinidamente bloqueado, sustentados apenas pelas linhas de corrente contínua da fonte de alimentação, sem necessitar de pulsos externos para manter a informação guardada. O circuito só inverte essa condição quando recebe um pulso elétrico deliberado em sua entrada, forçando o Tríodo A a cortar e o Tríodo B a conduzir.

### 6.3.3 Ring Counters
Para armazenar e operar números decimais, os biestáveis eram organizados em contadores de anel decádico. Cada anel representava uma única casa decimal (unidades, dezenas, centenas) e era formado por dez circuitos biestáveis interligados em uma fila circular fechada (circular no sentido de que após o nove vinha o número 0, não literalmente circular), numerados de 0 a 9. O terminal de saída do estágio 9 era conectado diretamente de volta à entrada do estágio 0, fechando o anel.

A representação do número dentro de cada década era puramente posicional, sendo que dentro dos dez estágios do anel, nove biestáveis permaneciam em repouso (repouso = Tríodo A conduzindo e Tríodo B em corte) e apenas um biestável permanecia ativado (ativado = Tríodo A em corte e Tríodo B conduzindo). O valor numérico correspondia à posição física do estágio ativado, por exemplo: Se o estágio 0 estivesse ativado, a década armazenava o número 0; Se o estágio 7 estivesse ativado e todos os outros nove em repouso, a década armazenava o número 7.

Para avançar o contador, todos os dez biestáveis do anel compartilhavam uma única linha comum de entrada de pulsos elétricos. O circuito funcionava por transferência de carga entre vizinhos. Quando um pulso de 100 kHz entrava na linha comum, ele atingia todos os dez biestáveis, mas apenas o estágio que já estava ativado possuía polarização para reagir. Esse pulso forçava o estágio ativado a desligar (revertendo seus tríodos ao estado de repouso). Ao desligar, a placa do seu tríodo sofria uma rápida elevação de tensão. Essa variação era canalizada por um pequeno capacitor ligado diretamente à grade do estágio seguinte no anel. Esse pico de tensão forçava o estágio seguinte a ligar.

Dessa forma, cada pulso recebido pela linha comum empurrava o estado ativado um passo à frente no anel (do 3 para o 4, do 4 para o 5). Quando o contador avançava do estágio 9 para o estágio 0, o fechamento do ciclo gerava um pulso de transporte de dezena (carry), enviado para a entrada da década imediatamente à esquerda (das unidades para as dezenas).

Um Acumulador completo continha dez desses anéis enfileirados lado a lado no painel (armazenando uma palavra de dez dígitos decimais), além de um biestável isolado no topo para indicar o sinal algébrico (Positivo ou Negativo).

### 6.3.4 Signal Transmission
A transformação dos números retidos nos anéis em pulsos móveis dentro das calhas de dados ocorria através da coordenação entre o Acumulador e a Unidade Cíclica. O Acumulador modulava os sinais contínuos gerados pela Unidade Cíclica para organizar a traduzir os números nos anéis em pulsos.

A transmissão operava dentro do Ciclo de Adição padrão de 200 microssegundos, dividido em 20 intervalos de 10 microssegundos. A Unidade Cíclica distribuía permanentemente para toda a máquina dois trens de pulso mestres pela bandeja de sincronização:

- Trem 10P: Uma sequência contínua de dez pulsos elétricos emitidos na primeira metade do ciclo (tempos 1/20 a 10/20).
- Trem 9P: Uma sequência contínua de nove pulsos elétricos emitidos nos tempos 1/20 a 9/20.

Quando um Program Pulse atingia o terminal de controle de um Acumulador, ordenando a emissão do seu valor, a unidade executava uma leitura por rotação completa, onde o Acumulador desviava o trem 10P da Unidade Cíclica diretamente para a linha de entrada comum dos seus anéis decádicos. Esses dez pulsos forçavam os anéis a avançarem exatamente dez passos, fazendo o estado ativado dar uma volta completa pelo anel e retornar ao mesmo número original. Simultaneamente, o trem 9P da Unidade Cíclica era aplicado à entrada de uma válvula pentodo (que operava como uma comporta de saída para a calha de dados). No instante exato em que o anel passava do estágio 9 para o estágio 0 durante a rotação, a tensão de transição acionava essa comporta pentodo, liberando a passagem dos pulsos restantes do trem 9P para o cabo de saída (Digit Trunk).

Por exemplo, para transmitir o dígito 4 o anel iniciava no estágio 4. Os primeiros seis pulsos do trem 10P avançavam o anel até o estágio 0 (5, 6, 7, 8, 9, 0). Nesse momento após o sexto tempo, a comporta pentodo abria. Os quatro pulsos restantes do trem 9P (nos tempos 7, 8, 9 e o complemento de fechamento) passavam livremente pela válvula aberta e entravam no Digit Trunk. Ao término do décimo pulso de 10P, o anel completava os quatro passos finais (1, 2, 3, 4), parando exatamente no estágio 4 onde havia começado.

Ao final do ciclo de 200 microssegundos, a chave de programa determinava o estado final do Acumulador:

- Modo de Retenção: O anel permanecia no estágio original (preservando o número 4 para cálculos futuros).
- Modo de Limpeza (Clear): No tempo 19/20, um pulso de Reset era injetado no anel, forçando o estágio ativo a ir para o estágio 0, apagando o resultado intermediário e liberando a unidade para receber novos dados.

## 6.4 Operand Identification
- Como dados específicos eram selecionados (conexão direta de cabos, não endereços)

## 6.5 Lack of Modern Addressing
- Por que conceitos como endereços de RAM ou ponteiros não se aplicam ao ENIAC

## 6.6 Switch-Based Data Selection
- Uso de chaves seletoras para indicar a um acumulador quais dados internos enviar para a saída

## 6.7 Access Bottlenecks (DO NOT READ THE BEGINNING OF THIS LINE, IT IS DEATH MAGIC!)
- Limitações físicas no encaminhamento de dados entre painéis distantes

