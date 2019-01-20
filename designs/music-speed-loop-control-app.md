# Music Speed/Loop Control App

## Background

Dancers often practice their choreography with music accompaniment, often slowly and/or in sections. Some music-playback apps have features that help with these tasks, such as a playback speed control, time markers, and A/B looping.

In particular, the following 3 apps support all of the above functionality:

- Music Speed Changer (Android)
- Tempo SlowMo (iOS)
- VLC (Linux/Mac/Windows)

However, they all have some drawbacks:

- Their interfaces could be more intuitive.
- They all have different interfaces, so someone using one of the apps can't help out the person using another app.
- The Android and iOS apps aren't open-sourced and have changed little over the years, suggesting that rebuilding such an app from scratch might be the only way to add extra features on top of it.

## Idea

Yet another music-playback app that with speed, marker, and loop controls, with the following:

- It should be open-source and built on web technologies, and should be available as a web app.

- It should have a UI that is generally the same on all platforms yet responsive such that the app is easy to manipulate on mobile.

- Often, dancers on a team practice using the same settings (or at least the same base settings) -- they are listening to the same song and need the same time markers. There should be a way for someone to upload a track, set markers, and generate a link that they can send out to the team. Dancers then have one-click access to their set music and this app.

## Notes

- After I wrote out this description, I found a project -- https://agrahn.gitlab.io/ABLoopPlayer/ -- that already has the basic functionality described above (but not the more advanced features nor a mobile-friendly UI). It's a great proof of concept that people want these and that it's possible to build one!
