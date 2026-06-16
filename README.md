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
npx skills add https://github.com/nashserv/ceo-skills --path skills/commercial-director/lead-qualification
npx skills add https://github.com/nashserv/ceo-skills --path skills/commercial-director/proposal-kp
npx skills add https://github.com/nashserv/ceo-skills --path skills/commercial-director/objections-logistics
npx skills add https://github.com/nashserv/ceo-skills --path skills/commercial-director/followup-logistics
npx skills add https://github.com/nashserv/ceo-skills --path skills/commercial-director/lessons-learned
```

## Skill company — `skills/skill-company`
General company-wide skills grouped here:

- `skills/skill-company/frontend-design` — from [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/frontend-design) (includes LICENSE.txt)
- `skills/skill-company/redesign-skill` — `redesign-existing-projects`, from [leonxlnx/taste-skill](https://github.com/leonxlnx/taste-skill) — audit & redesign existing sites to premium quality

Install:
```
npx skills add https://github.com/nashserv/ceo-skills --path skills/skill-company/frontend-design
npx skills add https://github.com/nashserv/ceo-skills --path skills/skill-company/redesign-skill
```
