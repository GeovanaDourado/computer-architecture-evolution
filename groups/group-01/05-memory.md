# 5. Memory Organization

![Uma operadora ao lado de uma pilha enorme de cartões perfurados](./images/memory/62500-punched-cards.jpg)

> Descrição da Imagem: Fotografia exibindo uma operadora posicionada ao lado de uma imensa pilha de cartões perfurados. A estrutura, que atinge quase a altura dos ombros da operadora, é composta por aproximadamente 62.500 cartões de papel cartonado. A imagem ilustra muito bem o volume físico equivalente a 5 milhões de caracteres (cerca de 5 megabytes) de dados, o que correspondia à capacidade total de armazenamento dos primeiros discos magnéticos comerciais da época, como o IBM 305 RAMAC. Atrás da pilha é visível o que parece ser uma Keypunch (máquina de perfurar cartões). A imagem ajuda a visualizar a escala material do volume de dados, indiretamente expondo o extremo esforço logístico e espacial exigido para o manuseio das informações. Todo esse volume precisava ser fisicamente perfurado, rigorosamente ordenado para evitar falhas de sequência, transportado e alimentado em lotes nos leitores eletromecânicos para garantir a continuidade dos cálculos. Isso causava um gargalo que iremos tratar no tópico 9.5 do arquivo 09-performance.

## 5.1 Distributed Memory
O armazenamento de informações no ENIAC era fisicamente descentralizado, com a arquitetura da máquina não possuíndo um bloco de hardware unificado para reter dados e instruções simultaneamente. A retenção dos dados era categorizada pela natureza da informação e distribuída de forma independente pelas 40 unidades funcionais do sistema.

Os dados numéricos transitórios residiam nas próprias unidades de processamento. Os Acumuladores mantinham os operandos ativos diretamente em seus circuitos de contagem durante a execução das operações. Valores fixos e constantes matemáticas exigidas pelas equações eram configurados e retidos mecanicamente em matrizes de chaves rotativas nas Tabelas de Função (Function Tables) e na Unidade de Transmissão de Constantes (Constant Transmitter).

O armazenamento das instruções operacionais era estritamente topológico. A lógica de execução não existia como um conjunto de códigos numéricos salvos em uma matriz de válvulas. O programa executado durante uma operação da máquina era definido pelo arranjo dos cabos coaxiais interligados nas bandejas frontais e pela posição dos muitos interruptores nos painéis de controle das unidades. A configuração elétrica e mecânica do hardware constituía, na prática, a memória de instrução do sistema.

## 5.2 External Storage
A restrição física dos circuitos valvulados exigia o uso de cartões perfurados padrão IBM como a mídia exclusiva de armazenamento de massa não-volátil do sistema. Os cartões funcionavam como um repositório estático. Tabelas de tiro balístico, parâmetros de calibração e operandos iniciais eram registrados mecanicamente através de furos no papel cartonado, preservando as informações de forma permanente desde que a integridade física do material e a ordenação do lote fossem mantidas.

> Nota: Armazenamento de massa refere-se a mídias capazes de reter (relativamente) grandes volumes de dados externamente aos circuitos principais. Não-volátil indica que a retenção da informação não depende de energia elétrica; uma vez perfurados, os dados permanecem gravados no papel indefinidamente, independentemente de a máquina estar ligada ou desligada (diferente dos valores intermediários, que dependiam de haver energia correndo pela máquina para continuarem acessíveis).

Cada cartão abrigava 80 colunas, o que corresponde matematicamente a 80 caracteres (ou 80 bytes de dados não compactados). Para lidar com o volume de milhares de cartões, os lotes eram guardados em gaveteiros metálicos modulares alocados na sala de operações. A manutenção desse arquivo exigia controle rigoroso do ambiente onde eles se encontravam, pois variações de umidade dilatavam ou deformavam o papel cartonado, causando atolamentos e desalinhamentos no cilindro eletrificado do leitor. Em termos de capacidade física, uma caixa contendo 12.500 cartões perfurados equivalia a aproximadamente 1 megabyte de informação.

A natureza não-destrutiva da leitura eletromecânica permitia a reutilização contínua dos mesmos lotes de dados. Em problemas de integração numérica ou equações diferenciais que exigiam múltiplas iterações sobre as mesmas variáveis, a equipe recolhia a pilha ejetada no empilhador do Leitor de Cartões e a realimentava no compartimento de entrada. Esse ciclo de reintrodução posicionava os cartões como uma memória estática de leitura repetitiva.

Esse meio também atuava como uma expansão do armazenamento temporário para contornar o esgotamento dos contadores internos. Quando um problema matemático complexo gerava uma quantidade de resultados intermediários superior ao número de Acumuladores disponíveis, a máquina acionava a perfuradora periférica para descarregar esses valores elétricos em cartões virgens. Posteriormente, a equipe reintroduzia essa pilha de resultados parciais no Leitor de Cartões para dar prosseguimento à equação, utilizando o papel como um mecanismo externo de armazenamento auxiliar para leitura e escrita cíclica.

## 5.3 Read/Write Memory (Accumulators)
- Como os 20 acumuladores funcionavam como resgistradores temporários/RAM

## 5.4 Read-Only Memory (Function Tables)
- Painéis de interruptores manuais para armazenar constantes/valores fixos

## 5.5 Decimal Ring Counters
- Como funcionava a configuração dos tubos usados para armazenar números de base 10

## 5.6 Decimal Representation
- Como os dados eram armazenados usando contadores em anel (base 10, não binária)

## 5.7 Memory Capacity
- Quantos dados era possível de se armazenar pelas diferentes formas de armazenamento

## 5.8 Access Speed
- O tempo que levava para ler/escrever nas diferentes formas de armazenamento

## 5.9 1953 Upgrade
- Adição posterior de memória de núcleo magnético

![Hardware da memória de núcleo magnético](./images/memory/magnetic-core-memory.jpg)

## 5.10 Modern Comparison
- Como as formas de memória do ENIAC se compara as formas de memória atuais

| ENIAC memory | Modern memory |