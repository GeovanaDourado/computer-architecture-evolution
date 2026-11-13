# 12. Legacy

## 12.1 Historical Importance

A importância histórica do ENIAC reside no fato de ter sido o primeiro computador digital eletrônico programável e de propósito geral a entrar em operação. Concluído no final de 1945 e apresentado publicamente em fevereiro de 1946 na Moore School of Electrical Engineering da Universidade da Pensilvânia, o projeto liderado por John Mauchly e J. Presper Eckert reuniu, em uma única máquina, características que antes só existiam de forma isolada em calculadoras mecânicas, analisadores diferenciais analógicos ou equipamentos eletromecânicos dedicados. Ao substituir engrenagens e relés por mais de 17 mil válvulas eletrônicas e incorporar desvios condicionais, o ENIAC alcançou uma capacidade de processamento sem precedentes, inaugurando a era da computação eletrônica em larga escala.

Um dos maiores marcos práticos do sistema foi demonstrar a viabilidade técnica de circuitos eletrônicos gigantescos. Na década de 1940, muitos engenheiros duvidavam que um equipamento com dezenas de milhares de válvulas pudesse operar por tempo suficiente sem falhas contínuas por superaquecimento ou queima de filamentos. Apesar da manutenção constante exigida, o ENIAC permaneceu em serviço ativo até outubro de 1955 e, durante o auge de sua operação entre o final da década de 1940 e o início da década de 1950, realizou mais operações aritméticas do que todos os demais computadores existentes combinados.

### 12.1.1 Influence on Modern Architecture and Industry
Embora a arquitetura física do ENIAC não tenha sido copiada diretamente em máquinas posteriores, suas limitações práticas impulsionaram o maior salto conceitual da história da computação. Como reconfigurar cabos e chaves para cada novo problema podia levar dias, a própria equipe envolvida no projeto (junto a John von Neumann) concebeu o seu sucessor, o EDVAC, baseado no conceito de programa armazenado em memória e na aritmética binária. Esse modelo, consolidado como arquitetura de von Neumann, estabeleceu o ciclo de busca, decodificação e execução que ainda fundamenta os processadores modernos.

O impacto institucional também foi decisivo para transformar protótipos acadêmicos em uma indústria global. Em 1946, as palestras ministradas na Moore School difundiram os princípios de projeto de computadores eletrônicos para pesquisadores dos Estados Unidos e da Europa, acelerando a criação de novas máquinas em universidades e laboratórios. Pouco depois, Eckert e Mauchly fundaram a Eckert-Mauchly Computer Corporation e desenvolveram o UNIVAC I, entregue em 1951 ao Departamento do Censo norte-americano, marcando a transição da computação estritamente militar e científica para o mercado comercial e administrativo.

### 12.1.2 Foundations of Computer Programming
O ENIAC também desempenhou um papel fundamental na consolidação da programação como atividade intelectual e técnica. As seis primeiras programadoras da máquina (Kay McNulty, Betty Jennings, Betty Snyder, Marlyn Wescoff, Fran Bilas e Ruth Lichterman), recrutadas originalmente como calculistas humanas no Laboratório de Pesquisa Balística, precisaram aprender a operar o sistema estudando diretamente seus diagramas lógicos, sem manuais ou precedentes. Ao decompor equações complexas em fluxos de controle, desvios condicionais e rotinas reutilizáveis, elas estabeleceram práticas essenciais da engenharia de software.

> Nota: Durante a inauguração pública do ENIAC em fevereiro de 1946, o trabalho das seis programadoras recebeu pouco reconhecimento formal, e seus nomes ficaram fora dos eventos comemorativos e de grande parte da cobertura inicial da imprensa. Somente décadas mais tarde a historiografia da computação resgatou sua contribuição decisiva, assim como o papel de Klára Dán von Neumann na adaptação do ENIAC para executar códigos armazenados a partir de 1948.

## 12.2 Scientific Contributions

