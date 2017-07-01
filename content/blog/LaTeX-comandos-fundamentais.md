+++
date = "2017-05-06T18:34:15-03:00"
title = "LaTeX 1 de 3: Introdução e Primeiro Passos."
description = ""
tags = ["latex"]
meta_img = "/images/image.jpg"
+++

<!-- ## Introdução -->
<!--  -->
<!-- O título veio a tona quando um amigo disse que precisava terminar o famoso Trabalho de Conclusão de Curso (TCC) em apenas 1 mês e não sabia absolutamente nada de LaTeX. Pelo menos há tempo, e não para para a semana que vem por exemplo. O post será bastante objetivo, falando exatamente dos comandos fundamentais que você usará na sua dissertação e, se faltar algum detalhe, não hesite em comentar para que eu possa atualizar o post e beneficiar futuros leitores. -->

## Para quem não sabe o que é LaTeX
LaTeX, é um sistema tipográfico de alta qualidade e um *software* livre. Pronuncia-se *Lah-tech* ou *lay-tech*. Teoricamente, com o LaTeX você não precisa se preocupar com a formatação, e sim apenas com o conteúdo. Infelizmente, no começo você apenas se preocupará com a formatação. Deverá dedicar um tempo apenas para "aprender LaTeX" e nada de escrever o seu trabalho por enquanto. Muito provavelmente esse esforço valerá a pena, pois o seu trabalho estará dentro das normas da ABNT e impecável.

## Preparação
Pra quem quer apenas formatar seu TCC em tempo recorde, não vou nem perder tempo falando da instalação do *tex live* no Windows ou Linux. Vá direto em sites como [ShareLaTeX](https://www.sharelatex.com/) ou [Overleaf](https://www.overleaf.com/). São editores de texto online cuja o objetivo é ser colaborativo, como o Google Docs, por exemplo. Nunca usei o Overleaf, por isso recomendo o ShareLatex.

### Passo 0: seu primeiro projeto

Depois de realizar o seu Login no [ShareLaTeX](https://www.sharelatex.com), clique em **Novo projeto** --> **Ver todos**, a última opção dos Modelos. Procure por **abntex** que você encontrará o **abnTeX2 Model Thesis**. Se a sua universidade exige um modelo específico, verifique se eles já não disponibilizaram um modelo próprio em LaTeX que você também poderá fazer o upload para o ShareLaTeX. Pronto, você criou o seu primeiro projeto! Agora é só clicar no modelo e depois no botão **Open in ShareLaTeX** que você encontrará uma tela parecida com essa (clique na imagem para ampliar):

[![tela 1](/img/latex_img/tela1.png)](/img/latex_img/tela1.png)

Ao clicar em **Recompilar**, você verá que todos esses comandos da esquerda se transformarão em um documento em PDF à direita. E também aparecerá um ícone para fazer download do arquivo. Esse documento foi muito bem elaborado para  mostrar todas as funcionalidades da classe abnTeX2, mas para nossos fins de aprendizado, é muita informação. O modelo que desenvolvi para o aprendizado do LaTeX, junto com a classe abnteX, é muito mais simples.

Vamos aprender todos os comandos para criar esse [arquivo aqui](/pdf/comandos_fundamentais.pdf). Sendo que a capa, folha de rosto, sumário, numeração de capítulos e seções, imagens, tabelas e referências bibliográficas, tudo isso será trabalho do LaTeX. A filosofia desse post será *Learning by doing* então vamos começar com esse [modelo](https://pt.sharelatex.com/project/590fc24f53edd69b2d6949fa), que não tem praticamente nada.

Após clicar no link, você poderá visualizar o projeto mas não editá-lo diretamente, já que isso impediria que outras pessoas copiassem o modelo em branco. Portanto, você deve criar uma cópia para a sua conta, clicando em **Menu** --> **Copiar Projeto**, conforme pode ser visto na imagem a seguir:

[![copia 1](/img/latex_img/copiar_projeto.png)](/img/latex_img/copiar_projeto.png)

Obs: Gostaria de enviar um singelo agradecimento ao Pedro Tadahiro que me forneceu essas imagens.


### Passo 1: Entendendo o LaTeX
Agora você verá um arquivo muito menor do que o primeiro, mas ainda assim com um monte de comandos desconhecidos. Para começar, vamos pela primeira linha:
```tex
% ----
% Criação do documento com a classe abntex2
% ----
\documentclass[a4paper, 12pt, openany, oneside, brazil]{abntex2}
```

Tudo que começa com o o símbolo `%` será tratado como um comentário, ou seja, o compilador do LaTeX vai ignorar essas linhas. Então você pode escrever esses comentários para facilitar o entendimento do documento, como fiz com essas três linhas, ou você pode omitir alguns trechos. O próprio ShareLaTeX tem um atalho para facilitar isso. Experimente selecionar um trecho do documento e digitar `Ctrl + /`. Será colocado o `%` em todas as linhas selecionadas. Se digitar `Ctrl + /` novamente, voltará ao normal.

Muito útil essa função quando o seu documento está dando vários erros e você não sabe exatamente onde está, então você comenta praticamente o documento todo e vai "descomentando" pequenas partes e compilando novamente. Aí, alguma hora você vai encontrar o erro, mas essa não é uma boa prática. O certo seria: **Escreva pouco** --> **Compila** --> **Verifica**.

Depois, temos a) o comando `\documentclass[a4paper, 12pt, openany, oneside, brazil]{abntex2}` dizendo para criar um documento do tamanho de uma folha A4, tamanho da fonte padrão 12; b) A opção `openany` indicando que os capítulos podem ser abertos em qualquer página, diferentemente da opção `openright` que permite apenas páginas ímpares; c) a opção`oneside` indicando que o documento não é frente-e-verso e, por conta disso, não há páginas em branco, ou seja, todo o documento é preenchido;  por fim, d) a classe `abntex2` serve para usarmos diversos comandos, tais como `/imprimircapa`, `/imprimirfolhaderosto` e `\autoref{}`, além de gerar título de Figuras e Tabelas em português e criação do sumário, tudo isso conforme as normas da ABNT.

