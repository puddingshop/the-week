# The Week — Project Brief

## What it is
A family wall-calendar dashboard. Alternative to Skylight / Hearth ($400+ commercial products). The TV-article concept was the spark; the design has since pulled hard toward Stendig / Karlsson / Dieter Rams territory.

## Hardware target
Any cheap wall display — iPad, Android tablet, smart frame. Phone for editing, wall for viewing. (Apple TV ruled out for input reasons.)

## The family
Jordan, Sarah, Phoenix, Lua. Adelaide, Australia.

## Data
One shared Google Calendar for all four people (live feed not yet wired — currently sample events).

## Visual references (and what we took from each)

### Skylight Calendar
- Original spark — 4 avatars, color-coded events, vertical timeline, bottom tabs
- **Rejected:** the busyness, the colored block fills, the chrome (weather/Wi-Fi/family-name)
- **Kept:** avatar row, person color identity, tab structure

### Stendig Calendar (Vignelli, 1966 — MoMA collection)
- Helvetica, monumental numerals, zero decoration
- **Adopted:** type does the work, no icons-as-decoration, big day numbers, hairline grids
- Single-day zoom view is most directly Stendig-influenced

### Karlsson Flip Wall Clock
- Year band on top, modular tile grid, asymmetric 2x2 windows, analog clock face
- **Adopted:** the Now/standby view is a direct homage — year band + month/day/time/weekday tiles, hairline dividers, 150px hero day number
- **Toned down:** no flip mechanism, white instead of black, clean digital typography

### macOS-style segmented controls
- Pill-shaped segmented buttons, soft fill on active state
- **Adopted:** the view-mode switcher (Weekend / Weekdays / Week) follows this exact pattern

### Spiral wall calendar (serif arch + sage)
- Considered briefly — rejected as too "kitchen poster," not "wall object"

### Handwritten 12-month poster
- Considered — rejected, too informal for the brief

## Design system

### Color
Two jobs:
1. **Identity** — each person owns a color (Jordan yellow, Sarah pink, Phoenix green, Lua purple)
2. **Focus** — saturation = importance

Hierarchy:
- Past events: 15% opacity, almost no saturation
- Resting (default future): washed out — `saturate(0.45)`, `opacity(0.72)`
- Next-up per person: full saturation, drop shadow, bold
- Tap-focus: tapped person's events snap to full saturation; others fade to 8% ghost

### Type
Helvetica Neue / Inter, tight tracking on numbers (`tabular-nums`, `letter-spacing: -0.05em` on heroes). Caps + wide letter-spacing for labels (0.2–0.4em).

### Accent
One color: Rams orange `#FF5E1F`. Used for: now-line, today indicator, weekday in Now-view tile, that's it.

### Layout
Modular tiles. Hairline dividers (#efefef). Generous negative space. Whole day always visible — no scrolling on calendar views (flex-grid distributes hour rows to fit available height).

## Interaction model (visionOS-spirit)

- **Tap avatar** → focus that person; their events snap to full color, others fade to ghost outlines
- **Tap day-header** → Stendig-style zoom into single day (hero 72px day number)
- **Tap top-date** → enter Now/standby hero view (Karlsson tile grid)
- **Segmented pill** → change zoom level: Weekend (2d) / Weekdays (5d default) / Week (7d)
- **Smooth view transitions** — View Transitions API, snappy 0.28s cross-fade

## Tabs

1. **Calendar** — always defaults to 5-day weekdays
2. **Meals** — weekly dinner planner; tap day → modal to enter name + ingredients
3. **Shop** — auto-aggregates ingredients across week's planned dinners + manual extras section, dedupes, check-off
4. **Jobs** (was Chores) — per-kid editable list with prices, live-updating earned/total

## Standby/home behavior
The Now view is the "standby" mode — Karlsson tile grid showing year, month, day, time, weekday. Reached by tapping the top-date in Calendar. Calendar tab itself never lands here — it always opens to 5-day weekdays.

## Dev
- Live URL: https://puddingshop.github.io/the-week/
- GitHub: https://github.com/puddingshop/the-week
- Dev panel: floating glass pill in grey area (idles desaturated, hover to bring back), with frame-size sliders + presets (Phone / iPad / 9:16 / Skylight)
- Favicon: orange now-line mark on rounded square, doubles as iOS home-screen icon
