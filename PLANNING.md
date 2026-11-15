# Seasonal Menu Planner: Guide

A back-of-house planning tool for **St. Stephen's Green**. Use it to design, cost, and roll out seasonal cocktails and food items before they reach the public menu. The tool lives in `planner.html` and is meant for staff, not diners.

## What it is and who it's for

The planner is a self-contained workspace for the kitchen and bar team to:

- Sketch seasonal cocktail and dish ideas.
- Work out ingredient cost per serve and a sensible menu price.
- Track each item from first idea through to retirement.
- Keep a rollout checklist so nothing is forgotten when an item goes live.

It is a staff tool. The public menu (`index.html` / `menu.html`) stays clean. A small "Staff: Seasonal Planner" link in the menu footer is the only pointer to it.

## How to run it

No install, no server, no login.

- **Double-click** `planner.html` to open it in any browser (it runs from a `file://` path).
- Or open it on the live site at the GitHub Pages URL, for example `https://<your-org>.github.io/<repo>/planner.html`.

Everything is plain HTML, CSS, and vanilla JavaScript, with no build step and no dependencies, matching the rest of this repo.

### Where your data lives

Your work is saved in the browser's **localStorage** under the key `ssg-seasonal-planner`. That means:

- Data is saved automatically on every change (add, edit, delete, status change, checklist toggle).
- Data is tied to **one browser on one device**. It does not sync. Opening the planner on a different computer, a different browser, or a private window shows a fresh, empty planner.
- Clearing site data or browser history can erase it.

To move data between devices or back it up, use Export and Import (see below).

## The seasonal calendar

Items are organized around five events. You can view or filter the planner by any of them:

1. **Spring**
2. **Summer**
3. **Autumn**
4. **Winter**
5. **St. Patrick's Day** (its own event, since the pub is Irish and the day deserves a dedicated lineup)

Each item belongs to one of these five. A starter idea bank seeds a few Irish-pub cocktail and food ideas for every event (think Guinness, Jameson, Baileys, and Tullamore). Pressing "Seed new item" on an idea immediately creates and saves a real item at status **idea**, loads it into the spec sheet, and shows its card on the calendar. From there you edit it freely (recipe lines, costing, price, method, allergens) just like any other item.

## The lifecycle workflow

Every item carries a status badge that moves through five stages in order:

1. **idea**: a concept worth exploring. Not costed or committed yet.
2. **testing**: being developed and trialed. Recipe, cost, and spec are getting worked out.
3. **approved**: signed off by the team, ready to schedule for the menu.
4. **live**: currently on sale to guests.
5. **retired**: taken off the menu. Kept for reference and for reuse next season. This is the final stage: the "Advance status" button stops here and is hidden once an item is retired, so the lifecycle never loops back to idea.

Advancing an item's status is a deliberate, one-way step through the stages above, so the badge always reflects where the item really is. To move a status backward (for example to revive a retired item), edit the item and pick a status from the dropdown.

## How costing works

For each item you enter recipe lines (one per ingredient or component), each with a short description and a line cost. From those the planner computes:

- **Cost per serve**: the sum of all line costs.
- **Suggested price**: the price that hits your target margin, calculated as `cost / (1 - target margin)`. It appears once you enter a positive target margin percentage. Until then it shows a neutral placeholder rather than the bare cost per serve, so it is never mistaken for a recommendation to sell at cost.
- **Actual margin %**: based on the menu price you actually set, calculated as `(price - cost) / price`.
- **Pour cost / food cost %**: the cost as a share of price, calculated as `cost / price`. Bars usually watch pour cost; kitchens watch food cost. Same formula, different name.

Values update live as you type. Empty fields and a price of zero are handled safely: you will see a neutral placeholder rather than an error or a `NaN`.

## The rollout checklist

Before an item goes live, work through the checklist. Its five steps are:

1. **Menu update**: add the item to the menu and set the price.
2. **QR / printables**: refresh the QR target and any printed menus, table cards, or specials boards.
3. **Staff training**: brief bar and floor staff on the recipe, spec, and sell.
4. **Inventory ordering**: order the ingredients and stock needed to serve it.
5. **4-week review**: after about a month, review sales and margin to decide whether to keep, tweak, or retire the item.

Checklist state is saved with the rest of your data, so it survives a page reload.

## Export and import (protecting your data)

Because data is stored per browser and does not sync, use Export and Import to keep it safe and to share it:

- **Export** writes all planner data to a JSON file and downloads it to your computer. No server is involved.
- **Import** reads a JSON file you select and loads it back into the planner, then re-renders. Import replaces all current planner data with the file's contents, so if you already have items the planner asks you to confirm before overwriting them. A malformed file shows an error message instead of breaking the page.

Good habits:

- Export a backup after a big planning session.
- To move your plan to another device or browser, Export on the first one and Import on the second.
- Keep a shared copy of the latest export (for example in a team drive) so the whole team works from the same plan.
