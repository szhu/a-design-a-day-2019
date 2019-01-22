# JSON Command-Line Programs

## Background

A lot of command-line output isn't suitable for parsing -- tab- and newline-separated output can give only so much structure. And the reality of the command-line programs in 2019 is that they're being parsed by a programming langauge like Python or JavaScript just as often as they're being piped to another program.

## Idea

Command-line programs should have an option to return their data as JSON (or in a JSON stream for streaming programs). Advantages:

- Makes command-line output easier to parse by non-command-line tools.

- Removes an articifial barrier to keeping command-line output simple.

- Creates a separation of presentation and content.

- Blurs the line between command-line tool and web API, lowering the cost to transitioning services to being distributed.
