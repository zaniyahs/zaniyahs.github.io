---
layout: essay
type: essay
title: "The Blueprints Behind the Code"
date: 2025-04-30
published: true
labels:
  - Design Patterns
  - Software Engineering
  - Next.js
---


There's a moment in every developer's journey when you realize you've solved the same problem before — just in a different project, a different language, a different context. You needed a single shared resource. You needed to break a UI into reusable pieces. You needed a clean wall between your business logic and your database. And every time, you probably built a slightly different solution from scratch, reinventing a wheel that someone else had already designed, named, and documented decades ago.

That's what design patterns are: named, reusable solutions to problems that appear over and over again in software development. They're not copy-paste code snippets. They're more like architectural blueprints — the kind a contractor uses not to dictate exactly where every nail goes, but to communicate a proven structural approach. When an architect says "we're using an open floor plan," every contractor on the crew immediately understands the tradeoffs: more light, less privacy, shared acoustics. Design patterns work the same way.

<img src="../img/blueprint.jpeg" 
     alt="Blueprint architecture" 
     style="width: 100%; border-radius: 8px; margin: 1.5rem 0;">

> "Design Patterns: Elements of Reusable Object-Oriented Software" — published in 1994 by the Gang of Four — catalogued 23 patterns across three families: Creational, Structural, and Behavioral. Decades later, the vocabulary has only grown richer.

## One Instance to Rule Them All

Consider the database connection. In a web application, every incoming request might trigger a database query. Naively, you might open a new connection for each one. But database connections are expensive — they consume memory, require handshakes, and have hard limits. Open too many, and your application collapses under its own weight.

The **Singleton Pattern** solves this by ensuring a class has exactly one instance, and providing a global point of access to it. Think of it like the single master key to a building — there's only one, it's carefully managed, and everyone who needs access goes through the same door.

In my Next.js project, this pattern lives in `lib/prisma.ts`:

```typescript
import { PrismaClient } from "@prisma/client";

const globalForPrisma = global as unknown as { prisma: PrismaClient };

export const prisma =
  globalForPrisma.prisma || new PrismaClient();

if (process.env.NODE_ENV !== "production") {
  globalForPrisma.prisma = prisma;
}
```

During development, Next.js hot-reloads modules constantly. Without this pattern, each reload would spin up a fresh `PrismaClient`, and you'd quickly exhaust your PostgreSQL connection pool. By caching the instance on the `global` object, we guarantee that no matter how many times the module reloads, only one client ever exists. One key. One door.

## Building with Bricks, Not Monoliths

Now imagine building a house not from pre-cut lumber but from one enormous, custom-shaped stone. Need to change a window? You're chiseling into the entire structure. That's what an unstructured frontend feels like — a monolithic tangle where changing one button risks breaking an entire page.

**Component-Based Architecture** is the antidote. It's the idea that a UI should be assembled from small, self-contained, reusable pieces — each responsible for one thing and one thing only. It echoes the classic Composite Pattern: build complex structures from simple, interchangeable parts. React was built around this philosophy.

In my project, this shows up everywhere. A `<Navbar />` doesn't know or care what page it's on. A `<RecipeCard />` renders any recipe you hand it. A `<LoadingSpinner />` is dropped in wherever async work is happening. These components are the bricks — uniform, stackable, replaceable. Server-side logic lives entirely separately, behind a clean wall. The UI never reaches directly into the database; it simply renders what the server hands it.

## The Repository: A Polite Fiction

Here's a question: does your React component need to know that your data lives in a PostgreSQL table called `recipes`, with a `jsonb` column for ingredients and a foreign key to a `users` table? Of course not. It just needs the data.

The **Repository Pattern** creates exactly this polite fiction. It hides the messy reality of data storage behind a clean, consistent interface. The rest of your application speaks in terms of domain objects — "give me all recipes," "save this user" — and the repository worries about how that actually happens under the hood.

In my stack, **Prisma** is the repository. Instead of writing raw SQL:

```sql
SELECT * FROM recipes WHERE author_id = $1;
```

I write:

```typescript
const recipes = await prisma.recipe.findMany({
  where: { authorId: userId },
});
```

Prisma's generated client is type-safe, readable, and database-agnostic. If I ever switched from PostgreSQL to MySQL, my application logic wouldn't change — only the Prisma configuration would. The repository absorbed the change so the rest of the app didn't have to.

## Why Any of This Matters

Design patterns aren't magic, and they're not always the right tool. Overusing them leads to over-engineered code that's harder to read than the "naive" solution would have been. But knowing them gives you something invaluable: a vocabulary for thinking about architecture, and a library of proven solutions to reach for when a familiar problem appears.

In my own project, three patterns quietly held everything together. The Singleton kept the database connection sane. Component-Based Architecture kept the UI flexible and maintainable. The Repository Pattern, embodied by Prisma, kept the data layer clean and decoupled. None of them were accidental. Each was a deliberate choice — a blueprint selected because it fit the problem.

And that, in the end, is what design patterns are really about: not cleverness for its own sake, but intentional, communicable, time-tested craftsmanship.
