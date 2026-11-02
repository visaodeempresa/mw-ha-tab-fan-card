# MW Tab Fan Confort Card

`custom:mw-tab-fan-card` — o climatizador inteiro em abas.

| aba | o que entra |
|---|---|
| **CLIMATIZADOR** | faixa de temperatura da casa (`mw-rainbow-card`) · foto · fileira de botões de papel (`mw-scene-button-card`) |
| **ENERGIA** | a tomada em `power-button-card`, com tensão/corrente/potência achados sozinhos |

Compositor: a casca e as abas são do `custom:mw-tab-card`; nada é redesenhado aqui.

## Dois modos de comando

| modo | de onde vem o toque |
|---|---|
| `control: scenes` | cenas do HA (`scene.*`) |
| `control: infrared` | teclas do **MW Infrared Controller** (`button.*` do controle pareado) |

Os cinco papéis: **ligar · desligar · velocidade · modo · oscilar**. O que aparece
depende do estado da tomada (`show_when`): apagada mostra ligar;
acesa mostra desligar, velocidade, modo e oscilar.

## Tomada: Tuya, LocalTuya, Tapo ou manual

Os sensores saem do dispositivo da tomada por nome, em português **e** inglês
(`voltagem`/`voltage`, `corrente`/`current`, `potência`/`current_power`).
Energia acumulada (kWh, `today_energy`) nunca entra como potência. Qualquer um
dos três pode ser escolhido à mão no editor.

## Exemplo

```yaml
type: custom:mw-tab-fan-card
power_entity: switch.tomada_climatizador_do_escritorio_socket_1
socket_device: <id da tomada>
image: /local/devices/climatizador-mondial-comfort-air-v2.webp
scenes:
  on: scene.ligar_climatizador_escritorio
  off: scene.desligar_climatizador_escritorio
  speed: scene.velocidade_do_climatizador_do_escritorio
  mode: scene.modo_do_climatizador_do_escritorio
  swing: scene.oscilar_o_climatizador_do_escritorio
rainbow_devices:
  - device: 2b2e01fa4c728068236f012cf609905a
```

## Depende de (HACS)

`MW Tab Card` · `MW Scene Button Card` (≥ 0.4.0, que aceita `button.*`) ·
`MW Rainbow Card` · `MW Power Button Card` · `Mushroom`

## Verificação

```bash
node --check dist/mw-tab-fan-card.js && node tools/probe.js
```

---

Autoria: MAYCON WILLIAN OLIVEIRA <visaodeempresa@gmail.com>
