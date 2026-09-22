# 3. Interconnections

![Foto de algumas senhoritas gerenciando os cabos do ENIAC](./images/photos/cable-management.jpg)  


## 3.1 Cabling Overview

A interconexão dos 40 painéis modulares do ENIAC era realizada por um sistema de cabeamento estritamente segmentado e roteado de acordo com a função elétrica. A estrutura de comunição e alimentação da máquinada máquina era dividida em três formas principais de cabeamento:
1. Cabeamento traseiro: Calhas de energia distribuíam as linhas de corrente contínua (DC) para as placas dos tubos e corrente alternada (AC) para os circuitos de aquecimento dos filamentos das válvulas. Nenhum dado numérico ou pulsos elétricos trafegavam por essa área.
2. Cabeamento Interno: Dentro de cada um dos 40 painéis, as conexões entre os tubos de vácuo, resistores, capacitores e relés eram fixas e soldadas diretamente nos chassis. Essa fiação interna resolvia a lógica local da unidade, as vias por onde o processamento era realizado.

![Circutos internos conectados à válulas de vácuo](./images/vacuum-tubes/tube-backend-circuitry.jpg)

> Descrição da Imagem: Vista inferior de um chassi modular plugável do ENIAC, evidenciando o cabeamento interno e a fiação ponto a ponto soldada manualmente. Destaque para a malha de barramentos de cobre, resistores, capacitores e o conector elétrico multipinos na extremidade inferior direita, utilizado para encaixar o módulo na estrutura fixa do painel.

![Mulheres do ENIAC segurando aparatos semelhantes ao da imagem anterior](./images/photos/eniac-woman.jpg)

> Descrição da Imagem: Demonstração da escala física dos componentes internos do ENIAC e sua evolução. À esquerda, uma operadora segura uma unidade decádica modular completa retirada de um dos painéis, revelando a densidade e o tamanho dos chassis de válvulas que compunham os circuitos internos da máquina.

3. Cabeamento Frontal: Comunicação global entre unidades distintas ocorria exclusivamente na na parte exterior da máquina. Para suportar o peso e organizar a enorme quantidade de fios necessários para interligar os painéis que podiam estar a vários metros de distância, o ENIAC utilizava um sistema de calhas metálicas horizontais chamadas de bandejas.
Essas bandejas percorriam toda a extensão das paredes da sala, fixadas na estrutura dos painéis. As bandejas inferiores e intermediárias acomodavam os vabos longos, enquanto as conexões diretas eram feitas plugando as extremidades desses cabos nos soquetes expostos nos painéis frontais e painéis de interruptores de cada unidade. A topologia da rede era definida pela disposição desses cabos frontais, cabos esses que permitiam a máquina operar de forma altamente paralela, conectando conjuntos de unidade que poderiam operar simultaneamente.

![Visão frontal de um acumulador](./images/panels/Accumulator-Front-View.png)  

> Descrição da Imagem: Desenho técnico da face frontal de um Acumulador evidenciando a infraestrutura de cabeamento da unidade. Destaque para a passagem horizontal das Digit Trays na região intermediária (calhas que acomodavam os cabos de 11 vias para tráfego numérico) e das Program Trays na base do painel (calhas para os cabos de pulsos de sincronismo e controle), demonstrando os pontos físicos exatos onde os cabos flexíveis eram plugados para conectar a unidade ao restante da máquina.

![Visão frontal de um acumulador](./images/panels/Panel-Diagram3.png)

> Descrição da Imagem: Diagrama esquemático de interconexão entre os Acumuladores 1 a 8 e as calhas de cabeamento durante um cálculo balístico. Destaque para a separação física entre as Digit Trunks no topo (cabos de 11 vias para transporte de dados numéricos) e as Program Lines na base (cabos para pulsos de controle), interligadas aos painéis por conexões verticais (patch cords) que definem a rota dos dados e a ordem de disparo das operações.

## 3.2 Signal Transmission
- Como pulsos elétricos (forma, duração, voltagem) representavam números e comandos

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
- Como sinais eram mantidos em sincronia entre os cabos

## 3.9 Setup Complexity
- As dificuldades de manusear os cabos na máquina

## 3.10 Absence of Address Bus
- Porque um barramento não era necessário nessa arquitetura

## 3.11 Network Diagram
- Representação visual dos dados e controle de rotas