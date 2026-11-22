# The stranger cadence

The release's whole claim is that a stranger, given this repository and nothing else, can build
the crate and run its proofs from the README alone. A real agent runs that check on a
cadence, and the weekly `stranger cadence` job fails when the
last run is past 28 days.

What a run is:

1. Clone the repository fresh.
2. Follow the README and nothing else: build, test, and run the proofs.
   The README must name the build and test commands (with any feature a test target needs), the
   bare-metal build with `rustup target add`, the Kani install before the first `cargo kani`, how
   long the proofs take and how to run one harness, what a passing run prints that looks alarming,
   how to run and revert one falsification patch, and how to check the minimum Rust version.
   Each one it lacks is a finding.
3. Note every place the README lied, omitted, or assumed. Those are findings against the README,
   not against the stranger.
4. Record the date on the line below.

Last run: 2026-11-22

Result of that run: a fresh agent with only the repository URL cloned `02d497b` and, from the
README alone, reached a passing build, 10 unit tests and 3 documentation tests, the library on all
three bare-metal targets, and all eleven Kani harnesses in about 14 seconds. It applied one
falsification patch, saw its harness fail at the patch's assertion, and reverted it. At Rust 1.88,
the stated minimum, the build and tests pass, and 1.87 refuses the crate. Kani and the targets were
already installed, so the run could not show whether the install steps work. It found no false
claim. It found five gaps, which the README now closes: how to run one harness, the module name in
a patch's file name, what a falsified run prints, the passing harnesses that report expected
panics, and how to check the minimum Rust version.
