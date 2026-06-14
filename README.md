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
