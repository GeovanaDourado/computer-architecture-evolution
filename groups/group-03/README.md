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

# Desenvolvimento do Projeto

Após a definição da arquitetura **MISD** e da estrutura inicial do sistema, o projeto será desenvolvido a partir de cinco questões principais.

Essas questões têm como objetivo organizar o desenvolvimento do projeto desde a identificação do problema até os testes e a avaliação da solução.

## Questões Orientadoras

### 1. Problema e solução

**Qual problema o projeto pretende solucionar e como será definida a solução?**

Nesta etapa, será apresentado o problema identificado, a necessidade do sistema e a solução proposta, incluindo sua relação com o conceito da arquitetura MISD.

### 2. Requisitos

**Quais são os requisitos necessários para o funcionamento do sistema?**

Nesta etapa, serão definidos os requisitos **funcionais e não funcionais** do projeto, descrevendo o que o sistema deverá fazer e quais condições deverá atender.

### 3. Arquitetura e componentes

**Como será definida a arquitetura e quais componentes serão utilizados?**

Nesta etapa, serão apresentados os principais componentes do sistema, como **sensores, ESP32, comunicação, computador/servidor, processamento, banco de dados e dashboard**, explicando como eles estarão relacionados.

### 4. Desenvolvimento e processamento

**Como o sistema será desenvolvido e como ocorrerá o processamento dos dados?**

Nesta etapa, será explicado como ocorrerá a implementação do hardware e do software, desde a coleta dos dados pelos sensores até o processamento e as diferentes análises realizadas sobre o mesmo fluxo de dados.

### 5. Testes e avaliação

**Como serão realizados os testes e como será avaliado o funcionamento do projeto?**

Nesta etapa, serão definidos os testes e critérios de avaliação utilizados para verificar se os componentes e as funcionalidades do sistema estão funcionando conforme o esperado.

---

## Organização do desenvolvimento

O projeto seguirá, de forma geral, o seguinte caminho:

```text
┌──────────────────────────────┐
│ 1. PROBLEMA E SOLUÇÃO        │
│ Identificação da necessidade │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ 2. REQUISITOS                │
│ O que o sistema precisa fazer│
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ 3. ARQUITETURA               │
│ Componentes e funcionamento  │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ 4. DESENVOLVIMENTO           │
│ Hardware, software e análise │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ 5. TESTES E AVALIAÇÃO        │
│ Verificação dos resultados   │
└──────────────────────────────┘
```
## Resolução:

# 1. Problema e Solução

> **Questão orientadora:**
> **Qual problema o projeto pretende solucionar e como será definida a solução?**

## 1.1 Identificação do problema

Em ambientes que possuem equipamentos e máquinas em funcionamento, informações como **temperatura, pressão e vibração** podem ser importantes para acompanhar as condições de operação.

Quando esses dados são coletados e analisados manualmente, podem surgir algumas dificuldades:

* demora para identificar alterações nos valores;
* dificuldade para acompanhar vários dados ao mesmo tempo;
* possibilidade de erros durante a análise manual;
* dificuldade para armazenar e consultar informações anteriores;
* ausência de uma visualização centralizada dos dados.

Dessa forma, o projeto propõe o desenvolvimento de um **protótipo de monitoramento de sensores**, capaz de coletar dados, enviá-los para um computador ou servidor e realizar diferentes análises sobre essas informações.

---

## 1.2 Situação sem a solução proposta

Sem um sistema automatizado, o acompanhamento das informações poderia depender de verificações manuais ou de sistemas separados.

Um exemplo seria um responsável precisar verificar individualmente os valores de temperatura, pressão e vibração e posteriormente comparar esses dados para identificar possíveis alterações.

Esse processo pode dificultar a identificação rápida de situações que necessitam de atenção.

A proposta do projeto é centralizar esse processo, permitindo que os dados sejam coletados e encaminhados para diferentes etapas de processamento.

---

## 1.3 Solução proposta

A solução consiste em desenvolver um **protótipo de sistema de monitoramento utilizando sensores conectados a um ESP32**.

O ESP32 será responsável por receber as informações dos sensores e realizar a comunicação com um computador ou servidor.

Após o recebimento dos dados, o sistema poderá realizar diferentes análises utilizando o mesmo fluxo de informações.

Por exemplo, uma mesma leitura de temperatura poderá ser:

1. comparada com um limite definido;
2. comparada com valores históricos;
3. analisada para identificar possíveis alterações ou anomalias.

Assim, diferentes instruções podem trabalhar sobre o **mesmo conjunto de dados**, permitindo demonstrar no projeto o princípio relacionado à arquitetura **MISD**.

---

# 1.4 Resolução em etapas

Para desenvolver a solução proposta, o projeto será dividido em etapas. Essa divisão permite organizar o desenvolvimento desde a coleta das informações até a apresentação dos resultados.

### Etapa 1 — Coleta dos dados

Primeiramente, os sensores serão responsáveis por coletar informações do ambiente ou do equipamento monitorado.

Os dados considerados inicialmente serão:

* **temperatura**;
* **pressão**;
* **vibração**.

