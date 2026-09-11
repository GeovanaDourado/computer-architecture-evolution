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

### Arquitetura/Processador Escolhido

**Arquitetura MISD (Multiple Instruction, Single Data)**

A arquitetura escolhida para o desenvolvimento deste projeto é a **MISD (Multiple Instruction, Single Data — Múltiplas Instruções, Um Único Dado)**, uma das classificações propostas pela taxonomia de Flynn para organização de sistemas computacionais paralelos.

Nesse modelo, **diferentes unidades de processamento podem executar instruções distintas sobre um mesmo fluxo de dados**. Dessa forma, enquanto uma arquitetura tradicional pode executar uma única operação por vez sobre determinado dado, a MISD permite que diferentes operações sejam realizadas de maneira paralela ou coordenada sobre o mesmo conjunto de informações.

A escolha da MISD está relacionada à possibilidade de analisar um mesmo dado sob diferentes perspectivas de processamento, sendo uma arquitetura conceitualmente adequada para cenários que exigem **processamento paralelo, redundância, análise simultânea e respostas rápidas**.

No contexto deste projeto, a arquitetura será estudada considerando sua **organização, funcionamento, fluxo de dados, unidades de processamento e aplicação prática**, relacionando esses elementos aos conceitos de paralelismo e organização de computadores abordados na disciplina.

### Breve Contexto Histórico e Modelo da Arquitetura MISD:

A arquitetura **MISD (Multiple Instruction, Single Data)** surgiu no contexto das pesquisas sobre **processamento paralelo**, sendo formalmente classificada na **Taxonomia de Flynn**, proposta por Michael J. Flynn em 1966. Essa classificação organiza os computadores de acordo com os fluxos de instruções e de dados, dividindo-os em SISD, SIMD, MISD e MIMD.

Na MISD, **múltiplas instruções são executadas sobre um único fluxo de dados**. Assim, o mesmo dado pode ser encaminhado para diferentes unidades de processamento, cada uma realizando uma operação distinta. Embora seja uma arquitetura pouco comum em computadores de uso geral, seu conceito teve importância no desenvolvimento de sistemas paralelos e especializados, principalmente em aplicações que exigem **confiabilidade, redundância e processamento simultâneo**.

De forma simplificada, seu modelo pode ser representado como:

**Um fluxo de dados → múltiplas instruções → diferentes unidades de processamento → resultados.**

Dessa forma, a MISD representa uma abordagem específica de paralelismo, na qual diferentes operações podem analisar ou transformar o mesmo dado de maneira simultânea ou coordenada.


### Características Técnicas Básicas

**ISA (Instruction Set Architecture):**
A arquitetura MISD não possui uma ISA própria. Por ser um modelo de organização de processamento, pode utilizar diferentes conjuntos de instruções, dependendo do processador ou sistema empregado. A característica principal está na execução de **múltiplas instruções sobre um mesmo fluxo de dados**, e não no conjunto específico de instruções.

**Tamanho da palavra:**
Também não existe um tamanho de palavra definido pela arquitetura MISD. Essa característica depende do processador utilizado na implementação. Podem ser utilizados processadores com palavras de **32 ou 64 bits**, por exemplo. Portanto, o tamanho da palavra deve ser especificado de acordo com o processador escolhido para representar ou implementar o modelo MISD.

**Em resumo:** a MISD define principalmente **como instruções e dados são processados**, enquanto características como ISA, número de bits, registradores e frequência dependem da implementação utilizada.


### Processador/Família Escolhida

**Família escolhida: Intel Xeon**

A família **Intel Xeon** foi escolhida como referência para o projeto por ser voltada a servidores e sistemas de alto desempenho, oferecendo processamento de **64 bits, múltiplos núcleos e recursos de processamento paralelo**.

No projeto de sensores, o Xeon pode atuar como **processador do servidor responsável por receber e analisar os dados coletados pelos sensores**. O mesmo dado poderá ser submetido a diferentes operações, como verificação de limites, análise de falhas e armazenamento, permitindo relacionar o sistema aos conceitos da arquitetura **MISD**.

