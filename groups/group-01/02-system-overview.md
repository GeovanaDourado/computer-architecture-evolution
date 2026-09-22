# 2. System Overview

## 2.1 General Description

O ENIAC, ou Eletronic Numerical Integrator and Computer, foi o primeiro computador eletrõnico de uso geral. Ele era um aparato gigantesco, e igualmente pesado. Em decorrência disso, seu consumo de energia também era exageradamente elevado. Diferente dos computadores modernos, ele era altamente modular e decentralizado, composto de 40 painéis distintos que podiam operar em paralelo, ligados entre si por uma grande quantidade de cabos também modulares.

## 2.2 Dimensions and Layout

O computador como um todo pesava 30 toneladas e ocupava um total de 180 metros quadrados, unindo em sua arquitetura um total de 17.468 válvulas eletrônicas, 70.000 resistores e 10.000 capacitores. O Eniac tinha um formato em U cobrindo três paredes completas de uma sala de aproximadamente 15 X 9 metros. Ele rea subdividido em 40 painéis ao longo de sua extensão, sendo que cada paínel tinha 60 centimetros de largura e profundidade, e 2,4 metros de altura. 

![Imagem de um simulador do Eniac](https://www.cs.drexel.edu/~bls96/eniac/eniacrun.png)   

Tanto os capacitores como os resistores eram alocados próximos as valvúlas termionicas. Os capacitores sendo usados para suprimir oscilações de alta frequência. Já os resistores eram colocados em série com a grade das válvulas, também impedindo oscilações, estas causadas por pequenas diferenças de fiação entre os chassis de plug-in.

## 2.3 Vacuum Tubes

Os tubos termiônicos podiam ser utilizados de duas formas distintas. Como um interruptor, onde seu estado era designado em relação ao potencial da grade presente entre o cátodo e a placa. 
Quando em potencial negativo em relação ao cátodo (estado de corte), a corrente é completamente bloqueada pela ação de repulsão dos eltróns presentes. Assim mantendo uma tensão alta nos tubos, mas sem nenhuma corrente fluindo. 
Inversamente, quando a grade era elevada a um estado positivo (ou só menos negativo) em relação ao cátodo(estado de saturação), a corrente e os eletròns voltavam a fluir livremente. Essa queda de tensão entre a placa e o cátodo ficava tão pequena que poderia ser considerada como um curto circuíto.

O segundo uso dos tubos era o estado de amplificador. Quando operado na região linear (entre corte e saturação), uma pequena variação na tensão da grade causa uma grande variação na corrente de placa. Esse efeito era usado para reforçar pulsos que se dissipavam após longas viagens pelos cabos de dezenas de metros. Também era usado para reforçar sinais mais fracos que podiam se perder ao longo dos circuitos. Para essas ações, existia o padronizador de pulso. Um circuito responsavel por "reformar" os pulsos entre cada uma das unidades dos 40 painéis presentes no Eniac.

Os tubos mais comuns e utilizados no Eniac eram os 6SN7, um tubo formado por um Duplo tríodo que era utilizado como padronizador de pulso e principalmente como contador em anel.
Já os 6V6 eram tubos usados como Drivers, que amplificavam o sinal para qie os contadores fossem acionados. E por serem um tétrodo de feixe, sua arquitetura de duas grades o permitia ser usado como "gate AND" para a programação do sistema. Esses em conjunto dos tubos 6L6formavam quase todo o sistemma de contagem da máquina, visto que, os pêntodos de potência (6L6) eram inversores de potência, e acionavam os cátodos dos contadores decimais. Cada um acionava um sinal de limpeza nos contadores decimais, permitindo assim a adição e subtração de números maiores com o uso de multiplos anies decimais em sequência se complementando.
E por último mas não menos importantes haviam os tubos 5T4, que erma simples díodos de dois eltretodos, servindo como retificadores e protegendo circuitos auxiliares.

## 2.4 Additional Hardware Components
- O papel de resistores, capacitores, relés e interruptores manuais

## 2.5 Power Supply and Consumption
- Requisitos de consumo elétrico e as linhas de energia dedicadas

## 2.6 Cooling System
- Como o sistema dissipava a quantidade enorme de calor gerada pelos tubos

## 2.7 Modular Panel Organization
- Divisão da máquina em 40 painéis distintos

## 2.8 Data Flow
- Como os dados se moviam pela arquitetura

## 2.9 Block Diagram
- Representação visual da lógica do hardware
(Add image)

## 2.10 Main Characteristics

Table

| Feature | Description |
|---------|-------------|