```text
┌─────────────────────┐
│       SENSORES      │
├─────────────────────┤
│ Temperatura         │
│ Pressão             │
│ Vibração            │
└──────────┬──────────┘
           ↓
      Dados coletados
```

---

### Etapa 2 — Recebimento pelo ESP32

Após a coleta, os dados serão enviados para o **ESP32**, que funcionará como o microcontrolador responsável por receber essas informações.

```text
Sensores
   ↓
ESP32
```

O ESP32 fará a ligação entre os sensores e as próximas etapas do sistema.

---

### Etapa 3 — Transmissão dos dados

Depois de receber os dados, o ESP32 realizará a transmissão das informações para um computador ou servidor.

Inicialmente, será considerada a utilização de **Wi-Fi**.

```text
Sensores
   ↓
ESP32
   ↓
Wi-Fi
   ↓
Computador / Servidor
```

O protocolo específico de comunicação poderá ser definido posteriormente, durante o desenvolvimento da arquitetura detalhada.

---

### Etapa 4 — Recebimento e organização

O computador ou servidor receberá os dados enviados pelo ESP32.

Nesse momento, as informações serão organizadas para que possam ser utilizadas pelas próximas etapas do sistema.

```text
ESP32
   ↓
Wi-Fi
   ↓
Computador / Servidor
   ↓
Organização dos dados
```

---

### Etapa 5 — Processamento

Depois de organizados, os dados serão encaminhados para o processamento.

Essa é uma das principais etapas relacionadas ao conceito **MISD**, pois o mesmo fluxo de dados poderá ser utilizado por diferentes processos de análise.

```text
                 ┌─→ Análise de limites
                 │
Dados recebidos ─┼─→ Análise histórica
                 │
                 └─→ Análise de anomalias
```

Cada processo terá uma finalidade diferente, mas utilizará os mesmos dados recebidos pelo sistema.

---

### Etapa 6 — Análise dos resultados

Após o processamento, cada análise produzirá um resultado.

Por exemplo, considerando uma determinada temperatura:

```text
Temperatura = 85 °C
       │
       ├──→ Está acima do limite?
       │
       ├──→ Como está em relação ao histórico?
       │
       └──→ Existe alguma alteração fora do padrão?
```

Dessa forma, o sistema poderá gerar informações que auxiliem na interpretação dos dados coletados.

---

### Etapa 7 — Armazenamento

Os dados coletados e os resultados obtidos poderão ser armazenados em um **banco de dados**.

O armazenamento permitirá manter um histórico das informações.

```text
Dados
  ↓
Processamento
  ↓
Resultados
  ↓
Banco de dados
```

Isso possibilitará consultar informações anteriores e utilizá-las em análises futuras.

---

### Etapa 8 — Apresentação das informações

Por fim, os dados e resultados poderão ser apresentados por meio de um **dashboard**.

O objetivo será facilitar a visualização das informações pelo usuário.

```text
┌──────────────────────────────────┐
│       DASHBOARD DE MONITORAMENTO │
├──────────────────────────────────┤
│ Temperatura: 28 °C               │
│ Pressão:     XX                  │
│ Vibração:    XX                  │
│                                  │
│ Status: NORMAL                   │
└──────────────────────────────────┘
```

O dashboard poderá apresentar os valores atuais, resultados das análises e possíveis alertas.

---

# 1.5 Componentes da solução

Para desenvolver o protótipo, serão utilizados diferentes componentes de hardware e software.

### 1.5.1 Sensores

O sistema contará inicialmente com sensores responsáveis pela coleta de diferentes tipos de informações:

| Sensor                | Informação coletada |
| --------------------- | ------------------- |
| Sensor de temperatura | Temperatura         |
| Sensor de pressão     | Pressão             |
| Sensor de vibração    | Vibração            |

Os sensores representam a entrada de dados do sistema.

---

### 1.5.2 ESP32

O **ESP32** será utilizado como microcontrolador do protótipo.

Sua função será receber os dados provenientes dos sensores e encaminhá-los para o restante do sistema.

A escolha do ESP32 está relacionada à possibilidade de trabalhar com sensores e comunicação de rede em um protótipo de baixo custo.

---

### 1.5.3 Comunicação Wi-Fi

A comunicação entre o ESP32 e o computador ou servidor será realizada inicialmente por **Wi-Fi**.

O objetivo será transportar os dados coletados pelos sensores até o sistema responsável pelo processamento.

```text
Sensores
   ↓
ESP32
   ↓
Wi-Fi
   ↓
Computador / Servidor
```

---

### 1.5.4 Computador / Servidor

O computador ou servidor será responsável por receber os dados enviados pelo ESP32 e executar as etapas de processamento.

Nesse ambiente ficará a parte de software responsável pelas análises, armazenamento e disponibilização das informações.

---

### 1.5.5 Processamento dos dados

Depois que os dados forem recebidos, o sistema poderá utilizar diferentes processos para analisar o mesmo fluxo de informações.

Por exemplo:

```text
              ┌─→ Análise de limites
              │
Dados ────────┼─→ Análise estatística
              │
              └─→ Análise de anomalias
```

