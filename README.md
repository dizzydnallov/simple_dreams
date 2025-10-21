# Introduction
Simple Dreams — a minimalist Home Assistant theme

![Light Theme](https://github.com/user-attachments/assets/8aab6d86-6213-49bb-8de9-4f4368dc2764)

![Dark Theme](https://github.com/user-attachments/assets/cd60d334-a4d9-4b31-b8d1-53aebb1cb9c7)

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
* Density: Favour 2–3 columns on tablets and 3–4 on large screens. One column for phones

> Note: While the theme works on smaller screens in portrait orientation (e.g., phones), it’s primarily optimised for tablets. Ongoing updates will continue to improve the mobile experience.

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
  - Alternatively, switch themes via automations at **sunset/sunrise**, on a **schedule**, or based on context. For example, you might enter **Dark Mode** when starting a movie or when setting a specific room ambience.
- In the same **Profile** screen, enable **Always hide the sidebar** for a cleaner, kiosk-like display.

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
- Use **conditionals** to only show cards when they’re **important** and **necessary** (e.g., show the TV card only when playing).  Conditionals can applied when setting up/ editing a card (under visibility tab) - when a condition is added, the card will only show when that condition applies

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

- **Repo:** `nutteloost/simple-swipe-card`
- **Install (HACS → Frontend):** Search **“Simple Swipe Card”**, install, then **Reload resources**.

> Note there is a different repo called "swipe-card" which may also work fine, but the examples below uses 'simple-swipe-card' NOT 'swipe-card'

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

### 6) Clock Weather Card

A HACS-available dashboard card that shows the current date, time, and a clean weather forecast — used in the screenshot for this theme.
- **Repo:** `pkissling/clock-weather-card`
- **Install (HACS → Frontend):** Search **“Clock Weather Card”**, install, then **Reload resources**.
- You’ll need at least one `weather.*` entity (e.g., `weather.home`) for the forecast. Home Assistant includes **Met.no** (Norwegian Meteorological Institute) out of the box—once your **Location** is set in **Settings → System → General**, a `weather` entity is typically available.  
  - If not, add **Weather (Met.no)** via **Settings → Devices & Services → + Add Integration**.  
  - Optional alternatives: **OpenWeatherMap**, **Met Office (UK)**, etc., which also provide `weather.*` entities.

# Exsample Cards to compliment this theme - high recommended!
Some of the cards in the screenshot have been designed specificly to complinet this theme and assist in minimising required cards. Below are the codes requires, and tuturiol on how to setup

### 1) Heavily Customised Weather Card (theme-matched)
![Weather(2)](https://github.com/user-attachments/assets/992d107a-8ae6-499a-94e1-142052b86b8f)

Combines the default **Weather Forecast** card with the **Clock Weather Card**, styled to complement the theme.

- **Custom weather icons** (included in the theme folder; load automatically).
- **Automatic carousel** for extra snippets (wind, precipitation, cloud cover); can also swipe manually.
- **Clock Weather Card** colours and layout tuned for Simple Dreams; the **clock is hidden** (see below for a clock/date variant).

> **Requires (HACS → Frontend, then Reload resources):**  
> `card-mod` (styling) · `stack-in-card` (grouping) · `simple-swipe-card` (carousel) · `clock-weather-card` (forecast bars)

**Placement:** Top-right of your dashboard is recommended for best use of background.  
**Locale:** The sample uses `en-GB`. Change to `en-US` (or your locale) as needed.  
**Entity:** Update `entity:` references if your weather entity differs (e.g., `weather.home`).

#### YAML
```yaml
type: vertical-stack
cards:
  - type: custom:stack-in-card
    mode: vertical
    card_mod:
      style: |
        ha-card {
          background: none !important;
          border: none !important;
          box-shadow: none !important;
        }
    cards:
      - type: weather-forecast
        entity: weather.forecast_home
        show_current: true
        show_forecast: false
        forecast_type: daily
        name: North Rauceby
        forecast_slots: 1
        grid_options:
          columns: full
          rows: 2
        card_mod:
          style: |
            ha-card {
              background: none !important;
              border: none !important;
              box-shadow: none !important;
            }
            .attribute {
              display: none !important;
            }

      - type: custom:mod-card
        style: |
          ha-card {
            margin-top: -52px !important;
            background: none !important;
            border: none !important;
            box-shadow: none !important;
            width: 103% !important;
          }
        card:
          type: custom:simple-swipe-card
          show_pagination: false
          auto_hide_pagination: 2000
          loop_mode: infinite
          enable_auto_swipe: true
          auto_swipe_interval: 7000
          cards:
            - type: markdown
              content: >
                <ha-icon icon="mdi:weather-windy"></ha-icon>
                {{ state_attr('weather.forecast_home', 'wind_speed') }}
                {{ state_attr('weather.forecast_home', 'wind_speed_unit') }}
              card_mod:
                style: |
                  ha-card {
                    background: none !important;
                    border: none !important;
                    box-shadow: none !important;
                    padding: 0 16px !important;
                    text-align: right !important;
                    font-size: 14px;
                    color: var(--secondary-text-color);
                  }
            - type: markdown
              content: >
                <ha-icon icon="mdi:water-percent"></ha-icon>
                {{ state_attr('weather.forecast_home', 'humidity') }}%
              card_mod:
                style: |
                  ha-card {
                    background: none !important;
                    border: none !important;
                    box-shadow: none !important;
                    padding: 0 16px !important;
                    text-align: right !important;
                    font-size: 14px;
                    color: var(--secondary-text-color);
                  }
            - type: markdown
              content: >
                <ha-icon icon="mdi:cloud"></ha-icon>
                {{ state_attr('weather.forecast_home', 'cloud_coverage') }}%
              card_mod:
                style: |
                  ha-card {
                    background: none !important;
                    border: none !important;
                    box-shadow: none !important;
                    padding: 0 16px !important;
                    text-align: right !important;
                    font-size: 14px;
                    color: var(--secondary-text-color);
                  }

  - type: custom:clock-weather-card
    entity: weather.forecast_home
    title: ""
    sun_entity: sun.sun
    weather_icon_type: animated
    animated_icon: true
    forecast_days: 5
    locale: en-GB
    hide_forecast_section: false
    hide_hourly_forecast: true
    hide_clock: true
    hide_date: true
    hourly_forecast: false
    card_mod:
      style: |
        /* Theme colours for bars */
        ha-card {
          --bar-fill:        #e79064;
          --bar-fill-precip: #4ecdc4;
          --bar-track:       rgba(255, 255, 255, 0.4);
          --bar-border:      rgba(30, 50, 45, 0.3);

          background: none !important;
          border: none !important;
          box-shadow: none !important;
          padding: 5px !important;
        }

        ha-card .forecast-text {
          color: var(--forecast-text-color) !important;
        }

        /* Temperature bar */
        ha-card forecast-temperature-bar {
          position: relative;
          width: 100%;
          height: var(--bar-height);
          border-radius: 0 !important;
          overflow: hidden;
        }
        ha-card forecast-temperature-bar-background {
          height: 20px !important;
          background: none !important;
          border-radius: 6px !important;
          border: 0 solid var(--bar-border) !important;
          box-shadow: none !important;
        }
        ha-card forecast-temperature-bar-range {
          height: 96% !important;
          border-radius: 5px !important;
          background: var(--bar-fill) !important;
          --gradient: var(--bar-fill) 0%, var(--bar-fill) 100% !important;
        }
        ha-card forecast-temperature-bar-current-indicator-dot {
          margin-top: 4.5px !important;
          width: 11px !important;
          height: 11px !important;
          border-radius: 3px !important;
          background: white !important;
          box-shadow: 0 0 0 0 rgba(255, 255, 255, 1) !important;
        }
        ha-card forecast-temperature-bar-current-indicator {
          z-index: 1 !important;
        }
        ha-card .day,
        ha-card .temp-high,
        ha-card .temp-low {
          color: var(--bar-text) !important;
          font-weight: 500 !important;
          text-shadow: 0 1px 2px rgba(255, 255, 255, 0.5) !important;
        }
        ha-card .icon {
          filter: none !important;
        }
```

### 2) Sliding Room Temperature / Humidity Cards
![Room](https://github.com/user-attachments/assets/b681c342-ac1a-49a0-a7fd-b190fceb793d)

A clean, central **carousel** that cycles through room panels showing **temperature** and **humidity** with transparent styling to match the Simple Dreams theme. Swipe manually or let it auto-rotate.

- **Large, uncluttered panels** with transparent backgrounds so the theme artwork shines through.
- **Automatic carousel** with optional manual swipe.
- **Placement:** Top-centre is recommended to stay within the theme’s **top utility zone**.

---

#### What you need to change
- **Room titles:** `# Living Room`, `# Outdoors` → set to your room names.
- **Entity IDs:** Replace the generic examples below with your own:
  - `sensor.living_room_temperature`, `sensor.living_room_humidity`
  - `sensor.outdoor_temperature`, `sensor.outdoor_humidity`
- Optional: tweak `auto_swipe_interval`, `hours_to_show` to suit personal preference
- Add more slides by duplicating a vertical-stack block and changing the room name + entities.

---

#### Dependencies (HACS → Frontend, then **Reload resources**)
- `kalkih/mini-graph-card`
- `thomasloven/lovelace-card-mod`
- `nutteloost/simple-swipe-card`

---

#### YAML
```yaml
# If you installed Swipe Card, change the next line to:
# type: custom:swipe-card
type: custom:simple-swipe-card
show_pagination: false
auto_hide_pagination: 2000
loop_mode: infinite
enable_auto_swipe: true
auto_swipe_interval: 10000   # rotate every 10s
cards:

  # ── Slide 1: Living Room ───────────────────────────────────────────────
  - type: vertical-stack
    cards:
      - type: markdown
        content: "# Living Room"     # ← change title
        card_mod:
          style: |
            ha-card { background: transparent; border: none; box-shadow: none; padding: 16px 16px 0 16px; }
            ha-markdown { padding: 0 !important; }
            h1 { font-size: 24px; font-weight: 600; margin: 0; }

      - type: horizontal-stack
        cards:

          # Temperature (change to your room temperature sensor)
          - type: custom:mini-graph-card
            name: Temperature
            icon: mdi:thermometer
            entities:
              - sensor.living_room_temperature      # ← change to your entity
            hours_to_show: 6
            points_per_hour: 2
            height: 90
            line_width: 12
            line_color: "#4ecdc4"
            show:
              name: true
              icon: true
              state: true
              fill: false
              points: false
            card_mod:
              style: |
                ha-card { background: transparent; border: none; border-radius: 8px; margin: 4px; padding: 16px; position: relative; }
                .name { margin-bottom: 8px; z-index: 2; }
                .state { color: #4ecdc4; font-weight: 700; font-size: 27px; line-height: 1; }
                .icon { float: right; margin-top: -8px; color: var(--primary-text-color); }
                .graph { opacity: 0.3; }

          # Humidity (change to your room humidity sensor)
          - type: custom:mini-graph-card
            name: Humidity
            icon: mdi:water-percent
            entities:
              - sensor.living_room_humidity         # ← change to your entity
            hours_to_show: 6
            points_per_hour: 2
            height: 90
            line_width: 12
            line_color: "#a29bfe"
            show:
              name: true
              icon: true
              state: true
              fill: false
              points: false
            card_mod:
              style: |
                ha-card { background: transparent; border: none; border-radius: 8px; margin: 4px; padding: 16px; position: relative; }
                .name { margin-bottom: 8px; z-index: 2; }
                .state { color: #a29bfe; font-weight: 700; font-size: 27px; line-height: 1; }
                .icon { float: right; margin-top: -8px; color: var(--primary-text-color); }
                .graph { opacity: 0.3; }

  # ── Slide 2: Outdoors ──────────────────────────────────────────────────
  - type: vertical-stack
    cards:
      - type: markdown
        content: "# Outdoors"        # ← change title if needed
        card_mod:
          style: |
            ha-card { background: transparent; border: none; box-shadow: none; padding: 16px 16px 0 16px; }
            ha-markdown { padding: 0 !important; }
            h1 { font-size: 24px; font-weight: 600; margin: 0; }

      - type: horizontal-stack
        cards:

          # Outdoor Temperature (change to your outdoor temperature sensor)
          - type: custom:mini-graph-card
            name: Temperature
            icon: mdi:thermometer
            entities:
              - sensor.outdoor_temperature           # ← change to your entity
            hours_to_show: 6
            points_per_hour: 2
            height: 90
            line_width: 12
            line_color: "#4ecdc4"
            show:
              name: true
              icon: true
              state: true
              fill: false
              points: false
            card_mod:
              style: |
                ha-card { background: transparent; border: none; border-radius: 8px; margin: 4px; padding: 16px; position: relative; }
                .name { margin-bottom: 8px; z-index: 2; }
                .state { color: #4ecdc4; font-weight: 700; font-size: 27px; line-height: 1; }
                .icon { float: right; margin-top: -8px; color: var(--primary-text-color); }
                .graph { opacity: 0.3; }

          # Outdoor Humidity (change to your outdoor humidity sensor)
          - type: custom:mini-graph-card
            name: Humidity
            icon: mdi:water-percent
            entities:
              - sensor.outdoor_humidity              # ← change to your entity
            hours_to_show: 6
            points_per_hour: 2
            height: 90
            line_width: 12
            line_color: "#a29bfe"
            show:
              name: true
              icon: true
              state: true
              fill: false
              points: false
            card_mod:
              style: |
                ha-card { background: transparent; border: none; border-radius: 8px; margin: 4px; padding: 16px; position: relative; }
                .name { margin-bottom: 8px; z-index: 2; }
                .state { color: #a29bfe; font-weight: 700; font-size: 27px; line-height: 1; }
                .icon { float: right; margin-top: -8px; color: var(--primary-text-color); }
                .graph { opacity: 0.3; }
```

### 3) Simple Date / Time
<img width="1000" height="192" alt="image" src="https://github.com/user-attachments/assets/401a72d2-ef40-4f5b-8b51-b7b8555eae0c" />

A clean, minimal date–time display.  
**Placement:** Top-right is recommended to stay within the theme’s **top utility zone**.

---

#### Dependencies (HACS → Frontend, then **Reload resources**)
- `piitaya/lovelace-mushroom`
- `thomasloven/lovelace-card-mod`

> **Note on live updates:**  
> Using `now()` inside `mushroom-title-card` updates automatically (about once per minute). No entity is required.  
> If your dashboard ever appears to pause updates, optionally enable the **Time & Date** integration to help keep the UI “ticking”.

---

#### What you can change
- **Format:** Choose 12-hour (`%I:%M %p`) or 24-hour (`%H:%M`).  
- **Locale style:**  
  - UK/EU date: `%A, %d %B` → e.g., *Monday, 20 October*  
  - US date: `%A, %B %d` → e.g., *Monday, October 20*
- **Alignment:** `alignment: end` keeps it right-aligned; use `center` or `start` if preferred.
- **Sizes:** Adjust `--title-font-size` and `--subtitle-font-size`.

---

#### YAML (12-hour time, US-style date)
```yaml
type: custom:mushroom-title-card
title: "{{ now().strftime('%I:%M %p') }}"
alignment: end
subtitle: "{{ now().strftime('%A, %B %d') }}"
card_mod:
  style: |
    ha-card {
      --title-font-size: 38px;
      --subtitle-font-size: 20px;
    }
```

## Credits & Thanks

**Core dependencies (HACS)**
- `piitaya/lovelace-mushroom`
- `thomasloven/lovelace-card-mod`
- `custom-cards/stack-in-card`
- `kalkih/mini-graph-card`
- `pkissling/clock-weather-card`
- `nutteloost/simple-swipe-card`

**Theme inspiration**
- Big thanks to **tgcowell/waves** — this theme began as a fork/inspiration of *Waves*. While many parts have evolved, some elements and sensibilities remain. 🙏

**Home Assistant**
- Huge thanks to everyone who continues to develop and maintain **Home Assistant** — core contributors, frontend and backend teams, integration authors, and the wider community. Your work makes projects like this possible. 🙏
