---
name: run
description: Run the PhilPapers Monthly Digest. Scrapes PhilPapers.org, generates Claude API summaries, and regenerates the static HTML digest.
---

Run the PhilPapers Monthly Digest tool.

## Steps

**Step 1: Check ANTHROPIC_API_KEY**

```bash
echo $ANTHROPIC_API_KEY
```

If the output is empty, tell the user:
> ANTHROPIC_API_KEY is not set. Add it to your ~/.zshrc:
> `export ANTHROPIC_API_KEY="sk-ant-..."`
> Then run `source ~/.zshrc` and try again.

Stop here if the key is missing.

**Step 2: Run the script**

```bash
cd /Users/whet/Desktop/claude/philpapers && python3 philpapers.py
```

Stream the output to the user as it runs. This takes 20–30 minutes on first run (backfilling Jan–Mar 2026) due to rate limiting. Subsequent runs are faster — only the new month is scraped.

**Step 3: Report completion**

When the script finishes, tell the user:
- Whether it succeeded or if there were any errors in the output
- Where the HTML file was written (`philpapers/philpapers_digest.html`)
- How to open it: `open /Users/whet/Desktop/claude/philpapers/philpapers_digest.html`

If the user passes `open` as an argument (`$ARGUMENTS` contains "open"), also run:
```bash
open /Users/whet/Desktop/claude/philpapers/philpapers_digest.html
```
