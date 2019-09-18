---
author: "David Fonseca"
date: 2019-09-18
title: Add-ons fundamentais para o estudo de concursos públicos no Anki
tags: ["anki", "repetição espaçada"]
---

Neste post, vamos instalar o Anki, sincronizar a conta e instalar os add-ons: 

- Frozen Fields: __516643804__;
- Hierarchical Tags Addon: __1835859645__;
- AnkiConnect: __2055492159__;
- Quick Colour Changing: __2491935955__;
- Change Order of Review Cards in Regular Decks: __3731265543__.

<!-- <img src="/img/david_goggins_bad_water.jpeg" alt="Foto de um cara distraído com o celular" style="width: 640px;" /> -->

## Download do Anki

Entre no site do [Anki](https://apps.ankiweb.net/) e faça dowload para o seu sistema operacional.
O Anki tem para Windows, Linux, Mac, iPhone/Android e toda sua conta pode ser sincronizada através do [Anki Web](https://ankiweb.net/about).
Crie uma conta e volte aqui.

## Sincronizando as contas

Conforme a imagem abaixo, abra o Anki e clique em __sync__.

<!-- <img src="/img/anki_initialized.png" alt="Foto de um cara distraído com o celular" style="width: 640px;" /> -->
<img src="/img/anki_initialized.png" alt="Imagem mostrando o botão sync no Anki" style="width: 400px;" />

Aparecerá a imagem abaixo e assim você poderá colocar a sua conta e senha para sincronizar.
O mesmo procedimento deve ser feito no celular caso tenha baixado também.

<img src="/img/account_required.png" alt="Imagem mostrando o link para logar na conta." style="width: 266px;" />

# Add-ons fundamentais

## Frozen Fields

[Frozen fields](https://ankiweb.net/shared/info/516643804) é um dos add-ons mais úteis no meu dia a dia, portanto, o primeiro que você instalará.
Ele serve para congelar os campos do card. Seja ele Front/Back (basic card) ou Text/Extra (cloze card), independente do tipo de card.

Para instalar, vá em _Tools_ --> _Add-ons_ --> _Get Add-ons_ que aparecerá uma janela para digitar o código do _Add-on_.
No link você pode verificar que o código do Frozen Fields é: __516643804___._

Após instalado, reinicie o Anki para aparecer esses flocos ao lado de cada campo. Na imagem o front está ativado e o back desativado.

<img src="/img/frozen_field.png" alt="Imagem mostrando o link para logar na conta." style="width: 551px;" />

## Hierarchical Tags Addon 

[Hierarquical Tags Addon](https://ankiweb.net/shared/info/1835859645) é o segundo add-on que mais utilizo no dia a dia.
Sem esse add-on, você tenderá a criar múltiplos decks para cada disciplina.
Não só transformará suas revisões maçiças - pois os cards estarão separdos em diversos decks -, mas também tenderá a ser desorganizado.

O uso das tags torna o estudo mais simples e fácil. 

Todos os cards podem ficar em um único deck, por exemplo: Medicina, Engenharia, Auditor-Fiscal, Polícia Federal.
Dessa forma você estará separando seus cards de acordo com a relação entre eles.
Se você estuda para concursos, provavelmente prestará diversos concursos ao longo da sua jornada.
Em cada prova podemos ajustar quais cards queremos revisar através de um único deck.

Todos os cards criados devem ser marcados com alguma tag. 
Esse add-on facilita a criação de tags hierarquicas, de forma que podemos criar múltiplos tags para cada disciplina organizadamente.

O código para instalar é: __1835859645.__

Veja um exemplo :

<img src="/img/direito_tributario_tags.png" alt="Imagem mostrando as tags do Direito tributário" style="width: 338px;" />

Essa é a visualização pelo browser após ter criado os cards com tags.
Na hora de criar as tags, digite assim: "Disciplina::materia-relacionada". 
Separe por dois pontos as tags hierarquicas, normalmente separo por disciplina e por aula, mas fique a seu critério.
Caso queira ter mais hierarquia, continue com os dois pontos, como, por exemplo: DireitoTributario::Aula00-conceitos::emprestimos-compulsorios.

Não use espaço. Espaços servem para separar múltiplos tags e não tags hierarquicas.
Às vezes você quer colocar essa tag e mais a tag "importante", assim deverá utilizar os espaços para tal.

## AnkiConnect

[Anki Connect](https://ankiweb.net/shared/info/2055492159) é o terceiro add-on mais útil no meu dia a dia.
Ele é uma extensão para programas externos se comunicaram com o Anki.
Sendo assim, criei um programa que mostra os cards selecionados no browser, seja ele Firefox ou Google Chrome.

Utilizo meu programa como uma forma de aprender o conteúdo antes de entrar no modo revisão.
Criarei um post futuramente para divulgar meu programa e mostrar como o utilizo. 
Por enquanto, apenas instale o add-on.

O código para instalar é: __2055492159.__

# Add-ons adicionais

Os três primeiros add-ons são indispensáveis para o meu _workflow_, porém, 
há outros que tornam a experiência do Anki ainda melhor.

## Quick colour changing 

[Quick Colour Changing](https://ankiweb.net/shared/info/2491935955) é um add-on que facilita na hora de mudar a cor do seu card através de um atalho.
Ultimamente eu tenho utilizado apenas duas cores: vermelho e azul.

O código para instalar é: __2491935955__.

Após instalar, vá em _tools -> add-ons -> selecione Quick Colour Changing -> clica em Config_.
Daí copie o código abaixo, utilizo o `ctrl+6` para a cor azul e `ctrl+7` para a cor vermelha.

```
{
    "keys": [
        [
            "#00007f",
            "ctrl+6"
        ],
        [
            "#ca0000",
            "ctrl+7"
        ]
    ]
}
```

Veja na imagem abaixo um exemplo de como as cores ficam.
Você pode criar quantos atalhos que desejar, desde que fique entre colchetes e seguindo o mesmo padrão acima.
Qualquer dúvida pode comentar que ajudarei.

<img src="/img/quick_colour_changing.png" alt="Imagem exemplo das cores do quick colour changing" style="width: 371px;" />

## Change Order of Review Cards in Regular Decks

[Change Order of Review Cards in Regular Decks](https://ankiweb.net/shared/info/3731265543) é um add-on que ajuda na hora da
revisão, pois por padrão os cards são organizados na ordem descrescente de intervalo, entretanto, podemos configurar para
organizar na ordem crescente de intervalo. Isso implica em sempre revisar os cards mais difíceis primeiro, para depois revisar
os cards mais fáceis.

O código para instalar é: __3731265543__.

Vá em configurações e mude o `order = "ivl desc"` para `order = "ivl asc"`.


## Conclusão

Feito essa configuração inicial, estamos prontos para começar utilizar o Anki.
Se você já é usário antigo do Anki e tem algum add-on que considere indispensável ou que acrescente na funcionalidade no seu dia a dia,
sinta-se a vontade para compartilhar nos comentários.
