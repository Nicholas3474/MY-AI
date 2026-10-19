# MY-AI: Daily Anchor

A personal daily dashboard that runs inside Claude as a private claude.ai artifact.

`dashboard/index.html` is the page source. It's published as a private artifact, and all personal data lives in that artifact's data store, not in this repo.

## What it does

- **Today:** greeting, morning check-in question or evening review, ESV verse of the day with a separate reflection, a daily quote with an honest attribution label, three commercial real estate reads, top 3 priorities, today's Google Calendar schedule with overlaps and free windows, and today's tasks.
- **Lists:** tasks, errands, reminders and shopping. Unfinished items carry forward into a short "From earlier" review (five at a time) instead of piling up. "Someday" parks things.
- **Proverbs:** one chapter a day matching the date (the last day of a short month covers the remaining chapters), linked to esv.org, with a "read" check, a note, and a month grid.
- **Assistant:** chat that can add to your lists, set priorities, plan around your calendar, and *suggest* calendar events. Events are only created after you tap **Add to calendar**.
- **Settings:** name, time zone, wake and sleep times, energy peak, goals, check-in times, notification preference, plus privacy details and a delete-all button.

## How the pieces connect

| Piece | How it works |
| --- | --- |
| Google Calendar | Read live through your claude.ai Google Calendar connector (`list_events`). The page only creates events (`create_event`) after you confirm. No tokens are stored in the page or this repo. |
| Your data | The artifact's private database, with access rules limited to the owner and editors. |
| Verse & quote | Built-in rotation keyed to your local date. Each stays the same all day, and none repeats until the full list has cycled (34 verses, 30 quotes). |
| CRE articles | A scheduled Claude task ("Daily CRE reads", 5:46 AM Central) searches free-to-read outlets (Connect CRE, CoStar News, CPE, CRE Daily) for US-only stories and saves three links to the artifact. |
| World briefing | The same morning task saves three world headlines from free outlets (NPR, Axios, CBS News, PBS). WSJ blocks Claude, so the card links straight to WSJ World, Economy and Real Estate instead. |
| Market snapshot | Read live in the page through your Alpha Vantage connector (free plan: 25 requests/day): VOO, QQQ, VXUS end-of-day closing prices (the free plan has no live or delayed quotes), fetched once after each close; 2/10/30-year Treasuries daily; Fed funds weekly. Saved in the artifact so devices share one budget. |
| Notifications | Off. The page can't notify you by itself; a scheduled task can be added later if you want phone notifications. |

## Limitations

- The page updates only while it's open. It doesn't run in the background.
- Assistant chat isn't saved between visits.
- Calendar editing and deleting are done by asking Claude in a conversation, always with confirmation first.

Scripture quotations are from the ESV® Bible (The Holy Bible, English Standard Version®), © 2001 by Crossway, a publishing ministry of Good News Publishers. Used by permission. All rights reserved.
