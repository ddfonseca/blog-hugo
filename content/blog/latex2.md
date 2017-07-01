+++
description = ""
tags = ["latex"]
meta_img = "/images/image.jpg"
date = "2017-05-13T20:30:35-03:00"
title = "LaTeX 2 de 3: Equações Matemáticas, Tabelas e Figuras."
+++

## Equações Matemáticas

No [primeiro post](https://davidfonseca.com.br/blog/latex-para-quem-quer-terminar-o-tcc-em-um-m%C3%AAs-parte-1/), vocês tiveram o primeiro contato com o LaTeX. Conheceram o [ShareLaTeX](https://pt.sharelatex.com) e algumas formatações básicas do texto. Hoje, vamos aprender a mexer com as equações matemáticas, figuras e tabelas. Quem nunca teve uma tremenda dor de cabeça para editar todas aquelas fórmulas no MS Word? No LaTeX pode até ser pior, mas só no começo. Com o tempo você se acostumará e só vai querer usar essas fórmulas.

### Equações na linha

```tex
\chapter{Equações Matemáticas} % estamos aqui
\section{Equação na linha}
Podemos utilizar símbolos matemáticos enquanto escrevemos, como por exemplo: $\sum_{n=1}^x n^2$.
No entanto, podemos atribuir o comando:  $\displaystyle\sum_{n=1}^{x} n^2$, para visualizá-las melhor.
```
Resultado:
![eq linha](/img/latex_img/eqlinha.png)

Aqui temos um exemplo dos comandos somatório `\sum`, sobrescrito "^" e subscrito "\_". Para incluir as equações no texto, enquanto estamos escrevendo, devemos colocá-las entre o cifrão ($). Desse modo, todos os [comandos matemáticos](/pdf/short-math-guide.pdf) estarão disponíveis para a gente. Esse foi um exemplo de três comandos matemáticos. O subscrito esteve entre chaves porque foi mais de um caractere, o mesmo poderia ocorrer com o subscrito. O comando `\displaystyle` melhora a visualização de algumas fórmulas na linha, como essa do somatório.


### Ambiente matemático


Vamos supor que você introduzirá uma equação no seu texto e depois explicará cada variável.

```tex
\section{Ambiente matemático} % Estamos aqui

O coeficiente de Reynolds ($Re$) é um número adimensional muito utilizado na mecânica dos fluidos.
Com ele, é possíve avaliar o regime do escoamento como laminar ou turbulento. É dado pela equação abaixo:
\begin{equation} \label{eq:re}
    Re = \frac{\rho V D}{\mu}
\end{equation}
Sendo que $\rho$ é a massa específica, $V$ a velocidade do fluido, $D$ o diâmetro e $mu$ a viscosidade cinemática.
```
Resultado:
![reyolds ](/img/latex_img/reynolds.png)

Aqui está um exemplo de uso real das equações matemáticas, vamos por partes. Primeiro, observe que não há espaço entre o texto e o `\begin{equation}`. Isso porque se houvesse o LaTeX criaria uma nova linha, deixando a sua equação ainda mais para baixo. O mesmo acontece no `end{equation}`. Experimente criar esses espaços e compile novamente. Segundo, criamos o ambiente `\begin{equation} ... \end{equation}`, nele o LaTeX centraliza a fórmula e atribui um número que será na ordem crescente. Está (2.1) porque o estamos no capítulo 2 e essa foi a primeira equação. A próxima seria (2.2) e assim por diante.

Podemos mudar a numeração ao incluir o comando `\counterwithout{equation}{chapter}` no preâmbulo, sugiro colocar na seção de comandos personalizados pelo usuário, entre as linhas 114~120. Assim, não incluirá mais o capítulo. Se o seu trabalho tem por volta de 5 páginas e poucas equações e mesmo assim você gostaria de uma capa, folha de rosto, sumário e referências bibliográficas nas normas, poderia usar esse template com essa opção.

Terceiro, colocamos um *label* (rótulo) na fórmula, de modo que poderíamos referenciar ela mais tarde. Dentro do *label* você pode incluir qualquer nome que desejar, eu particularmente gosto de ser coerente e por isso incluo um prefixo como *eq*, mas isso é opcional. Podemos então referenciar as equações utilizando três comandos: `\ref{eq:re}`, `\eqref{eq:re}` ou o meu predileto `\autoref{eq:re}`. O primeiro imprime o número, o segundo o número com um parênteses e o terceiro o nome da referencia mais o número, nesse caso "Equação (2.1)". Se fosse um *label* de uma Tabela ou Figura, ele incluiria os respectivos nomes.

Dentro do ambiente matemático, temos três comandos: duas letras gregas e uma fração. As letras gregas são escritas conforme são "faladas". Imagine então, o comando da letra grega pi? Acertou `\pi`!. A fração é dada por essa fórmula `\frac{numerador}{denominador}` em que o numerador e denominador são separados entre essas chaves.

Aliás, o ambiente matemático pode ser inicializado com a seguinte sequência no ShareLaTeX: \beeq\<CR\>
Obs: Como um leitor me avisou recentemente, as vezes a função autocompletar só funciona quando o comando já foi previamente inserido no texto. Se não funcionar com essa sequência, primeiro copie o código abaixo e depois digite a sequência.

```tex
A fórmula de Bhaskara é dada por:
\begin{equation}\label{eq:bhaskara}
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\end{equation}

Calcule as raízes da equação $x^2 + 12x - 13 = 0$ com a \autoref{eq:bhaskara}.
\begin{equation*}
 x = \frac{-12 \pm \sqrt{12^2 - (4)(1)(-13)}}{(2)(1)} = \frac{-12 \pm \sqrt{196}}{2} = \frac{-12 \pm 14}{2} = -6 \pm 7
\end{equation*}
Logo, as raízes são: $x_1 = 1$ e $x_2 = -13$.
```

Aqui está outro exemplo e dessa vez utilizamos o ambiente *equation\** para iniciar um ambiente matemático sem nenhuma numeração. Assim também podemos escrever as fórmulas centralizadas como o exemplo acima. O resultado:

![bhaskara](/img/latex_img/bhaskara.png)

O comando `\sqrt{}` e `\pm` significam *SQuareRooT* (raíz quadradra) e *plus-minus* (mais ou menos).

### Para fórmulas complicadas e aprendizado
Gostaria que vocês visitassem o [CodeCogs](https://www.codecogs.com/latex/eqneditor.php), que é um editor online para equações matemáticas basedo no LaTeX. Nele vocês podem brincar à vontade e verificar se a fórmula está como queiram. O *feedback* lá é imediato, de modo que podemos verificar se a sua equação está correta ou não. Junto com o [Short Math Guide for LaTeX](/pdf/short-math-guide.pdf), vocês têm praticamente tudo para tirar as suas dúvidas.


## Figuras

As figuras são tão simples nos editores convencionais. Basta arrastar para o arquivo e pronto! Sua figura está lá, ajeita um pouco com o mouse e tudo fica direitinho. No LaTeX implementar figuras é um pouquinho complicado, mas vamos lá:

```tex
\begin{figure}[!htb]
 \centering
 \caption{Título}
 \includegraphics[scale=0.5]{abntex2-modelo-img-grafico.pdf}
 \legend{Fonte: \citeonline[p. ~24]{araujo2012}}
\end{figure}
```

Criamos um novo ambiente chamado *figure*, nele o LaTeX (junto com a classe abntex2) começará a numerar as suas figuras. E como ele sabe que isso é uma figura, também criará automaticamente a Lista de Figuras. No caso, a gente retirou essa opção para ficar um trabalho mais simples, até porque, isso é opcional pelas normas da ABNT. Dentro desse ambiente, estamos centralizando tudo, a imagem, título e legenda com a comando `\centering`. O comando `\caption{}` cria o título da sua imagem, o comando `\includegraphics[opções]{caminho_da_imagem}` inclui uma figura nova, nesse caso colocamos já uma imagem que está no diretório raiz do projeto. Outros caminhos também são possíveis, como veremos adiante.

Utilizamos a opção *scale* com o dimensionamento da imagem em 50%, calhou que deu certo, mas normalmente utilizo a opção *width=0.95\textwidth* (dentro dos colchetes). Pois assim temos uma ideia melhor de como a imagem vai ser preenchida no texto. Se minha imagem tem uma altura muito maior que a largura, então colocaria um *width=0.4\textwidth* por exemplo, com a prática vocês vão pegando o jeito.

Pela norma, precisamos sempre colocar a fonte nas imagens, mesmo que seja uma imagem de sua autoria. Nesse caso, deverá ser colocado assim: "Figura produzida pelo autor.", ou algo semelhante. Também foi utilizado a citação direta do autor com o comando `\citeonline{bibkey}`, mas isso será falado no próximo post.

E se quisermos colocar figuras lado a lado ? Também é possível com o pacote *caption*, que permite utilizar o ambiente *subfigure*.

```tex
\begin{figure}[htb]
	\centering
        \caption{\label{fig:16-13} Uso de aletas para aumentar a transferência de calor de uma parede plana}
        \begin{subfigure}[t]{0.3\textwidth}
            \centering
            \includegraphics[width=0.95\textwidth]{img/fig16-13a.png}
            \caption{Superfície sem aletas}\label{fig:16-13a}
        \end{subfigure}
    	\hspace{10mm}
        \begin{subfigure}[t]{0.3\textwidth}
            \centering
            \includegraphics[width=0.95\textwidth]{img/fig16-13b.png}
            \caption{Superfície aletada}\label{fig:16-13b}
	\end{subfigure}
    \legend{Fonte: \citeonline{shapiro}}
\end{figure}
```

Resultado:
![lado a lado](/img/latex_img/ladolado.png)

Temos um comando gigante, não é? Em alguns editores de texto, existe uma função chamada de *snippet*. Essa função permite replicar uma parte do seu código com uma simples referência. No meu, apenas digito *sub<TAB>* que esse código enorme já abre, além disso conforme vou editando, continuo escrevendo e usando o tab para ir apenas nas partes em que é necessário editar, veja nesse exemplo:

<img src="/img/latex_img/snip.gif" alt="gif" style="width: 580px;"/>

Ok, vamos entender o código agora. Veja que temos o usual `\caption` logo depois do `\centering` para centralizar toda a imagem. Nesse caso temos mais duas subimagens e perceba que defini o tamanho como 1/3 da largura do papel. Poderíamos ter colocado *0.5\textwidth*, mas como sei que essa imagem tem uma altura maior que a largura, ficaria muito grande. Nesse caso, é possível incluir uma terceira imagem já que dividi o tamanho em 1/3, mas só coloquei duas. Por isso que adicionei um `\hspace{10mm}` no meio das duas figuras para não ficar muito colado. Dentro de cada subimagem também as preenchi com quase todo o tamnho disponível para elas, com 0.95\textwidht, essa opção normalmente não precisa mudar. Por fim temos a fonte das duas imagens e um *label* para cada subimagem e imagem.

Perceba que agora o caminho da imagem está dentro de uma pasta chamada *img*. Assim, o seu projeto ficará mais organizado caso tenha um universo de imagens para incluir.

## Tabelas

Criar tabela é bem chatinho no LaTeX. Veja o comando para criar uma tabela tão simples:

```tex
\begin{table}[!htb]
    \centering
    \caption{Dados dos alunos} \label{tab:teste}
    \begin{tabular}{lll}
        \hline
        Nome & Sobrenome & Idade \\
        \hline
        David & Fonseca & 25 \\
        Fulano & deTal & 35 \\
        \hline
    \end{tabular}
    \legend{Fonte: Tabela produzida pelos autores}
\end{table}
```

Resultado:
<img src="/img/latex_img/dados.png" alt="dados" style="width: 450px;"/>

O ambiente *table* é apenas para indicar que isso será uma tabela e criar aquela lista de tabelas que não foi incluso nesse *template*. Temos o usual *caption* e *legend*, igual em figuras, mas a tabela em si começa no ambiente *tabular*. Vamos entendê-lo. Temos três colunas, por isso temos três caracteres *{lll}* dentro das chaves. Esses caracteres definem o alinhamento do texto na coluna, que no caso estão alinhadas pela esquerda (*l* de *left*), para alinhar no centro, digite *c* e para a direita, digite *r*. Experimente colocar `{lcr}` e compile novamente. Para adicionar uma nova coluna, basta adicionar mais um caractere com o respectivo alinhamento.

O comando `\hline` serve para criar uma linha horizontal, mas também temos o `\toprule` ou `\bottomrule` para criar uma linha um pouco mais grossa no topo e no fundo da tabela. Vai de preferência de cada um. Lembra dos caracteres especiais do [primeiro post](https://davidfonseca.com.br/blog/latex-para-quem-quer-terminar-o-tcc-em-um-m%C3%AAs-parte-1/)? O **&** dentro do ambiente *tabular* serve para separar as colunas. Assim, vai digitando e separando-as pelo **&**. Para encerrar a linha, temos o comando `\\` é a mesma coisa que `\newline`. Ou seja, ele pula para a próxima linha da tabela. Pronto, criamos uma tabela simples! Essas partes o LaTeX deixam a desejar, mas existem muitas formas de transformar as suas tabelas muito mais bonitas do que os editores convencionais. Veja [esse](https://tex.stackexchange.com/questions/112343/beautiful-table-samples) e [esse outro](https://www.inf.ethz.ch/personal/markusp/teaching/guides/guide-tables.pdf) link. Uma vez que são apenas códigos, basta copiar e colar no seu arquivo que terá o mesmo efeito.

Para finalizar, uma tabela com duas colunas dentro de uma coluna:

```tex
\begin{table}[!htb]
    \centering
    \caption{Rugosidade para diferentes Materiais}
    \begin{tabular}{l l l} \toprule
	& \multicolumn{2}{c}{Rugosidade, \textit{e}} \\
	\cline{2-3}
	Tubo  & Pés & Milímetros \\
	\hline
	Aço rebitado & 0,003-0,03 & 0,9-9 \\
	Concreto & 0,001-0,01 & 0,3-3 \\
	Madeira & 0,0006-0,003 & 0,2-0,9 \\
	Ferro Fundido & 0,00085 & 0,26 \\
	Ferro Galvanizado & 0,0005 & 0,15 \\
	Ferro fundido asfaltado & 0,0004 & 0,12 \\
	Aço comercial ou ferro forjado & 0,00015 & 0,046 \\
	\bottomrule
    \end{tabular}
    \legend{Fonte: \citeonline{fox}.}
\end{table}
```

Resultado:
<img src="/img/latex_img/tabelamultipla.png" alt="tabela multipla" style="width: 500px;"/>

Se você quisesse escrever "Rugosidade, e" entre a segunda e terceira coluna encontraria problemas. A solução para isso é criar uma "multicoluna" que ocupará esse papel e junto com ela, uma linha que apenas cobre essas duas colunas. Vamos lá, primeiro observe que não temos nada na primeira coluna da primeira linha, por isso já inicio essa linha mudando para a segunda coluna com o **&**. Aqui criamos a coluna múltipla, que ocupará 2 colunas e que ficará centralizada, por isso o `{2}{c}`. Depois, preenchemos com o que queremos nessa coluna. Pulo a linha e inicio o `cline{2-3}`, que apenas criará uma linha na coluna 2 e 3. Fechou! O resto é igualzinho a tabela anterior. Adicionei o `\toprule` e `\bottomrule` também para vocês notarem a diferença.

### Sobre o comando `\label{}`

Esse comando você deve usar e abusar dele, porque é justamente com ele que torna a editação do LaTeX prazerosa de usar. Toda vez que criar um Capítulo, Seção, Equação, Figura ou Tabela que será referenciado ao longo do texto, use o `\label{}` e referencie com `\ref{}` ou `\autoref{}`. Desse modo, é possível retirar um capítulo inteiro do seu texto que o LaTeX automaticamente reorganizará a numeração dos Capítulos, Seções, Equações, Figuras e Tabelas. Assim, todas as referências com o `\label{}` estarão corretas. Quando vocês sentirem o poder do `\label{}`, vão entender porque escrever no LaTeX é tão prazeroso.

## Conclusão da parte 2

Bom, com isso já temos uma boa bagagem do LaTeX. Sabemos organizar a dissertação com capítulos e seções de modo que o LaTeX criará o sumário. Também aprendemos um pouco de equações matemáticas que infelizmente só pude mostrar o básico. Só com o tempo para aprender de fato esse universo. Também aprendemos a incluir Figuras e Tabelas. Fora isso, só vai faltar as referências bibliográficas para completar essa serie de posts sobre *comandos fundamentais do LaTeX*, ou em outras palavras, "como formatar o seu TCC faltando 1 mês".

Obs:  Utilizo o *snippet* para praticamente qualquer comando do LaTeX. Infelizmente não conheço os editores de texto para LaTeX do Windows, mas sei que no Linux existe o [Kile - An Integrated LaTeX Environment](https://kile.sourceforge.net) que possui essa opção. Isso apenas facilitaria o seu `Ctrl+C` e `Ctrl+V`, mas de modo geral, não é tão importante assim.