Concebido originalmente para acelerar o cálculo de tabelas de tiro de artilharia para o Exército dos Estados Unidos, o ENIAC rapidamente provou ser capaz de resolver problemas matemáticos muito além da balística. Graças à flexibilidade de sua arquitetura programável, a máquina tornou-se o principal instrumento de computação científica entre 1946 e o início da década de 1950, permitindo que pesquisadores abordassem equações diferenciais não lineares e simulações de grande escala que seriam inviáveis por métodos manuais ou mecânicos.

### 12.2.1 Ballistics, Aerodynamics, and Physics
No campo militar e da engenharia aplicada, o ENIAC transformou a produção de tabelas balísticas. Uma única trajetória de projétil, considerando variáveis como temperatura, umidade, resistência do ar e vento, exigia até 40 horas de trabalho em calculadoras mecânicas de mesa ou cerca de 30 minutos em analisadores diferenciais analógicos; no ENIAC, o cálculo passava a ser concluído em poucos segundos. Além da artilharia, a máquina foi amplamente empregada em estudos de aerodinâmica e no projeto de túneis de vento supersônicos, em cálculos de ignição térmica e em pesquisas sobre raios cósmicos, como no contrato do Projeto Chore para a Universidade de Chicago.

### 12.2.2 Nuclear Physics and Monte Carlo Simulations
De forma emblemática, o primeiro cálculo prático executado no ENIAC, em dezembro de 1945, não foi uma tabela de artilharia, mas um problema confidencial enviado pelo Laboratório Nacional de Los Alamos envolvendo a viabilidade da bomba de hidrogênio. Anos depois, em abril de 1948, uma equipe formada por John von Neumann, Klára Dán von Neumann, Nicholas Metropolis e Stanislaw Ulam utilizou o ENIAC (já modificado para ler códigos armazenados nas Tabelas de Função) para rodar as primeiras simulações computacionais pelo método de Monte Carlo.

Ao modelar estatisticamente o comportamento e o percurso de nêutrons em materiais físseis por meio de números pseudoaleatórios, essas execuções validaram a abordagem estocástica em larga escala. O sucesso obtido no ENIAC popularizou o método de Monte Carlo e inaugurou a simulação computacional moderna como ferramenta indispensável na física nuclear, na química, na biologia e na economia.

### 12.2.3 Numerical Weather Prediction
Em 1950, o ENIAC foi palco de outro marco científico histórico: a realização das primeiras previsões numéricas do tempo bem-sucedidas por computador. Liderado pelos meteorologistas Jule Charney e Ragnar Fjortoft ao lado de John von Neumann (com programação e gerenciamento de cerca de 100 mil cartões perfurados conduzidos por Klára Dán von Neumann), o experimento traduziu equações simplificadas da dinâmica atmosférica em rotinas executáveis pela máquina.

Embora o processamento completo de uma previsão de 24 horas levasse aproximadamente 24 horas devido ao tempo de leitura e reinserção dos cartões perfurados, o resultado demonstrou pela primeira vez que equações físicas podiam prever estados futuros da atmosfera antes mesmo que os fenômenos ocorressem. Esse experimento estabeleceu as bases práticas da meteorologia computacional e dos modelos climáticos atuais.

### 12.2.4 Computational Mathematics
Na matemática pura e aplicada, o ENIAC inaugurou o uso de computadores eletrônicos para investigar constantes matemáticas e testar hipóteses estatísticas. Em 1949, atendendo a uma sugestão de John von Neumann e Nicholas Metropolis para analisar a aleatoriedade na distribuição dos dígitos de constantes transcendentes, o matemático George Reitwiesner programou o ENIAC para calcular o valor de Pi com 2.037 casas decimais e, em seguida, o número de Euler (constante e) com mais de 2.000 casas decimais (resultados publicados em 1950).

> Nota: Como o ENIAC não possuía memória interna suficiente para reter milhares de dígitos simultaneamente, o cálculo de Pi exigiu cerca de 70 horas contínuas de operação nas quais os cartões perfurados de saída precisavam ser constantemente reinseridos no leitor de entrada como dados intermediários. Ainda assim, esse feito rompeu séculos de cálculos manuais e deu início à era computacional da teoria dos números.

## 12.3 Industrial Impact

## 12.4 Social Impact

## 12.5 Influence on Modern Computing

## 12.6 Lessons Learned

## 12.7 Future Perspectives
