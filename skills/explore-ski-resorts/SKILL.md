---
name: explore-ski-resorts
description: Find, compare and look up ski resorts with the NEU Ski connector. Use when the user asks which ski resorts are in a region or country, wants resorts for beginners, families, snowboarders or experts, asks about a specific resort's slopes, lifts, elevation, season or facilities, or wants to compare resorts or see a resort dashboard.
---

# Explore ski resorts with NEU Ski

The NEU Ski connector (`neu-ski`) has public reference data for 185 ski resorts.

## Pick the tool

- **Which resorts / where to ski:** call `search_neu_resorts`. Use `query` for a resort,
  region or mountain range ("Pyrenees", "Tahoe", "Alps"). Use `country` and `region` to narrow.
  Use `level` (`beginner`, `intermediate`, `advanced`) to rank by suitability. Add `familyFriendly`,
  `nightSkiing`, `snowParks` or `pass` (e.g. "Ikon", "Epic") only when the user asked. Default
  `limit` 8, up to 20.
- **Facts about one resort:** call `get_neu_resort` with its id or exact name. It returns slopes by
  difficulty, lifts, slope km, elevation, season, lift hours, features, highlights and links.
- **"Show me" a resort:** call `show_neu_resort_dashboard`. It shows an interactive card with
  photo and key stats; the user can open the full dashboard from it.
- **Comparing resorts:** call `get_neu_resort` for each (up to about four), then compare in a short
  table: slopes by difficulty, slope km, lifts, elevation range and family, night-skiing and
  snow-park features. End with a recommendation tied to what the user cares about.

Pass `lang` (`en`, `es` or `ca`) to match the user's language. If a resort isn't found, use the
suggestions the tool returns or search instead. NEU only covers resorts in its catalogue, so say
when a resort isn't in it rather than inventing data.

## Rules

- This is **published reference data, not live conditions**. For today's snow, open lifts or
  weather, give the official snow report or webcam link from `get_neu_resort`, and the resort's NEU
  page for webcams, snowfall forecast, trail map and 3D preview.
- Listed day-pass prices come from the NEU catalogue and may be outdated: present them as
  approximate and suggest checking the resort's website.
- Hotel and insurance links are affiliate links: keep them exact and include the disclosure the
  tool returns. Never book or buy anything.
- To turn the exploration into a trip, use the `plan-ski-trip` skill.
