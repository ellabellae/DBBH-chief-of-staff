# dBBH Chief of Staff

**Live demo (fictional data, no install):** https://ellabellae.github.io/DBBH-chief-of-staff/

<img width="100%" alt="chief-of-staff-brief" src="https://github.com/user-attachments/assets/0b7422eb-7a35-401a-b293-8087222dec02" />

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
| **Brief** | What needs me today: urgent actions, signals computed from the data, this week's events and meetings, and next steps from recent meeting notes. A **since last week** card compares sign-ups, first-time attendees, check-ins and actions with seven days ago, and drafts the Sunday exec update. Each meeting next step becomes a tracked action in one click (steps already tracked are marked). |
| **Members** | Sign-ups over time, class year, majors, interests, and what members want from the club. **Are we programming for it?** sets every interest against this semester's events and flags what nothing serves. **Follow up** names who RSVP'd and didn't come and who signed up but hasn't come yet, with a drafted note each. A searchable roster. A matcher that suggests pairs of members to introduce, based on shared interests and goals. |
| **Events** | RSVPs against turnout for every event, upcoming deadlines, which events are missing an RSVP link, and application counts for our programs. |
| **Forecast** | How many people will come to each upcoming event (a likely number and a range), whether the booked room fits, and how much money to request. It learns from past events how the day, start time, free food and point in the semester change turnout. A what-if panel lets us try another day, time or room before booking, and the funding request builds itself and copies straight into a sheet. **Who to invite personally** ranks members who haven't RSVP'd by interest fit and how likely they are to come, with a drafted invite each. It also checks itself: each past event is forecast without seeing its own result. In the demo, past events are fictional and generated with known patterns. |
| **Team** | What each VP owns, their open actions, when we last met, and my private notes. One click drafts a 1:1 agenda or a check-in message from the current data. |
| **Ask** | Questions about the club in plain words ("which seniors have never come?", "how much should we request this fall?"). Claude gets the current numbers and can look up specific members and who came to what: names, year, interests and attendance, never emails. |