**Observação:** O **Intel Xeon não é um processador MISD puro**, mas será utilizado como **referência de hardware e plataforma de processamento para o projeto**. A arquitetura **MISD será adotada como modelo conceitual** para representar o processamento de um mesmo fluxo de dados por diferentes instruções, permitindo demonstrar como os dados coletados pelos sensores podem passar por diferentes etapas de análise dentro do sistema.

### Memória

No projeto, a memória será responsável por **armazenar temporariamente os dados coletados pelos sensores e disponibilizá-los ao processador para serem analisados**. Como referência, o servidor equipado com processador Intel Xeon poderá utilizar **memória RAM DDR4 ou DDR5**, oferecendo velocidade adequada para o processamento contínuo das informações.

Quando um sensor realiza uma leitura, como temperatura, pressão ou vibração, o dado é enviado ao servidor e armazenado inicialmente na **memória RAM**. O processador então acessa essas informações para realizar os cálculos e análises necessários. Como a RAM é uma memória de acesso rápido, ela permite que os dados sejam lidos e processados rapidamente durante o funcionamento do sistema.

Após o processamento, os resultados podem ser enviados para um **banco de dados ou armazenamento permanente**, enquanto os dados temporários permanecem na RAM apenas enquanto forem necessários.

No projeto, o fluxo pode ser representado da seguinte forma:

**Sensor → Memória RAM → Processador → Análise dos dados → Banco de dados**

Assim, a memória atua como uma **ponte de alta velocidade entre a coleta dos dados e o processamento**, garantindo que as informações dos sensores estejam disponíveis rapidamente para as diferentes operações realizadas pelo sistema.


### Entrada/Saída (E/S)

Na arquitetura **MISD (Multiple Instruction, Single Data)**, os mecanismos de entrada e saída são responsáveis por permitir a comunicação entre o sistema de processamento e o ambiente externo. Os dispositivos de entrada fornecem os dados que serão processados, enquanto os dispositivos de saída recebem ou apresentam os resultados gerados pelo processamento.

De forma geral, os dados entram no sistema por meio de dispositivos como **sensores, interfaces de comunicação ou outros equipamentos de aquisição**. Após serem recebidos e armazenados temporariamente na memória, esses dados são encaminhados para diferentes unidades ou etapas de processamento, nas quais **instruções distintas podem ser executadas sobre o mesmo fluxo de dados**. Depois do processamento, os resultados podem ser enviados para dispositivos de saída ou armazenados para utilização posterior.

O fluxo básico pode ser representado como:

**Entrada → Memória → Múltiplas instruções → Processamento → Saída**

### Aplicação no Projeto de Sensores

No projeto, os **sensores serão os principais dispositivos de entrada**, responsáveis por coletar informações como temperatura, pressão e vibração. Esses dados serão enviados ao servidor por meio de uma rede de comunicação e armazenados temporariamente na memória.

Em seguida, o sistema poderá utilizar diferentes processos para analisar o mesmo dado. Por exemplo, uma mesma leitura de temperatura pode ser utilizada para **verificar limites de segurança, calcular estatísticas, identificar anomalias e gerar alertas**.

Após essas análises, os resultados serão enviados para dispositivos de saída, como **computadores, smartphones ou um painel de monitoramento**, além de poderem ser armazenados em um banco de dados.

Assim, no projeto, o fluxo será:

**Sensores → Comunicação → Memória → Processamento MISD → Resultados → Interface/Alertas/Banco de dados**


### Importância da Arquitetura MISD para a Evolução da Computação

A arquitetura **MISD** foi importante para a evolução da computação por contribuir para o desenvolvimento de técnicas de **processamento paralelo, redundância e confiabilidade**. Um exemplo marcante de aplicação desses conceitos pode ser encontrado nos sistemas computacionais utilizados no **Ônibus Espacial (Space Shuttle)**.

