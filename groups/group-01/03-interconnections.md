# 3. Interconnections

![Foto de algumas senhoritas gerenciando os cabos do ENIAC](./images/photos/cable-management.jpg)  


## 3.1 Cabling Overview

A interconexão dos 40 painéis modulares do ENIAC era realizada por um sistema de cabeamento estritamente segmentado e roteado de acordo com a função elétrica. A estrutura de comunição e alimentação da máquinada máquina era dividida em três formas principais de cabeamento:
### 3.1.1. Cabeamento traseiro
Calhas de energia distribuíam as linhas de corrente contínua (DC) para as placas dos tubos e corrente alternada (AC) para os circuitos de aquecimento dos filamentos das válvulas. Nenhum dado numérico ou pulsos elétricos trafegavam por essa área.
### 3.1.2. Cabeamento Interno
Dentro de cada um dos 40 painéis, as conexões entre os tubos de vácuo, resistores, capacitores e relés eram fixas e soldadas diretamente nos chassis. Essa fiação interna resolvia a lógica local da unidade, as vias por onde o processamento era realizado.

![Circutos internos conectados à válulas de vácuo](./images/vacuum-tubes/tube-backend-circuitry.jpg)

> Descrição da Imagem: Vista inferior de um chassi modular plugável do ENIAC, evidenciando o cabeamento interno e a fiação ponto a ponto soldada manualmente. Destaque para a malha de barramentos de cobre, resistores, capacitores e o conector elétrico multipinos na extremidade inferior direita, utilizado para encaixar o módulo na estrutura fixa do painel.

![Mulheres do ENIAC segurando aparatos semelhantes ao da imagem anterior](./images/photos/eniac-woman.jpg)

> Descrição da Imagem: Demonstração da escala física dos componentes internos do ENIAC e sua evolução. À esquerda, uma operadora segura uma unidade decádica modular completa retirada de um dos painéis, revelando a densidade e o tamanho dos chassis de válvulas que compunham os circuitos internos da máquina.

### 3.1.3 Cabeamento Frontal
Comunicação global entre unidades distintas ocorria exclusivamente na na parte exterior da máquina. Para suportar o peso e organizar a enorme quantidade de fios necessários para interligar os painéis que podiam estar a vários metros de distância, o ENIAC utilizava um sistema de calhas metálicas horizontais chamadas de bandejas.
Essas bandejas percorriam toda a extensão das paredes da sala, fixadas na estrutura dos painéis. As bandejas inferiores e intermediárias acomodavam os vabos longos, enquanto as conexões diretas eram feitas plugando as extremidades desses cabos nos soquetes expostos nos painéis frontais e painéis de interruptores de cada unidade. A topologia da rede era definida pela disposição desses cabos frontais, cabos esses que permitiam a máquina operar de forma altamente paralela, conectando conjuntos de unidade que poderiam operar simultaneamente.

![Visão frontal de um acumulador](./images/panels/Accumulator-Front-View.png)  

> Descrição da Imagem: Desenho técnico da face frontal de um Acumulador evidenciando a infraestrutura de cabeamento da unidade. Destaque para a passagem horizontal das Digit Trays na região intermediária (calhas que acomodavam os cabos de 11 vias para tráfego numérico) e das Program Trays na base do painel (calhas para os cabos de pulsos de sincronismo e controle), demonstrando os pontos físicos exatos onde os cabos flexíveis eram plugados para conectar a unidade ao restante da máquina.

![Visão frontal de um acumulador](./images/panels/Panel-Diagram3.png)

> Descrição da Imagem: Diagrama esquemático de interconexão entre os Acumuladores 1 a 8 e as calhas de cabeamento durante um cálculo balístico. Destaque para a separação física entre as Digit Trunks no topo (cabos de 11 vias para transporte de dados numéricos) e as Program Lines na base (cabos para pulsos de controle), interligadas aos painéis por conexões verticais (patch cords) que definem a rota dos dados e a ordem de disparo das operações.

## 3.2 Signal Transmission

Um pulso elétrico no ENIAC é uma variação transitória e repentina de tensão em um fio de cobre. Em estado de repouso, o fio é mantido em potencial elétrico negativo ou nulo. Quando uma válcula eletrônica no transmissor entre momentaneamente em saturação (condução plena), ele injeta corrente na linha, ela injeta corrente na linha, elevando a tensão abruptamente para cerca de +45 volts. A linha sustenta essa tensão por aproximadamente 2 microsegundo (ou 0,000002 segundos) até que a válvula corte a corrente, fazendo a tensão cair instantaneamente de volta ao repouso. Esse ciclo de subida, sustentação e queda forma uma onda quadrada conhecida como pulso. A lógica da máquina utilizava três categorias de sinais:

