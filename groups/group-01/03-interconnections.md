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

![Alguns painéis, incluindo a Unidade Cíclica](./images/photos/cycling-unit-and-others.jpg)

> Descrição da Imagem: Painéis originais do ENIAC em exibição na Universidade da Pensilvânia. O segundo painel vertical a partir da esquerda é a Unidade Cíclica (identificável pela tela circular do osciloscópio central, usada no monitoramento do clock de 100 kHz), ladeada por uma Tabela de Função portátil à esquerda, um Acumulador e o Programador Mestre à direita, todos interligados por cabos nas calhas inferiores.

Um pulsso no ENIAC é uma variação transitória e rápida de potencial elétrico em uma linha condutora. Em repouso, as linhas operavam polarizadas com alta tensão negativa (geralmente -345V de corrente contínua para acoplamento direto com as grades das válvulas). Quando um tubo transmissor entrava em saturação, ele injetava corrente na linha, elevando abruptamente o potencial para -290C por cerca de 2 microsegundos (ou 0,000002 segundos) antes de retornas o pulso elementar de trabalho da máquina.

![Diagrama listando tipos de sinais](./images/conns/cycling-unit-pulses-gates.png)

> Descrição da Imagem: Diagrama temporal oficial da Unidade Cíclica, ilustrando as formas de onda, níveis de tensão e janelas de atuação durante um ciclo de adição, que dura 200 microsegundos. Mais detalhes à baixo

Toda a operação do sistema era regida por três categorias de sinais elétricos sinconizados pela Unidade Cíclica ao encapsuladas em um ciclo de 200 microsegundos (dividido em 20 tempos, cada tempo possuíndo 10 microsegundos):

### 3.2.1. Pulsos de Dígito
Os dados trafegavam em base decimal através de trens de pulso emitidos na primeira metade do ciclo (tempos 1/20 a 10/20). A Unidade Cíclica não possuía geradores dedicados para cada um dos números de 1 a 9, em vez disso, ela gerava blocos fundamentais de pulsos com durações e espaçamentos temporais específicos:
- 1P: Emite 1 pulso no tempo 1/20
- 2P: Emite 2 pulsos sequenciais nos tempos 2/20 e 3/20
- 2'P: Emite 2 pulsos sequenciais nos tempos 4/20 e 5/20 (separados do 2P para evitar sobreposição)
- 4P: Emite 4 pulsos nos tempos de 6/20 a 9/20
- 1'P: Emite 1 pulso isolado no tempo 10/20
Qualquer número de 1 a 9 era sintetizado combinando essas linhas atravpe de posrtas lógicas. Exemplo: o dígito 7 era formado pela soma lógica de 1P + 2P + 4P.
As saídas 9P e 10P pré-fabricados com 9 e 10 pulsos contínuos, utilizados prioritariamente para operações de complemento de dez e aritmética de número negativos

### 3.2.2. Sinais de Controle
Os comandos e transições de rotina utilizavam pulsos unitários mais discretos:
- Central Programming Pulse: um pulso mestre gerado pontualmente no tempo 17/20 de cada ciclo.
- Program Pulses: Quando uma unidade encerrava seu cálculo, seu dicionário liberava a passagem do CPP daquele ciclo para a saída. Esse pulso unitário viajava pelas bandejas de programa até a entrada de outra unidade, depolarizando as grades das válvulas de corte e acionando o início do próximo cálculo em perfeito sincronismo temporal com a Unidade Crítica.

### 3.2.3. Sinais de Porta
o contrário dos pulsos curtos de 2, uma *Gate* era uma elevação contínua de tensão mantida estável para habilitar ou desabilitar válvulas pentodo (como as 6V6, operando como portas lógicas AND):
- Carry-Clear Gate: Janela temporal contínua que permanecia ativa entre os tempos 11/20 e 18/20 (70 microsegundos). Esse sinal desobstruía os circuitos de transporte de dezenas, permitindo que os contadores repassassem o "vai-um" gerado pela adição aos estágios seguintes sem colidir com os dados de dígitos (que haviam terminado no tempo 10).
- Reset Pulses: Pulsos de limpeza referenciados em 0V (com pico em +50V) disparados no tempo 13/20 e no tempo 19/20. O pulso 13 reiniciava os gatilhos de transporte, e o pulso 19 zerava os estados transitórios dos acumuladores, deixando todas as linhas estabilizadas para o tempo 0 do ciclo subsequente.

### Padronizador de Pulso
Conforme esses sinais viajavam por dezenas de metros de cabos e bandejas, as perdas capacitivas e resistivas deformavam as ondas quadradas e derrubavam os -290V nominais. Para que as válvulas operassem de modo confiável, circuitos padronizadores utilizavam tubos duplos 6SN7 para detectar o limiar da onda degradada e recriar bordas retangulares afiadas, enquanto tubos de potência 6V6 e 6L6 restauravam a amplitude de tensão antes de encaminhar o sinal para a unidade de destino.

![Esquema elétrico do circuito padronizador de pulsos](./images/conns/Pulse-Standardizer-Circuits.png)

> Descrição da Imagem: Esquema elétrico do circuito padronizador de pulso. O estágio inicial utiliza a válvula de duplo tríodo 6SN7 configurada como um gatilho monoestável para regenerar as bordas retangulares da onda deformada, enquanto os estágios seguintes com as válvulas de potência 6V6 e 6L6 restauram a amplitude de tensão e fornecem corrente suficiente para o sinal percorrer as longas linhas da máquina.

### Extra

