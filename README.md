Olá! 

Meu nome é Vanessa, sou bióloga, e desde Agosto de 2020 venho aprendendo programação 💻 

Minhas principais áreas de interesse são *Bioinformática* 🧬 e *Ciência de Dados* 🎲.

Nesse projeto, desenvolvi uma [**aplicação web no Streamlit**](https://share.streamlit.io/vanleiko/dna-streamlit/main/src/app-dna-v2.py) que realiza o **alinhamento de sequências de DNA**.

Abaixo encontra-se uma breve explicação sobre a importância e sobre como funciona o alinhamento de sequências biológicas.

😊

# Alinhamento de sequências de DNA 

Uma das práticas mais comuns na bioinformática é o **alinhamento de sequências biológicas** (DNA, RNA e proteínas).

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/alinhamentos-capa.jpg)

**Por que isso é importante?**

O alinhamento busca por **regiões com similaridades** entre duas ou mais sequências, nos fornecendo informações sobre **relações funcionais, estruturais e evolutivas**. 

Várias são as **aplicações** desse método, dentre elas:
- montagem de genomas
- descoberta de novas drogas
- reconstrução da história evolutiva
- buscas em bancos de dados
- análise de variantes
- dedução de função
- definição de regiões conservadas

O alinhamento de sequências pode ser global ou local, par a par ou múltiplo. 

### Alinhamento global

Realizamos o **alinhamento global** quando o objetivo é alinhar toda a extensão das sequências umas com as outras, ou seja, o alinhamento é realizado de ponta a ponta.

O alinhamento global pode ser **par a par**, quando alinhamos duas sequências:

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/alinhamento-global-par.jpg)

ou **múltiplo**, quando três ou mais sequências são alinhadas:

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/alinhamento-global.mul.jpg)

O algoritmo mais utilizado para realizar o alinhamento global par a par é o de **Needleman-Wunsch**, que tem uma resolução ótima. Para o alinhamento múltiplo, o **CLUSTAL**, de Higgins-Sharp, é o mais utilizado, com uma resolução aproximada (heurística). 

### Alinhamento local

O **alinhamento local** busca por região de alta similaridade entre subsequências das sequências analisadas, não importando as regiões adjacentes: 

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/alinhamento-local.jpg)

Para isso, o algoritm mais utilizado é o de **Smith-Waterman**, que produz uma solução ótima.

### Critério de pontuação

Focarei agora no alinhamento global par a par.

Os algoritmos de alinhamento analisam o ***score*** de cada alinhamento. O *score* é o resultado soma da pontuação para os ***matches*** (alinhamento de caracteres iguais), ***mismatches*** (alinhamento de caracteres diferentes), *gap opening* (abertura de lacuna)  e ***gaps*** (inserção ou deleção de caracteres), sendo que os *matches* são recompensados, enquanto *mismatches* e *gaps* são penalizados.

Vamos analisar como ficaria o alinhamento entre as duas sequências abaixo:

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/sequencias.jpg)

Primeiro, vamos considerar um alinhamento em que *mismatches* não são permitidos. A recompensa para *match* é +4 e a penalidade para *gap* é -3:

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/sem-mismatch.jpg)


Agora vamos analisar um alinhamento que permite *mismatches*, sendo este com penalidade de -2:

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/com-mismatch.jpg)


Podemos ver que o maior *score* está no alinhamento que permite *mismatches* (*score = 25*), sendo esse considerado um melhor alinhamento, isto porque a penalidade para *gap* é maior, visto que, do ponto de vista evolutivo, "há um maior custo" quando acontece uma deleção/inserção de caracter do que quando ocorre um troca de caracter.

Não existe uma regra que determine qual deve ser a pontuação para *match, mismatch* e *gap* em alinhamento de nucleotídeos. Para proteínas, existem as **Matrizes de Substituição** (PAM, BLOSUM) as quais contêm as probabilidades das trocas ou manutenção dos aminoácidos.

### Aplicativo para alinhamento de sequências de DNA

Diante dessas informações, construí uma [**aplicação web no Streamlit**](https://share.streamlit.io/vanleiko/dna-streamlit/main/src/app-dna-v2.py) que realiza o alinhamento global e local, par a par, de sequências de DNA, baseado nos algoritmos de Needleman-Wunsch e Smith-Waterman.

![](https://raw.githubusercontent.com/vanleiko/meus-projetos/main/st-image.png)

Além do alinhamento, esse *web app* também analisa a **Composição de Nucleotídeos** e o **Conteúdo GC** das sequências fornecidas, características importantes em estudos genéticos, evolutivos, taxonômicos e ecológico, uma vez que fornecem informações sobre o padrão de utilização dos códons, identificação de regiões gênicas, e auxiliam na síntese de vacinas de DNA e no desenho de primers.

👉 *O código, em **Python**, da aplicação web pode ser acessado [aqui](https://github.com/vanleiko/dna-streamlit/blob/main/src/app-dna-v2.py).* 













