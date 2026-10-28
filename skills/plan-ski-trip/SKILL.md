---
name: plan-ski-trip
description: Plan a ski or snowboard trip with the NEU Ski connector. Use when the user wants to plan or organise a ski trip or ski holiday, choose where to ski, or mentions ski dates, a group or family ski trip, ski budget, lessons, equipment rental, ski insurance or hotels near a ski resort, in any language, for example planificar un viaje de esquí or planificar un viatge d'esquí.
---

# Plan a ski trip with NEU Ski

Use the NEU Ski connector (`neu-ski`) to turn what the user wants into a practical trip proposal.
NEU covers 185 ski resorts in Andorra, Spain, France, Portugal, the United States, Canada,
Argentina and Chile.

## Workflow

1. **Find the resort, if the user named one.** Call `get_neu_resort` with the name or id. If it
   returns "not found", offer its suggestions or call `search_neu_resorts`. Never guess a resort
   id. If the user hasn't chosen a resort, plan with destination mode `recommend` (optionally with
   a preferred `country`).

2. **Open the planner with what the user already said.** Call `show_neu_trip_planner` with:
   - `lang`: `en`, `es` or `ca`, matching the user's language;
   - `resort`: the id from step 1, if any;
   - `preferences`: **only** the fields the user actually stated, using the exact option values in
     `references/preferences.md`.

   Never invent dates, a budget, a group size or priorities. Leave unknown fields out. The planner
   widget lets the user fill in the rest.

3. **If the tool says the preferences are complete,** it returns a planning brief. Use it to write
   the proposal (see "The proposal" below).

4. **If preferences are still missing,** the result lists them. Either let the user complete the
   planner (its "Send to chat" button posts the finished brief as their next message) or ask only
   the essential questions in chat and call `show_neu_trip_planner` again with the new answers.
   Ask at most two questions at a time.

5. **When the user sends a brief from the planner,** treat it as their full request and write the
   proposal. Don't ask again for what the brief already contains.

## The proposal

- For a chosen resort, give a practical plan for it. For "recommend", suggest up to three
  resorts, compare their trade-offs and name your preferred one.
- Include a day-by-day outline that matches the dates and the requested ski days.
- Cover where to stay, how to get there and around, and equipment rental, lessons and insurance
  when the user asked for them.
- Give costs as **estimates**, separate from verified prices, and say clearly when they don't
  fit the user's budget.
- If you can search the web, verify time-sensitive facts (prices, opening dates, snow and lift
  conditions, transport schedules) and cite sources. Otherwise say they need checking.
- Answer in the user's language.

## Rules

- NEU data is **published reference data, not a live snow report**. Never present slopes, lifts,
  prices or seasons as current conditions; point to the resort's official snow report link
  from `get_neu_resort` for live status.
- Never book, buy or reserve anything, and never claim a booking was made.
- Hotel (Trip.com) and ski-insurance (InterMundial) links are **affiliate links**. Keep the URLs
  exactly as the tools return them, and always show the disclosure the tool provides. Mention
  other providers when they fit the user better, and respect a user who prefers another provider.
- Discounts (Trip.com first-booking offers, the NEUSKI10 insurance code) are conditional. Say the
  user must check eligibility and conditions; never promise they apply.
- 3D maps, webcams and snowfall forecasts are on the resort's NEU page (`links.neuPage`), not in
  the chat.
