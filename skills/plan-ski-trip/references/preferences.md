# `show_neu_trip_planner` preference values

Pass only what the user said. Every field is optional.

| Field | Allowed values | Notes |
| --- | --- | --- |
| `destination.mode` | `known`, `recommend` | `known` needs a resort (use the tool's `resort` argument or `destination.resortId`) |
| `destination.resortId` | NEU resort id, e.g. `la_molina` | From `get_neu_resort` or `search_neu_resorts` |
| `destination.country` | e.g. `France`, `Spain`, `United States` | Preferred country when recommending |
| `dates.mode` | `dates`, `flexible` | `flexible` = no fixed dates; don't add any |
| `dates.arrival`, `dates.departure` | `YYYY-MM-DD` | Only real dates the user gave; same day = day trip |
| `dates.duration` | `1`, `weekend` (2 days), `3-4`, `week` (5–7 days) | Ski days, separate from nights |
| `group.type` | `solo`, `couple`, `friends`, `family` | |
| `group.people` | whole number 1–50 | Solo = 1, couple = 2, friends/family ≥ 2 |
| `group.ability` | `first`, `beginner`, `intermediate`, `advanced`, `mixed` | `mixed` for groups of different levels |
| `group.activity` | `ski`, `snowboard`, `both` | |
| `budget.band` | `under100`, `100-200`, `200-350`, `350plus`, `unsure` | Per person per day, lodging + pass + meals + rental, **transport excluded** |
| `budget.currency` | `EUR`, `USD`, `CAD`, `CLP`, `ARS` | A label only; no conversion is made |
| `transport.mode` | `car`, `public`, `flight`, `undecided` | |
| `transport.departureCity` | text, up to 80 characters | |
| `priorities` | up to 3 of `value`, `family`, `learning`, `challenging`, `quiet`, `apres`, `comfort` | |
| `stay.accommodation` | `hotel`, `apartment`, `either` | Not needed for a day trip |
| `stay.amenities` | any of `nearSlopes`, `kitchen`, `breakfast`, `spa` | |
| `stay.services` | any of `rental`, `lessons`, `insurance`, or only `none` | `none` can't be combined |
| `stay.specialRequirements` | text, up to 1000 characters | The user's own words; no passwords, payment or health details |

Example: "Two of us, intermediate skiers, want a weekend at La Molina, budget around 150 € a day,
driving from Barcelona":

```json
{
  "lang": "en",
  "resort": "la_molina",
  "preferences": {
    "dates": { "duration": "weekend" },
    "group": { "type": "couple", "people": 2, "ability": "intermediate", "activity": "ski" },
    "budget": { "band": "100-200", "currency": "EUR" },
    "transport": { "mode": "car", "departureCity": "Barcelona" }
  }
}
```

The dates mode, accommodation and services are still missing here, so the planner opens for the
user to finish.
