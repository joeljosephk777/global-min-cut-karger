# global-min-cut-karger

Interactive browser visualization and probability analysis of Karger's randomized contraction algorithm for the global minimum cut (Kleinberg–Tardos §13.2).

**▶ Live demo:** https://globalmincut.netlify.app/karger.html

## Contents

- **`karger.html`** — a self-contained, dependency-free interactive visualization. Open it in any browser to step through edge contractions on an example graph, watch the success-probability analysis update alongside the animation, and run the algorithm many times to compare the empirical success rate against the theoretical bound.
- **`presentation-script.txt`** — a speaker script / run-of-show for presenting the algorithm.

## Usage

Try it online at the [live demo](https://globalmincut.netlify.app/karger.html), or open `karger.html` in any modern web browser — no installation, build step, or internet connection required.

- **Step** — contract one uniformly random edge.
- **Auto-run** — contract automatically until two supernodes remain.
- **New random run** — reset with a fresh random seed.
- **Find a lucky run** — replay a run that succeeds in finding the minimum cut.
- **Run 100 / 1000 trials** — estimate the empirical success rate and compare it to the 1/C(n,2) bound.

Keyboard: <kbd>Space</kbd> steps, <kbd>R</kbd> resets.

## The algorithm

Repeatedly pick a uniformly random edge and contract it — merge its endpoints into one supernode, keep parallel edges, and drop self-loops — until only two supernodes remain; the edges between them form a cut. A single run finds any fixed minimum cut with probability at least 1/C(n,2) = 2/(n(n−1)), so repeating it O(n² log n) times and keeping the smallest cut finds the global minimum cut with high probability. A corollary: a graph has at most C(n,2) distinct global minimum cuts.

The built-in example is two K₄ clusters joined by a 2-edge bridge (n = 8, m = 14), whose unique minimum cut has size 2.
