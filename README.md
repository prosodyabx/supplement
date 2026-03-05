# Prosodic ABX — Supplementary Material

Interactive supplementary material for:

> *Prosodic ABX: A Language-Agnostic Method for Measuring Prosodic Contrast in Speech Representations*
> Submitted to Interspeech 2026

Hosted at: <https://prosodyabx.github.io/supplement/>

## Contents

| Path | Description |
|---|---|
| `index.html` | Single-page interactive visualisation (Apache ECharts) |
| `data/data.js` | All result data bundled as `window.WEBPAGE_DATA` for `file://` compatibility |
| `data/models.json` | Model metadata (19 models: 17 S3Ms + MFCC/FBank baselines) |
| `data/results_natural.json` | Layer-wise ABX error rates on natural speech |
| `data/results_synth.json` | Layer-wise ABX error rates on synthesised speech (TTS proxy) |
| `data/results_incontext.json` | Out-of-context vs. in-context results (Japanese pitch accent) |

## Updating the data

From the root of the main research repo, run the export script:

```bash
uv run scripts/export_webpage_data.py
```

This reads result CSVs from `results/` and rewrites `data/data.js` and the four JSON files in `paper/supplementary/data/`.

## Pushing to this repository

This repository is kept anonymous. All commits must use the neutral author identity below.

**The token is stored at `~/.prosody-abx-datasets-token` and is already embedded in the remote URL**, so no additional authentication setup is needed.

```bash
cd paper/supplementary

git add .

GIT_AUTHOR_NAME="Prosodic ABX Authors" \
GIT_AUTHOR_EMAIL="prosodyabx@users.noreply.github.com" \
GIT_COMMITTER_NAME="Prosodic ABX Authors" \
GIT_COMMITTER_EMAIL="prosodyabx@users.noreply.github.com" \
git commit -m "your message"

git push origin master
```

GitHub Pages redeploys automatically within a minute or two of each push.

### First-time setup on a new machine

If you need to re-clone (e.g. after `paper/supplementary/.git` is deleted):

```bash
cd paper/supplementary
git init
git remote add origin https://prosodyabx:$(cat ~/.prosody-abx-datasets-token)@github.com/prosodyabx/supplement.git
git push -u origin master
```