Nos sistemas de controle de voo do ônibus espacial, computadores trabalhavam de forma redundante para aumentar a segurança da missão. As informações recebidas dos sensores podiam ser processadas por diferentes unidades, permitindo comparar resultados e identificar possíveis falhas. Essa abordagem demonstrava como o processamento paralelo e a redundância poderiam ser utilizados em sistemas nos quais um erro poderia causar consequências graves.

Esse tipo de aplicação ajudou a demonstrar a importância de utilizar **múltiplos processamentos sobre informações críticas**, contribuindo para o desenvolvimento de sistemas computacionais mais confiáveis.

Atualmente, princípios semelhantes podem ser encontrados em sistemas de **aviação, automação industrial, veículos autônomos, equipamentos médicos e sistemas de monitoramento**, nos quais diferentes análises podem ser realizadas sobre os mesmos dados para aumentar a segurança e a eficiência.

No nosso projeto de sensores, esse conceito pode ser aplicado de uma forma bem prática. Os sensores irão coletar informações do ambiente, como **temperatura, pressão e vibração**, e esses mesmos dados poderão ser enviados para diferentes processos de análise. Por exemplo, uma leitura de temperatura pode, ao mesmo tempo, ser utilizada para verificar se está dentro do limite considerado seguro, analisar se houve alguma alteração fora do padrão e identificar uma possível falha no equipamento. Caso seja detectado algum problema, o sistema poderá gerar um alerta para o responsável.

Dessa forma, em vez de utilizar o dado coletado para apenas uma função, podemos aproveitar a mesma informação para realizar **várias análises diferentes**, tornando o sistema mais completo e confiável. Essa aplicação mostra como os conceitos relacionados à MISD podem ser utilizados no nosso projeto para melhorar o monitoramento dos sensores e permitir uma resposta mais rápida quando alguma situação anormal for identificada.

### Fluxograma de Funcionamento da Arquitetura MISD no Projeto de Sensores

                 ┌───────────────┐
                 │    INÍCIO     │
                 └───────┬───────┘
                         │
                         ▼
              ┌─────────────────────┐
              │   SENSORES (ENTRADA)│
              │ Temperatura, pressão│
              │    e vibração       │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ TRANSMISSÃO DOS     │
              │       DADOS         │
              │ Wi-Fi / 4G / 5G /   │
              │      Ethernet       │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │    MEMÓRIA RAM      │
              │ Armazena os dados   │
              │ temporariamente     │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │   MODELO MISD       │
              │ Mesmo dado recebe   │
              │ diferentes          │
              │ instruções          │
              └──────────┬──────────┘
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
   ┌────────────┐ ┌────────────┐ ┌────────────┐
   │ PROCESSO 1 │ │ PROCESSO 2 │ │ PROCESSO 3 │
   │ Verificar  │ │ Análise    │ │ Detectar   │
   │ limites    │ │ estatística│ │ anomalias  │
   └─────┬──────┘ └─────┬──────┘ └─────┬──────┘
         │              │              │
         ▼              ▼              ▼
   ┌────────────┐ ┌────────────┐ ┌────────────┐
   │ Resultado 1│ │ Resultado 2│ │ Resultado 3│
   │ Temperatura│ │ Média /    │ │ Falha ou   │
   │ normal?    │ │ tendência  │ │ anomalia?  │
   └─────┬──────┘ └─────┬──────┘ └─────┬──────┘
         │              │              │
         └──────────────┼──────────────┘
                        │
                        ▼
              ┌─────────────────────┐
              │ CONSOLIDAÇÃO DOS    │
              │     RESULTADOS      │
              │ Analisa todas as    │
              │ respostas obtidas   │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │    SAÍDA / AÇÃO     │
              │ Dashboard, aplicativo│
              │ ou alerta ao usuário│
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ BANCO DE DADOS      │
              │ Armazenamento dos   │
              │ resultados e histórico│
              └──────────┬──────────┘
                         │
                         ▼
                 ┌───────────────┐
                 │      FIM      │
                 └───────────────┘



---
