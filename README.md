<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d0d0d,50:1a1a1a,100:0d0d0d&height=220&section=header&text=XENKAII&fontSize=58&fontColor=e8e6e1&animation=fadeIn&fontAlignY=42&desc=systems%20engineer%20%2F%2F%20full-stack%20%2F%2F%20game%20architecture&descAlignY=62&descSize=15&descColor=8a8a8a" />

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&size=14&duration=3200&pause=1000&color=B0AEA8&center=true&vCenter=true&width=600&height=30&lines=building+Astral+%40+xen-labs;distributed+systems+%2F%2F+real-time+state;Kolkata%2C+India)](https://github.com/xen-labs)

<img src="assets/divider-ink.svg" width="480" alt="" />

</div>

<br/>

<table align="center">
<tr>
<td width="58%" valign="top">

```yaml
xenkaii:
  role:       Founder & Systems Architect, xen-labs
  building:   Astral — real-time multiplayer game platform
  stack:      TypeScript end-to-end, Node.js, MongoDB
  focus:
    - distributed state across chat-native + web clients
    - event-driven architecture, no polling, no cron hacks
    - game economy design: balance, sinks, progression curves
  believes:   "the interface is disposable, the state machine isn't"
```

</td>
<td width="42%" valign="top" align="center">


<img src="https://i.ibb.co/Hpn0HrDQ/1002996722.jpg" width="300" style="border-radius:2px; filter:grayscale(15%);" />

<sub><i>ref. panel — replace above</i></sub>

</td>
</tr>
</table>

<br/>

<div align="center">

## what I'm building

</div>

Astral started as a WhatsApp-native RPG — dice-roll combat, card mechanics, a persistent economy running entirely through chat commands. That's still the engine. What changed is the ambition around it: **the bot is the game server, the webapp is everything the chat window can't be** — stat sheets, guild pages, leaderboards, trade history, character sheets you can actually screenshot and be proud of.

Two repos, one platform:

<table>
<tr>
<td width="50%" valign="top">

### `astral-api`
**the engine.** Command routing, session orchestration, game state, economy logic. Every player action — win a duel, forge an item, join a raid — is an event this service owns and the web layer only *reflects*.

`TypeScript` `Node.js` `Fastify` `MongoDB` `Baileys`

- Multi-session bot architecture — several game instances, one shared core
- Command pipeline: middleware → auth/permission gate → handler → state mutation → broadcast
- Turn-based combat resolver with deterministic RNG (replayable, auditable rolls)
- Economy layer: currency sinks, drop tables, trade validation — designed so the numbers can't be gamed

<div align="center">
<img src="https://media.tenor.com/seGvGe7Cp2cAAAAi/anime-bocchi.gif" width="180" style="border-radius:4px;" />
<br/><sub>combat/dice/engine-flavored motion here</sub>
</div>

</td>
<td width="50%" valign="top">

### `astral-web`
**the mirror.** Players link their account once, then get everything the chat interface was never going to render well — animated stat cards, party management, a proper inventory grid.

`TypeScript` `Next.js` `Tailwind` `WebSockets`

- Magic-link auth — bot never DMs first, web never asks for a password
- Live-updating character sheets via socket push, not refresh-and-pray
- Guild/party dashboards, trade ledger, seasonal leaderboard
- Every screen designed to be screenshotted — this is the "flex" surface

<div align="center">
<img src="https://media.tenor.com/xKr1nlG8rgsAAAAj/spookiline-hi.gif" width="180" style="border-radius:4px;" />
<br/><sub>UI/interface-flavored motion here</sub>
</div>

</td>
</tr>
</table>

<br/>

<div align="center">
<img src="https://cdn.dribbble.com/userupload/22427615/file/original-7ff312faccfd3e7e495872e91c2b189b.gif" width="380" style="border-radius:4px;" />
<br/><sub>system/data-flow motion here — this one can be the biggest of the four</sub>
</div>

<br/>

<div align="center">

## how it's wired

</div>

```
                     ┌─────────────────┐
                     │   astral-api     │
                     │  (game engine)   │
                     └────────┬─────────┘
                              │
              ┌───────────────┼───────────────┐
              │                                │
     ┌────────▼────────┐             ┌─────────▼─────────┐
     │  Baileys socket   │             │   WebSocket        │
     │  (WhatsApp I/O)   │             │   gateway           │
     └────────┬────────┘             └─────────┬─────────┘
              │                                │
     players issue commands            astral-web renders
     from inside WhatsApp              live state, no polling
```

Every game action is a single event that fans out to both surfaces. The chat client never has more authority than the web client — both are just views into state the API owns. That constraint is deliberate: it's what keeps the economy consistent when two hundred people are rolling dice at once.

<br/>

<div align="center">

## stack

<img src="https://skillicons.dev/icons?i=ts,nodejs,mongodb,nextjs,tailwind,docker,git,figma&theme=dark" />

<br/><br/>

![Fastify](https://img.shields.io/badge/Fastify-0d0d0d?style=for-the-badge&logo=fastify&logoColor=cfcac2)
![Baileys](https://img.shields.io/badge/Baileys-0d0d0d?style=for-the-badge&logo=whatsapp&logoColor=cfcac2)
![WebSockets](https://img.shields.io/badge/WebSockets-0d0d0d?style=for-the-badge&logo=socketdotio&logoColor=cfcac2)
![Mongoose](https://img.shields.io/badge/Mongoose-0d0d0d?style=for-the-badge&logo=mongoose&logoColor=cfcac2)

</div>

<br/>

<div align="center">

## stats

<img src="https://github-readme-stats.vercel.app/api?username=Xenkaii&show_icons=true&theme=github_dark&hide_border=true&bg_color=0d0d0d&title_color=cfcac2&icon_color=8a8a8a&text_color=8a8a8a&rank_icon=github" height="165"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Xenkaii&layout=compact&theme=github_dark&hide_border=true&bg_color=0d0d0d&title_color=cfcac2&text_color=8a8a8a" height="165"/>

<img src="https://streak-stats.demolab.com?user=Xenkaii&theme=github-dark&hide_border=true&background=0d0d0d&ring=8a8a8a&fire=cfcac2&currStreakLabel=cfcac2" />

</div>

<br/>

<div align="center">
<img src="https://i.ibb.co/TMwzPKmd/chinese-calligraphy.gif" width="220" style="border-radius:4px;" />
<br/><sub>closing motion beat — something quiet, ink-drop or slow fade works</sub>
</div>

<br/>

<div align="center">

## connect

[![WhatsApp](https://img.shields.io/badge/message-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/916296247464?text=Yoo%20Xenkai)
[![Spotify](https://img.shields.io/badge/spotify-1DB954?style=for-the-badge&logo=spotify&logoColor=white)](https://open.spotify.com/user/31yg3xp63jqgmkph2cmphenarqci)

<sub>Kolkata ⟡ xen-labs ⟡ Astral</sub>

<img src="https://komarev.com/ghpvc/?username=Xenkaii&color=8a8a8a&style=flat-square&label=visitors" />

</div>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d0d0d,50:1a1a1a,100:0d0d0d&height=100&section=footer" />
