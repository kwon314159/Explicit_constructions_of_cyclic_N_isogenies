# Explicit Constructions of Cyclic N-isogenies

This repository contains SageMath code accompanying the paper:

> **Explicit Constructions of Cyclic N-isogenies**  
> *Daeyeol Jeon and Yongjae Kwon*

The code constructs explicit cyclic $N$-isogenies for sporadic levels where $X_0(N)$ has positive genus, combining:
- a uniform algebraic pipeline (default path), and
- an analytic CM cross-check pipeline for $N=163$.

## Key Features

- `Maps` Explicit rational-map recovery for $a_4, a_6, a_4', a_6'$ on supported $X_0(N)$.
- `Solver` Degree/precision-controlled workflow for practical high-genus levels.
- `Analysis` Point-wise isogeny analysis output (domain/codomain invariants, twists, labels).
- `Notebook UI` Interactive level selection and one-click runs.
- `N=163 Reference` Optional analytic cross-check notebook for reproducibility.

## AI-Assisted Development Note

Parts of implementation, refactoring, and code-organization tasks were assisted by **OpenAI Codex (GPT-5 family)**.  
All mathematical definitions, derivations, and final computed results were independently checked and validated by the authors.

## Repository Structure

- `Core` `modular_isogeny_lib.sage`  
  Core library (model data, modular forms, solver, evaluation utilities, isogeny analysis, notebook rendering helpers).

- `Notebook` `X0_main.ipynb`  
  Main notebook for algebraic construction and point-wise isogeny analysis.

- `Reference` `X_0(163).ipynb`  
  Optional standalone notebook for an analytic $N=163$ cross-check.
  It is included as a reference/reproducibility aid and was not used as the primary pipeline for the paper's final reported tables.

- `Docs` `FUNCTION_STRUCTURE.md`  
  Compact reference for function-level architecture.

- `Logs` `logs/`  
  Optional run logs from long computations.

## Supported Levels

The main notebook supports:
$$
N \in \{11,14,15,17,19,21,27,37,43,67,163\}.
$$

## Output Convention

Throughout the codebase, solver outputs are identified directly with paper coefficients:
- `u = a_4`, `v = a_6`,
- `u_N = a_4'`, `v_N = a_6'`.

The normalization matches
$$
a_6 = \frac{E_6}{864\,(E_2^{(N)})^3}.
$$

## Main Notebook Behavior (`X0_main.ipynb`)

- Uses `ipywidgets` dropdown for level selection.
- Uses deterministic fixed-degree fast paths for:
  - `N=43`: `u,u_N` degree 8; `v,v_N` degree 12.
  - `N=67`: `u,u_N` degree 15; `v,v_N` degree 19.
  - `N=163`: `u,u_N` degree 34; `v,v_N` degree 38.
- For these levels, optional adaptive fallback is available via:
  - `run_isogeny_construction(N, prec=..., allow_fixed_plan_fallback=True)`.

## Requirements

- SageMath **10.6+** (tested on 10.7)
- Jupyter + `ipywidgets` for notebook UI

## Database Note (Curve Labels)

Curve labels are obtained through Sage's Cremona database.

- With the default mini database (`cremona_mini.db`), labels may be unavailable for larger conductors.
- If labels appear as `n/a` for valid curves, install/expand the Cremona data in your Sage environment.

This does **not** affect the core rational-map construction; it only affects label display in analysis output.

## Quick Start

1. Open `X0_main.ipynb` in a Sage/Jupyter environment.
2. Ensure `modular_isogeny_lib.sage` is in the same directory.
3. Run all cells.
4. Select `N` in the dropdown and run.

For an independent $N=163$ analytic reference check, run `X_0(163).ipynb`.

## Citation

If you use this code in research, please cite:

```bibtex
@article{jeon_kwon_isogenies,
  title={Explicit Constructions of Cyclic N-isogenies},
  author={Jeon, Daeyeol and Kwon, Yongjae},
  journal={To appear},
  year={2026}
}
```

## License

MIT License.
