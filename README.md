# NL2FOL: Natural Language to Multi-Sorted First-Order Logic

This repository contains a dataset for translating natural-language database queries into **Multi-Sorted First-Order Logic (FOL)**. It also contains the **Z3-based equivalence results** for FOL formulas predicted by several large language models (LLMs).

## Repository Structure

```
.
├── dataset/
│   ├── NL2FOL_dataset.json     # NL queries with SQL, vocabulary, arity, sorts, axioms, and gold FOL
│   └── README.md               # dataset fields, loading, and intended use
├── results/
│   ├── z3_equivalence_results_<model>/   # one folder per LLM (DeepSeek, GPT-5.2, GPT-5.6, GPT-6, ...)
│   └── README.md               # result layout, check scripts, logs, and verdicts
└── README.md
```

| Directory | Contents |
|---|---|
| [`dataset/`](dataset/) | Each instance pairs an NL question with its SQL query, vocabulary, arity, global sorts, sort axioms, key/foreign-key axioms, and the reference (gold) multi-sorted FOL formula. See [`dataset/README.md`](dataset/README.md). |
| [`results/`](results/) | For each LLM, the predicted FOL is checked against the gold FOL using Z3. Each model folder contains the inputs, the generated check scripts, the logs, the errors, and the per-example verdicts and summary. See [`results/README.md`](results/README.md). |

## Equivalence Checking

A predicted formula is **equivalent** to the gold formula when it is equivalent to it **modulo the schema's sort axioms and key/foreign-key axioms**. Equivalence is checked in both directions:

- `Gold ⊨ Predicted`
- `Predicted ⊨ Gold`

Before the check, the free (answer) variables of the two formulas are paired by sort. Each example gets one of three verdicts: `EQUIVALENT`, `NOT EQUIVALENT`, or `UNKNOWN`.

## Quick Start

```bash
pip install z3-solver
python results/z3_equivalence_results_gpt_6/checks/equiv_check_0.py -v
```

## Citation

If you use this dataset or these results, please cite the associated paper. Citation details will be added upon publication.

## License

The dataset and results are released under the license in this repository. Source datasets (for example, Spider) remain subject to their own licenses.
