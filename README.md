
<h1 align="center">
  DDrace Network Mobile Config
  <br>
  <img width=50 src="https://github.com/user-attachments/assets/1d0e0547-99ec-485a-b2dc-31c82e6a8187">
  <br>
  <a href="https://ddnet.org/downloads/"><img src="https://img.shields.io/badge/ddrace-network-6AC1FF?style=for-the-badge&labelColor=FFA500"></a><a href="https://ddnet.org/downloads/"><img src="https://img.shields.io/badge/mobile-4A9CE6?style=for-the-badge"></a>
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

<br>

<h2 name="custom-config">Configuração e Personalização dos botões</h2>

Existem muitas maneiras de posicionar os botões na tela para se adaptar ao seu modo de jogo.  
Logo abaixo você irá aprender a personalizar os botões da maneira que mais se encaixa com a sua jogabilidade.

### Entendendo os botões
Se você der uma olhada no [código](#codigo), vai perceber que abaixo de `"touch-buttons"`  
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

#### `direct-touch`

<p name="posicoes"></p>

#### `x, y, w, h`

#### `shape`

#### `visibilities`

<p name="behaviors"></p>

#### `behavior, type, label, command, id`

<br>

## Personalização

<br>

<h2 name="erros">Identificação de Erros</h2>

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
