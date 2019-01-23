# Grouped Windows

## Background

People often use multiple apps, tabs, and windows together to accomplish a task. For example, a user might be recording numbers from a website into a spreadsheet, while discussing the task with someone else:

![](https://user-images.githubusercontent.com/1570168/51577858-33753300-1e70-11e9-957c-d901d4d71822.png)

Users often arrange their windows such that they fill up nearly, but not quite, the entire screen, like this:

![image](https://user-images.githubusercontent.com/1570168/51577891-57d10f80-1e70-11e9-936b-e1b646109786.png)

The main reason that they leave the windows staggered is so that the background windows are easily accessible with one click.

Users on a large monitor might arrange their windows side-by-size, as follows:

![image](https://user-images.githubusercontent.com/1570168/51577974-9666ca00-1e70-11e9-8de4-1f5a333b819f.png)


These are adequate ways for the user to accomplish their task with the current windowing system, but here are some disadvantages:

- There is too much wasted screen space relative to its usefulness -- we only need a small click target for the user to be able to access a window.

- If there are many windows, searching through background windows can get tedious.

- The interaction is modal/stateful. The depth of each window, and how to access each one, depends on the order in which the user opened and/or last accessed the windows, rather than directly placed where the user expects.

Modern windowing systems have some functionality to help solve this:

- A taskbar/dock and the alt/cmd-tab shortcut make it easier to have random access to apps and windows.
  - Drawback: In most places, the interaction depends on the order of the windows were last accessed.
  - Drawback: For pinned items in the Dock and taskbar, the interaction does not depending on last access. However, the pinned item opens the entire app, rather than a particular window. Finding a specific window still will change depending on which other windows the app has open.

- There are window snapping tools. The major operating systems all allow the user to snap a window to the left or right half of the screen, and various third-party Mac apps allow window snapping in non-fullscreen mode.
  - Drawback: Snapping windows is a larger commitment than most users are willing to make. In the split-screen screenshot above, notice that the user left a sliver in between the browser and the spreadsheet so that the messaging app could still be accessed. Snapping windows would require the user to fully commit to full-screening only two apps, with no obvious way to access the third.
  - Drawback: New users who are looking to arrange their windows in a particular way have a hard time finding third-party apps or window snapping shortcuts; none of these are suggested when the user attempts to manually arrange windows.

## Idea

Here are two ideas that could address all three disdvantages above.

### App tabs

![image](https://user-images.githubusercontent.com/1570168/51578815-b8ae1700-1e73-11e9-8172-632867578c93.png)

Tabs are nothing new. Everyone uses them and their benefit is obvious -- a space above the window content is allocated for navigating to any other window, which means that you can maximize the tabbed window and everything else would still be accessible. The problem is that we currently can't do have windows with tabs from multiple apps, and we really, really should be able to.

### Joined windows

When two windows are brought next to each other, the window manager will give a hint that the user can click to join the windows like so:

![image](https://user-images.githubusercontent.com/1570168/51578786-9ddba280-1e73-11e9-8e0c-27d8a9fad75e.png)

Unlike the Windows and Mac window snapping solutions, this solution is easily discoverable and doesn't cause the joined window to maximize or fullscreen, meaning that the user is free to still make use of the space in the periphery however they like.
