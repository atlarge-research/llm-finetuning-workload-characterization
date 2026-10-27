# Reproducibility capsule: LLM Fine-Tuning Workloads (WoAIS '26)

Regenerates the data figures (Figs. 2-6) of the paper *LLM Fine-Tuning Workloads: Characterization, Challenges, and
Opportunities for Serverless AI*, by Radu Nicolae, Daniele Lotito, and Alexandru Iosup (WoAIS '26, at Middleware 2026),
from IBM's public dataset LLMFineTuningBench.

## Run

Needs Docker, running. In a terminal:

```sh
git clone https://github.com/atlarge-research/llm-finetuning-workload-characterization.git
cd llm-finetuning-workload-characterization
docker build -t woais2 .
docker run --rm -v ./out:/capsule/out woais2
```

The figures are in `out/`.

Without Docker: `bash reproduce.sh` (needs Python 3.11 and the font Times New Roman).

## Checklist

1. **Program:** `plot.py` (Python 3.11, matplotlib 3.11.0, pandas 2.3.3).
2. **Data:** [`ibm-research/LLMFineTuningBench`](https://huggingface.co/datasets/ibm-research/LLMFineTuningBench),
   30,920 rows x 38 columns; if the Hub fails, the snapshot `data/ado-sfttrainer.csv`.
3. **Environment:** Docker 27.4, base image `python:3.11.16-slim-trixie`.
4. **Hardware:** none specific; tested on ARM64 (macOS) and x86-64.
5. **Output:** `out/fig2_*.pdf` to `out/fig6_*.pdf`, one PDF per figure of the paper (Figures 2-6).
6. **Disk:** about 1 GB (Docker image).
7. **Time:** about 2 minutes to build, under 1 minute to run.
8. **Data license:** Apache-2.0, IBM Research.
