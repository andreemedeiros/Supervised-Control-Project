# Projeto de Controle Supervisionado

## Index
- [Descrição](#Descrição)
- [Eventos](#Eventos)
- [Autômatos](#Autômatos)
- [Guardas](#Guardas)
- [Requisitos](#Requisitos)
- [Execução](#Execução)
- [Autores](#Autores)
- [Licença](#Licença)

## Descrição

O sistema consiste em uma torre com 5 salas conectadas em um ciclo (Sala 1 → Sala 2 → Sala 3 → Sala 4 → Sala 5 → Sala 1). Há um gato e um rato que se movem livremente entre as salas. Sem controle:

O gato não deve entrar na sala onde o rato está. Se isso acontecer o gato irá comer o rato (ou haverá uma "colisão" ou estado perigoso). Além disso, o sistema é não bloqueante (não deve travar) e permitir o máximo de liberdade ao gato e ao rato.

## Eventos

Controláveis: Movimentos do Gato

Não controláveis: Movimentos do rato (ocorrem espontaneamente).

- move_rato_esquerda, move_rato_direita

- move_gato_esquerda, move_gato_direita

## Autômatos

Depois de definir a topologia e separar os eventos controláveis e não controláveis, utilizamos o software Supremica para montar os autômatos conforme o funcionamento desejado. Ao criar o projeto, adicionamos os eventos e construímos as plantas necessárias (Rato, Gato e Portas). Assim, temos:

- Autômato do Rato

![](img/rato.png)

- Autômato do Gato

![](img/gato.png)

## Guardas

O sistema de controle do autômato utiliza "guardas" (guards) para gerenciar as transições de estado (movimentos) do gato e do rato entre as 5 salas circulares. O objetivo principal é prevenir a colisão, ou seja, impedir que ambos ocupem a mesma sala simultaneamente.

Antes de qualquer movimento, uma condição de guarda verifica se a sala de destino já está ocupada pelo outro personagem. Por exemplo, o gato só pode se mover para a próxima sala se o rato não estiver lá. Se o destino estiver ocupado, a guarda bloqueia a transição, agindo como uma "porta fechada". Essa lógica se aplica a todos os movimentos, garantindo que nunca haja colisão no autômato.

A lógica é implementada da seguinte forma:

Variáveis de Estado:

gato_state: Armazena a posição atual do gato (um valor de 1 a 5).

rato_state: Armazena a posição atual do rato (um valor de 1 a 5).

Condição de Guarda (Regra de Movimento):
Uma transição de um estado para outro só é permitida se a condição da guarda for verdadeira. A guarda verifica se a sala de destino de um personagem está desocupada pelo outro.

Implementação da Lógica:

Para o Gato se Mover: Um movimento controlável do gato de sua sala atual para uma nova sala (sala_destino) só é autorizado se a seguinte condição for satisfeita:

sala_destino != rato_state
Para o Rato se Mover: Um movimento não controlável do rato para uma nova sala (sala_destino) só ocorre se a condição for satisfeita:

sala_destino != gato_state

## Requisitos

- [Java versão 8.0+](https://www.java.com/pt-BR/)

- [Graphviz](https://www.graphviz.org/)

- [Supremica IDE](https://github.com/robimalik/Waters/releases/tag/v2.7.1)

## Execução

Utilize o software para simular o supervisório e verificar o correto funcionamento do sistema. Abra o arquivo Projeto1_SED.wmod no SUPREMICA, preferencialmente pelo supremica.jar. Para visualizar a simulação do supervisório:

1. Execute o arquivo "supremica.jar" dentro da pasta do Supremica:
```
supremica.jar
```

2. Com o Supremica aberto, abra o projeto "Gato&rato_v2.wmod" que se encontra na pasta source:
```
Gato&rato_v4.wmod
```

## Autores

- [André Medeiros](https://github.com/andreemedeiros)

- [João Marcelo](https://github.com/marcello-rbr)

- [Vitor Lucas](https://github.com/Vitorluca)

Contribua com o projeto [Supervised-Control-Project](https://github.com/andreemedeiros/Supervised-Control-Project/graphs/contributors)

Video explicativo no [Youtube](https://www.youtube.com/watch?v=b7xZtg6EASs)

## Licença

Este projeto é licenciado pela MIT License - veja [LICENSE.md](LICENSE.md) para mais detalhes.
