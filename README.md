# TradeVolley

TradeVolley is a Windower addon for FINAL FANTASY XI that deposits crystals, clusters, seals, and crests from Inventory in consecutive batches. It supports one character or all local characters with the addon loaded.

## Features

- Trades all eight elemental crystals and clusters to an Ephemeral Moogle.
- Trades Beastmen's Seals, Kindred's Seals, Kindred's Crests, High Kindred's Crests, and Sacred Kindred's Crests to Shemo in Port Jeuno.
- Uses up to eight mixed stacks per exchange, within item stack limits.
- Automatically closes Shemo's deposit receipt so trades can continue without pressing Enter.
- Waits for Inventory confirmation before sending the next batch.
- Supports cancellation on one character or all characters.
- Uses the short command `//tv`. The full command `//tradevolley` also works.

## Installation

1. Extract the ZIP into your Windower `addons` folder.
2. Confirm the file is at `Windower/addons/TradeVolley/TradeVolley.lua`.
3. Load it on each character you want to use:

```text
//lua load TradeVolley
```

To load it automatically, add this line to your Windower startup script:

```text
lua load TradeVolley
```

The addon loads idle. It does not trade until you start a run.

### Updating from CrystalVolley

When no trades are running, unload the old addon and load TradeVolley:

```text
//lua unload CrystalVolley
//lua load TradeVolley
```

Replace any old CrystalVolley startup entries with `lua load TradeVolley`. Do not run both addons together.

## Crystal and Cluster Trades

Stand idle within six yalms of an Ephemeral Moogle with menus closed.

| Command | Action |
| --- | --- |
| `//tv preview` | List eligible crystals and clusters without trading. |
| `//tv start` | Start this character. |
| `//tv start all` | Start all local characters with TradeVolley loaded. |

Each exchange uses up to eight stacks, with up to 12 items per slot, for a maximum of 96 crystals/clusters.

## Seal and Crest Trades

Stand idle within six yalms of **Shemo in Port Jeuno** with menus closed.

Supported items:

- Beastmen's Seal
- Kindred's Seal
- Kindred's Crest
- High Kindred's Crest
- Sacred Kindred's Crest

| Command | Action |
| --- | --- |
| `//tv seals preview` | List eligible seals and crests without trading. |
| `//tv seals start` | Start this character. |
| `//tv seals start all` | Start all local characters with TradeVolley loaded. |

Each exchange uses up to eight stacks, with up to 99 items per slot, for a maximum of 792 seals/crests. Different eligible types can share one exchange.

TradeVolley dismisses the recognized deposit receipt automatically. It does not select conversions or purchase orbs.

## Status and Cancellation

| Command | Action |
| --- | --- |
| `//tv status` | Show this character's current run and confirmed count. |
| `//tv cancel` | Cancel this character's run. |
| `//tv cancel all` | Cancel all local characters running TradeVolley. |

Healing or kneeling for three continuous seconds cancels that character's run. Standing sooner resets the cancellation timer.

An already-sent trade may still finish after cancellation.

## Hotkeys

A hotkey is recommended for convenience, especially when using multiple characters.

**Hotkeys are not installed or configured by this package. You must set them up yourself.**

The author's setup uses:

| Hotkey | Action |
| --- | --- |
| Windows + C + V | Start crystal/cluster trades on all characters. |
| Windows + T + V | Start seal/crest trades on all characters. |

These are examples of custom bindings, not built-in Windower shortcuts. Configure your preferred hotkey tool to invoke the corresponding `//tv start all` or `//tv seals start all` action.

The author's keyboard helper is not included.

## How a Run Works

TradeVolley queues eligible items already in main Inventory when the run starts, then continues until those items are traded or the run stops.

It does not retrieve items from other bags or add newly acquired items to an existing run.

There is no added startup delay. A run waits for an idle character with menus closed. A three-second pause separates confirmed exchanges.

Each character runs independently and must be within range of the correct NPC.

TradeVolley verifies the expected Inventory decrease before continuing. This confirms item removal; it does not independently verify the NPC's stored balance.

If the NPC refuses a trade, storage is full, or confirmation is incomplete, the run stops after its timeout instead of retrying an uncertain trade.

Combat, zoning, logout, an unavailable NPC, or unexpected changes to eligible Inventory items can stop a run. Avoid using another inventory-moving or trading tool during a run.

Other NPC menus are not automatically dismissed.

## Troubleshooting

- **No response:** Confirm TradeVolley is loaded on that character.
- **Hotkey does nothing:** Verify your custom binding and try the equivalent chat command.
- **NPC unavailable:** Move within six yalms of the correct NPC.
- **Menu or confirmation timeout:** Close menus, check Inventory and the NPC response, then start again once idle.
- **Updating an already-loaded addon:** When no trade is running, reload it on each character:

```text
//lua reload TradeVolley
```

## Version

**1.1.1**

Crystal/cluster trading and seal/crest deposits, including automatic Shemo receipt dismissal. Seal trading through the all-character hotkey was confirmed working on eight characters.

---

Author: **Soliserio**