```tex
% ---
% Pacotes fundamentais
% ---
\usepackage{lmodern}		% Usa a fonte Latin Modern
\usepackage[utf8]{inputenc}	% Codificação do documento (conversão automática dos acentos)
\usepackage{graphicx}		% Inclusão de gráficos/figuras.
...
```

É muito comum no LaTeX a inclusão de pacotes, que para quem já programou na vida, são semelhante às bibliotecas. Os pacotes são códigos pré-existentes para facilitar a sua vida no LaTeX. Esses três pacotes a cima, incluem uma bela fonte, a opção de usar os acentos sem problemas e a inclusão de figuras, respectivamente.

Toda essa parte escrita até o começo do do comando `\begin{document}` (linha 123) é chamada de preâmbulo, que são as configurações do seu arquivo. Dentre elas, as configurações dos pacotes e dos comandos como `/imprimircapa`.

### Passo 2: Configurando capa e folha de rosto
Essa etapa é muito simples, basta você ir na linha 62 e mudar a variável dentro dos colchetes. Desse modo, os comandos `/imprimircapa` e `\imprimirfolhaderosto` vão gerar uma capa e uma folha de rosto com as modificações feitas. Aqui já estamos vendo a inclusão do itálico pelo comando `\textit{texto}`, de modo que tudo dentro dos colchetes será transformado em itálico, como veremos mais adiante.

```tex
\autor{Nome do Aluno}
\titulo{Título do Trabalho}
\instituicao{Universidade Federal do Rio de Janeiro - \textit{campus} Macaé}
\local{Macaé -- RJ}
\data{2017}
\preambulo{Projeto semestral para aprovação da disciplina de X, ministrado pela Prof. Eng. YYYY da Universidade Federal do Rio de Janeiro - \textit{campus} Macaé.}
```

### Passo 3: Capítulos e seções?

Antes de começar, um aviso: agora **tudo** o que vamos escrever será dentro do comando `\begin{document}` (linha 123) ... `\end{document}` (linha 239) porque é aqui que começa o seu texto de fato. Vemos que os dois primeiros comandos são o `/imprimircapa` e `/imprimirfolhaderosto`, que já foram previamente configurados na etapa anterior. Em seguida, vem a parte do resumo e do abstract, criando uma página com o título "Resumo e Abstract" e inserindo o seu texto nele.

Como criar capítulos e seções? Basta digitar os comandos `\chapter{}` e `\section{}`, ou ainda, `\subsection{}` e `\subsubsection{}`. Vamos criar o sumário de tudo o que passaremos neste post. Vá para a linha 165 e digite:

```tex
\chapter{Formatação de texto}
\section{Formatação básica}
\section{Listas}
\section{Símbolos especiais}
\section{Notas de Rodapé}

\chapter{Equações matemáticas}
\section{Equação na linha}
\section{Ambiente matemático}

\chapter{Figuras e tabelas}
\section{Figura lado a lado}
\section{Tabelas}

\chapter{Referências bibliográficas}
```

Desse modo, o LaTeX criará o sumário já com as normas da ABNT e também com os capítulos e seções. Experimente colocar subseções dentro das seções e recompilar o arquivo.


### Passo 4: Formatação

Entre o capítulo "Formatação de texto" e a seção "Formatação básica", escreva:
```tex
\chapter{Formatação de texto} % apenas para ilustrar onde estamos.
Esse é um simples texto.            Não importa os espaços que o LaTeX apenas criará um.
```
Experimente escrever um texto com vários espaços assim e compile. Você perceberá que o LaTeX apenas criará um espaço, uma vez que você não deve se preocupar com a formatação. Assim, caso você cometa o erro de insrir um espaço duplo, o LaTeX corrigirá para você. O mesmo vale para espaços entre parágrafos. Como faço, então, para inserir espaços horizontais e verticais? Hmm, experimente os comandos `\hspace{unidade}` e `\vspace{unidade}` e me diga, sendo que unidade pode ser em centímetros (cm), milímetros (mm) ou polegadas (in).  Exemplo: `Foo \hspace{2cm} bar`. Inclusive, é possível inserir espaços negativos, como `\vpsace{-0.5cm}`, o que será muito útil quando quisermos corrigir alguma formatação indesejada do LaTeX.

