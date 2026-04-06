# Hadley's Diner — Game Concept & Current Functionality

**Created:** April 5, 2026
**Designed by:** Hadley
**Built with:** Phaser 3 (HTML/JS, runs in any browser or phone)
**Live at:** https://hadleys-diner.vercel.app

---

## Concept

Hadley's Diner is a 2D side-scrolling restaurant management game. The player controls two characters — **Hadley** (the cook) and **Alex** (the server) — switching between them to cook orders in the kitchen and deliver food to customers in the dining room before the customers lose patience and walk out.

---

## Game Layout

The world is **1600px wide** and scrolls left/right. The camera follows whichever character is active.

| Zone | World X | Description |
|------|---------|-------------|
| Kitchen | 0 – 750 | Three cooking stations, checkerboard tile floor |
| Dividing Wall | 750 – 800 | Brick wall with a door connecting the two rooms |
| Dining Room | 800 – 1600 | Four tables with chairs, customers seat themselves |

---

## Characters

### 👩‍🍳 Hadley (Cook)
- Long brown hair flowing over shoulders, fair skin, white chef hat and chef whites
- Starts in the kitchen
- Walk to a station to start cooking the next waiting order

### 🧑‍🍽️ Alex (Server)
- Blonde hair, red shirt
- Starts in the dining room
- Walk near a station to auto-pick up ready food
- Walk to a table to deliver the food

### Customers
- Three visual variants (different hair, skin tone, outfit color)
- Walk in from the right side of the dining room
- Sit at a free table
- Show a **speech bubble** with a pixel art food image + item name
- Show a **patience bar** that drains over ~26 seconds
- Leave happy (delivery made) or angry (patience ran out)

---

## Kitchen Stations

| Station | Position | Cooks |
|---------|----------|-------|
| GRILL | x=120 | Burger |
| FRYER | x=320 | Fries |
| PREP | x=520 | Pizza, Salad |

- Tap a station while controlling any character to walk there and start cooking
- A **progress bar** fills over 4 seconds while cooking
- A **dim food icon** appears at the station as soon as cooking starts
- When done, the icon brightens to full — food is ready to pick up
- The station bar flashes gold → green as cooking completes

---

## Menu

| Item | Pixel Art Colors |
|------|-----------------|
| Burger | Sesame bun, lettuce, patty, cheese |
| Fries | Yellow fries in a red container |
| Pizza | Triangle slice with crust, sauce, pepperoni |
| Salad | Green leaves in a brown bowl with tomatoes |

---

## Food Visibility

The food item is visible at every stage of its journey:

| Stage | Where food appears |
|-------|--------------------|
| Cooking | Dim icon at the station |
| Ready | Bright full icon on the station counter |
| Carried | Icon floating above the character's head |
| Ordered | Pixel art food image in the customer's speech bubble |

---

## Order Flow

1. Customer walks in → sits at table → speech bubble shows food image + name
2. Player switches to Hadley → taps a station → cooking begins
3. Progress bar fills → food sprite appears on counter
4. Player switches to Alex → walks near the station → **auto-picks up food**
5. Player taps the customer's table → Alex delivers → score awarded
6. Customer leaves happy ✅

---

## Scoring

| Event | Points |
|-------|--------|
| Successful delivery | +50 |
| Tip bonus (patience remaining) | +0 to +50 |
| Customer leaves angry (patience ran out) | −10 |

Score is displayed top-left at all times.

---

## Controls

| Action | How |
|--------|-----|
| Move character | Tap anywhere on the floor |
| Switch to Hadley | Tap the **👩‍🍳 Hadley** button (bottom-left) |
| Switch to Alex | Tap the **🧑‍🍽️ Alex** button (bottom-left) |
| Start cooking | Walk Hadley to a station (tap the station) |
| Pick up food | Walk any character near a ready station (auto) |
| Deliver food | Walk to a table while carrying food (tap the table) |

The active character has a **gold selection ring** under their feet and the camera follows them.

---

## UI Elements

- **Top-left:** Score panel (`★ 0`)
- **Top-right:** Live order list — shows each table's order and status (⏳ waiting / 🍳 cooking / ✅ ready)
- **Bottom-left:** Character switch buttons — highlighted gold when active
- **Bottom-center:** Hint bar with control reminder
- **Above characters:** Floating score popups when delivering
- **Camera:** Smooth follow with 0.08 lerp factor, bounded to world width

---

## Technical Stack

| Layer | Technology |
|-------|------------|
| Game engine | Phaser 3.60 (CDN) |
| Rendering | WebGL (AUTO, falls back to Canvas) |
| Art | Procedural pixel art drawn on HTML Canvas, loaded as Phaser textures |
| Scale | FIT mode — fills any screen size, centered |
| Platform | Single HTML file — works in desktop browser or mobile browser |
| Resolution | 800 × 450 (16:9), world 1600 × 450 |

---

## Pixel Art Characters

All characters are drawn programmatically using HTML Canvas (no external image files). Each "pixel" is 3×3 real pixels. Character height: ~93–108px on screen.

Color customization per character:
- Hair color (+ `longHair: true` flag for flowing long hair — used on Hadley)
- Skin color
- Shirt/outfit color
- Pants color
- Chef hat (optional — Hadley only)

---

## Files

| File | Description |
|------|-------------|
| `hadleys_diner.html` | The complete game (single file, open in browser) |
| `restaurant_game.html` | Original prototype — git-ignored, not deployed |
| `vercel.json` | Routes Vercel root `/` → `hadleys_diner.html` |
| `CONCEPT.md` | This document |

---

## Ideas for Future Sessions

- [ ] Name the server character (currently "Alex" — let Hadley pick)
- [ ] More menu items (milkshake, pancakes, pie)
- [ ] More tables and a busier rush hour
- [ ] Chaos events (kitchen fire, spill, surprise party walks in)
- [ ] Difficulty levels (Quiet Lunch → Friday Night Rush)
- [ ] Sound effects (sizzle, ding, door chime, angry grumble)
- [ ] High score / leaderboard
- [ ] Hadley can customize her chef outfit color
- [ ] Push to GitHub Pages so anyone can play it on their phone via a URL
