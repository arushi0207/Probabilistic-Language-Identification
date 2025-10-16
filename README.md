# 🧠 Probabilistic Language Identification (CS540 Homework 2)

This project implements a **Naïve Bayes–based language classifier** that determines whether a given text was written in **English** or **Spanish** using character-frequency analysis.

---

## 📘 Overview

Given a “shredded” text (a letter file), the program reconstructs statistical evidence to infer its language. It performs:

1. **Character Counting (Digital Shredder)** – Counts each letter A–Z (case-insensitive, ignores punctuation).
2. **Probability Computation** – Calculates the likelihood of English vs. Spanish text using multinomial probabilities.
3. **Bayesian Inference** – Applies Bayes’ Rule to compute the posterior probability:
   \[
   P(Y = \text{English} \mid X)
   \]
4. **Numerical Stability** – Uses log probabilities and conditional normalization to prevent underflow.

---

## ⚙️ How It Works

The model uses **multinomial distributions** of character frequencies for English and Spanish provided in two text files:
- `e.txt` → English probabilities  
- `s.txt` → Spanish probabilities  

It computes:
\[
F(y) = \log P(Y=y) + \sum_i X_i \log p_i
\]
Then normalizes to find:
\[
P(Y = \text{English} \mid X) = \frac{1}{1 + e^{F(\text{Spanish}) - F(\text{English})}}
\]
Special handling ensures stable results when exponent differences are extreme (≥100 or ≤−100).

---

## 💻 Usage

Run the program using:
```bash
python3 probability.py [letter_file] [english_prior] [spanish_prior]
