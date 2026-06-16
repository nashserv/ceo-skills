# ceo-skills

Markdown-only builds of two agent skills for use in **paperclip** (which rejects skills
containing executable scripts). The original `scripts/` folders were removed; all
instructional `.md` content is preserved verbatim.

## Skills
- `skills/brainstorming` — from [obra/superpowers](https://github.com/obra/superpowers) (scripts stripped)
- `skills/idea-refine` — from [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) (scripts stripped)

Credit and licenses belong to the original authors. Install:
```
npx skills add https://github.com/nashserv/ceo-skills --skill brainstorming
npx skills add https://github.com/nashserv/ceo-skills --skill idea-refine
```

## Commercial director (MM-Express) — `skills/commercial-director`
Markdown-only sales/logistics skills for the MM-Express commercial flow:

- `skills/commercial-director/lead-qualification` — qualify inbound leads (cargo, volume, direction, white/grey, one-off vs flow)
- `skills/commercial-director/proposal-kp` — build a commercial proposal (КП) after qualification + pricing
- `skills/commercial-director/objections-logistics` — handle objections (price, terms, reliability, customs, competitors)
- `skills/commercial-director/followup-logistics` — prepare a tactful, non-pushy follow-up
- `skills/commercial-director/lessons-learned` — capture/recall lessons before and after deals or incidents

Install (per skill):
```
npx skills add https://github.com/nashserv/ceo-skills --skill commercial-director/lead-qualification
npx skills add https://github.com/nashserv/ceo-skills --skill commercial-director/proposal-kp
npx skills add https://github.com/nashserv/ceo-skills --skill commercial-director/objections-logistics
npx skills add https://github.com/nashserv/ceo-skills --skill commercial-director/followup-logistics
npx skills add https://github.com/nashserv/ceo-skills --skill commercial-director/lessons-learned
```
