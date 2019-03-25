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

<div style="text-align:center">
<img src ="https://ztiromoritz.github.io/pico-8-shooter/gif/tut_1.gif" />
</div>

<br>

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
