# dBBH Chief of Staff

**Live demo (fictional data, no install):** https://ellabellae.github.io/DBBH-chief-of-staff/

Built for the president of a student organization to keep track of VP meetings, member data, and event performance, and to extract insights from all three. I'm co-president of [Duke Business Behind Health](https://www.dukebusinessbehindhealth.org), a 300-member club, and I built this so I can answer any question about our members in under a minute and create personalized experiences for them.

It reads our live attendance spreadsheet, Google Calendar, and meeting notes (I use Wispr Flow's notetacker), then answers the questions I used to dig for: how many people RSVP'd versus showed up, what members want from the club, which class years and majors are thin, and what each VP owes me before our next 1:1. It also flags data problems on its own and drafts my meeting agendas from the current numbers.

## Why I built it

We are keeping tack of 4 different programs and 300+ members- we want each experience to feel personalized for our members and rooted in connection and community, but still need to stay structured and driven by data, such as how many members are actually showing up to events and what are they interested in. Every week I would meet with VPs and in team meetings and the same questions came up: 

- How many people RSVP'd to the last event, and how many showed up?
- What are our members looking for from us, and are we programming for it?
- Who is signing up? Which class years and majors are thin?
- Which of my VPs is carrying the most, and what did we agree to last time?

The answers existed, but they were spread across an attendance spreadsheet with a dozen tabs, a Google Calendar, and meeting notes. Pulling them together took long enough that we mostly argued from memory. Now I open one page before the meeting and we look at the gaps together.

Now, we are able to run our Sunday exec meetings 10x more efficiently, staying rooted in the data for each event to quantify "success" and learn from our member's interests. Each meeting, we recap how many members RSVPd vs attended, how much we have grown in membership, if interests of members have shifted, etc.

## What it does

| View | What I use it for |
|---|---|
| **Brief** | What needs me today: urgent actions, signals computed from the data, this week's events and meetings, and next steps from recent meeting notes. |
| **Members** | Sign-ups over time, class year, majors, interests, and what members want from the club. A searchable roster. A matcher that suggests pairs of members to introduce, based on shared interests and goals. |
| **Events** | RSVPs against turnout for every event, upcoming deadlines, which events are missing an RSVP link, and application counts for our programs. |
| **Team** | What each VP owns, their open actions, when we last met, and my private notes. One click drafts a 1:1 agenda or a check-in message from the current data. |
| **Actions** | A follow-up list with owners, due dates, and priorities. Some are suggested by the data; the rest I add. |
| **Ask** | Plain-English questions about the club, answered from everything on the page. |

The **signals** on the Brief are the part I rely on most. They are rules run against the live data, and they have caught real problems: sign-ups with no row in the points tracker, an attendance column that credited 74 people when 96 had checked in, and a spreadsheet header someone had overwritten, which silently broke interest data for the whole site. The **Ask** is especially helpful in meetings where we want quick, member-specific data fast, such as "how many upperclassmen do we have", "what % of members are BME", "what was my idea about re-structuring GBMs from my last meeting?". I personally use Wispr Flow's notetaker for all meetings, then set it up as a connector so all meeting information is automatically imported and utilized. For example, if I say to one of my VPs "I will send you that article I read about XYZ", it will create an action "Send article XYZ to VP ___". 

## How it works

The spreadsheet stays the source of truth. The exec team already lives in it, and Google Forms write to it, so nothing about their workflow changed.

```
Google Forms ─┐
Exec edits ───┼─► attendance spreadsheet ─► this dashboard (read-only)
Website ──────┘            │
                           └─► Supabase ─► member portal on the website
```

- **Hosting.** It is a single HTML file published as a [Claude artifact](https://claude.ai), so there is no server to run. It reads data through connectors I have already authorized in my Claude account.
- **Spreadsheet.** Downloaded as `.xlsx` through the Google Drive connector and parsed in the browser with SheetJS. Tabs are found by name, with a fallback that recognizes each tab by its column headers, so renaming a tab doesn't break anything.
- **Calendar and meetings.** Google Calendar supplies the week ahead. Meeting notes come from Wispr Flow, and the page pulls the "next steps" section from each one.
- **Notes and actions.** Stored in the artifact's own small database, so they follow me across devices. My co-president and executive VP have edit access.
- **Drafts and answers.** Generated by Claude from a context block the page builds out of the current numbers. The prompt tells it to cite figures and to say when something is unknown.

One decision worth recording: the first version read the spreadsheet through Drive's text rendering, which was simple. It turned out to be a cached copy. On September 10 it was two days and 37 sign-ups behind the real sheet. I switched to downloading the actual file, which is always current.

Another: I wanted richer matching for member introductions and considered pulling LinkedIn profiles. Automated scraping breaks LinkedIn's terms and would have put my account at risk, so the tool uses an opt-in "About" note per member instead.

## About this demo

`index.html` is the real interface with the data layer swapped out.

- All 323 members are produced by a seeded random generator. Names, NetIDs, majors, and interests are invented. The exec team, their notes, and the meetings are fictional too.
- Dates are relative to today, so the demo always looks current.
- Outside Claude, the Ask tab and the draft buttons give scripted answers computed from the page's data. The real version sends the same context to Claude.
- Edits are saved in your browser only. "Reset demo" clears them.
- The real tool also has a Leadership view for our weekly officers' meeting. It isn't in the demo.

No real member data, spreadsheet IDs, or keys are in this repository.

## How it was built

I built it in [Claude Code](https://claude.com/claude-code) using the gstack skill suite, over about a week alongside the [club's website and member portal](https://github.com/ellabellae/DBBHwebsite).

1. **Sept 6.** First version: Brief, Members, Events, Team, Actions, Ask.
2. **Sept 7–10.** Used it in real VP meetings. Most of the signals came from things it surfaced that week.
3. **Sept 10.** Replaced the cached spreadsheet reader with a direct file download.
4. **Sept 12.** Added the Leadership view for the weekly officers' meeting, and gave my co-president and executive VP edit access.

## Run it locally

```bash
git clone https://github.com/ellabellae/DBBH-chief-of-staff.git
open DBBH-chief-of-staff/index.html
```

There is no build step and no dependencies.
