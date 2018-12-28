---
author: "David Fonseca"
date: 2017-08-20
title: Como plotar os resíduos do OpenFOAM com o gnuplot?
tags: ["openfoam", "residuo"]
draft: true
---
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js"></script>

<script type="text/x-mathjax-config">
  MathJax.Hub.Config({tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}});
</script>
<script type="text/javascript" async
  src="https://example.com/MathJax.js?config=TeX-AMS_CHTML">
</script>

<!-- <script type="text/javascript" async -->
<!--   src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"> -->
<!-- </script> -->

## Convergência Numérica
Um dos pilares da convergência, além da convergência da malha, é a **convergência da solução numérica**. Para isso, devemos monitar os seguintes parâmetros: resíduos da solução e uma variável de interesse (velocidade ou pressão) ou propriedades integradas (força, fluxos, temperatura média).

O resíduo das soluções numéricas depende de cada caso, se for transiente devemos observar o resíduo tempo a tempo, se for estacionário devemos observar um decaímento do resíduo conforme as variáveis vão chegando ao estado estacionário e, portanto, não variam muito entre si. O que isso quer dizer? Se a velocidade de um escoamento estacionário chegar a 10.309209 m/s e na próxima iteração chegar a 10.309207, o resíduo então está na ordem de 1e-6 (1x10^-6). Caso esse resíduo permaneça nessa grandeza por um longo tempo, dependendo do caso, podemos dizer que a solução chegou ao estado estacionário.

Segundo a [Lívia Jatobá](http://www.liviajatoba.com/), sobre as simualções que atingem o estado estacionário:

+ O estado estacionário será atingido quando o valor da variável de interesse não muda mais ao longo das novas iterações;
+ Se a simulação atinge o estado estacionário, o resíduo inicial do sistema algébrico diminui ao longo das iterações.

## Caso Particular

Nada melhor do que botar a mão na massa, não é mesmo? Vamos utilizar o caso mais simples de todos, o **cavity**, e como podemos diminuir o resíduo caso não esteja baixo o suficiente para os padrões. Já digo que tudo que falarei aqui veio das aulas da Lívia Jatobá disponibilizadas no [YouTube](https://www.youtube.com/watch?v=BpaG6XIdP8U), inclusive o próprio *script* do *gnuplot* foi retirado do site [dela](http://www.liviajatoba.com/uploads/8/3/6/7/8367135/modelo-plot-residuo.plt).

Primeiro entre no diretório **run** do OpenFOAM e digite:
<pre><code class="bash">cp -r $FOAM_TUTORIALS/incompressible/pisoFoam/RAS/cavity/ . </code></pre>

Queremos uma simulação que tenha problemas, e vocês devem imaginar que a solução dos tutoriais já estão bem planejadas para darem certo. Portanto, vamos modificar algumas coisas, por exemplo, a viscosidade cinemática (letra grega ni, $\nu$) que é dada pela viscosidade dinâmica ($\mu$) divido pela massa específica ($\rho$). Abra com o seu melhor editor de texto o arquivo `cavity/constant/transportProperties` e modifique o "nu" de `1e-5` para `0.01`. Depois modifique também o arquivo `cavity/constant/turbulence Properties`, a linha `simulationType RAS` para `simulationType laminar`. Vamos para


