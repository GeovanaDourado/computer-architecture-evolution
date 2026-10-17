# 7. Processing Units

## 7.1 Decentralized Processing
O poder computacional do ENIAC era descentralizado e distribuído ao longo de suas 40 unidades funcionais, delegando a execução das equações para módulos matemáticos especializados compostos por 20 Acumuladores para adições e subtrações, 1 Multiplicador de Alta Velocidade e 1 Divisor e Extrator de Raiz Quadrada. Cada módulo continha a infraestrutura de válvulas necessária para realizar a aritmética do início ao fim.

O processamento era gerido por pulsos de programa que, ao chegar numa porta de controle, ativavam a unidade para executar a operação configurada em suas chaves rotativas e emitir um pulso de saída para engatilhar a próxima etapa na malha de cabos. O transporte dos operandos numéricos entre essas unidades independentes ocorria pelas calhas frontais de dígitos, exigindo que a equipe conectasse cabos físicos interligando a saída de dados da unidade transmissora diretamente à entrada da unidade receptora. A configuração do cabeamento externo da máquina era o algorítimo programável responsável por definir as equações a serem realizadas, e as unidades de processamento eram como funções assíncronas que podiam ser chamadas durante a execução do algorítimo.

A descentralização agregava o armazenamento temporário e a lógica aritmética no mesmo circuito, eliminando a necessidade de transferir dados para um núcleo de cálculo central. A adição ocorria diretamente dentro dos contadores de anel do painel, que já guardavam o valor base e serviam de interface para visualizar o estado das operações (3 em 1!). Para gerenciar essa autonomia, cada unidade abrigava múltiplos circuitos locais de controle independentes, permitindo que um único Acumulador executasse até 12 comportamentos diferentes ao longo da execução do algoritmo dependendo exclusivamente de qual soquete frontal recebesse o pulso de programa.

O componente estrutural responsável por unificar o sistema era a Unidade Cíclica, que funcionava como o clock do computador ao distribuir os trens de pulso contínuos que coordenavam o tempo de execução de todas as unidades matemáticas (diferente de computadores modernos o clock era completamente fixo, e tentar dar um overclock (diminuindo as janelas de tempo dos ciclos e dos pulsos dentro dos ciclos) na máquina pravavelmente iria: 1. Apenas desincronizar tudo pois o hardware das unidades não conseguiria acompanhar o rítmo dos pulsos, ou 2. A sala inteira iria explodir). 

A distribuição física das tarefas em múltiplos módulos viabilizava a execução de operações em paralelo. A desvantagem dessa arquitetura era que uma grande proporção de painéis e válvulas permanecia inutilizada durante etapas de cálculo que não exigiam suas funções matemáticas específicas. Mas, em contrapartida, essa arquitetura distribuída e a constante presença de unidades ociosas forneciam uma redundância necessária para a manutenção do sistema (que possuia multiplos pontos de falha). A queima de uma válvula em um painel específico não paralisava a máquina de forma irreversível, permitindo que a equipe de engenharia isolasse o módulo defeituoso e retomasse o processamento redirecionando os cabos de dados e controle daquela etapa matemática para qualquer outro Acumulador livre na sala.

## 7.2 Parallelism
Como a arquitetura possuía dezenas de unidades matemáticas autônomas, a execução paralela no ENIAC ocorria pela ramificação dos cabos de controle, por exemplo: a equipe configurava o sistema para que um único pulso de programa ativasse múltiplos painéis no exato mesmo momento. Ao plugar o cabo de saída de uma operação concluída em conectores (1 - 1 unidades) ou utilizar amplificadores de pulso (tópico 3.2.6) para dividir o sinal (1 - n unidades), o pulso elétrico viajava simultaneamente para as portas de entrada de diferentes Acumuladores endereçados pela organização dos cabos.

O funcionamento simultâneo dessas unidades dependia da sincronização de ciclos gerenciada pela Unidade Cíclica. Como todas as unidades compartilhavam o mesmo ciclo básico de adição de 200 microssegundos, operações paralelas de mesma complexidade mantinham-se perfeitamente alinhadas no tempo. Se três Acumuladores recebessem um pulso de ativação simultâneo, os três iniciariam a leitura de seus operandos, executariam a soma e emitiriam seus pulsos de conclusão no exato mesmo instante, preservando a integridade cronológica da equação.

