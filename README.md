# BrightAges MetaAgent

A small Java desktop wrapper around the `claude` executable.

It does two things a terminal doesn't. Then it does a third thing, which is the actual
reason it exists.

---

## 1. Tabs, one per project

One tab per project folder. Open as many as you want and leave them all running.

Each tab is its own session, which means each tab can be its own **account**, its own
**permission posture**, its own working directory. The client project that gets
read-only, no-network treatment sits next to your own repo where everything is
allowed, and you switch between them by clicking instead of by remembering which
terminal window was which.

## 2. Panes that look under the hood

The agent is not actually a chat. It's a stream of structured events and a pile of
spawned shells, with a conversation printed on top for your benefit. MetaAgent shows
you the layer underneath:

- **The JSONL stream.** Every line the agent emits, listed as it arrives. Click any
  line to read the full JSON for that event — the whole tool call, the whole result,
  nothing summarized and nothing hidden.
- **The shells.** Every shell the agent is running, listed. Click one to read its
  standard output directly.

Not telemetry, not a debugger. Just the removal of the curtain. After a week of
watching the real event stream you stop guessing what the agent is doing and start
knowing, and your instructions get noticeably better as a result.

## 3. The point

Open a Claude terminal. Ask it to go get this repo and open the MetaAgent on its own
project folder.

Once it's up: **close your Claude TUI. Forever.**

From that moment you are working in your own IDE, which happens to be a program you
own the source to. When it's missing something, you don't file an issue and wait —
you ask for the feature, and it's there. The source lives on your machine. It's built
to be edited and relaunched constantly; relaunching is the dev loop, and the thing you
are editing is the thing you are editing it in.

MetaAgent then becomes one tab among your projects — including, in one of those tabs,
MetaAgent itself.

---

## Why it's deliberately this small

Because it's a seed, not a product.

Everything here is the minimum that earns its place: launch the CLI, tab the sessions,
expose the stream, expose the shells. No plugin architecture, no settings framework,
no abstraction waiting for a second implementation that will never arrive. All of that
is overhead for shipping to strangers, and this isn't shipped to strangers — it's
handed to you so you can take it somewhere specific.

Your copy should not look like this one a month from now. If it does, something went
wrong.

## No pull requests

This repo doesn't take them. That's economics, not hostility.

The communal megaproject — NetBeans, Eclipse, the decade-long shared IDE with a
foundation behind it — made sense when writing code was expensive. Pooling effort was
the only way anybody got a good tool. The roadmap, the RFC process, the maintainer
bandwidth, the governance: all of it is the coordination cost of expensive labor.

That cost collapsed. In the Bright Ages, every developer has their own IDE, as simple
or as elaborate as they personally want, grown by immediate request and immediate
implementation. There is no reason left to negotiate a single shared one.

So: fork it. Vendor it into a folder of your own monorepo. Delete the half you don't
want. There is no reason to think of your copy as part of this one, and nothing is
owed upstream. Upstream is a seed you already used.

## What replaces upstream

The one genuinely useful thing a maintainer did was survey what everybody built, judge
which parts were good, and merge them. That work is now doable on demand, by an agent,
for one person.

A unified MetaAgent — if anyone ever wants one — doesn't get released. It gets
**assembled at request time.** You ask for a feature, and an agent reads the population
of forks that exist, then hands you a menu: here are four people who already built
this, here's what each approach costs you, pick one and I'll graft it in. Or, if none
of them is any good, it skips the menu and just writes the feature on the spot.

Distribution stops being *merge-and-release* and becomes *survey-and-synthesize*. No
roadmap, no feature freeze, no waiting on a maintainer's attention — and the catalog
of available features is simply every fork that exists. The fork graph **is** the
package registry.

That's why a tiny Java wrapper is part of the Bright Ages and not just a utility. It's
the smallest honest demonstration that the old coordination machinery was scaffolding,
and the scaffolding can come down.

---

## Build and run

> **TODO — fill in before publishing.** I don't want to guess at your toolchain and
> have the first command in the README be wrong. Replace this block with the real
> steps: required JDK version, whether it's Maven / Gradle / plain `javac`, the run
> command, and anything the `claude` executable needs to be on `PATH`.

```bash
# e.g.
git clone https://github.com/brightages/MetaAgent
cd MetaAgent
./gradlew run          # <- or: mvn package && java -jar target/MetaAgent.jar
```

**Requires:** a working `claude` CLI on your `PATH` ([Claude Code](https://claude.com/claude-code)),
and JDK _TODO_ or newer.

## Asking Claude to set it up for you

The intended first run, verbatim, from any Claude Code terminal:

```
Clone https://github.com/brightages/MetaAgent, build it, then launch it
with its own folder open as the first project tab.
```

Then close the terminal and don't open it again.

## License

_TODO_ — pick one. Something permissive is the consistent choice given everything
above; MIT or Apache-2.0 both do the job.