![Diagrama preliminar de temporização do ENIAC](./images/conns/Synchronizing-Pulse-Gate.png)

> Descrição da Imagem: Diagrama preliminar de temporização desenhado em dezembro de 1943, demonstrando a concepção inicial de um ciclo de adição de 16 tempos de pulso. O documento ilustra o planejamento embrionário da relação entre Cycling Pulses, Carry-Clear Gate e pulsos de programa, antes da expansão definitiva da máquina para o ciclo padrão de 20 tempos de pulso.


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

O Eniac utilizava uma arquitetura genial chamada de Unidade de Ciclos, um mecanismo centralizado e a fonte única da maquina toda. Gerando pulsos em intervalos de 10 microssegundos (10 µs). A taxa de atualização do projeto era de 100kHz (cem quilohertz), contudo, foi posteriormente usada apenas em 60kHz por motivos de estabilidade. 
Como a Unidade de Ciclos era a fonte única e centralizada do sistema, era impossível que houvesse desincronização por meios mecánicos. Visto que não havia outra fonte de pulsos para funcionar em paralelo. A complexidade no entanto, era garantir que esses pulsos se estendessem pelas dezenas de metros até todos os paíneis. Para lidar com esta dificuldade foram utilizados pares de cabos 6L6 excitados por um cabo 6V6. Esses eram Drivers que funcionavam como amplificadores do sinal da Unidade de Ciclos, esse sinal amplificado era enviado para o Synchronizing trunk, um feixe de 11 cabos (trey de jumpers) que conectava todos os paíneis simultanemante. Evitando um possivel delay nos paíneis mais distantes. 
Um fator importante de se notar era que os ciclos da Unidade de Ciclos, levavam exatamante 200 µs, e cada operação da máquina consumia um número inteiro de ciclos. Como o sinal de relógio gerado pela Unidade de Ciclos era recebido e amplificado no mesmo instante, a sincronia era garantida por construção.
E a Unidade de Ciclos funcionava em 3 modos. O contínuo, onde o relógio estava sempre ativo e constantemente gerando cilcos. O modo One add time. Onde os ciclos eram executados um por um em adição, muito usado para depuração. E o modo One pulse, onde o era emitido apenas um pulso por vez, usado para gerar diagnósticos.

## 3.9 Setup Complexity

As maiores dificuldades relatadas pela equipe estavam relacionadas em principal aos cabos e outros erros decorrentes deles. A primeira parte envolvia o tempo e o esforço, pois, cada problema a ser excutado precisava da organização de milhares de cabos em aproximadamente 40 plugboards. Cada um com metros de de largura. Somente a etapa de configuração física levava varios dias, e a verificação podia levar ainda mais tempo. Havia por efeito, erros de depuração, onde um cabo mal encaixado, ou switch mal posicionado era extremamente dificil de encontrar. Ainda não havia nenhuma estrutura de Trace ou Breakpoint nativo. A equipe na verdade desenvolveu a ténica de Break point. Puxando um cabo de um soquete para interromper a cadeia de pulsos e congelando a máquina. Permitindo inspeciona-la internamnete. Ainda assim, a equipe constatava que era "Absurdamente difícil" de solucionar o problema. Por fim havia os erros gerados por operações concorrentes. Como o Eniac executava as operções aritimeticas e de transferẽncia de forma simultanea, a programação se tornava um desafio a parte. Visto que era preciso planejar meticulosamente a sequência dos cabos para que as operações paralelas não entrassem em conflito. foi apenas após a intervenção de Jonh Von Neumann que introduziu um código de de conversor para forçar a operação de forma serial que este problema foi resolvido. 

## 3.10 Absence of Address Bus

O Eniac não necessitava de um Barramento, e isso ocorria justamente por sua arquitetura. Já que ele não tinha memória de instrução para que pudesse ser endereçada. Em suma, O Eniac não tinha memória, pois o "Programa" era estruturado pela junção de cabos e soquetes, logo o endereçamento era direto e fisíca no próprio hardware do sistema. As operações feitas eram padronizadas pela fiação e pelos interruptores, e até mesmo as tabelas de função utilizadas eram acessadas por fiação fixa. Em termos técnicos, o Eniac funcionava mais como um grafo de fluxo do que como uma CPU diretamente. Sem conexões e programas extras a serem utilizidos. Sem necessidade de barramento.

## 3.11 Network Diagram
A representação mais próxima do visual dos dados e controle de rotas pode ser encontrado no seguinte documento.

# IMAGENS DO BRENNO:

![](./images/tables/tabulation-of-cables.png)
![](./images/tables/setup-of-exterior-ballistics-equations.png)
![](./images/conns/constant-tansmiter-interconn-diagram.png)
![](./images/conns/accumulator-interconn-diagram.png)
![](./images/conns/function-table-interconn-diagram.png)


Como se usa imagens localmente?
É bem simples, você coloca a imagem em qualquer lugar na mesma pasta que esse arquivo ou em pastas inferiores (nesses caso, pastas dentro da pasta images). Após isso é só colocar o caminho para imagem a partir do POV desse arquivo aqui (que é representado por um ./). A pertir do arquivo em que estamos, a imagem que a gente quer está, por exemplo, dentro da pata imagens, então o link para ela é ./images... Dentro de da pasta images tem outras pastas, onde estão os arquivos das imagens. Para pegar uma imagem especifíca você precisa ir até a pasta onde ela está e perguntar pelo nome do arquivo da imagem, como você pode ver nos exemplos abaixo (que são as imagens que vc quer usar)