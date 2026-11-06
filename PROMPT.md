# Build me a calm LinkedIn reader

I want a small desktop app that shows me what the people I actually know are
doing on LinkedIn, and nothing else. Build it, run it, and keep improving it
until it does everything below. How you get there is up to you.

## Why

I use LinkedIn to keep an eye on my professional network, not for news or
inspiration. LinkedIn's own feed makes that hard: even sorted by "most recent",
most of it is ads, suggestions and posts by strangers that someone I know
happened to like. I want to open the app, see in one glance what happened since
I last looked, and close it again. It must never invite endless scrolling.

The model is Bluesky: a chronological feed of the people I follow, plus a
separate feed of what those people found worth engaging with.

## What it shows

**Only my 1st-degree connections.** Not people I merely follow, not companies,
not "suggested for you". When the app is unsure whether someone is a
connection, it leaves them out.

Three tabs:

1. **Following**: posts my connections wrote themselves, newest first. No ads,
   no suggestions, no "X likes this". When a connection reposts something, with
   or without a comment, that counts as activity and belongs in the second tab.
2. **Popular with peers**: posts my connections reacted to, commented on or
   reposted, ranked so that the posts several of them engaged with come first,
   recent posts beat old ones, and a viral post cannot drown out one that three
   of my connections cared about. Above each post: who of my connections
   engaged. Below it: what they commented, if they did.
3. **My posts**: my own recent posts with a picture, views, comments and the
   faces of who engaged. New comments stand out and give the tab an unread
   badge. A post opens to its numbers, the reactions by type, and its comments
   as a conversation. A second page, "When your contacts are active", shows by
   weekday and by hour when my connections like, comment and repost (anyone's
   posts), as a hint for when to post.

A post in either feed opens on its own page, like on Bluesky: the whole post,
all comments below it with replies threaded, and a bar at the bottom to write
my own comment.

Posts look the way they look on LinkedIn, just calmer: text with "show more",
images (several in a grid, opening full-size), videos, link previews, document
carousels that can be paged through, and career milestones (new position,
anniversary).

## What I can do

- **React and comment from the feed.** A click on the heart opens a list of
  LinkedIn's six reactions by name. Nothing is sent until I pick one, so I can
  never like something by accident. The list shows the reaction I already gave,
  and picking it again takes it back.
- **Mute** words, phrases and #tags, and mute people per tab: hide someone's
  posts from Following, or ignore their likes and comments in Popular, without
  removing the connection. People I blocked on LinkedIn never show up, not even
  inside someone else's repost. Text I select in a post can pre-fill the mute
  dialog.
- **Get notified** (desktop notifications) of new comments on my posts, and of
  messages from connections. Messages from strangers and recruiters stay silent.

## How it behaves

- It refreshes on its own every couple of minutes. There is no refresh button,
  because a refresh button suggests the feed needs one. The keyboard works:
  `1`/`2`/`3` switch tabs, `R` refreshes right away, `Escape` goes back.
- It remembers what it has seen. LinkedIn only ever hands out part of what
  happened, so the app keeps what it learns locally (for about two weeks) and
  the tabs fill up the longer it runs. An empty tab says so honestly.
- It is useful from the first refresh. Right after I sign in, every tab and
  page shows what LinkedIn has to offer, not only what happens from then on.
  Following catches most of what my connections post, not just the few posts
  that one view of LinkedIn's feed happens to carry.
- It stays quiet: no counters that do not matter, no animations that pull
  attention, no infinite scroll.
- It looks like the reference screenshots: one narrow column, light, LinkedIn
  blue as the only accent, system font. A dark mode that follows the system is
  welcome. Use the app icon from the repository below (`icon/icon.svg`, and
  `icon/icon.png` at 1024 px).

## Hard rules

- **I sign in on linkedin.com itself**, in a window the app opens. My password
  never passes through your code. The app only keeps the resulting session,
  locally, and nothing leaves my machine except requests to LinkedIn.
- **No scraping.** The app reads only what I could see in my own feed, my own
  posts, my connections list and my inbox. It does not crawl other people's
  profiles or activity pages, and it keeps its request volume close to what a
  person browsing LinkedIn would cause.
- **It only writes to LinkedIn when I click.** While you build and test, never
  react, comment, post, message or connect on my behalf, not even once to "see
  if it works". If you need to test a write, stop and ask me to do it.
- Every name, number and post in your own tests and screenshots stays on my
  machine. When you look at the app, capture its own windows only, never my
  whole screen.

## How to work

There is no official API for any of this. Find out how to get the data from my
own logged-in session; what LinkedIn's own web app does is fair to look at.

It has to be an app of its own, with its own window: not a browser tab, not a
browser extension. Pick whatever stack you like for my operating system (for
example Electron). Keep the LinkedIn session apart from the user interface:
the interface itself never gets to see the session cookies. Only signing in
and talking to LinkedIn may depend on the platform. Everything else (what is
stored, how the tabs are put together, ranking, muting, what counts as new)
belongs to the shared part, so that an app on my phone would only need a thin
shell of its own.

Work in loops: build something small that runs, look at it, compare it with the
goals above and the reference screenshots, and improve the part that is
furthest off. Check your work in the running app, not only in the code. A goal
is reached when you have seen it work with my real data. If it rests on an
assumption about LinkedIn (for example, that LinkedIn already filters something
out), check the assumption, or ask me to help you check it. To find out whether
a tab misses things, ask me which connections posted recently. Keep a
short `PROGRESS.md` with what works, what does not yet, and what you learned
about the data, so you can pick up again after a break.

When you need me (to sign in, to confirm a write, or because something is
unclear), ask. Otherwise keep going until the app does everything above. Then
tell me how to start it.

## Reference screenshots and icon

The screenshots and the app icon are in https://github.com/fgnass/within-prompt.
Before you start, download them into a `reference/` folder of the project, and
look at each screenshot yourself. Use plain downloads (for example `curl`), so
that nothing needs to be installed first. The raw files are at
`https://raw.githubusercontent.com/fgnass/within-prompt/main/<path>`, where
`<path>` is `icon/icon.svg`, `icon/icon.png` or `screens/<file>` below.

The screenshots (made with made-up data) show what the result should look and
feel like:

1. `1-following.png`: the Following tab
2. `2-react.png`: the reaction list, opened from the heart
3. `3-popular.png`: Popular with peers, with the connections who engaged and
   their comment
4. `4-post.png`: a post on its own page, comments threaded, comment bar at the
   bottom
5. `5-my-posts.png`: My posts, with views, comments, faces and new comments
6. `6-my-post-detail.png`: one of my posts in detail
7. `7-timing.png`: When your contacts are active
8. `8-muted.png`: the mute dialog

They are a target for the look, not a pixel spec.
