---
layout: essay
type: essay
title: "My Honest Experience with Effort Tracking on Rainbow Locator"
# All dates must be YYYY-MM-DD format!
date: 2026-05-11
published: true
labels:
  - Software Engineering
  - Nextjs
  - React
  - Bootstrap 5
---

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=IBM+Plex+Mono:wght@400;600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />
  <style>
    :root {
      --ink: #0f0e0d;
      --paper: #f5f1eb;
      --accent: #2a6496;
      --accent-soft: #d0e4f0;
      --muted: #7a7068;
      --rule: #d6cfc4;
      --callout-bg: #f0f6fb;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    body {
      background-color: var(--paper);
      color: var(--ink);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      font-size: 1.08rem;
      line-height: 1.8;
      overflow-x: hidden;
    }

    header {
      position: relative;
      padding: 5rem 2rem 4rem;
      max-width: 860px;
      margin: 0 auto;
      border-bottom: 2px solid var(--ink);
    }

    .kicker {
      font-family: 'IBM Plex Mono', monospace;
      font-size: 0.72rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--accent);
      font-weight: 600;
      margin-bottom: 1.4rem;
      display: flex;
      align-items: center;
      gap: 0.6rem;
    }
    .kicker::before {
      content: '';
      display: inline-block;
      width: 2rem;
      height: 2px;
      background: var(--accent);
    }

    h1 {
      font-family: 'DM Serif Display', serif;
      font-size: clamp(2.2rem, 5vw, 3.6rem);
      line-height: 1.1;
      color: var(--ink);
      letter-spacing: -0.02em;
      margin-bottom: 1.6rem;
    }
    h1 em { font-style: italic; color: var(--accent); }

    .byline {
      font-family: 'IBM Plex Mono', monospace;
      font-size: 0.8rem;
      color: var(--muted);
      display: flex;
      gap: 2rem;
      flex-wrap: wrap;
    }

    main {
      max-width: 860px;
      margin: 0 auto;
      padding: 3.5rem 2rem 6rem;
    }

    h2 {
      font-family: 'DM Serif Display', serif;
      font-size: 1.9rem;
      margin-top: 3.5rem;
      margin-bottom: 1rem;
      line-height: 1.2;
      color: var(--ink);
      letter-spacing: -0.01em;
    }

    p { margin-bottom: 1.4rem; color: var(--ink); }
    em { font-style: italic; }
    strong { font-weight: 500; }

    .rule {
      border: none;
      border-top: 1px solid var(--rule);
      margin: 3rem 0;
    }

    .callout {
      background: var(--callout-bg);
      border-left: 3px solid var(--accent);
      padding: 1.2rem 1.5rem;
      margin: 2rem 0;
      border-radius: 0 4px 4px 0;
    }
    .callout p { margin: 0; font-size: 0.95rem; }
    .callout strong {
      display: block;
      font-family: 'IBM Plex Mono', monospace;
      font-size: 0.7rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 0.5rem;
    }

    .hero-img {
      width: 100%;
      border-radius: 8px;
      margin: 2rem 0;
      display: block;
    }

    .stat-row {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1rem;
      margin: 2.5rem 0;
    }
    .stat-card {
      background: white;
      border: 1px solid var(--rule);
      border-radius: 8px;
      padding: 1.4rem;
      text-align: center;
    }
    .stat-card .number {
      font-family: 'DM Serif Display', serif;
      font-size: 2.2rem;
      color: var(--accent);
      line-height: 1;
      margin-bottom: 0.4rem;
    }
    .stat-card .label {
      font-family: 'IBM Plex Mono', monospace;
      font-size: 0.68rem;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      color: var(--muted);
    }

    @media (max-width: 600px) {
      .stat-row { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

<header>
  <div class="kicker">ICS 314 — Effort Estimation Reflection</div>
  <h1>Estimating the <em>Unestimatable</em>: My Honest Experience with Effort Tracking on Rainbow Locator</h1>
  <div class="byline">
    <span>Za'Niyah Smith</span>
    <span>May 2026</span>
    <span>University of Hawaiʻi at Mānoa</span>
  </div>
</header>

<main>

  <img src="../img/effort.png" alt="Effort estimation" class="hero-img" />

  <h2>Introduction</h2>

  <p>
    When I first heard the words "effort estimation," I thought it sounded simple enough — just guess how long
    something will take, write it down, and move on. What I didn't expect was how much that simple act of
    guessing would teach me about myself as a developer, about my team's workflow, and about the unpredictable
    nature of building software from scratch. Working on <em>Rainbow Locator</em>, a lost and found website
    built for students at the University of Hawaii, gave me a real world crash course in project management
    that no textbook could have fully prepared me for.
  </p>

  <p>
    Rainbow Locator allows UH students to report lost items by submitting a description, a date, and the last
    known location on campus. Students who find items can also log them into the system, making it easier to
    reunite people with their belongings. My primary role on the team was focused on the front end — making
    sure the interface was clean, intuitive, and visually appealing. I had a smaller hand in the functional
    side of the app, but that didn't mean my tasks were any easier to estimate. Beyond the technical work,
    I also ended up serving as the team's live representative during class presentations, which meant I had
    to develop a thorough understanding of the entire project — not just the pieces I personally built. That
    experience gave me a unique perspective on the project as a whole and pushed me to stay informed about
    progress across the board, even on features outside my immediate lane. To be honest without having to do
    that I probably would have been very confused for 80% of the project.
  </p>

  <hr class="rule" />

  <h2>How I Made My Estimates</h2>

  <p>
    With only about four months of software development experience under my belt, I didn't have a deep well
    of historical data to draw from when making estimates. I couldn't look back at a portfolio of past projects
    and say, "Oh, this is similar to that feature I built six months ago." Instead, I leaned heavily on
    intuition and task decomposition — breaking each issue down into smaller mental steps and assigning rough
    time blocks to each one — which the professor helped with tremendously by constantly reminding us that
    "you need to break that up into smaller issues."
  </p>

  <p>
    For example, when estimating styling tasks like building out a card component for lost item listings, I
    would think through the steps: researching the layout, writing the CSS, testing it across screen sizes,
    and making adjustments. Each of those felt like maybe 15–20 minutes individually, so I'd add them up and
    round to the nearest half hour. It wasn't scientific, but it gave me a structured starting point rather
    than just throwing out a random number. For issues that felt familiar — anything involving basic UI layout —
    I felt more confident. For anything touching logic or backend integration, I padded my estimates generously
    because I knew those areas were less predictable for me.
  </p>

  <hr class="rule" />

  <h2>Did Estimating Help Even When I Was Wrong?</h2>

  <p>
    Honestly, yes — even when my estimates were off, the act of estimating forced me to actually <em>think
    through</em> a task before diving in. It made me ask: what does this issue actually require? That question
    alone saved me from starting work without a clear plan — which is a crucial step for a coder that is often
    overlooked.
  </p>

  <div class="stat-row">
    <div class="stat-card">
      <div class="number">60</div>
      <div class="label">minutes estimated for delete button</div>
    </div>
    <div class="stat-card">
      <div class="number">10</div>
      <div class="label">minutes it actually took</div>
    </div>
    <div class="stat-card">
      <div class="number">6×</div>
      <div class="label">overestimate — and that's okay</div>
    </div>
  </div>

  <p>
    One example that sticks out is the delete item button. I estimated it would take around 60 minutes,
    thinking there might be some confirmation logic or styling work involved. In reality, it took closer to
    10 minutes. I had overestimated because I was thinking about edge cases that turned out to be already
    handled elsewhere in the codebase. While that particular estimate was off, the exercise of thinking it
    through beforehand meant I wasn't scrambling when I actually sat down to work on it — I already knew
    my mental steps.
  </p>

  <p>
    On the flip side, there were times where my estimate being wrong in the <em>other</em> direction was
    equally informative. Those moments reminded me that software development rarely goes exactly as planned,
    and that building in buffer time is a skill worth developing.
  </p>

  <hr class="rule" />

  <h2>The Admin Login Page: When Estimation Gets Humbling</h2>

  <p>
    The most instructive experience I had with effort tracking came from working on the admin login page. At
    first glance, it seemed like a straightforward task — we already had a login page for regular users, so
    how different could it be? I estimated it would take about the same amount of time, maybe slightly more.
  </p>

  <div class="callout">
    <strong>The Lesson</strong>
    <p>
      What I learned from that experience wasn't just that I underestimated — it was <em>why</em> I
      underestimated. I had assumed similarity without verifying it. Going forward, I started asking more
      questions upfront before locking in an estimate, specifically looking for hidden complexity that might
      not be obvious at first glance.
    </p>
  </div>

  <p>
    I was wrong. The admin login needed to be meaningfully different from the regular user flow — different
    UI cues to signal elevated access, and different validation logic. It took noticeably longer than I had
    planned, and I had to push back other tasks on my list to accommodate.
  </p>

  <hr class="rule" />

  <h2>How I Tracked My Actual Effort</h2>

  <p>
    I tracked my time using manual start-stop notes on my phone. Whenever I sat down to work on an issue,
    I'd log the time I started, and when I stopped — I'd log that too. I kept these notes either in the
    GitHub issue comments or in a simple running document I kept open on the side.
  </p>

  <p>
    Was it perfectly accurate? Not at all. I didn't count bathroom breaks or social media scroll breaks.
    There were moments where I forgot to note my stop time and had to estimate it after the fact, which
    introduced some imprecision. That said, I believe my tracking was not <em>reasonably</em> accurate for
    coding tasks. Non-coding effort, like reading documentation, thinking through a design problem, or
    collaborating with teammates about layout decisions, was harder to capture consistently and likely
    slightly undercounted in my logs.
  </p>

  <hr class="rule" />

  <h2>AI Assistance: Claude as a Debugging Partner</h2>

  <p>
    I used Claude (by Anthropic) during this project, primarily as a debugging aid when I got stuck on code.
    My use was relatively light — I didn't use it to generate large blocks of code wholesale, but rather to
    help me understand why something wasn't working the way I expected.
  </p>

  <p>
    A typical interaction looked like this: I'd paste in a snippet of code that was producing an unexpected
    result, describe what I wanted it to do, and ask Claude to help me identify the issue. In most cases,
    the explanation helped me understand the problem well enough to fix it myself. Occasionally I'd adapt a
    suggested fix directly into my code, but I always reviewed it carefully to make sure it fit the context
    of our specific project.
  </p>

  <div class="callout">
    <strong>Effort Accounting</strong>
    <p>
      I counted the time I spent formulating my prompts, reviewing Claude's responses, testing any suggested
      fixes, and integrating changes as part of my coding effort. This felt like the most honest way to
      capture it — that time was genuinely spent working on the code, just with an AI collaborator in the loop.
    </p>
  </div>

  <hr class="rule" />

  <h2>What I'd Do Differently Next Time</h2>

  <p>
    Looking back, there are a few things I'd change about my process. First, I'd ask more questions before
    estimating. The admin login page taught me that surface level similarity between tasks can be deceiving.
    A quick five minute conversation with a teammate about the full scope of an issue before writing down an
    estimate would have saved me from several misses.
  </p>

  <p>
    I'd also be more intentional about tracking non-coding effort. Design thinking, planning sessions, and
    even the time spent reading documentation all contribute to how long an issue actually takes. Leaving
    that out of the picture gives an incomplete view of where time actually goes in a project.
  </p>

  <hr class="rule" />

  <h2>Conclusion</h2>

  <p>
    Effort estimation seems pointless in the beginning, but I learned that it was needed in order to stay
    on track. It forces clarity, surfaces assumptions, and creates a feedback loop that makes you better
    over time. Working on Rainbow Locator taught me that the goal of estimation isn't to be right — it's
    to be reasonable, stay curious about why you were wrong, and use that information to improve. That,
    more than any specific tool or technique, is the real skill worth building.
  </p>

</main>
</body>
</html>
