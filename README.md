# philphapers-digest
# philpapers-digest

A Claude Code plugin that runs the PhilPapers Monthly Digest — scraping PhilPapers.org, generating AI summaries via the Claude API, and writing a static HTML digest.

## Installation

```bash
claude plugin install /path/to/philpapers-plugin
```

Or, if you're installing from the directory itself:

```bash
claude plugin install .
```

## Prerequisites

The plugin drives the Python script in the `philpapers/` directory. Before using it:

1. Install Python dependencies:

   ```bash
   pip3 install requests beautifulsoup4 anthropic
   ```

2. Set your Anthropic API key in `~/.zshrc` (or `~/.bashrc`):

   ```bash
   export ANTHROPIC_API_KEY="sk-ant-..."
   ```

   Then reload: `source ~/.zshrc`

## Usage

Once installed, invoke the skill from any Claude Code session:

```
/philpapers-digest:run
```

To run the digest and immediately open the result in your browser:

```
/philpapers-digest:run open
```

Claude will:
1. Verify `ANTHROPIC_API_KEY` is set (and tell you how to fix it if not)
2. Run `philpapers.py`, streaming output as it goes
3. Report success or errors and tell you where the HTML file was written

On the first run the script backfills January–March 2026, which takes 20–30 minutes due to rate limiting. Subsequent monthly runs are faster — only the new month is fetched.

The output file is written to:

```
philpapers/philpapers_digest.html
```

## Skills

| Skill | Description |
|-------|-------------|
| `run` | Scrape PhilPapers, summarize with Claude, and render the HTML digest |

## Related

- `philpapers/README.md` — setup, cron scheduling, and selector troubleshooting for the underlying Python tool
- `philpapers/philpapers.py` — the script this plugin drives