Cada análise terá uma finalidade diferente, mas poderá utilizar os mesmos dados recebidos pelos sensores.

---

### 1.5.6 Banco de dados

Após o processamento, os resultados poderão ser armazenados em um banco de dados.

O armazenamento permitirá manter um histórico das informações coletadas e dos resultados das análises.

```text
Sensores
   ↓
ESP32
   ↓
Comunicação
   ↓
Processamento
   ↓
Banco de dados
```

---

### 1.5.7 Dashboard

Os dados armazenados e processados poderão ser apresentados em um **dashboard**.

O dashboard terá como objetivo facilitar a visualização das informações, permitindo apresentar valores dos sensores, resultados das análises e possíveis alertas.

---

# 1.6 Fluxo completo da solução

De forma geral, o funcionamento inicial do projeto poderá ser representado da seguinte maneira:

```text
┌───────────────┐
│    Sensores   │
│ Temp./Press./ │
│   Vibração    │
└───────┬───────┘
        ↓
┌───────────────┐
│     ESP32     │
└───────┬───────┘
        ↓
┌───────────────┐
│      Wi-Fi    │
└───────┬───────┘
        ↓
┌───────────────┐
│ Computador /  │
│    Servidor   │
└───────┬───────┘
        ↓
┌────────────────────┐
│ ORGANIZAÇÃO DOS    │
│      DADOS         │
└─────────┬──────────┘
          ↓
┌────────────────────┐
│    PROCESSAMENTO   │
└─────────┬──────────┘
          ↓
   ┌──────┼──────┐
   ↓      ↓      ↓
Limites Histórico Anomalias
   │      │      │
   └──────┼──────┘
          ↓
┌───────────────────┐
│  Banco de Dados   │
└─────────┬─────────┘
          ↓
┌───────────────────┐
│     Dashboard     │
└───────────────────┘
```

---

# 1.7 Relação com o conceito MISD

A relação com o MISD ocorre principalmente na etapa de **processamento**.

O sistema recebe um fluxo de dados proveniente dos sensores e esse mesmo fluxo pode ser utilizado por diferentes análises.

Por exemplo:

```text
                 MESMO FLUXO DE DADOS
                          │
             ┌────────────┼────────────┐
             ↓            ↓            ↓
        Limites       Histórico    Anomalias
             ↓            ↓            ↓
         Resultado     Resultado    Resultado
```

Dessa maneira, o projeto utiliza o conceito de **múltiplas instruções aplicadas sobre um mesmo fluxo de dados** como referência para organizar o processamento.

É importante destacar que o projeto é um **protótipo acadêmico para demonstrar o conceito MISD**. O uso de um computador ou de uma plataforma como referência não significa que o hardware utilizado seja, fisicamente, um processador MISD.

---

# 1.8 Tecnologias inicialmente previstas

As principais tecnologias consideradas para o desenvolvimento são:

| Área                 | Tecnologia                      |
| -------------------- | ------------------------------- |
| Microcontrolador     | ESP32                           |
| Sensores             | Temperatura, pressão e vibração |
| Programação do ESP32 | C/C++                           |
| Processamento        | Python                          |
| Banco de dados       | SQL                             |
| Interface            | HTML, CSS e JavaScript          |
| Comunicação          | Wi-Fi                           |

Essas tecnologias representam a proposta inicial e poderão ser ajustadas durante as próximas etapas do projeto.

---

# 1.9 Escopo inicial

O projeto será desenvolvido inicialmente como um **protótipo acadêmico**.

O objetivo não é construir um sistema industrial certificado, mas demonstrar de forma prática:

* coleta de dados;
* comunicação entre dispositivos;
* armazenamento;
* processamento;
* aplicação de diferentes análises sobre os dados;
* visualização dos resultados;
* relação desses processos com o conceito MISD.

---

# 1.10 Resultado esperado

Ao seguir essas etapas, espera-se que o protótipo seja capaz de:

1. **Coletar** informações dos sensores;
2. **Receber** os dados através do ESP32;
3. **Transmitir** as informações por Wi-Fi;
4. **Organizar** os dados no computador ou servidor;
5. **Processar** o mesmo fluxo de dados;
6. **Realizar diferentes análises**;
7. **Armazenar** os resultados;
8. **Apresentar** as informações no dashboard.

### Fluxo resumido

```text
COLETAR
   ↓
RECEBER
   ↓
TRANSMITIR
   ↓
ORGANIZAR
   ↓
PROCESSAR
   ↓
ANALISAR
   ↓
ARMAZENAR
   ↓
VISUALIZAR
```

---

# 1.11 Conclusão

A solução proposta busca desenvolver um protótipo de monitoramento capaz de integrar **sensores, ESP32, comunicação, processamento, banco de dados e dashboard**.

A principal característica relacionada ao tema do projeto está na utilização de um mesmo fluxo de dados para diferentes processos de análise.

Com isso, o projeto estabelece uma aplicação prática e didática do conceito de **MISD**, servindo como base para as próximas etapas de definição dos requisitos, arquitetura detalhada, desenvolvimento e testes.



