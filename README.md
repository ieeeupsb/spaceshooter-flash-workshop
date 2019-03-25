# Spaceshooter Flash Workshop - Programação de um jogo 8-bit!
Quick live programming workshop to demonstrate to kids that programming is fun and easy.

**Objetivo**: Ajudar no ato de lecionar o workshop com este guia.

## 00. Introdução à programação

Este workshop é direcionado a alunos de secundário, sem ou com alguma experiência de programação. A programação, é simplesmente escrever uma sequência de instruções que o computador interpreta! Ele não sabe fazer nada, e tudo o que acontece é porque alguém (neste caso tu!) lhe disse para fazer.

Explicar que:
1. Vamos utilizar é quase como se fosse um computador *virtual* (**PICO8**), com a linguagem de programação *Lua*.
2. Para programar é preciso ter pensamento **lógico e muita tentativa e erro**! Nunca ter medo de estragar coisas, **experimentar** à vontade!
3. O objetivo não é perceber tudo, mas sim perceber os conceitos. Mas qualquer dúvida podem perguntar!
4. Para gravar o progresso, usar o comando `save name`, e para usar esse código posteriormente, escrever `load name.p8`. 

## 01. Desenhar a nave

Criar as funções base `_init` e `_draw`. Funções responsáveis pela inicialização das variáveis de jogo e por desenhar, no ecrã, as *sprites* criadas (explicar que uma *sprite* é uma imagem de um objeto, por exemplo, a nave).

```lua
function _init()
 ship = {x=60,y=60} --explicar posição no ecrã
end

function _draw()
 cls() --para limpar o ecra
 spr(1,ship.x,ship.y) -- explicar o 1 (número da sprite) e posição
end
```

## 02. Animaçãp da propulsão

1. Desenhar duas *sprites* da nave com diferente geometria da propulsão, de forma a criar a aparência de movimento. 
2. Criar a função `_update` que, para já, será utilizada apenas para ir trocando entre as duas sprites da nave.
3. Explicar que função `_update` é chamada 30x por segundo.

```lua
function _update()
 t=t+1
 if(t%6<3) then
  ship.sp=1
 else
  ship.sp=2
end
```

## 03. Movimento básico da nave.

1. Criar movimento com a utilização das setas do teclado.
2. O `btn(0)` é o botão da seta para a esquerda, tenta descobrir os outros!

```lua
 if btn(0) then ship.x-=1 end --explicar if e 
 if btn(1) then ship.x+=1 end
 if btn(2) then ship.y-=1 end
 if btn(3) then ship.y+=1 end
```
  