### 3.2.1. Pulsos de Dígito
- Fisicamente, era uma sequência rápida de pulsos repetidos (chamada de trem de pulsos) em um mesmo fio, disparando a intervalos de 10 microsegundos (ou 0,00001 segundos (ou 1 x 10^-5 segundos)) pela Unidade Cíclica, equivalente a uma frequência base de 100 kHz.
- O número transferido é quantificado pelo número exato de picos de tensão que passam pelo fio durante um ciclo. Se o número for 4, o transmissor faz a tensão subir e descer para +45V quatro vezes seguidas. Ao chegarem à unidade receptora, cada salto de tensão altera o estado de uma válvula dento de um anel, avançando o contador em uma posição por pulso recebido.

### 3.2.2. Pulsos de Programa

### 3.3.2 Sinais de Porta

## 3.3 Cross-Panel Communication
- Como, por exemplo, um acumulador em um canto enviava dados para um multiplicador em outro canto

## 3.4 Cable Materials and Connectors
- Composição física dos cabos de conexão, plugues e conectores multipinos

## 3.5 Digit Trays
- Sobre os cabos usados para transmitir dados de valores numéricos

## 3.6 Program Trunks
- Cabos responsáveis por enviar pulsos de ativação e sincronização

## 3.7 Patch Cords & Plugs
- Os cabos usados para rotear dados e instruções

## 3.8 Synchronization

O Eniac utilizava uma arquitetura genial chamada de Unidade de Ciclos, um mecanismo centralizado e a fonte única da maquina toda. Gerando pulsos em intervalos de 10 microssegundos (10 µs). A taxa de atualização do projeto era de 100kHz (cem quilohertz), contudo, foi pesteriormente usada apenas em 60kHz por motivos de estabilidade. 
Como a Unidade de Ciclos era a fonte única e centralizada do sistema, era impossível que houvesse desincronização por meios mecánicos. Visto que não havia outra fonte de pulsos para funcionar em paralelo. A complexidade no entanto, era garantir que esses pulsos se estendessem pelas dezenas de metros até todos os paíneis. Para lidar com esta dificuldade foram utilizados pares de cabos 6L6 excitados por um cabo 6V6. Esses eram Drivers que funcionavam como amplificadores do sinal da Unidade de Ciclos, esse sinal amplificado era enviado para o Synchronizing trunk, um feixe de 11 cabos (trey de jumpers) que conectava todos os paíneis simultanemante. Evitando um possivel delay nos paíneis mais distantes. 
Um fator importante de se notar era que os ciclos da Unidade de Ciclos, levavam exatamante 200 µs, e cada operação da máquina consumia um número inteiro de ciclos. Como o sinal de relógio gerado pela Unidade de Ciclos era recebido e amplificado no mesmo instante, a sincronia era garantida por construção.
E a Unidade de Ciclos funcionava em 3 modos. O contínuo, onde o relógio estava sempre ativo e constantemente gerando cilcos. O modo One add time. Onde os ciclos eram executados um por um em adição, muito usado para depuração. E o modo One pulse, onde o era emitido apenas um pulso por vez, usado para gerar diagnósticos.

## 3.9 Setup Complexity

As maiores dificuldades relatadas pela equipe estavam relacionadas em principal aos cabos e outros erros decorrentes deles. A primeira parte envolvia o tempo e o esforço, pois, cada problema a ser excutado precisava da organização de milhares de cabos em aproximadamente 40 plugboards. Cada um com metros de de largura. Somente a etapa de configuração física levava varios dias, e a verificação podia levar ainda mais tempo. Havia por efeito, erros de depuração, onde um cabo mal encaixado, ou switch mal posicionado era extremamente dificil de encontrar. Ainda não havia nenhuma estrutura de Trace ou Breakpoint nativo. A equipe na verdade desenvolveu a ténica de Break point. Puxando um cabo de um soquete para interromper a cadeia de pulsos e congelando a máquina. Permitindo inspeciona-la internamnete. Ainda assim, a equipe constatava que era "Absurdamente difícil" de solucionar o problema. Por fim havia os erros gerados por operações concorrentes. Como o Eniac executava as operções aritimeticas e de transferẽncia de forma simultanea, a programação se tornava um desafio a parte. Visto que era preciso planejar meticulosamente a sequência dos cabos para que as operações paralelas não entrassem em conflito. foi apenas após a intervenção de Jonh Von Neumann que introduziu um código de de conversor para forçar a operação de forma serial que este problema foi resolvido. 

## 3.10 Absence of Address Bus

O Eniac não necessitava de um Barramento, e isso ocorria justamente por sua arquitetura. Já que ele não tinha memória de instrução para que pudesse ser endereçada. Em suma, O Eniac não tinha memória, pois o "Programa" era estruturado pela junção de cabos e soquetes, logo o endereçamento era direto e fisíca no próprio hardware do sistema. As operações feitas eram padronizadas pela fiação e pelos interruptores, e até mesmo as tabelas de função utilizadas eram acessadas por fiação fixa. Em termos técnicos, o Eniac funcionava mais como um grafo de fluxo do que como uma CPU diretamente. Sem conexões e programas extras a serem utilizidos. Sem necessidade de barramento.

## 3.11 Network Diagram
A representação mais próxima do visual dos dados e controle de rotas pode ser encontrado no seguinte documento.

