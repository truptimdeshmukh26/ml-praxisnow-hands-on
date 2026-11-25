# Hands-on ML for AI Product Managers: the PraxisNow case 🩺

A new problem for everything you learned in the last four days (logistic regression, KNN, decision trees, feature engineering), from a raw table to a decision.

**PraxisNow** is a (fictional) booking app for medical practices. About **1 in 5 booked appointments ends with an empty chair**. Lena, Head of Operations, wants to know: *can we see the no-shows coming, and what should we do about them?* You build the model, then decide when to send an SMS, whom to call, and when to double-book a slot, and you check who pays for the model's mistakes.

You fill in short blanks in prepared notebooks, run them cell by cell, and answer product questions. There are no functions to write.

## Learning Objectives

By the end of this repository, you should be able to:

- Frame an ML problem: target, **prediction moment**, and which mistake costs more **for which action**.
- Remove **leaks**, beat a **baseline**, and split data **by time** the way it will be used.
- Compare **logistic regression, KNN and a decision tree** with one recipe, and read their confusion matrices and train-vs-test gaps.
- Turn **scores** into decisions: a top-k list for a fixed capacity, a money-based threshold, and see how the threshold moves when the costs change.
- Check **who carries the cost** of the model's mistakes, and why removing a column doesn't make a model fair.
- Write a **ship / pilot / improve** recommendation with a KPI and a guardrail.

## Learning Path

| Day | File | What you do |
|---|---|---|
| Tue | [**1 - Your First No-Show Model**](1_first_model.ipynb) | Size up the problem, find two leaks, beat "everyone comes", build features from dates, split by date, compare three models, fix an overfitting tree, see what the model relies on. Milestones **M1–M3**. |
| Wed (start Tue afternoon) | [**2 - From Score to Policy**](2_from_score_to_policy.ipynb) | Scores instead of labels, SMS (no model needed?), 300 calls, the double-booking threshold in euros, a fairness check, your recommendation for Lena. Milestones **M4–M5**, plus a bonus "day-before" model. |

### Milestones

| | Where | Done when… |
|---|---|---|
| **M1** | NB 1, Steps 1–5 | an honest table: no leaks, date features, split by date |
| **M2** | NB 1, Steps 6–8 | three models compared against the baseline, confusion matrices read |
| **M3** | NB 1, Steps 9–10 | the overfitting tree fixed, and you can say which model you'd pick and what it relies on |
| **M4** | NB 2, Steps 1–4 | a call list for 300 calls and a double-booking threshold based on money |
| **M5** | NB 2, Steps 5–6 | a fairness check and a written recommendation, pitched at the Wednesday stand-up (3 min per group) |

### How the notebooks work

| Marker | Meaning |
|---|---|
| ▶️ **Run** | Just run the cell. |
| ✏️ **Your turn** | Replace every `___` with your answer, then run. |
| ✅ **Check** | Tells you if you got it right, with a hint if not. |
| 🧠 **Think** | A PM question: write 1–3 sentences in the answer cell below it. |

### Additional Folders and Files

| File / Folder | Description |
|---|---|
| [**Data**](data/) | `praxisnow_appointments.csv` (6,228 synthetic appointments) and the data dictionary. |
| [**Solutions**](solutions/) | Both notebooks, solved, with outputs and sample answers. |
| [**pyproject.toml**](pyproject.toml) | Project configuration and dependencies. |
| [**uv.lock**](uv.lock) | Dependency lock file. |

## Setup

Use [uv](https://docs.astral.sh/uv/getting-started/installation/) 0.13.5 or newer and Python 3.13 (uv downloads it for you).

> [!NOTE]
> Text in angle brackets like `<repo-name>` is a **placeholder**. Replace it, including the `< >`.

### 1. Create the Repository from the Template

Click **Use this template** on GitHub, set yourself as the **Owner**, choose a name, disable **Include all branches**, and click **Create repository**.

### 2. Clone the Repository

```bash
git clone <copied-ssh-url>
```

### 3. Install the Dependencies

```bash
cd <repo-name>
uv sync
```

### 4. Open the Notebooks

```bash
code .
```

Open `1_first_model.ipynb` and select the Python environment created by `uv sync` (`.venv`) as the kernel. Run the cells from top to bottom with `Shift + Enter`.

> [!TIP]
> If `uv sync` complains about the Python version, run `uv self update` and try again.

## References & Further Reading

- [scikit-learn: Tuning the decision threshold](https://scikit-learn.org/stable/modules/classification_threshold.html): why 0.5 is rarely the right cut-off.
- [scikit-learn: Common pitfalls](https://scikit-learn.org/stable/common_pitfalls.html): leakage and preparing data inside a pipeline.
- [Google: Fairness in machine learning](https://developers.google.com/machine-learning/crash-course/fairness): proxies, and measuring outcomes per group.
