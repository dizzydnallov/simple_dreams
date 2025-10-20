![Light Theme](https://github.com/user-attachments/assets/8aab6d86-6213-49bb-8de9-4f4368dc2764)

# Introduction
Simple Dreams — a minimalist Home Assistant theme

## Purpose

Simple Dreams is a Home Assistant theme that prioritises clarity and calm. By pairing a softly styled background with restrained UI elements, it reduces visual clutter so you can navigate faster and focus on what matters.

## Design principles

* Minimal, not bare: Fewer distractions, but never at the expense of readability or usability.
* Top-weighted content: Place interactive cards and key status at the top; leave the art to breathe below.
* Meaningful colour: Use colour sparingly to communicate state (on/off, temperature ranges, alerts).
* Comfortable touch targets: Buttons and cards should feel generous, with consistent spacing.
* Accessible by default: Respect contrast, readable type sizes, and motion sensitivity.

## Background & composition

Simple Dreams is provided with an elegant background where the bottom portion is decorative and the top portion is functional.

* Top “utility” zone: Primary cards, navigation, and glanceable info.
* Bottom “atmosphere” zone: Background only; avoid overlaying cards here to keep the scene calm and legible.

## Layout rules (recommended)

* Safe areas:
    - Top: place your most important content within the top 60–70% of the screen.
    - Bottom: keep the lower 30–40% free of cards, pop-ups, or persistent chips.
* Gutters & spacing: Use consistent horizontal margins (16–24 px) and a vertical rhythm (8 px base scale).
* Density: Favour 2–3 columns on tablets and 3–4 on large screens. One column for phones.
* Z-order: Keep headers, tabs, and quick actions above the safe line; toast/snackbar messages should appear near the top-centre.

---

# Installation

## Prerequisites
- **File Editor** add-on (Settings → Add-on Store).
- **HACS (Home Assistant Community Store)** — optional but recommended for extra cards/themes with details below

> If you don’t have HACS yet, install it via the official HACS guide, then restart Home Assistant.

---

## 1) Enable themes in Home Assistant
Add (or confirm) the following in `configuration.yaml`:

~~~yaml
frontend:
  themes: !include_dir_merge_named themes
~~~

Restart Home Assistant after saving.

---

## 2) Add the theme files
1. Create the folder: `/config/themes/`
2. Place `simple_dreams.yaml` inside `/config/themes/`
3. Create the folder: `/config/www/simple_dreams/`
4. Copy the `backgrounds` and `weather_icons` folders into `/config/www/simple_dreams/`  
   - **Example file:** `/config/www/simple_dreams/backgrounds/uhd_background.webp`

> `config` is the top folder; depending on how you installed Home Assistant, the folder name/path may be called somthing different (i.e. homeassistant), and will incude your configuration.yaml file

---

## 3) Reload themes
- Go to **Developer Tools → YAML → Reload Themes**  
  *or* restart Home Assistant.

---

## 4) Apply the theme
- Open **Profile** (click your username in the sidebar) → **General** → **Theme**
- Select **Simple Dreams**

### Optional
- In **Profile → General**, set **Theme** to **Auto** to follow your device’s light/dark setting.  
  - Alternatively, use an automation to switch themes at **sunset/sunrise** or on a **schedule**.
- In the same **Profile** screen, enable **Always hide the sidebar** for a cleaner display.

---

## Common pitfalls & fixes
- **Theme not listed** → Ensure the `frontend:` section above exists, YAML is valid, then Reload Themes or restart.
- **Background not loading** → Files must be under `/config/www/...` and referenced as `/local/...` in the YAML.
- **Mobile cache** → Hard refresh the app or clear the app cache if changes don’t appear.

---

# Implementation & Recommendations

The following HACS repositories pair beautifully with **Simple Dreams** and help you achieve the clean, glassy look shown in the screenshots.

## Recommended HACS Repositories

### 1) Mushroom

Minimal, modern Lovelace cards that match the theme’s minimalist aesthetic.  
- **Repo:** `piitaya/lovelace-mushroom`  
- **Install (HACS → Frontend):** Search **“Mushroom”**, install, then **Reload resources**.

**Tips**
- Use **fewer, richer** Mushroom cards (chips, entity, climate, lights) in the **top 60–70%** of the view.
- Use **conditionals** to only show cards when they’re **important** and **necessary** (e.g., show the alarm card only when armed, or show a leak sensor card only when it’s detecting).  Conditionals can applied when setting up/ editing a card (under visibility tab)

<img width="2048" height="1080" alt="image" src="https://github.com/user-attachments/assets/d1a8de69-1d49-4f35-ba11-6949a466c3fe" />

---

### 2) card-mod

Lets you apply CSS to Home Assistant UI elements for glass/blur, borders, and polish.
- **Repo:** `thomasloven/lovelace-card-mod`
- **Install (HACS → Frontend):** Search “card-mod”, install, then **Reload** resources.

#### Per-card glass effect (simple)
Add this to any card’s YAML to create a soft, frosted glass effect:

```yaml
card_mod:
  style: |
    ha-card {
      backdrop-filter: blur(20px);
    }
```
### 3) Simple Swipe Card
Create horizontal or vertical swipeable stacks to keep the top area clean while giving quick access to related cards.

- **Repo:** `bramkragten/swipe-card`
- **Install (HACS → Frontend):** Search **“Swipe Card”**, install, then **Reload resources**.

---

### 4) Stack In Card
Nest multiple cards inside a single frame

- **Repo:** `custom-cards/stack-in-card`
- **Install (HACS → Frontend):** Search **“Stack In Card”**, install, then **Reload resources**.

---

### 5) Mini Graph Card
Compact, configurable time-series visual for quick trend scanning without heavy visuals.

- **Repo:** `kalkih/mini-graph-card`
- **Install (HACS → Frontend):** Search **“Mini Graph Card”**, install, then **Reload resources**.


