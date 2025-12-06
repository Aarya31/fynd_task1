📘 Fynd AI Intern – Task 1: Rating Prediction via Prompt Engineering

This task focuses on predicting 1–5 star ratings for Yelp reviews using LLM prompting techniques only (no fine-tuning).
The objective is to explore how prompt engineering impacts:

Prediction accuracy

JSON validity

Reliability and consistency of outputs

A clean comparison of three prompting styles is performed.


📝 Task Overview
⭐ Objective

Predict Yelp review star ratings using prompt engineering only, without training or fine-tuning a model.

⭐ Requirements

Use Yelp Reviews dataset from Kaggle

Implement at least 3 prompting strategies

Evaluate and compare

Output must follow strict JSON format:

{
  "predicted_stars": 4,
  "explanation": "Short reasoning for the rating."
}

📊 Dataset

Dataset:
📌 https://www.kaggle.com/datasets/omkarsabnis/yelp-reviews-dataset

For efficiency, a random 200-review sample was extracted containing:

text — review text

stars — ground truth rating

🧠 Models & API

All prompting experiments use:

Model: deepseek/deepseek-chat

Provider: OpenRouter API

Temperature: 0 for stability

JSON extraction: Regex-based extraction for 100% validity

🎯 Prompting Strategies
1️⃣ Zero-Shot Prompt

No examples provided.
Strict instructions enforce valid JSON output.

2️⃣ Few-Shot Prompt

Three labeled examples illustrate rating logic:

Negative → 1 star

Neutral → 3 stars

Positive → 5 stars

This helps the model anchor its rating behavior.

3️⃣ Chain-of-Thought (Hidden Reasoning) Prompt

Model is allowed to think step-by-step internally, but only final JSON is returned.

🔍 Evaluation Method
Metrics:

Accuracy: predicted == actual

JSON Validity: successful JSON parsing rate

Reliability: consistency across similar reviews

Evaluation loop:

For each review → send prompt → parse JSON → compute metrics

Results stored in CSV

🧪 Results
Prompt Type	Accuracy	JSON Validity
Zero-Shot	0.655	1.000
Few-Shot	0.665	1.000
Chain-of-Thought	0.635	1.000
Summary:

Few-Shot performed best overall

Zero-Shot was close and highly stable

CoT produced slightly lower accuracy due to over-reasoning

JSON formatting reached 100% validity across all prompts

📚 Key Insights

Prompt engineering alone can achieve 60–67% accuracy similar to classical ML baselines.

Few-shot prompting helps the model interpret borderline reviews more consistently.

Strict JSON constraints + regex extraction eliminate formatting errors.

Zero temperature (0.0) ensures reproducible predictions.


Run the Colab or Jupyter notebook

Download dataset using KaggleHub

Load sample

Insert OpenRouter API key

Run evaluation blocks

3. View results

Metrics print in console

Comparison table is generated

CSV files saved under /content/ or project folder

🔐 API Key Handling

Set your key as an environment variable:

export OPENROUTER_API_KEY="sk-or-v1-xxxxxxxx"


Never commit your API key to GitHub — use:

.env file (local only)

Streamlit / Colab secret manager

GitHub Actions secrets if automating

📄 Report

A detailed report summarizing:

Prompt design

Iterations

Model behavior

Evaluation

Comparisons

Conclusions

is included as:
📄 task1_report.pdf

🏁 Conclusion

Task 1 demonstrated:

The power of prompt engineering

Reliability of LLMs for sentiment→rating mapping

Importance of controlling output format

How few-shot prompting offers measurable improvement

This task builds the foundation for Task 2 by developing strong prompting strategies and structured LLM output handling.
