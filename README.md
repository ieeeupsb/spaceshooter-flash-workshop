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

## 02. Animação da propulsão

1. Desenhar duas *sprites* da nave com diferente geometria da propulsão, de forma a criar a aparência de movimento. 
2. Criar a função `_update` que, para já, será utilizada apenas para ir trocando entre as duas sprites da nave.
3. Explicar que função `_update` é chamada 30x por segundo.
4. Explicar que queremos contar o tempo e criar global `T=0`.

```lua
function _update()
 t=t+1
 if(t%6<3) then
  ship.sp=1
 else
  ship.sp=2
 end
end
```

## 03. Movimento básico da nave.

1. Criar movimento com a utilização das setas do teclado.
2. Dá deduzir o valor dos botões, por exemplo `btn(0)` é para a esquerda. 

```lua
 if btn(0) then ship.x-=1 end --explicar if e 
 if btn(1) then ship.x+=1 end
 if btn(2) then ship.y-=1 end
 if btn(3) then ship.y+=1 end
```
  
## 04. Prepara a nave para disparar.

1. Explicar que para uma bala SUBIR no ecrã a coordenada *y* tem de DIMINUIR. 
2. O botão **Z** (`btn(4)`) será o botão a clicar para disparar.

Adicionar o seguinte à função `_init()`:
```lua
bullets = {} --explicar o que é um vetor
```

Criar agora uma função de disparo:
```lua
function fire()
 local b = { --explicar que vamos criar uma variavel primeiro
  sp=3, --sprite
  x=ship.x, --ponto de partida
  y=ship.y,
  dx=0,
  dy=-3 --perguntar qual será o movimento se a bala tem de subir
 }
 add(bullets,b) --adicionar ao vetor anterior
end
```

Adicionar o seguinte à função `_draw()`:
```lua
for b in all(bullets) do 
  spr(b.sp,b.x,b.y)
end
```

Adicionar o seguinte à função `_update`:
```lua
for b in all(bullets) do
  b.x+=b.dx
  b.y+=b.dy
end
if btnp(4) then fire() end
```

## 05. Apagar as balas

Explicar que as balas não podem navegar infinitamente pelo ecrã, então, temos de as remover do jogo! Tentar ver se eles sabem quando é que as apagamos.

```lua
if b.x < 0 or b.x > 128 or
   b.y < 0 or b.y > 128 then
   del(bullets, b)
end
```
