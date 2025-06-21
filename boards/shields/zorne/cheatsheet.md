# ZMK Cheatsheet – **zorne** shield

---

> Everything below reflects the current source files you shared.  
> Legend used: **tap** → default key sent, **hold** → secondary behaviour, **DT** → double-tap, **SL** → sticky-layer, **SS** → sticky-shift, **HRM** → *home-row-mod*.

## 1  Layers & how to reach them

| # | Name | Purpose | How to enter |
|---|------|---------|--------------|
| 0 | **DEF** | Default alpha layer (Colemak-ish) & HRMs | Powered-on default |
| 1 | **NAV** | Navigation / media / system | • Hold **A** or **O** (HRMs with suffix `NAV`) → SL  \
|   |      | | • Thumb **ESC** key (`&lt NAV ESC`) – hold  \
| 2 | **NUM** | Numbers, F-keys, reset & power | • Thumb **TAB** key (`&lt NUM TAB`) – hold  \
|   |        | | • Thumb **BSPC** key (`&bs_del_nav NUM 0`) – hold |
| 3 | **MSE** | Mouse keys & Bluetooth switching | • Thumb **SPACE** (`&lt_spc MSE 0`) – hold |
| 4 | **GM1** | Gaming mode 1 (WASD etc.) | Toggle key bottom-left on **MSE** (`&tog GM1`) |
| 5 | **GM2** | Gaming mode 2 (numbers on left) | Layer-tap **SPACE** in GM1 (`&lt GM2 LALT`) |

## 2  Home-row modifiers (HRMs)

Left hand (prefix `hml`/`hmll`)

| Key | tap | hold |
|-----|-----|------|
| Q | `Q` | — |
| W | `W` | **LGUI** |
| F | `F` | **LCTRL** |
| P | `P` | **LSHFT** |
| B | `B` | **LALT** |
| A | `A` | **SL NAV** |
| R | `R` | **LGUI** |
| S | `S` | **LCTRL** |
| T | `T` | **LSHFT** |
| G | `G` | **LALT** |

Right hand (prefix `hmr`/`hmlr`)

| Key | tap | hold |
|-----|-----|------|
| J | `J` | **RALT** |
| L | `L` | **RSHFT** |
| U | `U` | **LCTRL** |
| Y | `Y` | **LGUI** |
| ' | `'` | — |
| M | `M` | **RALT** |
| N | `N` | **RSHFT** |
| E | `E` | **LCTRL** |
| I | `I` | **LGUI** |
| O | `O` | **SL NAV** |

> HRMs use *balanced* flavour (tap-preferred but quick hold if opposite hand key pressed).  
> Quick-tap window `175 ms`, tapping-term `280 ms`.

## 3  Thumb cluster

```
LH3  &lt NAV ESC   → tap ESC, hold SL NAV
LH2  &lt NUM TAB   → tap TAB, hold SL NUM
LH1  (Space mirror)
LH0  &lt_spc MSE 0 → tap SPACE, shift-tap ". " + SS, hold SL MSE

RH0  &lt_spc MSE 0 (mirror of LH0)
RH1  &lt MSE RETURN (tap RETURN, hold SL MSE)
RH2  &bs_del_nav NUM 0  (BSPC / (shift)DEL / hold SL NUM)
RH3  &lt NAV ESC  (mirror of LH3)
```

## 4  Combos

Fast combos (`≈12 ms`) fire on neighbouring keys; slow combos (`≈20 ms`) on vertical columns. All combos have `require-prior-idle-ms = 200` so they don't interrupt rolling.

### 4.1  Horizontal – left hand

| Keys | Output |
|------|--------|
| LT3 + LT2 | **ESC** |
| LT2 + LT1 | **RET** |
| LM3 + LM2 | **TAB** (with HRM-repeat) |
| LM2 + LM1 | **RET** |
| LB3 + LB1 | **CUT** (`LC X`) |
| LB3 + LB2 | **COPY** (`LC INS`) |
| LB2 + LB1 | **PASTE** (`LS INS`) |

### 4.2  Horizontal – right hand

| Keys | Output |
|------|--------|
| RT1 + RT2 | **BSPC** |
| RT2 + RT3 | **DEL** |
| RM1 + RM2 | **(** / **<** (HRM `lpar_lt`) |
| RM2 + RM3 | **)** / **>** (HRM `rpar_gt`) |
| RB1 + RB2 | `[` |
| RB2 + RB3 | `]` |

### 4.3  Vertical symbol combos

Left: `@ # $ %`, ` \ = ~`  
Right: `^ + / * &`, `_ - |` … (see `combos.dtsi` for full list).