A execução paralela de operações com quantidades de ciclos diferentes exigia mecanismos de ressincronização. Uma adição consumia apenas 1 ciclo (200 microssegundos), enquanto uma multiplicação consumia cerca de 14 ciclos e uma divisão podia ultrapassar 140 ciclos. Se uma ramificação do algoritmo calculasse uma soma em paralelo com uma divisão, a ramificação mais rápida precisava aguardar o término da mais lenta antes que os resultados pudessem ser combinados.

Para alinhar os ciclos de operações desincronizadas, a equipe utilizava programas fictícios (Dummy Programs). Um Acumulador ocioso recebia o pulso de conclusão da operação rápida e era configurado para não realizar nenhuma aritmética, atuando apenas como um temporizador de espera. Ele consumia a quantidade exata de ciclos em branco necessária até que a operação matemática longa fosse finalizada. O avanço para a próxima etapa unificada da equação só ocorria quando as trilhas paralelas terminavam e seus respectivos sinais se realinhavam temporalmente. Exemplo: quanto dá (10 + 1) + a raiz quadrada de (500000 + 498001)? As duas adições seriam feitas em 1 ciclo, mas o resultado da primeira (11) teria que esperar 139 ciclos até a raiz quadrada de 998001 ser encontrada (999) e adição final ser feita para encontrar o resultado (1010) em 141 ciclos. O gargalo era enorme quando analisamos que: No espaço de 140 ciclos, cada acumulador podia fazer 140 adições. Haviam 20 acumuladores, ou seja, o tempo para encontrar uma raiz quadrada era igual ao tempo para encontrar o resultado de 2820 adições. (Devemos entrar em mais detalhes sobre isso no arquivo 09-performance, tópico 9.2 Computational Speed)

![Gif demonstrando a adição de 500000 + 498001 no contador de anel de um acumulador](./images/simulator/2026-10-17%2013-18-03.gif)

> Descrição da Imagem: 

O paralelismo não se limitava à execução simultânea de múltiplas equações em painéis distintos, operando também em nível interno durante a aritmética básica. A transferência e a soma dos operandos ocorriam de forma paralela em todas as casas decimais de uma palavra matemática. Ao somar dois valores de dez dígitos, a máquina não processava as unidades, depois as dezenas e depois as centenas sequencialmente. Os trens de pulso correspondentes a todas as dez casas decimais viajavam pelas 10 primeiras das 11 vias paralelas de um Digit Trunk e atingiam os contadores de anel do Acumulador receptor no exato mesmo microssegundo, garantindo que o ciclo de adição levasse os mesmos 200 microssegundos independentemente da magnitude dos números envolvidos.

A principal limitação estrutural para a escala do paralelismo global era a disponibilidade de rotas de comunicação isoladas. A execução simultânea de múltiplas operações exigia que cada par de unidades transmissora e receptora utilizasse um caminho de dados exclusivo nas bandejas frontais. Se duas operações paralelas independentes tentassem transmitir seus resultados através da mesma calha de dígitos (Digit Trunk) durante o mesmo ciclo temporal, os pulsos elétricos colidiriam fisicamente no condutor de cobre, fundindo os sinais e corrompendo os operandos. A equipe precisava mapear rotas de cabos estritamente independentes para cada ramificação paralela da equação, o que frequentemente esgotava as vias de comunicação disponíveis na máquina antes mesmo de esgotar o hardware de processamento.

## 7.3 Accumulators
- Como estes performavam adições e subtrações usando trens de pulso

## 7.4 High-Speed Multiplier
- Unidade dedicada à operações de multiplicação

## 7.5 Divider & Square-Rooter
- Unidade dedicada à aritimética mais complexa

## 7.6 Internal Components
- Sobre os tubos à vácuo e relés necessários para o funcionamento de cada undiade

## 7.7 Cycling Unit
- Equivalente ao clock do sistema

## 7.8 Master Programmer
- Unidade de controle para loops, ramificações e sub-rotinas

## 7.9 Mathematical Precision
- Operação com números decimais com sinal de 10 dígitos (tamanho da palavra) 

## 7.10 Processing Cycle
- Como um pulso desengatilhava uma sequência de operações pelas unidades
