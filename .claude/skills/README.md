# Skills

Claude Code loads every skill in this folder automatically when you open the repo. Each skill is a
folder with a `SKILL.md` (a name, a description of when to use it, and instructions).

| Skill | Use it for | Source |
|---|---|---|
| `shorts-automation-guide` | Planning and building your automation: the decision interview and build order | Written for this template |
| `viral-youtube-shorts` | Hooks, retention, endings, calls to action, Shorts strategy | [vyralcontent/content-skills](https://github.com/vyralcontent/content-skills), MIT, © Vyral. Includes a section about Vyral's paid product; it's optional |

## Recommended plugin

**Superpowers** (MIT, by Jesse Vincent) adds skills for the build itself: `brainstorming` (turn an idea
into a design), `writing-plans`, `test-driven-development`, `systematic-debugging`,
`verification-before-completion`. Install inside Claude Code:

```
/plugin install superpowers@claude-plugins-official
```

## Add your own

1. Create a folder here, for example `.claude/skills/tiktok-trends/`.
2. Add a `SKILL.md`:

   ```markdown
   ---
   name: tiktok-trends
   description: Use when choosing topics or sounds for TikTok videos in <your niche>.
   ---

   Instructions for Claude...
   ```

3. Add a row to the table above, so you and Claude know it exists.

Only add skills whose licence allows it, and keep their licence file in their folder.
