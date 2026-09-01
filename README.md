# Did It Ship?

A one-page ledger that answers a single question before you check out at an
online tackle shop: **when this retailer says "In Stock," how often does it
actually ship with tracking within three business days?**

It exists because "phantom stock" (site says in stock, charges your card, then
cancels, backorders, drop-ships from a vendor who doesn't have it, or goes
silent) is the one complaint that shows up in reviews of all ten major US
fishing-supply websites. The research behind that claim is in
[RESEARCH.md](RESEARCH.md).

## What it does, and only that

- Log an order: retailer, what the site claimed, order date, what happened,
  and the day tracking arrived.
- Each in-stock order is scored **Kept** (tracking within 3 business days),
  **Phantom** (cancelled, backordered, partial, shipped late, or silent past
  3 business days), or **Pending** (too early to say).
- The scoreboard shows the ships-as-promised rate per retailer, the count
  behind it, and the median business days to tracking.
- Beside it, 25 documented incidents quoted from public reviews and forums
  during research, with source links. They are context and are not counted
  in the rate.

No accounts, no scraping, no price tracking, no back-in-stock alerts. Those
already exist and solve a different problem.

## Running it

Open `index.html` in a browser. Nothing to build or install. Fonts load from
Google Fonts; everything else is in the one file.

- **Standalone**: orders are saved in that browser's localStorage.
- **Published as a claude.ai artifact with the `db` capability**: the ledger
  is shared live between everyone who opens the page. The page detects which
  mode it is in and says so in the top-right pill.

## Scoring rules

Business days are weekdays between the order date and the tracking date,
excluding the order day. The threshold is 3. Orders where the site said
"Backordered" or "Ships from vendor" are recorded for days-to-tracking but
never count toward the rate, because the site did not make the promise.
