## Integrantes:
- Guilherme Henrique Rezende Gonçalves
- João Pedro dos Santos Barcelos
- Marcos Vinicius Vieira de Souza
- Otávio Souza Santos
- Renato Santos Kitada
- Victor Francisco Rodrigues Pereira Melo

## Arquitetura escolhido: 
- Arquitetura Harvard 

## Breve contexto histórico: 
- O nome Harvard está associado ao Harvard IBM Mark I, concebido por Howard Aiken em 1937 e desenvolvido em colaboração com a IBM. O Mark I entrou em operação em Harvard em 1944 e tornou-se um marco nos primeiros computadores programáveis.

## Características técnicas básicas:
- Duas memórias separadas: O sistema possui uma memória de programa (onde ficam as instruções de código) e uma memória de dados (onde ficam as variáveis e informações temporárias) em locais físicos distintos.Barramentos independentes: Cada tipo de memória tem seu próprio conjunto de caminhos de ligação (barramentos) com o processador.Acesso em paralelo: O processador consegue buscar uma nova instrução de código e ler ou gravar um dado ao mesmo tempo, o que acelera o funcionamento do sistema

## Memória:
- Na arquitetura Harvard, existem duas memórias separadas: uma para armazenar instruções e outra para armazenar dados. Isso permite que o processador acesse instruções e dados ao mesmo tempo, tornando o processamento mais rápido.

## Entrada/saída:
- As unidades de E/S permitem a comunicação com sensores, atuadores, periféricos e usuário. No trabalho, também é mencionado que periféricos podem ser acessados pelo espaço de dados, por exemplo através de Memory-Mapped I/O.

## Importância dessa arquitetura para a evolução da computação:
- A principal contribuição da organização Harvard foi mostrar as vantagens de separar os caminhos de instruções e dados, permitindo que o processador acesse ambos de forma independente. Isso reduz a disputa pelo barramento, aumenta o paralelismo e pode elevar o desempenho. Esse princípio tornou-se especialmente relevante em microcontroladores, sistemas embarcados e processadores de sinais digitais (DSPs). 