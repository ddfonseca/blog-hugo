+++
date = "2017-05-17T21:40:09-03:00"
title = "LaTeX 3 de 3: Referências Bibliográficas."
description = "Desc"
tags = ["latex"]
meta_img = "/images/image.jpg"

+++

## Referências Bibliográficas

Certamente o maior motivo pelo qual eu quis utilizar o LaTeX para o meu TCC foi essa possibilidade de lidar as referências bibliográficas de acordo com as normas da ABNT. A norma é bem confusa e tem muitos detalhes para cada tipo de trabalho. Felizmente, existe dois pacotes para lidarmos com as referências: o *abntex2cite* e o *biblatex-abnt*. As duas são muito boas e tem suas particularidades. A segunda está tendo mais atualizações (última atualização foi dia 17 de Março de 2017), enquanto a primeira menos (última atualização 26 de Fevereiro de 2016). Utilizaremos o *abntex2cite* porque até hoje não encontrei nenhum problema que me fez migrar para o *biblatex-abnt*. Contudo se você observar o [Grupo abnTeX2](https://groups.google.com/forum/#!forum/abntex2), perceberá que a maioria das dúvidas referentes a problemas com a classe *abntex2cite* podem ser resolvidas com o *biblatex-abnt*.

### Cuidado: normas nebulosas!

Os próprios criadores da classe abnTeX2 comentam na seção 3.2 da [documentação do pacote](http://mirror.unl.edu/ctan/macros/latex/contrib/abntex2/doc/abntex2cite-alf.pdf), que as normas são confusas. Inclusive o próprio nome **abnTeX2** não vem de ABNT e sim de [*ABsurd Norms for TeX*](http://www.abntex.net.br/). Veja o que contém nessa seção:

> Nós elaboramos os estilos debruçados diretamente sobre os originais da ABNT e as seguimos escrupulosamente.  Mas não se iluda!  O que a sua coordenação de pós-graduação, ou orientador, ou chefe etc., entendem por ‘normas ABNT’ pode não ter qualquer vínculo com a realidade. Por isso não garantimos que ao usar os estilos do abnTeX você esteja em conformidade com as normas da sua instituição ou empresa.

> Um exemplo clássico é o sistema de chamada numérico. Embora *todas* as ‘normas’ da ABNT (ABNT, 1988; ABNT, 2000; ABNT, 2002b, 2002b; ABNT, 2001; ABNT, 2002a) ‘autorizem’ seu uso, a maioria das instituições, orientadores, membros de banca, revisores de artigo. . . dirão que isso não é ABNT. Acredite se quiser.

Dito isso, vamos ao trabalho!


Na linha 26 do comandos_fundamentais.tex (seu projeto atual), terá a seguinte linha:

```tex
\usepackage[alf]{abntex2cite}
```

Aqui estou utilizando o pacote *abntex2cite* com a opção **alf**. Por padrão vamos utilzar o sistema autor data que maioria das instituições entendem como norma da ABNT, do contrário seria o sistema numérico, **num**.

Ao lado esquerdo do seu [projeto](https://www.sharelatex.com/project/590fc24f53edd69b2d6949fa), estará um arquivo chamado **bibliografia.bib**. É nesse arquivo que todas as suas referências bibliográficas devem estar. Clique nele, você verá que já está incluso as referências mais frequentes, como livro, artigo, mestrado e doutorado. Para entender o que cada formato significa, [veja esse link](https://pt.wikipedia.org/wiki/BibTeX).  Esses formatos não tem muito mistério não, mas vamos pegar um exemplo e explicar cada passo (esse não tem cor maneirinha):

```tex
@book{shapiro,
author={Howard N. Shapiro and Michael J. Moran and Bruce R. Munson and David P. DeWitt},
address={New York},
title={Introduction to thermal systems engineering},
subtitle={thermodynamics, fluid mechanics, and heat transfer},
isbn={9780471204909},
lccn={2002728440},
year={2003},
publisher={John Wiley \& Sons, Inc},
} % importante
```

O formato começa com **@** seguida do tipo do trabalho, nesse caso é um livro. A primeira palavra (shapiro) é chamada de *bibkey*, que é exatamente o texto que você digitará no LaTeX. Existem duas formas de citar as referências, o `\cite{bibkey}` e `\citeonline{bibkey}` que falarei mais adiante. Em seguida, temos algumas entradas como *author*, *address*, *title*, etc. Essas entradas não precisam estar nessa ordem, mas em qualquer uma. Nem todas são obrigatórias, como *isbn* e *lccn*. Não se preocupa muito com isso não, o que você mais vai fazer é procurar algum exemplo pronto [desse link](http://linorg.usp.br/CTAN/macros/latex/contrib/abntex2/doc/abntex2cite.pdf) ou [desse outro link](https://github.com/abntex/biblatex-abnt/blob/master/doc/biblatex-abnt.bib) e apenas reescrever. Dê um `ctrl+f book` para ver alguns exemplos.

Quando for digitar mais de um autor, deve separá-los todos por "**and**" e não com a usual vírgula e "and" no final. Caso precise digitar algum texto em caixa alta, colocá-los entre chaves {}, por exemplo "title={Volume of Fluid ({VOF}) Method for the Dynamics of Free Boundaries}". Caso precise de algum caractere especial como **&**, utilizar o comando de escape \\. Veja que todas as entradas terminam com uma chave e vírgula "}," e não esqueça da última chave para fechar o formato. O resto é autoexplicativo.

Depois que você preencher todas as entradas, está na hora de citar. No arquivo comandos\_fundamentais.tex, lá no final estará o comando `\bibliography{bibliografia}` que é o nome desse arquivo sem a extensão *.bib*. O abntex2cite criará uma página chamada Referências e nele colocará todas as referências que você **citar** no texto. As vezes as pessoas se confundem que só porque o arquivo *bibliografia.bib* está cheio de referências, que automaticamente elas estarão inseridas no trabalho. Só estarão inseridas, caso você cite de forma direta ou indiretamente no texto, que veremos agora.


### Citações direta e indireta

Usualmente utiliza-se o `\citeonline{bibkey}` para citações diretas e `\cite{bibkey}` para citações indiretas. O primeiro criará um comando "Autor (Data)", por exemplo: Janna (1994). O segundo, "(AUTOR, DATA)", por exemplo: (JANNA, 1994). Para mais informações veja o final [desse arquivo](/pdf/comandos_fundamentais.pdf).

Exemplo de citação direta:

```tex
\citeonline{janna} define um fluido como toda substância que ao sofrer uma tensão de
cisalhamento deforma continuamente.
```
Resultado: Janna (1994) define um fluido como toda substância que ao sofrer uma tensão de cisalhamento deforma continuamente.

É possível incluir a página na citação, por exemplo: `\citeonline[p. ~1]{janna}`. O *~*  serve para que esse texto permaneça junto (p. n°) ao citar no texto, que ele não caia para a próxima linha caso esteja no final de uma frase.

### Referência citada por outra referência (apud)

Caso você deseje citar uma referência que foi previamente citada pelo autor que você leu, você deve utilizar o `\apud` e `\apudonline`. Esse comando funciona assim:

```tex
\apud{autor_indireto}{autor_direto}
\apudonline{autor_indireto}{autor_direto}
```

Sendo que *autor\_indireto* e *autor_direto* são **bibkeys** definidas no seu arquivo *.bib*. Então caso você queira citar dessa forma, ainda assim precisará incluir todas as entradas dos dois *bibkeys*. Esses comandos funcionam de forma semelhante ao `\cite{}`, o primeiro cita indiretamente e o segundo diretamente.


## Fim dessa série

O LaTeX é um mundo, existe muita coisa que poderíamos fazer com ele. Apenas falei dos principais comandos e configurações para fazer um trabalho nas normas. Veja esse [link das maravilhas](https://tex.stackexchange.com/questions/1319/showcase-of-beautiful-typography-done-in-tex-friends) que podem ser feitas no LaTeX.

Para quem nunca programou, esse modelo de escrever pode ser um pouco intimidador. Mas acredite, é apenas uma questão de compreender a estrutura dos comandos que a coisa flui.

### Onde encontrar ajuda?

E agora? Se precisar de alguma ajuda, você pode comentar aí nos comentários ou procurar se a sua dúvida já foi respondida nos seguintes links:


1. [Grupo abnTeX2](https://groups.google.com/forum/#!forum/abntex2)
2. [Grupo LaTeX-BR](https://groups.google.com/forum/#!forum/latex-br )
3. [Wiki abnTeX2](https://github.com/abntex/abntex2/wiki)
4. [TeX StackExchange](http://tex.stackexchange.com/)

Apesar dos dois primeiros links serem de um grupo da Google, você deve estar pensando: ninguém usa esses grupos! Errado, porque quem está inscrito no grupo recebe as notificações por e-mail, aí as pessoas respondem. A frequência não é tão alta, mas existe atividade de pelo menos uma pergunta por semana. A última foi dia 15 de Maio de 2017.

Por fim, caso queira apostilas bem completas sobre LaTeX, basta digitar no Google: [latex filetype:pdf](https://www.google.com.br/search?q=latex+filetype:pdf&ie=utf-8&oe=utf-8&client=firefox-b-ab&gws_rd=cr&ei=nhgeWYWsC8L9wQTh_JDIDQ#safe=active&q=latex+filetype:pdf), que vocês encontrarão diversas apostilas e mini cursos sobre LaTeX.

Obrigado!
