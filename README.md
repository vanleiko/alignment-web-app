Olá! 

Meu nome é Vanessa, sou bióloga, e desde Agosto de 2020 venho aprendendo programação 💻 

Minhas principais áreas de interesse são *Bioinformática* 🧬 e *Ciência de Dados* 🎲

👉 Nesse projeto, desenvolvi uma [**aplicação web no Streamlit**](https://share.streamlit.io/vanleiko/dna-streamlit/main/src/app-dna-v2.py) que realiza o **alinhamento de sequências de DNA**.

Abaixo encontra-se uma breve explicação sobre a importância e sobre os algoritmos de alinhamento de sequências biológicas.

😊

# Alinhamento de sequências de DNA 

Uma das práticas mais comuns na bioinformática é o **alinhamento de sequências biológicas** (DNA, RNA e proteínas).

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/alinhamentos-capa.jpg)

**Por que isso é importante?**

O alinhamento busca por **regiões com similaridades** entre duas ou mais sequências, nos fornecendo informações sobre **relações funcionais, estruturais e evolutivas** dos e entre os seres vivos. 

Várias são as **aplicações** desse método, dentre elas:
- montagem de genomas
- descoberta de novas drogas
- reconstrução da história evolutiva
- buscas em bancos de dados
- análise de variantes
- dedução de função
- definição de regiões conservadas

O alinhamento de sequências pode ser:
- global ou local
- par a par ou múltiplo 

### Alinhamento global

Realizamos o **alinhamento global** quando o objetivo é alinhar toda a extensão das sequências, ou seja, o alinhamento é realizado de ponta a ponta.

O alinhamento global pode ser **par a par**, quando alinhamos duas sequências:

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/alinhamento-global-par.jpg)

ou **múltiplo**, quando três ou mais sequências são alinhadas:

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/alinhamento-global.mul.jpg)

O algoritmo mais utilizado para realizar o alinhamento global par a par é o de **Needleman-Wunsch**, o qual tem uma resolução ótima. Para o alinhamento múltiplo, **CLUSTAL**, de Higgins-Sharp, é o algoritmo mais utilizado, com uma resolução aproximada (heurística). 

### Alinhamento local

O **alinhamento local** busca por região de alta similaridade entre subsequências das sequências analisadas, não importando as regiões adjacentes: 

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/alinhamento-local.jpg)

Para isso, o algoritmo mais utilizado é o de **Smith-Waterman**, que produz uma solução ótima.

### Matriz de pontuação

Os algoritmos de alinhamento par a par analisam o ***score*** de cada alinhamento. O *score* é o resultado da soma das pontuações para ***matches*** (alinhamento de caracteres iguais), ***mismatches*** (alinhamento de caracteres diferentes) e ***gaps*** (inserção ou deleção de caracteres), sendo que os *matches* são recompensados, enquanto *mismatches* e *gaps* são penalizados.

Vamos analisar como ficaria o **alinhamento global** entre as duas sequências abaixo:

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/sequencias.jpg)

Primeiro, vamos considerar um alinhamento mais simples, em que *mismatches* **não são permitidos**, e que a recompensa para *match* é +4 e a penalidade para *gap* é -3:

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/sem-mismatch.jpg)

Por trás dos panos, o algoritmo de Needleman-Wunsch constrói uma matriz pontuando todos os alinhamentos possíveis. 
Para visualizarmos o alinhamento, fazemos o *tracebacking* a partir do **último valor** da matriz e seguimos o caminho do qual cada pontuação se originou, sendo que "↖" indica um *match*, "↑" um *gap* na sequência que está na horizontal da matriz, e "←" um *gap* na sequência que está na vertical da matriz:

![](https://raw.githubusercontent.com/vanleiko/alignment-web-app/main/matriz-sem-mismatch-traceback.png)


Agora vamos analisar um alinhamento que **permite** *mismatches*, sendo este com penalidade de -2:

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/com-mismatch.jpg)

A matriz é semelhante, com a diferença de que agora existe um *mismatch* entre "A" e "C":

![](https://raw.githubusercontent.com/vanleiko/alignment-web-app/main/matriz-com-mismatch-traceback.png)


Podemos ver que o maior *score* está no alinhamento que permite *mismatches* (*score = 25*), sendo esse considerado um melhor alinhamento. Isto porque a penalidade para *gap* é maior visto que, do ponto de vista evolutivo, "há um maior custo" quando acontece uma deleção/inserção de caractere do que quando ocorre uma troca de caractere.

Para o **alinhamento local**, o algoritmo de Smith-Waterman é uma modificação do de Needleman-Wunsch para que sempre que uma pontuação fica com valor negativo, a matriz é reiniciada com zero. Além disso, o *tracebacking* não começa pelo último valor, mas sim pelo **maior valor** da matriz, e termina quando encontra uma pontuação igual a zero. 
O alinhamento local abaixo teria a seguinte matriz:

![](https://raw.githubusercontent.com/vanleiko/alignment-web-app/main/alinhamento-local.jpg)

![](https://raw.githubusercontent.com/vanleiko/alignment-web-app/main/matriz-local-traceback.png)


Não existe uma regra que determine qual deve ser a pontuação para *match, mismatch* e *gap* em alinhamento de nucleotídeos. Para alinhamento de proteínas, existem as **Matrizes de Substituição** (PAM, BLOSUM) as quais contêm as probabilidades das trocas ou manutenção dos aminoácidos.

### Aplicativo para alinhamento de sequências de DNA

Diante dessas informações, construí uma [**aplicação web no Streamlit**](https://share.streamlit.io/vanleiko/dna-streamlit/main/src/app-dna-v2.py) que realiza o alinhamento global e local, par a par, de sequências de DNA, baseado nos algoritmos de Needleman-Wunsch e Smith-Waterman.

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/st-image.png)

Além do alinhamento, esse *web app* também analisa a **Composição de Nucleotídeos** e o **Conteúdo GC** das sequências fornecidas, características importantes em estudos genéticos, evolutivos, taxonômicos e ecológicos, uma vez que fornecem informações sobre o padrão de utilização dos códons, identificação de regiões gênicas, e auxiliam na síntese de vacinas de DNA e no desenho de primers, por exemplo.

👉 *O código, em **Python**, da aplicação web pode ser acessado [aqui](https://github.com/vanleiko/dna-streamlit/blob/main/src/app-dna-v2.py).* 
