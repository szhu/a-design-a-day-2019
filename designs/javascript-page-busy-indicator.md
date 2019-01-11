# JavaScript Page Busy Indicator

## Background

Most operating systems have a way to show that an entire app is frozen:

- On Windows, the app grays out and the titlebar says "Not Responding".
- On macOS, the "spinning wait cursor" beach ball of death appears.

While users don't particularly enjoy encountering these UI elements, they probably appreciate knowing that their system is stuck. The UI lets the user know that the blame is on the app, not the system.

Just like apps, web pages can get stuck too -- it's actually a more common occurrence because JS is single-threaded. However, web pages don't have an equivalent "page is not responding"  indicator.

## Idea

A busy indicator for webpages that is easily implementable. Possible ideas:

- Changing the CSS cursor to be `wait` before each synchronous function starts, and changing it back after it ends. (Similar behavior to the wait cursor behavior on macOS.)
- Applying a filter or opacity animation so that the page fades out after a few seconds. According to this StackOverflow post, CSS animations are not blocked while JS code is running: https://stackoverflow.com/q/15368087/782045. (Similar behavior to the fade out behavior on Windows.)
