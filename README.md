This project combines web analytics and social media text analytics for e-commerce brand Shopee MY.
Part 1 evaluates web KPIs like page load time, bounce rate, SEO, mobile optimisation, and user engagement features.
Part 2 scrapes 2,000+ social media posts via Apify and runs two complementary sentiment analysis pipelines: unsupervised (VADER lexicon-based or LDA topic modelling) and supervised (Naive Bayes / Logistic Regression / SVM with labelled data), producing positive/negative/neutral classifications, word clouds, and a confusion matrix comparison.
Part 3 delivers actionable recommendations in one chosen digital strategy area.

## 📒 Report Sections

---

### 1️⃣ 🌐 Introduction — Brand Selection
> Analysing a major e-commerce brand's digital & social media presence

- 🏪 **Brand selected:** [Your chosen e-commerce brand]
- 📍 **Location & Market:** Overview of brand's digital footprint
- 👥 **Target Audience:** Consumer demographics & platform presence
- 🎯 **Why This Brand:** Accessible data, strong social media activity, rich keyword landscape

---

### 2️⃣ 📡 Part 1 — Web Analytics Landscape

**Area 1: 📊 Web Metrics Comparison**

| KPI | What Was Measured | Tool Used |
|---|---|---|
| ⏱️ Page Load Time | Desktop vs Mobile load speed | SimilarWeb / GTmetrix |
| 🚪 Bounce Rate | % of single-page sessions | SimilarWeb |
| ⏳ Session Duration | Average time on site | SimilarWeb |
| 🛒 Conversion Rate | Visits → purchases | Estimated from benchmarks |

**Area 2: 🔍 SEO & Visibility**
- 🔑 Keyword strategy analysis (branded + non-branded terms)
- 🔗 URL structure evaluation
- 📝 Meta descriptions and title tag audit
- 📈 Organic search visibility & ranking trends

**Area 3: 🎮 Interactivity & User Engagement**
- 🤖 Chatbot presence and functionality
- 🛍️ Recommendation engine behaviour
- 🖼️ Interactive product views (360°, zoom, AR features)

**Area 4: 📱 Mobile Optimisation**
- ⚡ Mobile page load speed assessment
- 📲 Responsive design vs dedicated mobile app
- 🧭 Ease of navigation on mobile devices
- 🔍 Mobile SEO performance

---

### 3️⃣ 🕷️ Part 2 — Data Collection (Social Media)
> Scraping brand-related posts for sentiment analysis

| Detail | Value |
|---|---|
| 🛠️ Tool Used | Apify / Python (BeautifulSoup / Scrapy) |
| 📊 Minimum Posts | 2,000 social media posts |
| 🔎 Keywords Used | Brand name + hashtags + product names |
| 📁 Output Format | CSV archived in Appendix |

---

### 4️⃣ 🧹 Data Cleaning & Preparation

**Steps Applied:**
- ❌ Remove duplicate posts
- ❌ Filter irrelevant/off-topic content
- 🔡 Lowercasing all text
- ✂️ Remove URLs, mentions (@), hashtags (#), punctuation
- 🌿 **Lemmatization / Stemming** — reduce words to root form
  - e.g. `"running"` → `"run"` | `"products"` → `"product"`
- 🚫 Remove **stopwords** (the, is, at, which...)
- ✅ Final clean corpus ready for analysis

---

### 5️⃣ 🤖 Sentiment Analysis — Unsupervised (No Labels)
> Inferring sentiment without any pre-labelled data

**Method chosen:** VADER Lexicon-Based OR LDA Topic Modelling

| Approach | How It Works | Output |
|---|---|---|
| 📖 VADER | Assigns polarity scores to each word using a sentiment dictionary | Positive / Negative / Neutral per post |
| 🗂️ LDA | Groups words into latent topics; each topic interpreted for sentiment | Dominant themes + tone per topic |

**Outputs Reported:**
- 📊 Sentiment distribution chart (pie / bar)
- ☁️ Word clouds per sentiment class
- 🗂️ Dominant themes driving positive & negative conversations

---

### 6️⃣ 🏷️ Sentiment Analysis — Supervised (With Labels)
> Training an ML classifier on labelled sentiment data

| Step | Detail |
|---|---|
| 📥 Labelled Dataset | Manually labelled OR publicly available (Kaggle) |
| 🏷️ Classes | Positive · Negative · Neutral |
| 🤖 Models Tested | Naive Bayes · Logistic Regression · SVM |
| 📐 Evaluation | Accuracy + Confusion Matrix |

**Model Performance Table:**

| Model | Accuracy | Strength |
|---|---|---|
| 🔵 Naive Bayes | — | Fast, good baseline for text |
| 🟢 Logistic Regression | — | Interpretable, strong for sparse text |
| 🟠 SVM | — | Best for high-dimensional text features |

---

### 7️⃣ ⚖️ Comparison — Supervised vs Unsupervised

| Dimension | 🤖 Unsupervised (VADER/LDA) | 🏷️ Supervised (ML) |
|---|---|---|
| Labels needed? | ❌ No | ✅ Yes |
| Speed | ⚡ Fast | 🐢 Slower (training needed) |
| Accuracy | 🟡 Moderate | 🟢 Higher |
| Interpretability | 🟢 High | 🟡 Depends on model |
| Best for | Quick brand monitoring | Precise classification tasks |

---

### 8️⃣ 💡 Part 3 — Strategic Recommendations
> One focused recommendation area based on sentiment findings

**Selected Area:** [e.g. Social Listening Strategy]

- 🔍 **Insight 1:** Key theme driving positive sentiment → [finding]
- 🚨 **Insight 2:** Key theme driving negative sentiment → [finding]
- 📣 **Recommendation 1:** [Actionable strategy]
- 📣 **Recommendation 2:** [Actionable strategy]
- 📣 **Recommendation 3:** [Actionable strategy]
