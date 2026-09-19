# Teaching demos

Small, self-contained browser demos for teaching machine learning evaluation.
Each demo is a single HTML file with no dependencies, no build step, and no
data leaving the browser.

## Demos

### Where the threshold goes — ROC and precision–recall

**Live:** https://YOUR-USERNAME.github.io/teaching-demos/roc-pr/
**Source:** [`roc-pr/index.html`](roc-pr/index.html)

An interactive explorer for binary classification metrics. Students drag a
decision threshold across two simulated score distributions and watch the
confusion matrix, ROC curve, and precision–recall curve respond in real time.

Controls:

- **Threshold** — the cut that turns scores into predictions
- **Model quality** — separation between the two score distributions (d′)
- **Positives in the data** — class prevalence, π
- **Sweep** — animates the threshold from 1 to 0, tracing both curves
- **Draw a new sample** — resamples at the same settings, showing how unstable
  the metrics are when positives are scarce

Points the demo is built to make:

1. A point on either curve *is* a threshold.
2. ROC-AUC measures ranking only, and is invariant to class prevalence.
3. PR-AUC has a no-skill floor of π, not 0.5, so it is meaningless without the
   prevalence reported beside it.
4. Under heavy imbalance the two curves disagree, and both are correct — they
   answer different questions.

Suggested exercises are included at the bottom of the page.

## Embedding

The demos are plain static pages and can be embedded in a course site or LMS
with an iframe:

```html
<iframe src="https://YOUR-USERNAME.github.io/teaching-demos/roc-pr/"
        style="width:100%; height:1400px; border:0;"
        title="ROC and precision-recall explorer"
        loading="lazy"></iframe>
```

## License

MIT — reuse and adapt freely for teaching. Attribution appreciated.
