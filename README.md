# Teaching demos

Small, self-contained browser demos for teaching machine learning evaluation.
Each demo is a single HTML file with no dependencies, no build step, and no
data leaving the browser.

**Site:** https://gorthiittp.github.io/teaching-demos/

## Demos

### Where the threshold goes — ROC and precision–recall

**Live:** https://gorthiittp.github.io/teaching-demos/roc/
**Source:** [`roc/index.html`](roc/index.html)

An interactive explorer for binary classification metrics. Students drag a
decision threshold across two simulated score distributions and watch the
confusion matrix, the ROC curve and the precision–recall curve respond.

Controls:

- **Threshold** — the cut that turns scores into predictions
- **Model quality** — separation between the classes on the latent scale (d′)
- **Positives in the data** — class prevalence, π
- **Score transform** — monotone reshapings of the scores; ranking is untouched
- **Sweep** — animates the threshold from 1 to 0, tracing both curves
- **Draw a new sample** — resamples at the same settings, showing how unstable
  the metrics are when positives are scarce
- **Copy link to this setup** — the full state lives in the URL hash, so a
  configuration can be set as an assignment or sent back by a student

Points the demo is built to make:

1. A point on either curve *is* a threshold; dragging the slider slides the
   marker along a fixed curve rather than reshaping it.
2. ROC-AUC measures ranking only, and does not move with class prevalence.
3. PR-AUC has a no-skill floor of π, not 0.5, so it is meaningless without the
   prevalence reported beside it.
4. Under heavy imbalance the two curves disagree, and both are correct — they
   answer different questions.
5. Any order-preserving transform of the scores leaves ROC-AUC and average
   precision bit-for-bit identical while Brier score and ECE degrade. Ranking
   metrics cannot see calibration.

Suggested exercises are at the bottom of the page.

### Implementation notes

Scores are the exact posterior probability from a Gaussian latent model,
`σ(d·z − d²/2 + logit π)`, so the untransformed scores are perfectly calibrated
by construction and the calibration numbers reflect the chosen transform rather
than an artefact of the simulation. Average precision is accumulated per
distinct score rather than per positive, which keeps it correct when scores tie
— the degenerate `d = 0` case returns AP = π exactly.

## License

MIT — reuse and adapt freely for teaching. Attribution appreciated.
