# NEU Ski for Claude

Plan ski and snowboard trips with Claude using NEU Ski's catalogue of 185 ski resorts in Andorra,
Spain, France, Portugal, the United States, Canada, Argentina and Chile. Search and compare
resorts, open a resort dashboard with slopes, lifts and elevation, and turn your dates, group,
budget and priorities into a planning brief that Claude answers with a day-by-day trip proposal.
No account is needed and nothing is ever booked.

## What's inside

- **NEU Ski connector** (`.mcp.json`): the remote MCP server at
  `https://neu-ski-mcp.vercel.app/claude/mcp`, with four read-only tools:
  - `search_neu_resorts`: find resorts by name, region, country, level or features;
  - `get_neu_resort`: reference facts and links for one resort;
  - `show_neu_resort_dashboard`: an interactive resort card with photo and key stats;
  - `show_neu_trip_planner`: an interactive trip-planning form that prepares a planning brief.
- **Skills**:
  - `plan-ski-trip`: how Claude gathers your preferences, uses the planner and writes the trip proposal;
  - `explore-ski-resorts`: how Claude searches, compares and presents resorts.

## Use it

1. Add the plugin, then connect the **NEU Ski** connector from the plugin's **Connectors** tab.
   It needs no sign-in.
2. Ask, for example:
   - "Find family-friendly ski resorts in the Pyrenees"
   - "Show me the Grandvalira dashboard"
   - "Plan a weekend at La Molina for two intermediate skiers in February"
   - "Compara Baqueira Beret y Formigal para principiantes"
3. In the planner, open the full form, complete it and press **Send to chat**. Claude then writes
   your proposal.

In Claude Code you can also install it from this repository:

```text
/plugin marketplace add wuops/neu-ski-claude-plugin
/plugin install neu-ski@neu-ski
```

## Data and privacy

- **What is sent, and where:** when Claude uses a NEU tool, it sends the tool's arguments to
  `https://neu-ski-mcp.vercel.app/claude/mcp`, hosted by Vercel in the United States. Depending
  on the tool, these are your search text, a resort name or id, your language and, for the trip
  planner, the trip preferences you give: destination, dates, group, ability, budget band,
  transport, departure city, priorities, accommodation, services and any special requirements you
  type.
- **What NEU keeps:** NEU uses those arguments only to build the response and does not store
  them. NEU has no accounts, sets no cookies and receives no Claude account details. Vercel keeps
  short-lived technical request logs (about one hour).
- **What the widgets load:** they load images only from `https://www.neuski.xyz`, run no
  external scripts, and contain no analytics or advertising trackers. "Send to chat" posts the
  planning brief to your conversation as your own message.
- **Links:** these open only when you choose them. They go to www.neuski.xyz, the resort's
  official website, Trip.com hotel search (through `trip.tpo.li`), InterMundial ski insurance and
  the NEU app on the App Store. If you chose travel dates, the Trip.com link includes your check-in
  and check-out dates, and nothing else from your preferences.
- **Policies:** see the privacy policy (https://www.neuski.xyz/en/claude-privacy-policy) and the
  terms of use (https://www.neuski.xyz/en/claude-terms-of-use).

The plugin itself contains only these instructions and the connector address. It runs no code on
your computer.

## Affiliate disclosure

Hotel links (Trip.com) and ski-insurance links (InterMundial) are affiliate links, and NEU may earn
a commission. NEU shows no ads, sponsored results or promotional offers, and you're free to use any
provider. Check prices, terms and availability with the provider before you book.

## Limitations

Resort statistics, seasons and listed prices are published reference data, not a live snow
report, and may be outdated. Check conditions, prices and availability with official sources
before you travel or pay. NEU does not make bookings or take payments.

## Support

Email hola@guillembruix.com or use https://guillembruix.com/store/contact/.

## License

MIT. See [LICENSE](LICENSE).
