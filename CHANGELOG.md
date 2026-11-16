# Changelog

What changed in each public release of Arbiter, newest first. Every release's downloads, their SHA256
checksums and the signature over them are on its page under
[Releases](https://github.com/TheAuditorTool/ArbiterMCP/releases).

## [0.1.4](https://github.com/TheAuditorTool/ArbiterMCP/releases/tag/v0.1.4), November 16, 2026

An update to the 0.1.3 pre-release: the Seats page covers Codex as well as Claude Code, a Codex terminal that
reaches its usage limit continues by itself when the limit resets, the Overview tells you what each terminal
did in the last half hour, the Seats page has a 7-day chart you can read, the chat's brain reads whole
documents and follows the conversation, and a new installation starts in a stronger security mode.

### Highlights
- **Codex joins the Seats page.** The Codex account you are logged into gets the same card as a Claude seat:
  the 5-hour and weekly meters with their resets, the plan, a credit balance where the plan has one, and the
  limit resets the provider has granted. Store several Codex logins and switch between them like Claude seats,
  by hand or with Auto-rotate.
- **Codex terminals carry on by themselves.** When a Codex terminal reaches its usage limit, your phone learns
  when the limit resets, and at that moment Arbiter types the continue message for you.
- **The Overview says what each terminal did.** One sentence per Claude terminal from your local model: what
  it worked on in the last half hour, and why. Compact mode gives one line per terminal, the ones waiting on
  you first.
- **Your week at a glance.** A 7-day chart per account on the Seats page, readable with the mouse or the
  arrow keys, and a third forecast at this week's average pace.
- **A chat that keeps up.** The brain reads whole documents and follows the conversation, so "yes, do it" and
  "and the second one?" read as follow-ups.
- **Safer from the first start.** A new installation starts in the `balanced` security mode.

### Upgrade notes
- Nothing needs doing. An existing installation keeps the security mode it runs in; only a new installation
  starts in `balanced` (see Changed).
- The command line of a release build carries what the app, the installers, the service and agents run, plus
  support: `arbiter daemon`, `service`, `setup-llm`, `setup-mcp`, `mcp`, `doctor` and `error-lookup`.
  Everything else is done in the app or from the phone, activating and deactivating the license included.
- Tickets have a new type, `security`. A build before 0.1.4 cannot read a ticket of that type, so before going
  back to 0.1.3, give such tickets another type. The app and the engine must be of the same version to show it.

### New
- **Codex on the Seats page.** Tick "Codex account" on the Seats page and the account your Codex client is
  logged into gets a card like a Claude seat: the 5-hour and weekly meters with their resets, the plan, a credit
  balance where the plan has one, and how many limit resets the provider has granted. Arbiter asks the installed
  Codex client itself; it imports nothing and makes no request of its own to the provider. The account is also
  in the phone's `/usage`, the morning brief and the brain's status answer, and an account that is nearly used
  up is a "needs you" item.
- **Several Codex logins.** "Import current Codex login" stores the login under a label, and each stored login
  has Activate, Reserved and Remove, like a Claude seat. A Codex that is already running keeps the account it
  started with; one started or resumed after the switch uses the new login. "Close and resume" on a terminal
  waiting on a limit moves it onto the new login, once you confirm. With Auto-rotate on, Arbiter switches the
  login by itself when the live account is spent and a terminal is waiting on it.
- **A Codex terminal continues after its usage limit resets.** Arbiter reads the limit message in a Codex
  terminal it launched, tells your phone when the limit resets, and at that time types a continue message into
  the terminal. On by default ("Continue Codex after limit reset", on the Sessions page and on the Seats page);
  each waiting terminal has Continue now and Cancel. When the account can be read through the Codex client, an
  early reset continues the terminal at once. A workspace that is out of credits is held for you, with one phone
  notice, instead of being tried again and again. Claude Code continues after its own limit by itself, so this
  is for Codex only.
- **The Overview says what each terminal did.** Each Claude terminal carries one sentence from the local brain:
  what it worked on in the last half hour, and why. A "Compact" switch shows one line per terminal, those
  waiting on you first.
- **The Sessions page opens the same terminal window as the Overview:** what the terminal waits for, its latest
  turns and a reply box. The menu shows how many sessions are waiting for you beside both pages.
- **A 7-day chart on the Seats page**, one card per account: the week in blue and the 5-hour window in orange,
  with a legend and day labels. Move over it, or use the arrow keys, to see both meters at that moment, how far
  each moved, where the week reset, and, for the account in use, how many terminals and sub-agents were
  running. "As a table" lists each day's highest readings.
- **A third forecast on the Seats page**, at this week's average pace since its reset, beside the pace of the
  last day and of the last 72 hours.
- **Limit resets of a Claude account** are shown under the seat when the provider reports them to Arbiter.
  Today the provider tells only its own client, and the seat says so. Arbiter never spends a reset.
- **Tickets have a `security` type**, in the app, on the phone and for agents, with a template of its own.
- **On the phone**, `/ticket new Login fails` asks for the project and the type with buttons and keeps every
  word of the title. `/usage` names the provider of every seat.
- **Where the brain's model sits.** After the model loads, Arbiter checks whether it is on the graphics card;
  when a quarter or more of it ended up in system memory, Home lists it and `arbiter doctor` shows it
  (Windows).
- **A database check at start.** Each database's tables are compared with what this version expects; a
  difference is logged and `arbiter doctor --check-home` reports it. Nothing is refused because of it.
- **Home and the Brief lead somewhere.** The Terminals, Runs and Projects tiles open their pages, and each
  "Needs you" line in the Brief has a button to the page where you deal with it.

### Changed
- **A new installation starts in security mode `balanced`:** your provider keys and Claude seats are locked to
  the license, and the other databases use the license's key. Its first start needs no license server. The key
  that unlocks your provider keys is now kept sealed on this machine, so a license server outage at a start no
  longer locks them. The privacy notice says when the license server is contacted.
- **A picture handed to an agent keeps only what is needed to draw it:** everything else in a JPEG, PNG, GIF or
  WebP file is removed, not only location and camera details. A PNG or WebP stored on its side keeps which way
  up it is. Old Word, Excel and PowerPoint files are recognised by their content, and one with macros comes with
  a warning. Malformed pictures that standard decoders reject are refused.
- **The chat.** The brain reads whole documents, in parts when they are long, and follows the conversation, so
  "yes, do it" and "and the second one?" read as follow-ups. It can name only tools that exist, and a wrong
  argument is refused before you are asked to approve. A running turn shows "Working", its time and Stop, and
  the brain's thoughts are readable, marked "Brain, thinking". An answer cut off at its length limit says so.
- **The Brief and the status report** give two to four sentences of substance per project, and a brief over
  many projects no longer fails as a whole.
- **The Curator page** shows Curator's health in short: its status, what you can act on, and its capture queue.
  The detailed internal report is gone.
- **The License panel** shows when Arbiter next checks the license with the server (a week after the last
  check) and, separately, the date by which it must be confirmed. When a license ends and Arbiter moves your
  provider keys and Claude seats onto this machine's own key, the License panel and the phone say so.
- **The first-start question** of how much Arbiter should ask before it acts is kept across restarts, and
  nothing is preselected. In a group chat, only the member who asked can answer an approval.
- **The Seats and Activity pages** show what they showed last at once and refresh in place, and the Activity log
  refreshes every second.
- **Connect on the Projects page** says what it does: it gives Claude Code in that project Arbiter's tools,
  writes two files and backs both up first.
- **Keep timers warm** covers the Codex account too, through the real Codex client, under the same rules as a
  seat.

### Fixed
- An `OTEL_PROPAGATORS` value naming a propagator that Arbiter does not carry (for example `b3`) stopped every
  `arbiter` command at start, in 0.1.3 too. Arbiter now loads none in that case and says so in one line.
- A long message typed into a terminal could be left in its input box, typed and never sent.
- On a Windows computer whose clients run in WSL, Arbiter could pick a Windows install of Codex that cannot run
  inside WSL and keep it until the next restart, and the Codex card then had no numbers.
- A Codex seat's usage could show one model's own allowance instead of the account's.
- When the live Claude client sat idle, the seat history filled with "unknown". The last real reading now
  stands, with its age.
- A claude or codex that Arbiter ran through WSL could keep running inside WSL after Arbiter stopped it.
- On AMD graphics cards under Windows, most of the brain's model sat in system memory instead of on the card.
- Every engine restart left the Curator page on "degraded" for up to an hour.
- The brain sometimes said it could not file a ticket it had just filed.
- A Curator search was lost when you left the page.
- The Inbox was treated as a repository: the Brief called it unreachable and Connect failed on it.
- After a `/rename` inside Claude Code, Arbiter's messages about that terminal use the new name.
- On Windows, a Codex session whose program crashed read as open until Codex next started.
- Importing a Codex login from a client that keeps it in the system keyring now says how to switch it to a
  login file.
- A delegate that refuses to start fails its run with its reason.
- The Overview said "No terminal is running" when its first read failed; it now says nothing could be read yet.
- One leftover folder of document copies could stop every document handover to agents.
- In 0.1.3 the answer to the first-start question was lost at the next start, which began on manual again.

### Removed
- **The fleet**, which started several workers on the same task with nothing to compare or merge them, with the
  Overview's "Earlier fleets" list and the License panel's worker row.
- The chat's heartbeat and token count, which showed no real progress.

## [0.1.3](https://github.com/TheAuditorTool/ArbiterMCP/releases/tag/v0.1.3), November 12, 2026

An update to the 0.1.2 pre-release: the phone's commands now help instead of failing, `/tail` says when
things happened and what a session is waiting on, agents can read documents attached to a ticket, and a
license that ends no longer locks your stored credentials in the stronger security modes.

### Fixed
- In security mode balanced, extended or strict, a license that ran out, was revoked or refunded, or whose
  seat on this machine was deactivated, left `credentials.db` (your provider keys and Claude seats) locked for
  good. Now, while the engine runs, Arbiter moves `credentials.db` onto this machine's own key, switches the
  home to security mode compat and says so in the log, with how to switch back after renewing. This also
  happens when the license's end date passes while the license server cannot be reached; a renewed license
  is checked first and never taken for an ended one. 14 days before a license ends, the log warns that
  `credentials.db` needs it. If the engine starts after the license has ended, it says plainly that
  `credentials.db` is locked until the license covers this machine again, and that nothing in it was
  changed. The default mode, compat, was never affected. While a license has not ended, a network error or a
  server error never moves a key.
- `arbiter deactivate` no longer says that no database is stranded when it could not move one; it says why.
- On the phone, `/ticket attach ARB-041` sent as a message answered that there is no ticket "attach", and a
  photo sent with no caption was refused. Both work now (see New).
- An album sent from the phone no longer answers "Queued behind the turn that is running" for every photo
  after the first, and one sent while a turn runs is no longer cut to five photos.
- The agent count in `/agents` never went down: it counted every agent a session had ever started. It now
  says what they are doing, for example `agents: 2 running, 14 finished`.
- The usage forecast read days spent at the weekly limit as an idle week, so after a reset it put the pause
  days too late or said the week "does not run out". Averages now leave out the time a seat was locked out,
  and the forecast says how much it left out.
- The Windows installer showed a rights notice where the pre-release terms belong. It now shows the Arbiter
  pre-release terms, and the activation screen has a `Read the terms` button that shows the same text.
- The message of a build past its 365 days now says where to get the current version: arbitermcp.com or
  the GitHub releases page.

### New
- `/tail` starts every line with its time on your own clock: `23:18` for today, `Tue 23:18` for this week,
  `11 Nov 23:18` for older days. The header says when the session started and when it last did anything.
- `/tail` lists the background work a session is waiting on, newest first, and its last background result.
  A session that is idle but waiting on background work says so, in `/tail` and in `/agents`.
- `/tail arbiter agents` lists that session's agents, running ones first. `/tail arbiter agent 2` reads one.
  You can name an agent by its number in the list, the start of its id, or words from its description.
- Attach files from the phone in three ways. Send `/ticket attach ARB-041` as a message, then send photos or
  files: for ten minutes each one is kept on that ticket, and a caption is added as a note;
  `/ticket attach off` stops it. Or send a photo or file with no caption: Arbiter asks once which ticket
  should keep it, with buttons for your open tickets, a new Inbox ticket, or Ignore. Or write the ticket key
  as the caption.
- A mistyped command on the phone answers with the nearest commands as buttons, plus a button to ask the
  brain instead. A ticket, project or ticket type that does not exist answers with the nearest ones. Nothing
  runs until you tap.
- Ticket keys are read the way you type them: `arb-41`, `ARB 41` and `arb41` all mean ARB-041. A key that
  could mean two of your tickets is never guessed: Arbiter asks which one.
- `/ticket new` with parts missing walks you through it: tap the project, tap the type, then send the title
  as your next message. `/ticket done`, `drop`, `reopen`, `block` and `note` with no key show the tickets
  they can apply to.
- `/help` is one short page with topic buttons. `/help tickets`, `/help tail` and `/help all` go further,
  and every command comes with an example to copy.
- An agent can read a PDF, Word, Excel, PowerPoint, old Office or OpenDocument file attached to a ticket.
  Arbiter gives it a private copy to open with its own tools and removes the copy when the connection
  closes. Arbiter itself never opens the file. A file with macros, or in an old Office format, comes with a
  warning. Programs and archives are still never handed to an agent.

### Changed
- Everything an agent reads from a ticket attachment starts with a label: the ticket, the file's name, type
  and size, where and when it was added, and a reminder that what the file says is information, not
  instructions. Photos and screenshots are handed over without location, camera details or comments; the
  picture itself is not changed, and a damaged image is refused. A text file comes between two marked lines
  that nothing inside the file can imitate. Sibling apps: `docs/tickets_mcp_contract.md` describes the new
  answer of `arbiter_ticket_attachment`.
- Phone buttons carry only a one-time code that expires after ten minutes. A tap runs exactly as if you had
  typed the command, so approvals, 2FA codes and stop-all still apply. `/approve`, `/release`, `/auth` and
  `/stopall` are only ever suggested as text, and a mistyped command never shows your 2FA code back to you.
- Phone replies no longer show patterns such as `/release <2FA code>`: each one shows an example to copy,
  such as `/release 123456`.
- `/ticket done`, `drop` and `reopen` change nothing when more words follow the ticket key; they ask instead.
- A seat whose usage poll fails now says why in the log, once for each new reason.
- The app shows each attachment's type in plain words, such as Word document, image or PDF document.
- Arbiter's MCP server runs on the mcp 2.3.0 SDK (it was 1.30.0). The protocol version it offers is
  unchanged, and every refusal still reaches the agent with its reason.
- The license notice shipped with Arbiter names the pre-release terms as the agreement under which you use
  it. The pre-release terms themselves are unchanged.

## [0.1.2](https://github.com/TheAuditorTool/ArbiterMCP/releases/tag/v0.1.2), November 5, 2026

An update to the 0.1.1 pre-release: a first install gets its local model without a command line, and Claude
seats on plans with a weekly limit only (Ultra) are forecast and handled like the others, with a usage
forecast that checks itself against what really happened.

### Security
- Arbiter's own HTTPS connections now distrust the eMudhra intermediate certificates whose keys were disclosed
  on 2026-10-20 (CVE-2026-111943). Earlier versions, 0.1.0 and 0.1.1, trusted certificates issued with those
  keys, so someone on your network path holding them could have impersonated the services Arbiter connects to.
  No misuse has been reported. Updating to 0.1.2 is recommended.

### Fixed
- A first install could leave the local brain without its model and point you to a command line. The model
  is a separate download of about 5 to 7 GB (Gemma 4, Apache 2.0 license, from Hugging Face; no account is
  needed). The Windows setup now offers it at the end, once, when your graphics card can run it; say yes and
  it downloads when Arbiter starts, with the progress shown in the app. Until the model is in place, every page
  of the app says so and downloads it with one click, as do Config, Brain and a "Brain not downloaded" chip at
  the top. `arbiter setup-llm` still downloads it on a machine without the app.
- On a machine without Memory (Curator), the MCP page no longer lists it as down, and adding a project with a
  memory domain no longer reports a failure: the project keeps the domain name.
- The daemon's log no longer names a separate product's command on machines where that product was never
  installed.
- Keep timers warm no longer starts a session on a seat whose plan has no 5-hour window. Such a seat was
  started every 30 minutes for nothing.
- "Next free" on the Seats page and in the Telegram report now judges a seat by its most used account window
  against the rotation percentage. A seat whose week was past that percentage, or one with a weekly limit only,
  used to read as free while rotation refused it.

### Changed
- Claude seats on a plan with a weekly limit only (no 5-hour window, such as Ultra) are forecast in week
  points: when the week fills at your pace, who takes over and when everything pauses, instead of "no pace
  yet". The top bar, the Overview tile, the brief and the rotation reply name the week when it is the limit.
- The usage forecast checks itself. It replays its candidate paces (recent slopes, averages over hours and
  days, the average since the reset, and a model of how many terminals and agents are working against your
  usual load at that hour) over the last 7 days, scores how far each was off 1 to 72 hours later, and projects
  with the blend that did best, or keeps its previous rule where nothing beat it. The panel says how far off
  it was, for example "missed the week by about 8 points 24 hours ahead".
- Model weekly limits such as Fable's are forecast with their seat: when the model runs out on each seat and
  across all of them, and when it is back.
- Seats on different plans count the same work at their own size: measured once a seat has been in use,
  otherwise estimated from the plan (an Ultra week is 10 Pro weeks), and said so. Each seat shows how long it
  would last on its own.
- Tickets record their share of the week on every seat, are fitted in the unit of the seat in use, and say how
  long they take at their own terminals' pace.

## [0.1.1](https://github.com/TheAuditorTool/ArbiterMCP/releases/tag/v0.1.1), October 31, 2026

An update to the 0.1.0 pre-release: the local model now fits itself to your graphics card, so a card with
8 GB runs it, and its answers no longer drift after a long request.

### Changed
- The local model fits itself to your graphics card. At start Arbiter reads how much memory the card has and
  picks the model and the largest context window that still leave room for your desktop. A card with 10 GB or
  more runs Gemma 4 12B at the full 65,536-token window. An 8 GB card runs the same model at a smaller
  quantization (Q3_K_S, about 6.3 GB on the card), which matched or beat the full-size file on every job in
  Arbiter's own benchmark. Config, Brain and `arbiter doctor` show the card's memory and why the model and
  window were chosen, and `arbiter setup-llm` and the app's Get started download the model this card runs. A
  model or window you choose yourself is kept, with a warning when it looks too large for the card.
- On a card with less than 8 GB, the local model no longer tries to start and fails: Arbiter says how much
  memory the model needs and how much the card has, and everything else keeps working.

### Fixed
- The local model's answers no longer drift after a long request. With Gemma 4 the brain kept part of the
  previous request's working memory that its sliding-window layers had already overwritten, so a call that
  followed a long chat step could come back wrong: approvals, routing, titles and Curator's extraction on the
  shared brain. A call on such a model now starts from a fresh context, or from a point saved exactly where
  its prompt stops matching a recent one, so a chat step re-reads only what changed since the step before:
  about 5.9 s a step for Gemma 4 12B on a 16 GB card, with the same scores on Arbiter's own benchmark.
- The app, `arbiter mode status` and Config, Brain said the local model was loaded when it had failed to
  load, for example before the model was downloaded. They now say loaded only once the model is in memory.
- On Windows, closing Arbiter from another program now ends it while it is hidden in the tray. An installer,
  a script or `taskkill` used to leave it running there, with its program file locked; your own close still
  hides it.

## [0.1.0](https://github.com/TheAuditorTool/ArbiterMCP/releases/tag/v0.1.0), October 30, 2026

The first public pre-release of Arbiter, the command center above your AI tools: an early build for early
adopters, and the rough edges found here shape v1.

### Before you start
- Arbiter needs a license. During the pre-release it is free: ask for one at arbitermcp.com, and the email
  brings your key. Activate it in the app's first screen or with `arbiter activate`.
- Windows will warn that it protected your PC, because this build is not code-signed yet: choose More info,
  then Run anyway. Every download is listed with its SHA256 in a SHA256SUMS file signed with the Code Reality
  Labs release key, so you can check what you got.

### Added
- A desktop app (Windows, Linux) with pages for Home, Overview, Chat, Runs, Sessions, Tickets, Activity,
  Brief, MCP, Projects, Channels, Seats and Config. The Auditor and Curator pages appear when TheAuditor or
  Curator is installed beside it.
- One program, `arbiter`: the daemon (`arbiter daemon`), the MCP server for your coding agents
  (`arbiter mcp`), and the commands for projects, runs, tickets, settings, accounts, seats, schedules, the
  license, telemetry, 2FA and the service (`arbiter project`, `arbiter run`, `arbiter ticket` and the rest;
  `arbiter <command> --help` describes each one).
- A local daemon that dispatches, supervises and recovers work across coding clients, provider APIs and a
  local model. Its control surface is a named pipe on Windows and a Unix socket on Linux; no network port is
  opened unless you enable the HTTP control plane or Telegram's webhook mode.
- Tickets: a work list joined to what your terminals provably did, with phases, estimates from closed tickets,
  and MCP tools so your agents can file and update them.
- Cost-aware routing of each job to Claude Code, Codex, a provider API or the local model, with the decision
  and its reasons recorded.
- Terminals for Claude Code and Codex that survive their window and can be driven remotely: owned consoles on
  Windows (or tmux inside WSL, if you choose that host), tmux on Linux.
- Remote control from Telegram, with Signal and WhatsApp in beta: allowlisted users may read status. Once a
  channel is configured, two-factor approval is on by default: anything that runs code or sends a prompt needs
  a TOTP code from an enrolled authenticator, and is refused until one is enrolled.
- Seats: switch the logged-in Claude account without logging out, by hand or, when enabled, automatically
  before the active one runs dry, with a usage forecast.
- `arbiter service install` starts Arbiter at sign-in: a per-user entry on Windows, and on Linux a systemd user
  unit it writes and enables. `arbiter service start|stop|status` controls it.
- `arbiter doctor` checks this machine (including whether it can run the terminals it is configured for), and
  `arbiter doctor --bundle` collects versions, masked settings, recent logs and error references for a bug
  report; `arbiter error-lookup` shows the details behind an error reference.

### Security
- All state is kept in SQLCipher databases whose keys are bound to this machine and user. Security modes add
  a license-held key fragment; the credentials database is only openable online in those modes.
- Settings that decide who may drive the machine, what it runs or where secrets go need a 2FA code once an
  authenticator is enrolled. Wrong codes are rate-limited: the sixth within 15 minutes locks further attempts
  for 15 minutes, doubling with each further lockout up to a day.
- Secrets are never shown back by the app or the CLI, and `arbiter settings set` reads them from a hidden
  prompt or stdin.
- The HTTP control plane is off by default, refuses keys shorter than 16 characters and requires TLS to listen
  beyond this machine.

### Telemetry
- Telemetry shows a notice before anything is sent. The default level, lite, sends counts, durations, error
  types and an abstract routing record; it never sends prompts, code, file names, paths, project names or
  keys. `arbiter telemetry off` stops all of it, and `arbiter telemetry status` lists every field.
- Licensing is not telemetry: the license is checked in with the license server, and a seat you add talks to
  its provider with the login you gave it.

### Requirements and known limitations
- Windows 10 or 11 (x64), or Linux x64. On Linux Arbiter needs glibc 2.34 or newer, and the desktop app needs
  WebKitGTK 4.1. macOS is not supported yet.
- The local model runs on your graphics card through Vulkan, so it needs a graphics driver with Vulkan
  support. It is not bundled: `arbiter setup-llm` downloads it.
- Claude Code and Codex are installed separately; Codex 0.158 or newer is required.
- This is a pre-release: the databases are versioned and migrate forward, but interfaces may still change.
