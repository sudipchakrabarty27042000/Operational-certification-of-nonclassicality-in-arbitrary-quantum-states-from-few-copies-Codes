# Operational certification of nonclassicality in arbitrary quantum states from few copies

Code accompanying the manuscript *Operational certification of nonclassicality in arbitrary quantum states from few copies* by Sudip Chakrabarty, Bivas Mallick, Ananda G. Maity and A. S. Majumdar.

One self-contained Jupyter notebook, `wigner_negativity_moments_reproduction.ipynb`, reproduces every number, table and figure of the Letter, its End Matter and the Supplemental Material. All functions are defined inside the notebook and no data files are needed.

## Quick start

```bash
git clone <this repository>
cd wigner-moments-certification
pip install -r requirements.txt
jupyter notebook wigner_negativity_moments_reproduction.ipynb
```

The first code cell holds a single switch.

| `QUICK` | What it does | Run time (2 CPU cores) |
|---|---|---|
| `True` | Fewer repetitions and lower orders, for a fast end-to-end check | about 10 minutes |
| `False` (default) | Reproduces the published numbers | several hours |

Results are written to `data/*.json` and the figures to `figs/*.pdf`, with the file names used in the manuscript. The notebook was tested with Python 3.13, NumPy 2.5, SciPy 1.18, mpmath 1.3, QuTiP 5.3 and Matplotlib 3.11. Figures use the TeX Gyre Termes font when it is installed and otherwise fall back to a Times-like serif font.

## Conventions

Quadratures are x = (a + a†)/√2 and p = (a − a†)/(√2 i) with ħ = 1, so the vacuum has W = exp(−x² − p²)/π. The Wigner moments are wₙ = ∫ Wⁿ dx dp. The interferometer of Theorem 1 measures the parity biases sₙ = n πⁿ⁻¹ wₙ. All certificates use confidence 1 − δ = 0.95 and report the smallest total number of copies (a k-copy shot counts as k copies) for which at least 90% of simulated experiments certify.

## Contents of the notebook

| Section | Result |
|---|---|
| 1 | Core functions: polynomial Wigner kernel, exact moments by Gauss-Hermite quadrature, exact moments of noisy cat states, checks against QuTiP |
| 2 | Theorem 1 verified with an explicit Helmert interferometer in Fock space (agreement to 10⁻¹⁵) |
| 3 | Table I and Fig. 1(a): exact detection sets of the LP, LC and Hankel hierarchies up to n = 20 for λ|0⟩⟨0| + (1 − λ)|1⟩⟨1|, at 150 digits |
| 4 | Fig. 1(b): detection sets up to n = 20 for the noisy even cat state with α = 2 |
| 5 | Fig. 3 (End Matter): detection rates on random Hilbert-Schmidt states with cutoffs N = 1, …, 8 |
| 6 | Gaussian value of L₄, its behaviour under loss, and invariance under readout errors |
| 7 | Fig. 2(c): finite-copy Γ₃ and H₂ certificates, sufficient budget of Proposition 3, false-certification rates |
| 8 | Fig. 2(a,b): interferometer, displaced-parity tomography and Haar shadows for ρ_0.2 and a noisy odd cat with α = 1, with an unbiasedness check; the α = 4 cat for SM Table |
| 9 | Non-adaptive displaced-parity search versus an unknown displacement (SM G) |
| 9b | Fig. 2(d): calibrated and model-free adaptive strategies versus the moment certificate, for noisy cat states up to n̄ = 144 |
| 9c | Fig. 2(a,b) and Fig. 4: unbiased homodyne tomography with pattern functions, simulated and as a leading-order lower bound |
| 10 | Fig. 4 (End Matter): energy scaling for noisy odd cat states |
| 11 | Fock states |0⟩, …, |10⟩ |
| 12 | Imperfect mode overlap (permanent model) and heralded sources |
| 12b | Detector efficiency required by the certificates (SM G) |
| 13 | Cost of Haar-shadow certification versus Fock truncation, against the interferometer |
| 14 | Comparison with Fock-fidelity witnesses and Bochner (characteristic-function) certificates under unknown squeezing and phase |
| 15 | L, L₄, L₆ for N00N and photon-added coherent states |
| 16 | All figures of the Letter and the Supplemental Material |

## Reference values (full mode)

| Quantity | Value |
|---|---|
| Hankel thresholds λₙ, mixed Fock state, n = 1, …, 5 | 0.30923, 0.41919, 0.45271, 0.46816, 0.47678 |
| Hankel threshold, n = 20 / n = 40 | 0.49719 / 0.49909 (exact boundary 1/2) |
| Hankel threshold, noisy even cat, n = 20 | 0.99597 (exact boundary 0.99966) |
| Copies to estimate Γ₃ to 20%, ρ_0.2 / odd cat α = 1 | interferometer 1.3×10⁴ / 1.8×10³, tomography 1.1×10⁵ / 5×10⁴ |
| Moment certificate, ρ_0.2 / odd cat α = 4 | 2.5×10⁴ / 4.2×10³ copies |
| Point search, r_u = 10, ρ_0.2 / odd cat | 1.4×10⁵ / 1.7×10⁵ copies |
| Point search, r_u = 20, ρ_0.2 / odd cat | 7.1×10⁵ / 8.5×10⁵ copies |
| Bochner certificate, ρ_0.2 (known frame) | 1.0×10⁵ copies, fails from 3 dB of squeezing |
| Bochner certificate, odd cat, phase-robust | 8.9×10⁴ copies |
| Mode overlap with no false certificates | V ≥ 0.5 |
| Calibrated targeted test, unknown frame, ρ_0.2 / cat α = 4 | 165 to 256 / 476 to 534 copies |
| Model-free scan and test, cats at n̄ = 1.3 / 16 / 144 | 834 / 3.8×10³ / 1.8×10⁵ copies (moments: about 4×10³) |
| Homodyne tomography, 20% error, cats n̄ = 1.3 to 25 (lower bound) | 1.4×10³ to 7.9×10³ copies |
| Efficiency needed by the Γ₃ certificate, ρ_0.2 | η > 0.864 |

Monte Carlo budgets can differ between machines, typically by 10 to 25%, because tiny floating-point differences change the random path of the budget searches. The numbers in the manuscript are those of the run stored in this repository.

## License

MIT, see `LICENSE`.