#### Formatação Básica

Como deixo o texto em **negrito** ou em *itálico*? São dois comandos bem úteis: `\textbf{}` e `\textit{}`. Escreva:

```tex
\section{Formatação básica} % apenas para ilustrar onde estamos.

Essa será uma \textbf{palavra em negrito}. Essa \textit{outra em itálico}.
Podemos combinar \textbf{Negrito \textit{junto com} itálico}.
\emph{Emph} também serve para enfatizar, se está normal vai transformar em itálico.
Se está em \emph{itálico vai \emph{transformar em normal}}
```

Acha chato ter que escrever esses comandos toda hora para fazer uma atividade simples como essa? O ShareLaTeX tem a opção de autocompletar, o que significa que se você escrever `\tbf`, aparecerão dois comandos e você poderá mover as setinhas para cima ou para baixo, pressionando `TAB` para escolher. Depois de escrever dentro dos colchetes o que você quiser tornar negrito, pressione a tecla `TAB` novamente para continuar escrevendo o seu texto, pois ele sairá daquele comando. Experimente a sequência:


    \tbf<TAB>teste<TAB> continua escrevendo

O resultado deverá ser:

```tex
\textbf{teste} continua escrevendo.
```
 O mesmo vale para `\emp<TAB>` e qualquer  outro comando deste post.

#### Listas

Como criar aqueles itens de pontinhos pretos ou itens numeradas? No LaTeX, eles são chamados de listas.

Agora, veremos o nosso primeiro ambiente. Tudo o que começa com `\begin{ambiente}`, precisa terminar com `\end{ambiente}`, senão ocorre um erro. Mas não se preocupe: utilizaremos a função autocompletar do ShareLaTeX para facilitar a nossa vida.

```tex
\section{Listas}  % idem...
\subsection{Listas não-ordenadas} % adicionei, por que não?
\begin{itemize}
    \item Primeiro item.
    \item Segundo item.
    \item Terceiro item \ldots
\end{itemize}
```

O código acima pode ser facilmente escrito digitando a sequência:

    \bitem<TAB>Primeiro item.<CR>\ite<TAB> Segundo item.<CR>\ite<TAB> Terceiro item \ldots.

Sendo que `<CR>` significa [enter](https://pt.wikipedia.org/wiki/Carriage_return).

E para as listas ordenadas? Use o ambiente *enumerate*. O exemplo abaixo mostra que é possível criar listas dentro de listas também.

```tex
\section{Listas} % idem
\subsection{Listas não-ordenadas}
...
\subsection{Listas ordenadas} % adicionei novamente
\begin{enumerate}
\item Primeiro item
  \begin{enumerate}
  \item Primeiro item dentro do primeiro item
  \item Segundo item denetro do primeiro item
    \begin{enumerate}
      \item Mais um item dentro de item.
     \end{enumerate}
  \end{enumerate}
\item Segundo
\item Vocẽs pegaram né?
\end{enumerate}
```

Listas fazem parte das atividades diárias e são facilmente criadas em editores de texto comuns, sobretudo em *slides*. No LaTEX, pense no atalho da função autocompletar para digitar a sequência acima.

#### Símbolos especiais

Existem alguns caracteres que você não conseguirá escrever porque são considerados símbolos especiais, isto é, fazem parte da linguagem TeX para o compilador reconhecer algumas funções. Já vimos a porcentagem `%` para inserir comentários, mas existem outros como estes:

|  $ |  & |  % |  # |  _ |  { |  } |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| \$ | \\& | \% | \\# | \\_ | \\{ | \\} |

Caso precise digitá-los em seu texto, basta inserir a contrabarra `\` e o carácter especial.

#### Notas de rodapé

Notas de rodapé também são simples de serem inseridas no LaTeX. Utilizando o comando `\footnote{}` no texto, será inserida uma nota de rodapé ao final da página. Por exemplo:

```tex
\section{Notas de rodapé} % idem...
Escrevendo qualquer coisa apenas para ter a nota de rodapé\footnote{teste1}. \newline
Escrevendo mais coisas apenas para ter nota de rodapé.\footnote{test2}
```
O resultado você já sabe, pode conferir no [arquivo de pdf](/pdf/comandos_fundamentais.pdf). O comando `\newline` vocês já podem imaginar o que acontece, né?

## Continua ...
Bom, acho que para o primeiro contato está valendo. Estou pensando que é melhor separar este assunto em alguns posts, dois ou três, só para não ficar muito condensado em um só. Qualquer dúvida, é só comentar aí embaixo!

Até a próxima!
