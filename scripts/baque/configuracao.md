---
description: Veja as todas configurações disponiveis em nosso sistema.
---

# Configuração

## Introdução

Essa página diz referente o arquivo `shared/config.lua` da resource `zhawty-baque`.

## Comandos

Configurações para alterar os comandos da resource.

* `panel` - Comando que irá abrir o painel principal.
* `initEvent` - Comando que irá começar o evento (Somente caso o `InitMode` seja `command`).

## Regras

Configurações para alterar as regras de funcionamento da resource.

* `daysToExpire` - Dias para expirar o baque e virar uma invasão.
* `maxDayToInvasion` - Quantidade máxima de dias que uma área tem para invadir antes que vire um baque novamente.&#x20;
* minAttackers - Regra para quantidades minimas de atacantes para os eventos.
  * invasion - Quantidade minima de atacantes dentro de uma área para invadir.
  * thud - Quantidade minima de atacantes dentro de uma área para baquear.
  * police - Quantidade minima de policiais dentro de uma área para invadir.
  * onlinePolice - Quantidade minima de policiais ativos para invadir.
* `invasionTime` - Todas as horas que uma invasão pode ocorrer.
* `thudTime` - Todas as horas que um baque pode ocorrer.
* `policeTimeInterval` - Intervalo de tempo entre uma invasão policial e outra.
* `timeToOpenChest` - Tempo máximo em segundos que uma área tem para abrir um baú caso ganha uma invasão.
* `minDefensors?` - Minimo de defensores que uma área precisa ter para que um evento possa ocorrer dentro dela.&#x20;

## Interface

Configurações para editar valores exibidos na interface.

* `MainColor` - Um valor RGB em formato de `string` por exemplo: `255, 36, 98`.

## Áreas

Configurações para criar uma nova área.

```lua
['NOME_DA_AREA'] = {
    displayName = 'NOME_DE_EXIBICAO', -- Nome que será exibido em logs e etc
    perms = { 'PERMISSÕES_DA_AREA' }, -- Permissões de acesso
    police = false, -- Caso seja da policia coloque somente até essa parte e coloque como `true`
    main = {
        coord = vec3(0.0, 0.0, 0.0), -- Coordenada que irá ser baseado para criação da area
        init = vec3(0.0, 0.0, 0.0), -- Coordanada do marker (Caso o InitMode seja 'gaza')
        range = 150.0, -- Range máximo de área
        flags = {
            model = `prop_mp_barrier_01`, -- Modelo da bandeira
            coords = { -- Coordernadas das bandeiras
                ['1'] = { -- Sempre o valor sendo uma string
                    coord = vec3(1313.07,-756.93,67.18) -- Coordenada da bandeira
                },
            }
        }
    },
    poly = { -- Polyzone, opcional:
        vector2(0.0, 0.0)
    }
},  
```

## Combatlog

Configuração do sistema de combatlog.

* `Combatlog` - Objeto com as configurações das regras de combatlog.
  * `mode` - Modo em que o sistema funcionará.
    * `global` - Irá funcionar sempre que um player der um tiro e se desconectar do servidor dentro de um tempo configurado.
    * `default` - Irá funcionar somente quando o player se desconectar do servidor morto durante um baque ou invasão.
  * `time` - Tempo em milisegundos que o player ficará em cooldown até poder se desconectar (Somente caso o `mode` seja `global`)
* `DropItems` - Array de items que irão ser removidos do inventário do player punido e irão aparecer para serem pegos no como configurado.

## Modos de inicialização

Explicação de todos os modos de inicialização.

* `InitMode` - Váriavel principal para definir o funcionamento.
  * `command` - Inicia pelos commandos informados no inicio desse documento.
  * `automatic` - Inicia de forma automatica quando tiver a quantidade necessária para iniciar o evento.
  * `gaza` - Inicia baseado no marker configurado em cada área chamado pela variável `init`, necessitando apertar a tecla `E` para iniciar o evento.

## Sistema de "Gaza"

Configurações extras para o sistema quando o `InitMode` for `'gaza'`.

* GazaMarker - Configuração do marker que irá ser exibido.

```lua
GazaMarker = {
    type = 1, -- Tipo do marker.
    width = 1.0, -- Largura do marker.
    height = 1.0, -- Altura do marker.
    color = { r = 255, g = 0, b = 0, a = 155 } -- Configuração de cor do maker.
},
```
