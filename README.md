<img src="icon/icon.svg" width="96" alt="within app icon">

# About _within_

I built myself a calm LinkedIn reader: only the people I actually know, a chronological feed of what they post, and a separate tab for what they found worth engaging with. What I share here is not the app but the recipe for it, as an experiment. How someone uses LinkedIn is quite personal, and I want to keep my app simple. A prompt seems the better starting point: a coding agent builds the app from it, and you can shape it into the reader you want.

## How to use it

Open [Claude Code](https://claude.com/claude-code) (or a similar coding agent)
in an empty folder. Copy all of [`PROMPT.md`](PROMPT.md) (the "Copy raw file"
button on GitHub does this) and paste it in as your first message. You do not
need to clone this repository: the prompt tells the agent where to download the
screenshots and the icon.

The agent will ask you to sign in to LinkedIn in a window it opens. LinkedIn
may ask you to confirm that sign-in with a code, as it does for any new device.
It takes a while (about an hour in my test): let it work, and answer when it
asks you something.

## What you get

The pictures below show the original, filled with made-up posts by historical
figures. Your build will look different in the details.

The prompt asks for a desktop app for your operating system. It keeps the
LinkedIn part apart from the rest, so that a phone app needs only a thin shell
of its own (mine runs on the Mac and on Android). Android lets you install your
own app directly. On iOS you need Xcode, and without a paid Apple developer
account the app stops working after seven days.

|                                                 |                                              |
| ----------------------------------------------- | -------------------------------------------- |
| ![Following](screens/1-following.png)           | ![Popular with peers](screens/3-popular.png) |
| ![A post with its comments](screens/4-post.png) | ![My posts](screens/5-my-posts.png)          |

More in [`screens/`](screens). The prompt itself is [`PROMPT.md`](PROMPT.md).

## Before you start

LinkedIn has no public API for any of this. The app reads what you can see in
your own feed, with your own session, and LinkedIn's terms do not allow
automated access. If you build and use it, you do so at your own risk.

Portraits and pictures in the screenshots are public domain or CC0, from
Wikimedia Commons.
