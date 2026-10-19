# 4. Memory Organization

## 4.1 Organização do armazenamento
A Arquitetura de Harvard organiza o armazenamento do computador em dois espaços distintos: a memória de instruções e a memória de dados. A memória de instruções é responsável por armazenar os comandos que orientam o processador sobre quais operações devem ser executadas, enquanto a memória de dados guarda as informações utilizadas durante o processamento, como números, variáveis e resultados intermediários. Essa separação permite que o processador busque instruções e acesse dados simultaneamente, desde que a implementação possua caminhos de comunicação independentes e recursos adequados. Dessa forma, é possível reduzir a disputa pelo acesso à memória e melhorar o desempenho do sistema. Apesar de desempenharem funções diferentes, os dois espaços trabalham em conjunto durante a execução dos programas: as instruções determinam as operações, e os dados fornecem as informações necessárias para realizá-las. É importante destacar que a Arquitetura de Harvard não exige uma tecnologia específica para essas memórias, pois seu princípio fundamental está na separação entre o armazenamento e o acesso às instruções e aos dados.

## 4.2 RAM

## 4.3 ROM

## 4.4 Cache

## 4.5 Storage
Na Arquitetura Harvard clássica, os limites de armazenamento e velocidade dependem estritamente das tecnologias físicas adotadas na implementação analisada, não sendo uma limitação do modelo teórico em si. 

Tomando como caso concreto o **Harvard Mark I (IBM ASCC)**, o sistema utilizava suportes eletromecânicos e físicos distintos para guardar instruções e dados:

### 1. Tecnologias Utilizadas
* **Memória de Programa (Instruções):** Utilizava fita de papel perfurada de 24 canais. As instruções eram lidas mecanicamente sequência a sequência através de contactos elétricos que detetavam os furos na fita.
* **Memória de Dados (Variáveis e Registos):** Utilizava relés eletromecânicos e contadores de rodas dentadas (acumuladores mecânicos) para armazenar valores numéricos temporários durante os cálculos.

### 2. Capacidade de Armazenamento
* **Capacidade de Dados:** O sistema possuía 72 acumuladores mecânicos principais para armazenamento de dados temporários, onde cada acumulador conseguia guardar um número de até 23 dígitos decimais (mais um sinal positivo/negativo).
* **Capacidade de Instruções:** Praticamente ilimitada na prática, pois dependia apenas do comprimento físico da fita de papel perfurada fornecida ao leitor.

### 3. Velocidade e Limitações de Acesso
* **Velocidade de Leitura de Instruções:** A leitura da fita de papel era limitada pelo avanço mecânico do leitor, operando a uma taxa aproximada de **200 passos por minuto** (cerca de 3,3 instruções por segundo).
* **Tempo de Acesso aos Dados:** O tempo de acesso e modificação dos acumuladores mecânicos era determinado pela rotação dos eixos e acionamento dos relés, levando cerca de **0,3 segundos para adições/subtrações** e até **6 segundos para multiplicações**.
* **Impacto no Funcionamento do Sistema:** A extrema lentidão no acesso mecânico e a impossibilidade de realizar desvios condicionais simples na fita (saltos/loops dinâmicos sem intervenção manual ou fitas em loop fechado) faziam com que o tempo global de execução dependesse do ritmo dos componentes eletromecânicos e da preparação correta das mídias físicas.
## 4.6 Memory Capacity

## 4.7 Comparison with Modern Systems

Table
