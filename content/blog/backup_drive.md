---
author: "David Fonseca"
date: 2018-12-27
title: Como criar um backup automático para o Google Drive (No Linux).
tags: ["linux","backup", "google-drive"]
---

Sempre tive a preocupação de manter em segurança certos arquivos do meu computador, seja por motivo afetivo (ex: fotos) ou por realmente não querer perde-los (ex: configs do linux). Uma solução simples é enviar tudo para a nuvem, certo? Ok, mas e caso você tenha uma pasta, ou um grupo de arquivos que são editados constantementes (pelo menos 1x por semana)? Ter que fazer isso manualmente se torna uma tarefa tediosa e desnecessária.

Pensando nisso que existe programas como o __cron__ (executa comandos de forma automática em certo horário/data) e __rclone__ (uma espécie de cópia do rsync para a núvem). Nesse artigo, vou detalhar como podemos utilizar os dois para que um diretório seu tenha um backup regularmente, que pode ser uma vez por dia, uma vez por semana, como quiser.

## Configurando Rclone

O processo para configurar o __rclone__ encontra-se [nessa página](https://rclone.org/drive/). Não vou detalhar aqui pois muito provavelmente ao longo de novas versões o artigo ficaria desatualizado e também não é tão complicado assim seguir os passos. Qualquer coisa pode comentar que poderei ajudar.


### Criando seu primeiro backup com rclone
Pois bem, com o rclone instalado e configurado vamos fazer um simples teste. Crie uma pasta chamada play (mkdir play) e vamos também criar uns arquivos: touch arquivo1.txt arquivo2.txt arquivo3.txt. Agora volta para o diretório anterior e digite:
```
rclone sync play remote:play
```
Caso você tenha configurado o nome do servidor conforme está escrito no tutorial original, você terá feito com o nome __remote__, caso contrário, digite o nome do qual você colocou. Dessa forma, ele vai sincronizar todos os arquivos dentro da pasta play e vai criar uma nova pasta play dentro do Google Drive. Se você deletar algum arquivo e digitar esse comando novamente, o rclone também deletará o arquivo dentro do Google Drive. Dessa forma, o comando __sync__ funciona como esperado: ele sincroniza totalmente a sua pasta de origem para a pasta de destino.

Caso queira apenas copiar os arquivos do seu computador para o servidor, troque o comando para "copy", ficando assim:
```
rclone copy play remote:play
```

## Automatizando Rclone no Cron

Agora vamos para o que interessa. O __cron__ muito provavelmente já está instalado na sua máquina de Linux, se não estiver, basta instála-lo com seu gerenciador de pacotes do sistema, em seguida, digite no terminal:

```terminal
crontab -e
```

Abrirá um arquivo com o seu editor de texto, agora, podemos configurar de tempo em tempo que o cron vai executar os comandos descritos.

No exemplo abaixo, eu peço para o cron que execute o comando "rclone sync ..." da minha pasta pessoal do Anki para o Google Drive, de 4h em 4h horas, todos os dias da semana. Como eu costumo usar o computador ao longo do dia, muito provavelmente ele vai executar o rclone nos períodos: 8h, 12h, 16h e 20h. Mas também faria caso eu estivesse com o computador ligado por 00h e 04h da manhã. Gosto de colocar essa frequência alta porque estou todos os dias modificando e criando novos Cards no Anki, dessa forma gostaria de estar o mais atualizado possível caso perca esses arquivos.

```terminal
0 */4 * * * rclone sync  -q $HOME/.local/share/Anki2 remote:Anki\ sync/Anki2
```

## Explicando como funciona o crontab

O mais importante é saber como funciona as 5 primeiras colunas, pois são nessas colunas que você programa em qual dia/horário será executado seus comandos.

Pois bem, veja a tabela abaixo no qual é mostrado o significado de cada coluna (campo):



Campo  | Significado  |Valores |
:-----:|:------------:|:-----: |
1      | Minutos      | 0 a 59 |
2      | Hora         | 0 a 23 |
3      | Dia do mês   | 1 a 31 |
4      | Mês          | 1 a 12 |
5      | Dia da semana| 0 a 7 (0 e 7 = domingo)|
6      | Comando a ser executado | qualquer comando|


Portanto, no nosso exemplo acima, o primeiro campo coloquei 0 porque representa no minuto 0, se fosse 30, seria no minuto 30. No segundo, eu coloquei a ada 4 horas. Nos campos 3, 4 e 5, qualquer dia do mês, qualquer mês, qualquer dia da semana respecticamente, ou seja, __todos os dias__.

Um ótimo site para brincar com esses números é o [crontab.guru](https://crontab.guru/).

### Exemplo 1: Toda segunda-feira às 9h da manhã. (Semanalmente)

```
0 9 * * 1 [comando]
```
Será executado em: \\
2018-12-31 09:00:00 \\
2019-01-07 09:00:00 \\
2019-01-14 09:00:00 \\
2019-01-21 09:00:00 \\
2019-01-28 09:00:00

### Exemplo 2: De segunda-feira a sexta-feira às 22h. 

```
0 22 * * 1-5 [comando]
```

Será executado em: \\
2018-12-28 22:00:00 (hoje é quinta-feira depois das 22h, logo será amanhã sexta-feira e depois só segunda-feira novamente) \\
2018-12-31 22:00:00 \\
2019-01-01 22:00:00 \\
2019-01-02 22:00:00 \\
2019-01-03 22:00:00
### Exemplo 3: Todo dia primeiro de cada mês às 12h30m. (Mensalmente)

```
30 12 1 * * [comando]
```

Será executado em: \\
2019-01-01 12:30:00 \\
2019-02-01 12:30:00 \\
2019-03-01 12:30:00 \\
2019-04-01 12:30:00 \\
2019-05-01 12:30:00 

### Exemplo 4: Todos os dias a cada 4h de 8h até 20h. (Diariamente)

```
0 8-20/4 * * * [comando]
```
Será executado em: \\
2018-12-28 08:00:00 \\
2018-12-28 12:00:00 \\
2018-12-28 16:00:00 \\
2018-12-28 20:00:00 \\
2018-12-29 08:00:00


Pronto, e assim nunca mais você precisa se preocupar se os seus arquivos estão seguros pois o cron e o rclone fazem o papel de salva-los para você.
