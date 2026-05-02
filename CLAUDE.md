# The Week — Working Instructions

Read BRIEF.md first for the full design brief (visual references, design system, interaction model).

## Architecture
Single-file app: everything lives in `index.html` (HTML + CSS + JS). No build step, no framework. Served as a static file.

## The family
Jordan (yellow), Sarah (pink), Phoenix (green), Lua (purple). Based in Adelaide, Australia.

## Views
- **Day** (1 col), **Weekend** (2), **Weekdays** (5), **Week** (7) — segmented pill switcher in topbar
- **Month** — grid calendar with date numbers, accessed via the grid icon
- **Now/Standby** — Karlsson-inspired tile grid (year, month, day, time, weekday)

## Key features
- **Solo focus**: tap a person's avatar to show ONLY their events at full width. All other events are removed from rendering (not just hidden via CSS). Tap again to return to combined view.
- **Day focus**: tap a day header to highlight that column with full-color events.
- **Multi-day events**: rendered as spanning bars in week view (e.g. NYC trip). Month view TODO: make these span across day cells as joined bars.
- **Birthdays**: marching-ants dashed border animation on birthday person's column.
- **Now line**: red horizontal line showing current time on today's column.
- **Next-up**: each person's next upcoming event gets full color + drop shadow.

## Style rules
- Helvetica Neue / Inter. Tight tracking on numbers.
- Only accent color: Rams orange `#FF5E1F` (now-line, today indicator).
- Past events: 15% opacity. Default future: washed out. Next-up: full saturation.
- No scroll on calendar — hour rows flex to fill available height.
- No icons-as-decoration. Type does the work.

## Dev setup
- Dev panel: floating glass pill in the grey area outside the frame, with size presets
- Local server: `python3 -m http.server 8000` (configured in .claude/launch.json)
- Live: https://puddingshop.github.io/the-week/
- GitHub: https://github.com/puddingshop/the-week
