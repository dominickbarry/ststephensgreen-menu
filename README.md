# St. Stephen's Green — Digital Menu

A mobile-friendly, single-page digital menu for **St. Stephen's Green**, an Irish pub & restaurant at 223 Castro Street, Mountain View, CA.

## What's here

- `index.html` / `menu.html` — the full menu page (identical content). `index.html` is what GitHub Pages serves at the site root.
- `planner.html`: the staff Seasonal Menu Planner, a back-of-house tool for designing, costing, and rolling out seasonal cocktails and dishes.
- `PLANNING.md`: the guide to the planner. Covers how to run it, the seasonal calendar, the lifecycle workflow, the costing model, and data export/import.
- Self-contained: plain HTML + CSS, no build step, no dependencies. Opens instantly on any phone.

## Sections

Appetizers · Salads, Bowls & Healthy Options · Irish Favourites & Entrées · Burgers & Sandwiches · Dessert · Sides · Drinks

## Editing

- **Food** prices and items are the restaurant's confirmed menu.
- **Drink** prices are marked with a small gold **est** (estimate) and should be replaced with actual prices. The beer taps are confirmed; cocktails and whiskeys are typical Irish-pub selections to adjust.
- To edit, open the HTML and change the text inside each `.item-name`, `.item-desc`, and `.price`.

## QR code

A QR code at the bottom of the page links diners to the online menu. Once this page is live on GitHub Pages, point the QR at the Pages URL by editing the `data=` value in the QR `<img>` `src`.

## Seasonal planning tool

`planner.html` is a staff-only workspace for planning seasonal menu changes. It organizes cocktail and food items around five events (Spring, Summer, Autumn, Winter, and St. Patrick's Day), works out cost per serve and pricing, and tracks each item through a lifecycle (idea, testing, approved, live, retired) with a rollout checklist. Data is saved per browser in localStorage, with JSON export/import to back it up or move it between devices. A discreet "Staff: Seasonal Planner" link in the menu footer points to it. See `PLANNING.md` for the full workflow guide.
