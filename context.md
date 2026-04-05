# Restaurant Management Game — Context

**For:** Hadley (granddaughter)
**Created in chat:** March 26, 2026
**Status:** Working prototype was built in Claude — not yet saved as a standalone file

## Concept

Hadley's idea: Work in a restaurant kitchen. Cook orders and deliver them to patrons at their tables before time runs out. Patrons are impatient, the kitchen is chaotic, and multiple orders pile up at once.

## How It Works

1. **Orders appear** at the top — each shows patron name, food item, table location, and a patience bar draining in real time
2. **Click an order** to select it, then **click the correct kitchen station** to start cooking
3. **Watch the station** — a progress bar fills as it cooks; when done, the order flips to "Ready!"
4. **Click the table** in the dining room to deliver and earn points
5. Repeat — managing multiple concurrent orders under time pressure

## Scoring

| Event | Points |
|-------|--------|
| Base delivery | +50 |
| Tip bonus (patron still happy) | +variable |
| Patron goes furious (too slow) | −10 |

## Chaos Events

Fire every 12–20 seconds at random:
- Kitchen station catches fire (station disabled until cleared)
- Spill resets cooking progress on a station
- New party walks in unexpectedly (new order added)

## Game Feel

- Multiple orders visible and active at once
- Each patron has a visible patience bar — visual urgency
- Kitchen stations are distinct zones (grill, fryer, prep, etc.)
- Dining room is a separate area with labeled tables
- No playable file exists yet — the prototype ran inside the Claude chat session

## Possible Next Steps

- **Build the HTML game** from the concept (the prototype logic is well-defined)
- Add more menu items and station types (fryer, salad bar, dessert)
- Add more tables and a busier dining room
- Difficulty levels (slow lunch vs. Friday dinner rush)
- Sound effects (sizzle, ding, angry patron grumble)
- High score / leaderboard
- Name the restaurant (let Hadley pick)
- Add Hadley's name to the title screen
