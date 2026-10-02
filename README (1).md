# IKEA BILRESA scroll wheel – IKEA-style blueprint

> **Based on the original blueprint by [jhol-byte](https://gist.github.com/jhol-byte/b2731a4d2476f530d76b9ff409f7f3a4)** – all credit for the original idea, trigger logic and entity detection goes to them.

Home Assistant blueprint for the IKEA BILRESA scroll wheel (Matter) that behaves like the
official IKEA button table and adds **white (colour temperature) control**.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fjakubhegr18-design%2Fha-bilresa-ikea-style%2Fblob%2Fmain%2FIkea_bilresa_ikea_style.yaml)

## Behaviour (per channel)

| Product group | Press | Double-press | Triple-press | Scroll | Long-press |
|---|---|---|---|---|---|
| Lights | on/off | next colour | previous colour | dim **or white** | switch scroll dim ↔ white |
| Speakers | play/pause | next track | previous track | volume | optional custom action |
| Plugs | on/off | – | – | – | optional custom action |
| Custom | your action | your action | your action | your action | your action |

The button under the LED switches channels on the remote itself.
When switching dim/white the lights flash: short = dim, long = white.

## Setup

1. Import the blueprint (button above) and create an automation for your BILRESA.
2. For every channel with lights create an `input_boolean` helper (e.g. `input_boolean.bilresa_white_ch1`)
   and select it as *White mode helper*. Without it, scroll only dims.
3. Pick the product group and target entities per channel.

No helper scripts are needed.

For the `instant` scroll mode the 9 hidden sensor entities of the BILRESA device must be enabled.
If you have several BILRESA remotes, give each device a unique name (entity names must not end with a number).

## Credits

Remix of [Ikea_bilresa_scroll_wheel](https://gist.github.com/jhol-byte/b2731a4d2476f530d76b9ff409f7f3a4)
by **jhol-byte** ([forum thread](https://community.home-assistant.io/t/ikea-bilresa-scroll-wheel-blueprint-matter-the-original/965365)).
The original has no license; the trigger/entity detection is taken from it. Changes: IKEA-style defaults per
product group, inline colour/white logic (no helper scripts), dim ↔ white mode toggle on long-press.
