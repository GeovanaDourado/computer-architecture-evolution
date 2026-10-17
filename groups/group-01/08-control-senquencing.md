# 8. Control and Sequencing

## 8.1 Initiating an Operation
- Como o botão de início acionava o primeiro pulso eletrônico

## 8.2 Cycling Unit
- Geração dos pulsos fundamentais para sincronizar a máquina

![Diagram do painel da unidade ciclíca](./images/panels/cycling-unit.png)

> Descrição da Imagem: Desenho técnico oficial da face frontal da Unidade Cíclica. No topo, destaca-se a abertura circular para a tela do osciloscópio de raios catódicos, utilizado no monitoramento dos sinais do clock de 100 kHz. Logo abaixo, a placa de referência "CYCLING UNIT PULSES AND GATES" ilustra o diagrama temporal dos 20 intervalos de 10 microssegundos do ciclo básico de adição, mapeando os trens de pulso padronizados (CPP, 10P, 9P, 1P a 4P, CCG e RP). Na seção inferior, localizam-se os controles de operação, à direita, a chave seletora ("OPERATION") que alterna entre os modos de execução Contínuo (CONT.), Ciclo Único de Adição (1 ADD.) e Pulso Único (1 PULSE); ao centro, a chave seletora de entrada do osciloscópio ("OSCILLOSCOPE INPUT"), usada para inspecionar cada forma de onda individualmente; e, à esquerda, o botão de avanço passo a passo ("1 PULSE & 1 ADDITION"), utilizado para testes e depuração de cálculos. Na base, os terminais PA, EXT., 1A e CONT. permitiam a conexão de extensões de controle remoto e equipamentos externos de calibração.

## 8.3 Master Programmer
- Mestre da operação, controlava a sequência, os loops e as iterações

## 8.4 Stepper Counters
- Como a máquina acompanhava as iterações dos loops 

## 8.5 Conditional Branching
- Como a máquina alterava o fluxo de operações com base em um resultado positivo ou negativo

## 8.6 Absence of Fetch-Decode-Execute
- Por que o ciclo moderno de busca, decodificação e execução não se aplica

## 8.7 Operation Sequence
- Diagrama lógico, passo a passo, de como as operações eram encadeadas e detalhamento do processo
(Add image)