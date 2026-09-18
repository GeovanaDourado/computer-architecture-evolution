# 2. System Overview

## 2.1 General Description

O ENIAC foi um "super-computador" para sua geração. Ele era um aparato gigantesco em formato de U, ocupando uma sala de 167 metros quadrados, pesando aproximadamente 30 toneladas e consumindo 150 mil watts de energia. Diferente dos computadores modernos, ele era altamente modular e decentralizado, composto de 40 painéis distintos que podiam operar em paralelo, ligados entre si por uma grande quantidade de cabos também modulares.

## 2.2 Main Components

- **CPU**: A CPU não era uma unidade centralizada como geralmente imaginamos. O processamento matemático era disbtribuído entre os Acumuladores (faziam soma e/ou subtração), Multiplicador de alta velocidade (faziam Multiplicações) e o Divisor/Raiz "Quadrador" (divisão e raiz quadrada). O controle e a sincronização operacional da arquitetura eram feitos pelo "Pogramador Mestre" (controlava loops e a sequência de execução) e pela Unidae Ciclíca (que gerava pulsos de clock a 100kHz). Esses últimos dois seriam o mais semelhante à um CPU para o ENIAC.
- **Memory**: A memória principal era composta por: 1. 20 Acumuladores, que armazenavam dados temporariamente (continuavam salvos enquanto o ENIAC se mantia ligado) para realização de contas; 2. Tabelas de Função, que eram painéis com chaves mecânicas que funcionavam como uma memória ROM para constantes matemáticas e valores que seriam reutilizados várias vezes durante a operação do ENIAC (similar à uma variável, como concebemos atualmente!).
- **Bus**: A comunicação entre as diferentes partes da arquitetura era feita por duas redes de cabos separadas. As Bandejas de Dados transportavam os números decimais entre as unidade. As Linhas de Programa transportavam pulsos elétricos de controle que sinalizavam às unidade quando iniciar sua operação.
- **I/O**: O ENIAC utilizava equipamento da IBM para tratar do input/output. A entrada era feita por uma leitora de cartões perfurados conectada ao Transmissor Constante. A saída era feita por uma perfuradora de cartões conectada à unidade de impressão.

- (Podemos reescrever isso aqui tratando dos reais componentes do ENIAC (as diferentes unidades, suas funções e funcionamento))

## 2.3 Block Diagram

(Add image)

## 2.4 Data Flow

Explain how data moves through the architecture.

## 2.5 Main Characteristics

Table

| Feature | Description |
|---------|-------------|
