# Notes on Sources

For each source: what information is relevant and which part of the thesis it supports. The keys in parentheses match the entries in `references.bib`.

---

## 1. LLMs and Nutrient Estimation

### NutriBench (`hua2024nutribench`)
- **What it is:** a benchmark of 11,857 natural-language meal descriptions; 12 LLMs evaluated on carbohydrate estimation using standard prompting, Chain-of-Thought, and RAG.
- **Relevant:** the best model (GPT-4o + CoT) reaches ~67% accuracy within a 7.5 g margin, so almost a third of estimates are off. Models are more accurate when they break a meal down into individual foods. RAG with per-100 g values performed poorly for natural portions ("a cup of rice"), so the database must match the way people actually talk about food.
- **Caveat:** the authors conclude that LLMs are comparable to nutritionists. This does not contradict my thesis, but the argument must be phrased carefully: the problem is not that AI is weak, but that the errors are too large for a daily food log.
- **Used in:** state of the art; architecture (parsing into items → database lookup); unit conversion ("a slice" → grams).

### Taiwanese meal study (`hsuan2025chatbots`)
- **What it is:** 5 chatbots (ChatGPT, Claude, Gemini, Grok, Copilot) compared with dietitians on ready-to-eat meals.
- **Relevant:** 70–90% accuracy for calories and macronutrients, but sodium and saturated fat were strongly underestimated; weak on micronutrients.
- **Used in:** the argument for taking values from a database, especially for micronutrients.

### Peruvian meal study (`peru2025llm`)
- **What it is:** Gemma 3 models (4B, 12B, 27B) estimate 6 nutrients from descriptions of traditional Peruvian meals.
- **Relevant:** only 15% agreement for iron and 19% for vitamin A; the authors conclude that accuracy is not sufficient for consumer applications. It also shows that local cuisines are a problem for general-purpose models, and the authors recommend RAG with local databases.
- **Used in:** justifying a database of Romanian foods; micronutrients taken from USDA rather than estimated.

### Chain-of-Thought (`wei2022cot`)
- **Relevant:** step-by-step reasoning technique; cited for the meal-parsing step.
- **Used in:** architecture / prompting chapter.

---

## 2. Voice-Based Meal Logging

### base2Diet (`chikwetu2023base2diet`)
- **What it is:** iOS app with a text mode and a voice mode; 28-day pilot study.
- **Relevant:** the voice group logged 1.7 times more meals and had fewer dropouts (1 vs. 5). **Important:** no participant corrected their logs, even though they could; users trust automatically filled-in data. This directly justifies the decision to take values from a verified database. Limitations: speech recognition struggled with accents; only young participants.
- **Used in:** motivation for voice input; argument for the database; differentiation (my work: Romanian language, older adults).

### Voice input for food intake (`millard2023voice`)
- **Relevant:** development and usability of voice-based collection of food and drink intake.
- **Used in:** state of the art.

### Spoken language mapped to food databases (`taylor2021spoken`)
- **Relevant:** the approach closest to mine: spoken descriptions automatically mapped to food composition data.
- **Used in:** state of the art; comparison with my architecture.

### Speech2Health (`hezarjaribi2018speech2health`)
- **Relevant:** mobile framework that extracts dietary composition from speech; a pre-LLM approach.
- **Used in:** background / state of the art.

### Whisper (`radford2023whisper`)
- **Relevant:** multilingual speech-to-text model (including Romanian) that can also run locally.
- **Used in:** technical chapter on transcription.

---

## 3. Older Adults and Usability

### JMIR Aging study (`sung2026speech`)
- **What it is:** crossover study with 18 people aged 65+: voice logging vs. written food diary.
- **Relevant:** SUS score of 72.78 (voice) vs. 66.25 (written diary), with comparable accuracy.
- **Used in:** argument for the 50+ audience and for the simple mode.

### Voice-added food reporting (`liu2020voiceadded`)
- **Relevant:** usability for older adults improves with a visual layout, larger fonts, and simplified interaction.
- **Used in:** justifying the UI decisions of the simple mode.

### Voice-assisted food recall (`liang2022voicerecall`)
- **Relevant:** 60% of older adults preferred the voice version over the web version.
- **Used in:** state of the art, target audience.

### Voice assistants among older adults (`pradhan2020voiceassistants`)
- **Relevant:** how older adults with little technology experience use voice assistants.
- **Used in:** argument for voice as the interface for the target audience.

---

## 4. Self-Monitoring and Micronutrients

### Self-monitoring (`burke2011selfmonitoring`)
- **Relevant:** systematic review: dietary self-monitoring is associated with better weight-loss outcomes.
- **Used in:** introduction, motivation for the app.

### Iron (`hurrell2010iron`)
- **Relevant:** iron bioavailability and the factors that influence it (e.g., vitamin C increases it).
- **Used in:** logic behind the simple micronutrient recommendations.

---

## 5. Food Databases

### USDA FoodData Central (`fukagawa2022fdc`, `usda_fdc`)
- **Relevant:** main source for generic foods and micronutrients (laboratory data).
- **Used in:** chapter on data sources.

### Open Food Facts (`openfoodfacts`)
- **Relevant:** packaged products with barcodes, including from Romania; ODbL license (attribution required).
- **Used in:** data sources; barcode scanning; legal aspects.

---

## 6. RAG, Embeddings, Vector Search

### RAG (`lewis2020rag`)
- **Relevant:** the paper that introduced Retrieval-Augmented Generation. The app applies the principle: the model receives candidates from the database and only selects among them; it does not generate values.
- **Used in:** architecture chapter.

### Sentence-BERT (`reimers2019sbert`)
- **Relevant:** sentence-level embeddings for semantic search.
- **Used in:** explanation of semantic food search.

### HNSW (`malkov2020hnsw`)
- **Relevant:** the approximate nearest-neighbor search algorithm used by the pgvector index.
- **Used in:** technical chapter on the database.

### pgvector and pg_trgm (`pgvector`, `pgtrgm`)
- **Relevant:** documentation for the PostgreSQL extensions for vector search and text similarity search.
- **Used in:** search implementation.

---

## 7. Technologies and Legal Framework

### Expo, React Native (`expo_docs`, `reactnative_docs`)
- **Used in:** chapter on the technologies used.

### GDPR (`gdpr2016`)
- **Relevant:** health data is a special category (Art. 9) and requires explicit consent.
- **Used in:** chapter on security and data protection (impairments, family mode).
