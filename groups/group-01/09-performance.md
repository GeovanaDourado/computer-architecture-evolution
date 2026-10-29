# 9. Performance, Integration and Limitations

## 9.1 Hardware Integration
- Como o processamento, o controle e o armazenamento funcionavam em conjunto

## 9.2 Computational Speed
- Avaliação comparativa do desempenho das diferentes operaçãoes que o ENIAC fazia

## 9.3 Setup x Execution
- Levar dias para conectar os cabos de um programa que era executado em segundos

## 9.4 Energy Consumption
- Quanta energia o ENIAC usava para operar normalmente

## 9.5 Vacuum Tube Failure Rate
- Com que frequência as válvulas queimavam e quanto tempo era necessário para encontrar a defeituosa

## 9.6 I/O Bottleneck
- Havia um gargalo enorme entre o input/output mecânico e processamento eletrônico

## 9.7 Suitability for Ballistics
- Por que essa arquitetura específica era perfeita para calcular trajetórias de artilharia

## 9.8 Architectural Decisions
O ENIAC foi desenvolvido para executar cálculos complexos em alta velocidade comparado às opções da época. Uma das suas funções era o processamento paralelo, que auxiliava justamente na contagem balística dos EUA na época em que foi lançado publicamente.
O computador possuía 20 acumuladores eletrônicos e cada um era capaz de armazenar números decimais de 10 dígitos com sinal (+ ou -), além de resolver operações de adição e subtração.
O paralelismo era especialmente útil no processamento de equações matemáticas, pois vários acumuladores podiam trabalhar simultaneamente em diferentes etapas de um mesmo problema.

## 9.8.1 Especificações técnicas da velocidade
Frequência dos pulsos de sincronização, 100 kHz
Intervalo entre os pulsos, 10 microssegundos
Ciclo básico de adição, 200 microssegundos
Velocidade de adição, até 5.000 adições por segundo, por unidade em funcionamento
Multiplicação de 2 números de 10 dígitos, aproximadamente 2,8 milissegundos

Os pulsos de sincronização eram comandados pela Cycling Unit, que comandava e coordenava todas as unidades independentes e ditava quando deveriam ser feitas as operações matemática, como fosse o "coração" do computador.


## 9.8.2 Como o paralelismo aumentava a velocidade?
O processamento paralelo permitia que vários acumuladores realizassem operações matemáticas ao mesmo tempo, desde que um não dependesse do resultado do outro.

Por exemplo, 4 acumuladores precisam realizar 4 operações diferentes:
Acum. 1: 100 + 200 = 300
Acum. 2: 500 + 200 = 700
Acum. 3: 300 - 120 = 180
Acum. 4: 600 + 150 = 750

Considerando os ciclos citados, sem o paralelismo seriam necessários 4 ciclos para realizar as 4 operações. Porém, com o paralelismo integrado, todas as 4 operações são realizadas em um mesmo ciclo de 200 microssegundos. Sendo assim, o paralelismo nesse caso evolui de 800 μs (4 ciclos de 200 μs) para 200 μs (1 ciclo). 

## 9.8.3 Dificuldade de configuração
Apesar da velocidade de processamento, a configuração do computador ainda era um processo complexo, demorado e sujeito a erros humanos.
Ao contrário dos computadores atuais, a configuração do ENIAC era física (com cabos, bandejas, cartões perfurados) e precisava ser configurado novamente para cada novo conjunto de cálculos.

## 9.8.4 Principais dificuldades técnicas
Conexões físicas: os cabos de programação e transmissão de dados precisavam ser alterados e reconfigurados a cada problema matemático, grandes alterações no algoritmo podiam exigir alterar diversas conexões.
Sincronização dos acumuladores: as operações paralelas não necessariamente finalizavam ao mesmo tempo, por isso era necessário coordenar os pulsos para que uma unidade não tentasse utilizar um resultado que ainda não estivesse pronto.
Identificação de erros: uma conexão incorreta poderia comprometer os resultados, assim era necessário verificar fisicamente as conexões e testar operações para conseguir identificar a raiz do erro.
Tempo de preparação: problemas mais complexos podiam exigir dias de configuração, mesmo sequer antes de iniciar a execução dos cálculos, pois tudo precisava estar de acordo antes de colocar o computador para funcionar. Segundo relatos históricos do governo dos EUA, a preparação de um problema de trajetória balística podia levar até 3 dias, enquanto a execução do problema podia ser finalizada em segundos.

## 9.8.5 Por que o paralelismo dificultava a programação (ainda mais)
A principal dificuldade do paralelismo, em relação à programação, era ter de organizar várias sequências de operações simultâneas.
No ENIAC, o programador precisava considerar quais unidades podiam trabalhar simultaneamente, quais resultados seriam compartilhados entre unidades e o momento certo em que a operação deveria começar. Assim, o processamento paralelo exigia ainda mais planejamento do que um processo sequencial, necessitando atenção detalhada nas conexões e fluxo de pulsos elétricos.

## 9.8.6 Relação entre a velocidade e o tempo de configuração
A relação entre ambos se assemelhava ao conceito do gargalo de Von Neumann. Enquanto tínhamos à disposição uma velocidade de processamento considerável, que realizava diversos cálculos complexos em segundos, a configuração e planejamento exigiam horas ou até dias de trabalho dos programadores.
Assim, a utilização do ENIAC era especialmente importante em problemas que exigiam cálculos repetitivos, como as tabelas balísticas dos EUA. 

![Cabos na Bandeja](./images/photos/lil-cables-in-tray.png)