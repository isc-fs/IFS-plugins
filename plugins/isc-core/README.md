# ISC Core

Team-wide workflows for the ISC Formula Student Racing Team. **Every board member
installs this**, alongside their department plugin.

## What it does

| Skill | Use it for |
| --- | --- |
| `onboard-member` | Getting a new person into the systems and pointed at the right briefing |
| `log-decision` | Recording what was decided and why, while the reasoning still exists |
| `handover-pack` | Assembling what a departing member knows, and checking team readiness |

## Setup

Connect Notion, with access to the `IFS 09` teamspace. Nothing else.

## The problem this plugin exists for

Every board turns over in September. The people who spent a year learning why the
accumulator is packaged that way, which supplier actually delivers, and which sponsor
contact replies all graduate at once.

Formula Student teams lose more to this than to any engineering failure. The same
mistakes get repeated every three or four years, because the car is documented in GitHub
and the *reasoning* is documented nowhere.

The fix is not a better end-of-season document. Those are written by exhausted people
reconstructing nine months from memory, which is why they are thin and wrong. The fix is
**recording the reason on the day the decision is made**, so handover becomes a
byproduct of working normally rather than a project in June.

That is the whole design. `log-decision` costs two minutes; `handover-pack` is then
mostly assembly rather than archaeology.

## The data lives in Notion

In the `IFS 09` teamspace:

- **Team Directory**: who is here, what they own, handover state
- **Decision Log**: what was decided, why, and what was rejected
- **Handover**: how handover works and what good looks like

## The plugin set

| Plugin | Who installs it |
| --- | --- |
| `isc-core` | Everyone |
| `isc-pm` | Project Management |
| `isc-sponsorship` | Sponsorship |
| `isc-marketing` | Marketing |

Technical work runs on Claude Code against the `isc-fs` GitHub organisation with the
general `engineering` plugin. There is no ISC-specific technical plugin, by design: that
setup already works.

## Maintaining this plugin

Ask Claude to "customize the isc-core plugin".
