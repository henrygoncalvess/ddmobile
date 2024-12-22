
<h1 align="center">
  DDrace Network Mobile Config
  <br>
  <img width=50 src="https://github.com/user-attachments/assets/1d0e0547-99ec-485a-b2dc-31c82e6a8187">
  <br>
  <a href="https://ddnet.org/downloads/"><img src="https://img.shields.io/badge/ddrace-network-6AC1FF?style=for-the-badge&labelColor=FFA500"></a><a href="https://ddnet.org/downloads/"><img src="https://img.shields.io/badge/mobile-4A9CE6?style=for-the-badge"></a><a href="https://ddnet.org/downloads/"><img src="https://img.shields.io/badge/download-000000?style=for-the-badge"></a>
</h1>

Tutorial de como configurar e personalizar os controles do jogo mobile

![ddrace print touchs](https://github.com/user-attachments/assets/ac3cbcc8-2f69-43b1-846c-c77a7a7fafb6)

![ddrace print using touchs](https://github.com/user-attachments/assets/dc581954-ae2d-4a4e-92d2-7193dc6749f9)

<br>

<p name="tabela"></p>
<details open="open">
<summary>Tabela de Conteúdos</summary>
  
- [Código dos controles](#código-dos-controles)
- [Aplicação dos controles](#aplicação-dos-controles)
- [Configuração e Personalização dos botões](#custom-config)
  - [Entendendo os botões](#entendendo-os-botões)
    - [Atributos](#atributos)
      - [direct-touch](#direct-touch)
      - [x, y, w, h](#posicoes)
      - [shape](#shape)
      - [visibilities](#visibilities)
      - [behavior, type, label, command, id](#behaviors)
  - [Personalização](#personalização)
- [Identificação de Erros](#erros)
  
</details>

<br>

## Código dos controles

#### [---CLIQUE AQUI---](#codigo) para acessar

<br>

## Aplicação dos controles

#### 1. Após copiar o [código](#codigo), abra o menu e clique na coluna `Jogo/Game`

#### 2. Marque a opção `Editar controles de toque / Edit touch controls`

![editar](https://github.com/user-attachments/assets/32a19ded-8e7d-4774-9649-ea3f11729fc8)

#### 3. Selecione `Importar da área de transferência / Import from clipboard` e confirme

![importar](https://github.com/user-attachments/assets/abaaa77b-f746-455f-abc8-1f572ca5dc38)

#### Demonstração:

https://github.com/user-attachments/assets/e175f945-754f-4655-9a6b-512a9b118fbe

> [!CAUTION]
> Leia [Identificação de Erros](erros) e [Entendendo os botões](#entendendo-os-botões)  
> se der problema

<br>

<h2 name="custom-config">Configuração e Personalização dos botões</h2>

Existem muitas maneiras de posicionar os botões na tela para se adaptar ao seu modo de jogo.  
Logo abaixo você irá aprender a personalizar os botões da maneira que mais se encaixa com a sua jogabilidade.

### Entendendo os botões
Se você der uma olhada no [código](#codigo), vai perceber que abaixo de `"touch-buttons"` (linha 2)  
todos os botões do jogo são separados por vírgula `,` após um par de chaves `{}`.  

EXEMPLO:  

``` json
botão 1
{ <-- primeiro par de chave
  "x": 123456,
  "y": 123,
  "w": 12345,
  "h": 1234,
  "shape": "rect",
  "visibilities": ["ingame"],
  "behavior": {
    "type": "bind",
    "label": "LEGENDA DO BOTÃO",
    "label-type": "localized",
    "command": "COMANDO DO BOTÃO"
  }
}, <-- segundo par de chave e vírgula que indica a separação de outros botões
{
  ... outro comando
}
```

### Atributos

Repare também que **dentro de todos os pares de chaves** `{}` estão armazenados os atributos dos botões (_que são responsáveis  
pelo posicionamento do botão na tela, tamanho, texto etc._) Eles são identificados por:

``` json
"nome do atributo": "valor do atributo"
```

Cada atributo manipula o botão de uma forma diferente. Percebeu que todos os botões tem os atributos:  
`"x"`, `"y"`, `"w"`, e `"h"`? isso acontece porquê esses atributos são responsáveis pelo pociocionamento,   
altura e largura dos botões. Logo abaixo você irá aprender para quê cada atributo serve.

---

### `"direct-touch"`
Este atributo é encontrado nas duas primeiras linhas após a primeira chave `{`.

[---VER CODIGO---](#codigo)

``` json
{
  "direct-touch-ingame": "disabled",
  "direct-touch-spectate": "aim",
  ...
}
```

`"direct-touch-ingame"` é responsável por controlar o que vai acontecer se você tocar diretamente na tela  
do celular durante o jogo

VALORES DISPONÍVEIS | DESCRIÇÃO
:---: | :---
`"disabled"` | desabilitado
`"action"` | ação ativa / executa a ação ativa no momento (_padrão: atirar_)
`"aim"` | mira
`"fire"` | atirar / bater
`"hook"` | gancho / enganchar

`"direct-touch-spectate"` é responsável por controlar o que vai acontecer se você tocar diretamente na tela  
do celular quando estiver no modo **pause** ou **espectador**

VALORES DISPONÍVEIS | DESCRIÇÃO
:---: | :---
`"disabled"` | desabilitado
`"aim"` | mira - permite movimentar a tela

<p name="posicoes"></p>

---

### `"x", "y", "w", e "h"`
Estes atributos são sempre os primeiros a aparecer dentro dos pares de chaves `{}`.

[---VER CODIGO---](#codigo)

``` json
{
  "x": 0,
  "y": 0,
  "w": 200000,
  "h": 100000
}
```

os atributos `"x", "y", "w", e "h"` são responsáveis por controlar a posição e o tamanho dos botões.

> [!IMPORTANT]
> os valores variam de acordo com largura e altura

ATRIBUTO | MÍNIMO | MÁXIMO
:--- | :---: | :---:
`"x"` - eixo horizontal | 0 | variável
`"y"` - eixo vertical | 0 | variável
`"w"` - width (largura) | 50000 | 500000
`"h"` - height (altura) | 50000 | 500000

![2](https://github.com/user-attachments/assets/23c221b5-15d7-447c-898a-01bb25c0deb9) ![sla](https://github.com/user-attachments/assets/89e15d9a-25e1-40b4-864b-b0984dfa6c6b)

---

### `"shape"`
encontrado logo após os atributos de posições, `"shape"` é responsável por definir o formato do botão.

[---VER CODIGO---](#codigo)

``` json
{
  ...
  "w": 200000,
  "h": 100000,
  "shape": "rect"
}
```

VALORES DISPONÍVEIS | DESCRIÇÃO
:---: | :---
`"rect"` | retângulo
`"circle"` | círculo

---

### `"visibilities"`
abaixo de `shape`, `"visibilities"` é responsável por controlar a exibição dos botões e a visão do jogador
[---VER CODIGO---](#codigo)

``` json
{
  "visibilities": ["ingame"]
}
```

VALORES DISPONÍVEIS | DESCRIÇÃO
:--- | :---
`"ingame"` | botão visível
`"zoom-allowed"` | em andamento...
`"vote-active"` | em andamento...
`"dummy-allowed"` | em andamento...
`"dummy-connected"` | em andamento...
`"rcon-authed"` | em andamento...
`"demo-player"` | em andamento...
`"extra-menu"` | em andamento...
`"extra-menu-2"` ao `"extra-menu-5"` | em andamento...

<p name="behaviors"></p>

### `"behavior", "type", "label", "command", "id"`
em andamento...

<br>

## Personalização
Para personalizar, adicionar ou remover um botão:

#### 1. Copie o [código](#codigo) e cole em qualquer editor de texto de sua preferência,  
como o próprio bloco de notas do seu celular, por exemplo.

#### 2. Personalize
Adicione, remova, ou personalize os botões da maneira que desejar, mas sempre seguindo uma estrutura correta.

> [!TIP]
> Leia [Entendendo os botões](#entendendo-os-botões) para editar corretamente

A regra para adicionar ou remover um botão é simples.  
Todos os botões são reconhecidos por um par de chaves `{}` logo depois de `touch-buttons`.

EXEMPLO:

``` json
{
  botão 1
  "x": 123456,
  "y": 123,
  "w": 12345,
  "h": 1234,
  "shape": "rect",
  "visibilities": ["ingame"],
  "behavior": {
    "type": "bind",
    "label": "LEGENDA DO BOTÃO",
    "label-type": "localized",
    "command": "COMANDO DO BOTÃO"
  }
}, <- vírgula que separa um botão de outro
{
  botão 2
  "x": 123456,
  "y": 123,
  .....
}
```

Como você pode ver, para adicionar um botão é só colocar uma vírgula ao final de um par de chaves `{}`  
e respeitar as configurações para personalizá-lo

Para remover um botão, apague o par de chaves `{}` e as configurações dentro dele, incluindo a vírgula

#### 3. Quando terminar de personalizar, copie novamente seu código e siga os passos de --> [Aplicação dos controles](#aplicação-dos-controles)

<br>

<h2 name="erros">Identificação de Erros</h2>
Se você tentou importar suas configurações de controle e recebeu um erro como este:  

![erro](https://github.com/user-attachments/assets/1dc8bb35-01a5-4d6a-99ea-8bd8d318dd29)

#### 1. Abra o menu e selecione a opção **`console`**

![console](https://github.com/user-attachments/assets/7b1a1dae-c429-4b33-b686-a7aec118f336)

O problema vai aparecer na mensagem mais recente

EXEMPLO:  

![desc-erro](https://github.com/user-attachments/assets/104f6894-5a55-4933-97b0-d0dd36ed5d9e)

_Tradução:_ falha ao analisar o botão de toque: o atributo `"w"` deve especificar um número inteiro entre 50000 e 500000.  

Assim como foi explicado em -> [Entendendo os botões](#entendendo-os-botões), o atributo responsável pela largura do botão `"w"`,  
deve ter um valor entre 50000 e 500000.

Então nesse caso, para resolver o problema, basta acessar o texto do código e alterar para um valor válido.  
Mas caso o motivo do erro seja outro, é só olhar o console e ler a mensagem para saber como resolver o problema.

> [!NOTE]
> repare que a mensagem diz "_could not parse button at index 0_" - Tradução: "não foi possível analisar o botão no índice 0"

Isso acontece porquê todos os botões possuem um índice / posição. O índice / posição do botão, nos ajuda a  
entender aonde se encontra o erro

``` json
{
  índice 0
  "atributo-exemplo": "valor-exemplo"
},
{
  índice 1
  "atributo-exemplo": "valor-exemplo"
},
{
  índice 2
  "atributo-exemplo": "valor-exemplo"
},
...
```

De acordo com essa regra, o meu problema de exemplo se encontraria dentro do primeiro par de chaves `{}` logo  
abaixo de `"touch-buttons"` no código, pois este par de chaves que é o **índice 0** 

<br>
<br>

[---VOLTAR---](#tabela)

<p name="codigo"></p>

``` json
{
  "direct-touch-ingame": "disabled",
  "direct-touch-spectate": "aim",
  "touch-buttons": [
    {
      "x": 5000,
      "y": 740000,
      "w": 150000,
      "h": 260000,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "esquerda",
        "label-type": "localized",
        "command": "+left"
      }
    },
    {
      "x": 165000,
      "y": 740000,
      "w": 150000,
      "h": 260000,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "direita",
        "label-type": "localized",
        "command": "+right"
      }
    },
    {
      "x": 830000,
      "y": 725000,
      "w": 150000,
      "h": 230000,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "pular",
        "label-type": "localized",
        "command": "+jump"
      }
    },
    {
      "x": 95000,
      "y": 20000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "Prev. weapon",
        "label-type": "localized",
        "command": "+prevweapon"
      }
    },
    {
      "x": 178333,
      "y": 20000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "Next weapon",
        "label-type": "localized",
        "command": "+nextweapon"
      }
    },
    {
      "x": 5000,
      "y": 20000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": [],
      "behavior": {
        "type": "predefined",
        "id": "extra-menu",
        "number": 1
      }
    },
    {
      "x": 95000,
      "y": 180000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu", "zoom-allowed"],
      "behavior": {
        "type": "bind",
        "label": "-Zoom",
        "label-type": "localized",
        "command": "zoom-"
      }
    },
    {
      "x": 178333,
      "y": 180000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu", "zoom-allowed"],
      "behavior": {
        "type": "bind",
        "label": "Default zoom",
        "label-type": "localized",
        "command": "zoom"
      }
    },
    {
      "x": 261666,
      "y": 180000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu", "zoom-allowed"],
      "behavior": {
        "type": "bind",
        "label": "+Zoom",
        "label-type": "localized",
        "command": "zoom+"
      }
    },
    {
      "x": 95000,
      "y": 100000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu"],
      "behavior": {
        "type": "bind",
        "label": "Scoreboard",
        "label-type": "localized",
        "command": "+scoreboard"
      }
    },
    {
      "x": 268333,
      "y": 20000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "Chat",
        "label-type": "localized",
        "command": "chat all"
      }
    },
    {
      "x": 358333,
      "y": 20000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "Team chat",
        "label-type": "localized",
        "command": "chat team"
      }
    },
    {
      "x": 430000,
      "y": 890000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu", "vote-active", "-demo-player"],
      "behavior": {
        "type": "bind",
        "label": "Vote yes",
        "label-type": "localized",
        "command": "vote yes"
      }
    },
    {
      "x": 530000,
      "y": 890000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu", "vote-active", "-demo-player"],
      "behavior": {
        "type": "bind",
        "label": "Vote no",
        "label-type": "localized",
        "command": "vote no"
      }
    },
    {
      "x": 590000,
      "y": 320000,
      "w": 320000,
      "h": 500000,
      "shape": "circle",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "predefined",
        "id": "joystick-aim"
      }
    },
    {
      "x": 881000,
      "y": 16667,
      "w": 119000,
      "h": 270000,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "pular",
        "label-type": "localized",
        "command": "+jump"
      }
    },
    {
      "x": 5000,
      "y": 100000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu"],
      "behavior": {
        "type": "bind",
        "label": "Pausar",
        "label-type": "localized",
        "command": "say /pause"
      }
    },
    {
      "x": 5000,
      "y": 180000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["-ingame", "extra-menu"],
      "behavior": {
        "type": "predefined",
        "id": "spectate"
      }
    },
    {
      "x": 351666,
      "y": 180000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu"],
      "behavior": {
        "type": "bind",
        "label": "Morrer",
        "label-type": "localized",
        "command": "kill"
      }
    },
    {
      "x": 185000,
      "y": 100000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu"],
      "behavior": {
        "type": "bind",
        "label": "Mostrar outros",
        "label-type": "localized",
        "command": "say /showothers"
      }
    },
    {
      "x": 275000,
      "y": 100000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu"],
      "behavior": {
        "type": "bind",
        "label": "Travar time",
        "label-type": "localized",
        "command": "say /lock"
      }
    },
    {
      "x": 365000,
      "y": 100000,
      "w": 83333,
      "h": 66667,
      "shape": "rect",
      "visibilities": ["extra-menu"],
      "behavior": {
        "type": "bind",
        "label": "HUD",
        "label-type": "localized",
        "command": "toggle cl_overlay_entities 0 100"
      }
    },
    {
      "x": 335000,
      "y": 890000,
      "w": 70000,
      "h": 50000,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "Laser",
        "label-type": "localized",
        "command": "+showhookcoll"
      }
    },
    {
      "x": 765000,
      "y": 16667,
      "w": 110000,
      "h": 270000,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "HOOK",
        "label-type": "localized",
        "command": "+hook"
      }
    },
    {
      "x": 652000,
      "y": 16667,
      "w": 110000,
      "h": 270000,
      "shape": "rect",
      "visibilities": ["ingame"],
      "behavior": {
        "type": "bind",
        "label": "FIRE",
        "label-type": "localized",
        "command": "+fire"
      }
    }
  ]
}
```