## 5  Special behaviours & morphs

| Behaviour | tap | shift-tap | ctrl-shift-tap |
|-----------|-----|-----------|----------------|
| `comma_morph` | `,` | `;` | `<` |
| `dot_morph`   | `.` | `:` | `>` |
| `qexcl`       | `?` | `!` | — |
| `lpar_lt`     | `(` | `<` | — |
| `rpar_gt`     | `)` | `>` | — |
| `copy_cut` (tap-dance) | COPY | DT → CUT | — |

Mouse helpers:

* `mouse_up` / `mouse_down`: cursor move; **shift** = scroll.
* Pointing defaults: move `1200`, scroll `600`, smooth acceleration (time-to-max 1–1.5 s).

Other hold-taps:

* `lt_spc` – tap SPACE, **shift-tap** inserts ".␠" then sticks SHIFT; hold = SL MSE.
* `bs_del_nav` – tap BSPC / shift=DEL / rshift=SHIFT-DEL; hold = SL NUM.

## 6  Layer contents (condensed view)

```text
NAV ─ Prev  RW  Play FF Next | Del-word  Home PgDn PgUp End
        Vol↓ Vol↑ Mute      | BSPC  ← ↓ ↑ →
        Brightness CapsWord Cancel …

NUM ─ F-keys, USB/BLE toggle, Bootloader, Sys-reset, Soft-off
        Numpad 789 / 456 / 123 • 0.

MSE ─ BT profiles 0-3 / clear | Mouse buttons MB1-5
        Cursor move  ← ↓ ↑ →  | Wheel ← ↓ ↑ →
        Toggle GM1 bottom-left

GM1 ─ WASD cluster, modifiers on left, Space on thumbs; toggle bottom-left.

GM2 ─ TYWER on left, numbers mid row, Space thumbs; returns via toggle.
```

## 7  System / power / output keys

| Key / Behaviour | Location | Action |
|-----------------|----------|--------|
| `&soft_off` | NUM layer, thumbs | Power off (hold ≥ 3 s) |
| `bootloader` | NUM top-left/right | Enter UF2 bootloader |
| `sys_reset` | NUM mid-bottom | MCU reset |
| `out OUT_TOG` | NUM mid row | Toggle USB ↔ BLE |
| `bt BT_SEL n` | MSE top row | Select BLE profile 0-3 |
| `bt BT_CLR`   | MSE top row | Clear bond list |

## 8  Timings & constants

* **QUICK_TAP_MS** – 175 ms  
* **HRM tapping-term** – 280 ms  
* **Generic hold-tap term** – 200 ms  
* **Combo timeout** – *fast* 12 ms / *slow* 20 ms  
* **Sticky-key release** – 900 ms  
* **Soft-off hold-time** – 3000 ms

---

### Tips

1. HRMs are *balanced*: rolling to the opposite hand (incl. thumbs) favours **tap**.
2. Combos require prior idle (200 ms) so they never trigger in the middle of fast rolls.
3. The **Cancel** key (NAV bottom-right) exits Caps-Word, Num-Word, Smart-Mouse, etc.
4. Shift-tap on **SPACE** inserts ".␠" and activates one-shot **Shift** for the next char.

Happy typing! 🚀 