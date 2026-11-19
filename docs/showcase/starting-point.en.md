# Starting point

## A lookup app that grew

I never set out to build a character manager. What I wanted was an app for my phone, because the descriptions of talents and spells are spread across the Earthdawn books, and leafing through them at the table gets tedious. So the first idea was a "let me look that up" app.

Step by step, that lookup app turned into a tool for managing whole characters. There were alternatives: spreadsheet solutions (which require Excel), and small, very old Windows programs that probably no longer run on current machines. Back then I was a Mac-only user anyway. What did not exist was a web app that does what EDChar does today. Compared to the web apps I know for D&D, I think EDChar is far ahead.

## Not a developer, but not a beginner either

I learned Turbo Pascal at school and C++ at university, between 2000 and 2003. Since then I have played with various languages, but never with a project of this size.

EDChar started in Swift, which I loved: intuitive, and very well documented online. Flutter came in because I wanted something cross-platform. That turned out to be a lucky choice. Flutter made it easy to turn a smartphone app into a web app, and the web app is what EDChar is today.

## What vibe coding could do, and where it stopped

I started with ChatGPT, then ChatGPT Pro, then Claude Pro, all in a vibe-coding style: one chat, one problem. That worked really well for "here is a problem, take a look and show me how to solve it".

The limit came with complexity. As the app grew, single chats were no longer enough. They got slow and used too many tokens, and every new chat started from zero. I needed something that remembers, but works more independently than a single chat.

## From my head to a board

The step to several agents with a shared board was driven by sheer volume: features, bugs, improvements. Before the board, all of it lived in my head, and I had to remember everything myself. When that started to fail, I looked for an alternative to Jira. The project was not on GitHub at that time, so GitHub Issues was not an option. The result was a Markdown board in Git, which is still the backbone of the setup today (see the decision record on the board).

At that time, neither the frontend nor the backend was on GitHub. I compiled the app myself and uploaded it to the server with FileZilla. Looking back, that was a very amateur setup. Today every push runs through a CI/CD pipeline with automated tests, and changes reach the live server only through a GoLive.

The switch from chats to agents happened on 22 June 2026 (see [Facts and figures](facts.md#history-and-tools)).

## Why agentic, and why this way

I wanted to make my own experiences and see how far I could get. And I wanted to develop agentically from the start, not as an add-on to classic coding.

As someone who is not a developer by trade, I enjoy this way of working a lot. I can understand that some developers miss the actual coding. For me, the interesting part is a different one: deciding what gets built, setting the rules, and seeing a team of agents turn that into a working product.
