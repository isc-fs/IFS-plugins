<img width="470.235" height="179.4" alt="isc-full-primary" src="https://github.com/user-attachments/assets/31365569-11bf-427e-ae3e-8d81ca87d765" />

# IFS-plugins

Claude plugins for the ISC Formula Student Racing Team. Four plugins, fifteen skills, all of them working against the team's Notion workspace.

A plugin is a set of instructions describing how this team works, which Claude reads when it needs them. Install one and Claude already knows our department codes, our pages and our rules. Nobody has to explain them again, and next year's board inherits the same behaviour without inheriting anybody's old conversations.

---

## Install

The repository is public, so nobody needs a GitHub account. Two lines, once:

```
/plugin marketplace add isc-fs/IFS-plugins
/plugin install isc-core@isc-plugins
```

**Everybody installs `isc-core`.** On top of that, install the one for your job:

```
/plugin install isc-pm@isc-plugins
/plugin install isc-sponsorship@isc-plugins
/plugin install isc-marketing@isc-plugins
```

In the Claude desktop app, use the plugin browser rather than typing the commands.

Installing this way means you get fixes. When a plugin is updated here, your copy
is told there is a new version. The alternative below does not do that.

### Without the marketplace

The packaged files live in `dist/`. Download one and open it in the Claude desktop
app to install it. Use this only if the marketplace route fails, because a file
installed this way never learns that a newer version exists.

---

## What is in each plugin

| Plugin | Who | Skills |
| --- | --- | --- |
| `isc-core` | Everybody | `onboard-member`, `log-decision`, `handover-pack` |
| `isc-pm` | Board, department heads | `reschedule`, `task-triage`, `season-roadmap`, `board-sync` |
| `isc-sponsorship` | Sponsorship | `prospect-research`, `draft-outreach`, `build-proposal`, `pipeline-review`, `deliverables-check` |
| `isc-marketing` | Marketing, comms | `brand-system`, `content-formats`, `season-content-plan` |

You do not memorise any of this. Say what you want and the right skill gets used. "What am I late on?", "research this company as a sponsor", "draft a build update for Instagram".

### Before they work

Every plugin reads and writes the team's Notion workspace, so **connect Notion in Claude first**. Without it the skills will run and find nothing.

The full guide to the workspace and to Claude lives in the team OneDrive, `ISC FS/09`, in English and Spanish.

---

## Publishing a change

The `version` field is what tells people an update exists. Change a skill without bumping it and nobody gets the fix.

1. Edit the plugin under `plugins/<name>/`.
2. Bump `version` in **both** `plugins/<name>/.claude-plugin/plugin.json` and the matching entry in `.claude-plugin/marketplace.json`. They must agree.
3. Rebuild the shareable file: `cd plugins/<name> && zip -Xr ../../dist/<name>.plugin .`
4. Commit on a `feat/<n>` branch, PR into `dev`, merge to `main`.

The zip must include the hidden `.claude-plugin/` directory. A plugin file without its manifest fails validation on install, and `zip -x '.*'` silently excludes it. That is worth remembering because it has already happened once.

Skill descriptions cannot contain angle brackets. `<company>` in a description fails validation with a message that does not mention the brackets. Use plain words instead.

---

## Layout

```
.claude-plugin/marketplace.json   the catalogue Claude reads
plugins/<name>/                   the source of each plugin
  .claude-plugin/plugin.json      its manifest, including version
  skills/<skill>/SKILL.md         one file per skill
  references/                     shared context the skills read
dist/<name>.plugin                packaged file, for sharing without GitHub
```

---

## How we work with this repository

Same convention as the rest of `isc-fs`. `main` is production, `dev` is integration, and all work happens on a `feat/<n>` or `fix/<n>` branch cut from `dev` and merged back by pull request. Never commit directly to `main` or `dev`.

Pushing a `feat/*` or `fix/*` branch opens its tracking issue automatically. See [ROADMAP.md](ROADMAP.md) for the delivery plan.
