# Group 03

## Architecture

To be defined

---

## Members

- Tiago Henrique Souza Lima
-Emanuel Borges Vale
-Elaine Cardoso de Souza Barros
-Augusto Spolavori Siqueira
-Joao Guilherme Alves de Souza Oliveira
-João Victor Ferreira de Lima Moura

---

## Weekly Progress

| Week | Status |
|-------|---------|
|1|⬜|O MISD é, portanto, a categoria em que várias instruções — ou várias funções distintas — atuam sobre o mesmo fluxo de dados. Ela deve ser entendida como uma classificação conceitual dentro da taxonomia, e não como o nome de uma arquitetura comercial específica ou de uma família de processadores amplamente disponível. Diferentemente de SISD, SIMD e MIMD, que descrevem organizações comuns em computadores de uso geral, o MISD tem ocorrência prática rara, e a literatura não é unânime sobre quais sistemas reais se enquadram nela — ponto que retomamos nas questões de investigação, ao final deste documento.

|2|⬜|2. Qual é a ideia central? O problema arquitetural que o MISD representa é: como aplicar processamentos diferentes a uma mesma entrada, sem exigir que todas as unidades executem a mesma operação? A resposta conceitual é distribuir o fluxo de dados para caminhos distintos de execução, cada um respondendo a uma pergunta ou aplicando uma função diferente sobre o mesmo dado. Ao final, esses resultados podem ser comparados, combinados ou usados como base para uma decisão. Isso é justamente o que diferencia o MISD do SIMD: no SIMD, uma única instrução é replicada sobre vários dados; no MISD, várias instruções distintas analisam o mesmo dado. São lógicas opostas dentro da mesma taxonomia, e é comum haver confusão entre as duas — algo que procuramos evitar ao longo deste trabalho

|3|⬜| Para que serve essa organização? A literatura associa o princípio MISD a situações em que um mesmo dado precisa ser submetido a análises independentes — por exemplo, quando se deseja comparar os resultados de diferentes algoritmos aplicados à mesma entrada, ou quando a redundância de processamento é usada como mecanismo de verificação. Esse tipo de necessidade aparece com mais frequência em sistemas onde a confiabilidade do resultado importa mais do que a simplicidade da arquitetura, como em contextos de checagem cruzada de sinais. Tratamos essa aplicação como uma motivação conceitual, não como uma lista fechada de usos comprovados, já que exemplos comerciais inequívocos são difíceis de identificar.

|4|⬜|FONTE / SENSOR │ ▼ FLUXO ÚNICO DE DADOS (D) │ ▼ CONTROLADOR  —  recebe D e disponibiliza o mesmo fluxo a caminhos distintos │ ┌─────────────┬──────────────┬──────────────┬─────────────┐ ▼             ▼              ▼              ▼ UNIDADE A     UNIDADE B      UNIDADE C      UNIDADE D verificar     analisar       detectar       validar limite        tendência      anomalia       o dado │             │              │              │ └─────────────┴──────────────┴──────────────┘ │  resultados RA, RB, RC, RD ▼ COMPARADOR / VOTADOR  —  consolida os resultados │ ▼ SAÍDA / DECISÃO  (registro, alerta ou comando)

|5|⬜|Componente Papel na proposta do grupo Observação técnica Fonte / sensor Fornece o valor ou sinal de entrada compartilhado. Definido pela aplicação; não faz parte da taxonomia. Controlador Recebe o fluxo e o disponibiliza às unidades de processamento. Não existe um controlador MISD padronizado. Unidades de processamento Executam instruções diferentes sobre o mesmo dado. Quantidade e função dependem do projeto. Registradores Guardam operandos e resultados locais de cada unidade. Conjunto definido pela implementação escolhida. Memória e cache Armazenam instruções, dados e resultados intermediários. Hierarquia não é imposta pela taxonomia. Interconexão Transporta dados e sinais de controle entre os blocos. Pode ser barramento, canais dedicados ou rede-on-chip. Comparador / votador Consolida RA–RD em uma saída única. Regra de decisão é definida pela aplicação

