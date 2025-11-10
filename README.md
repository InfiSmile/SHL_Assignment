# Grammer Scoring Using Multimodal Learning (SHL_Assignment)
📘 **Overview**

This project focuses on predicting grammar scores (ranging from 0 to 5) using both text and audio data. The idea was to explore how linguistic features (from text) and paralinguistic cues (from audio) together can improve grammar quality prediction.




1️⃣ **Initial Approach — Simple Feature Concatenation**

At first, I combined audio and text embeddings directly and trained a regression model.
It worked, but the results showed that the model wasn’t fully capturing the complementary nature of both modalities.

2️⃣ **Text-Only Experiments**

To understand how well textual features alone perform, I fine-tuned models like:

**Sentence Transformer**

**DeBERTa**

These text-only models gave decent results but highlighted one key point — audio features add valuable context (like tone, pauses, or fluency) that text alone can’t represent.

3️⃣ **Audio Transcription**

For audio, I used NVIDIA’s Parakeet-TDT 0.6B-v2 model to transcribe speech into text.
This helped extract linguistic information directly from the spoken responses, making audio data more interpretable.

4️⃣ **Ensemble Modeling**

After experimenting with both modalities separately, I moved to an ensemble approach to combine their strengths.
I implemented different blending methods such as:

Value-based NNLS Ensemble

Rank-based NNLS Ensemble

Confidence-weighted Blending (giving more weight to models with lower uncertainty)

These ensemble techniques significantly improved performance and stability.

⚙️ **Utility Functions**

I also implemented several helper functions:

Metrics: For MAE, RMSE, and Pearson correlation

Clip Function: To ensure predictions stay in the valid 0–5 range

Rank Scaling: To normalize model outputs for ensemble blending

📊 **Results Summary**

By blending multiple models, the final system achieved better correlation and lower error compared to single-model baselines.
This showed that combining text and audio models provides a more holistic understanding of grammar quality.

🧩 **Key Takeaways**

Text models alone perform well but audio adds nuance.

Ensembles are powerful for stabilizing predictions.

Confidence-weighted blending helps when model uncertainties differ.

🛠️ **Tech Stack**

Python, PyTorch, Transformers

Sentence Transformer, DeBERTa, NVIDIA Parakeet-TDT

Scikit-learn, NumPy, Pandas