|6|⬜|Entrada uma fonte externa fornece o dado D. 2 · Aquisição o controlador recebe D. 3 · Distribuição o mesmo D é disponibilizado a caminhos de processamento distintos. 4 · Execução concorrente cada unidade aplica sua própria instrução ou função sobre D. 5 · Consolidação os resultados são comparados, combinados ou avaliados por uma regra de decisão. 6 · Saída - Exemplo didático: um sensor fornece a leitura 85 °C. A Unidade A poderia executar verificarLimite(85); a Unidade B, analisarTendência(85, histórico); a Unidade C, detectarAnomalia(85, contexto); e a Unidade D, validarSensor(85). Cada função responde a uma pergunta diferente sobre a mesma entrada, e o comparador poderia então classificar o resultado como NORMAL, ATENÇÃO ou ALERTA. Esse exemplo tem finalidade exclusivamente didática — não descreve um sistema real documentado.

|7|⬜|A Taxonomia de Flynn classifica a relação entre fluxos de instruções e de dados; ela não define, por si só, a organização de memória, cache, registradores ou conjunto de instruções de um sistema. Por isso, distinguimos a classificação MISD — que é conceitual — da implementação física, que é uma decisão de projeto separada. Em uma organização possível, a memória principal manteria instruções, dados e estados; a cache reduziria a latência de acessos repetidos; os registradores guardariam operandos locais de cada unidade; e uma área de resultados reuniria as saídas RA a RD antes da consolidação. Quando várias unidades leem o mesmo dado, a interconexão e as políticas de consistência de memória precisam evitar gargalos e leituras divergentes — mas, novamente, isso depende da implementação escolhida, não da classificação MISD em si.

|8|⬜|Como ocorre a comunicação O caminho crítico da proposta é entrada → distribuição → unidades → consolidação → saída. Uma implementação concreta poderia usar barramentos compartilhados, canais ponto a ponto, controladores de memória dedicados, interfaces de E/S e mecanismos de sincronização entre as unidades. A escolha entre essas opções depende de fatores como latência, largura de banda disponível, confiabilidade exigida, custo e número de unidades envolvidas. Os principais desafios de comunicação em uma organização desse tipo seriam: latência na distribuição do fluxo compartilhado, disputa por largura de banda entre as unidades, sincronização entre caminhos com tempos de execução diferentes, possíveis gargalos no controlador, consistência dos dados lidos simultaneamente e integridade do dado original ao longo de todo o percurso. Como o grupo ainda não implementou nenhuma dessas soluções, essas afirmações devem ser lidas como hipóteses de projeto a serem aprofundadas.

|9|⬜|O paralelismo do MISD aparece quando diferentes instruções processam o mesmo fluxo de dados de forma simultânea ou sobreposta. Isso o diferencia do paralelismo típico do SIMD, cujo objetivo costuma ser aumentar o throughput aplicando a mesma operação a muitos dados de uma vez. No MISD, o ganho não é necessariamente de velocidade bruta: é a possibilidade de obter, ao mesmo tempo, diferentes interpretações do mesmo dado — o que favorece redundância, comparação e, em tese, maior confiabilidade do resultado final.

|10|⬜|Vantagem principal e limitações Vantagem principal Permitir que um mesmo fluxo de dados seja submetido a operações diferentes, favorecendo diversidade de análise, comparação de resultados e, em aplicações críticas, maior tolerância a falhas. Principais limitações • organização rara, com poucos exemplos comerciais inequívocos; • replicação de unidades, interconexões e mecanismos de consolidação aumenta custo e consumo de energia; • maior complexidade de sincronização entre as unidades; • ausência de padronização dificulta comparação entre implementações.
|11|⬜|
|12|⬜|
|13|⬜|
|14|⬜|
|15|⬜|

---
