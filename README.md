This project combines web analytics and social media text analytics for e-commerce brand Shopee MY.
Part 1 evaluates web KPIs like page load time, bounce rate, SEO, mobile optimisation, and user engagement features.
Part 2 scrapes 2,000+ social media posts via Apify and runs two complementary sentiment analysis pipelines: unsupervised (VADER lexicon-based or LDA topic modelling) and supervised (Naive Bayes / Logistic Regression / SVM with labelled data), producing positive/negative/neutral classifications, word clouds, and a confusion matrix comparison.
Part 3 delivers actionable recommendations in one chosen digital strategy area.

## 📒 Report Sections

---

### 1️⃣ 🛍️ Introduction and Brand Overview
> Shopee Malaysia: Southeast Asia's leading hybrid e-commerce platform

| Detail | Description |
|---|---|
| 🏢 Brand | **Shopee Malaysia** (shopee.com.my) |
| 📍 HQ | Kuala Lumpur, Malaysia |
| 🗓️ Founded | 2015 |
| 🏪 Model | Hybrid C2C + B2C marketplace |
| 🎯 Focus | Reducing transactional friction via integrated logistics & payments |
| 📊 Data Scope | Web analytics + 2,793 public user reviews |

> Shopee manages massive Big Data assets defined by high traffic **Volume**,
> transactional **Velocity**, and content **Variety**, making it an ideal
> candidate for full-stack digital analytics.

---

### 2️⃣ 🌐 Web Analytics Landscape

---

#### 📊 Web Metrics Comparison

**Traffic Volume & Conversion**

| KPI | Shopee Malaysia | Interpretation |
|---|---|---|
| 📈 Total Visits (Dec 2025) | **58.07 million** | "High-Volume" digital asset |
| 🚪 Bounce Rate | **24.18%** 🟢 | 76% of users stay & explore |
| ⏱️ Avg. Visit Duration | **4 min 57 sec** 🟢 | Strong user stickiness |
| 📄 Pages per Visit | **7.12** 🟢 | Deep browsing behaviour |

> 💡 These numbers are powered by **gamification tools** like Shopee Games,
> Live Streaming, and Personalised Recommendations — lengthening the customer journey.

**Technical Performance (Google Core Web Vitals 2026)**

| Metric | Shopee Score | Google Threshold | Status |
|---|---|---|---|
| ⏳ Largest Contentful Paint (LCP) | **6.6 seconds** | < 2.5s | ❌ FAIL |
| 🎨 First Contentful Paint (FCP) | **2.9 seconds** | < 1.8s | ❌ FAIL |

> 🚨 **Business Risk:** A 6.6s LCP causes **micro-abandonment** — users leave
> before the page finishes loading, especially during high-traffic sale events.

**Competitive Context**

| Platform | Monthly Visits | Country Rank |
|---|---|---|
| 🏆 **Shopee Malaysia** | **58.07 million** | **#6** |
| 🔵 Lazada | 10.3 million | #45 |
| 🎵 TikTok Shop | 1.5 million | — |

> Shopee receives **nearly 5× more traffic** than its closest competitor Lazada.
> TikTok Shop drives brand **Velocity** (discovery), but Shopee dominates
> purchase **Volume** (conversion).

---

#### 🔍 SEO & Visibility

**Organic Performance**

| Metric | Value |
|---|---|
| 🏅 Domain Authority (Ubersuggest 2026) | **89 / 100** |
| 🔗 Referring Domains (Backlinks) | **3,973** |
| 🔑 Organic Keywords Ranked | **~0.8 million** |
| 📊 Organic Traffic Share | **20.83%** (vs 12.60% paid) |

> Organic outperforms paid traffic meaning Shopee's SEO generates
> **free, sustainable acquisition** at scale, suppressing customer acquisition costs.

**SEO Strategy Breakdown**

| SEO Element | Strategy | Business Impact |
|---|---|---|
| 🔑 Keywords | Intent-based targeting (branded + transactional) | Captures both loyal & new-to-brand users |
| 📝 Meta Descriptions | Include CTAs: "Buy Online", "Free Shipping" | Boosts Click-Through Rate from SERPs |
| 🔗 URL Structure | Clean hierarchy: `shopee.com.my/product-name` | Efficient crawling + user trust |

---

#### 🎮 Interactivity & User Engagement

**Chat Infrastructure — Two-Tier System:**
- 🤖 **Sophie Chatbot** — Automated first responder for vouchers & order tracking
- 💬 **Chat with Sellers** — Direct buyer-to-seller messaging inside the app
  *(eliminates friction that causes tab abandonment)*

**Engagement Features:**
- 📺 **Shopee Live** — Live commerce / social shopping
- 🪙 **Shopee Coins** — Gamified reward system driving repeat visits
- 🎮 **Shopee Games** — In-app games increasing session duration

---

#### 📱 Mobile Optimization

| Detail | Value |
|---|---|
| 📲 Mobile Traffic Share | **59.93%** of all visitors |
| 📱 Platform Availability | iOS App + Android App + Mobile Web |
| ⚡ Mobile LCP | 6.6s ❌ (fails Core Web Vitals) |
| 🔍 Mobile SEO Fixes | Structured data schema + AMP principles applied |

> Despite slow mobile load times, Shopee maintains high mobile SERP visibility
> through AMP and structured data, compensating technically for its speed deficit.

---

### 3️⃣ 🕷️ Data Collection

**Tool Used:** Apify (web scraping)

| Source | Content Scraped |
|---|---|
| 📱 Google Play Store | Official Shopee Malaysia app reviews |
| ⭐ Trustpilot | Publicly available brand reviews |

| Detail | Value |
|---|---|
| 📊 Total Reviews Collected | **2,793 reviews** |
| 📁 Raw File | `Shopee_Reviews.csv` |
| 📋 Columns | Date · Star Rating · Review Text · User Display Name |
| 🔒 Privacy | Only publicly available data collected |

---

### 4️⃣ 🧹 Data Processing & Wrangling
> Full pipeline built in **Google Colab** for transparency & reproducibility

**Steps Applied:**

| Step | Method | Result |
|---|---|---|
| 📚 Load Libraries | pandas, VADER, sklearn, transformers, deep_translator | All dependencies ready |
| 📥 Load Dataset | `pd.read_csv('Shopee_Reviews.csv')` | 2,793 rows loaded |
| 🔁 Duplicate Removal | `df.drop_duplicates(inplace=True)` | Zero duplicates remaining |
| 🩹 Missing Values | Mean (numeric) + Mode (text) imputation | 0 missing values confirmed ✅ |
| 🌏 Language Translation | `GoogleTranslator(source='auto', target='en')` | All Malay/mixed reviews → English |
| 😊 Emoji Handling | Custom regex `EMOJI_PATTERN` detector | Emoji-only reviews preserved as-is |

> 💡 **Why translate?** Shopee Malaysia users write in Malay, English, and
> *Manglish* (mixed). Translating to English first ensures VADER and ML models
> can process all reviews in one consistent pipeline.

---

### 5️⃣ 🏷️ Manual Labelling
> Creating a "gold standard" ground truth for model validation

- 🙋 The translated dataset was **manually reviewed** by the team
- Each review was labelled: ✅ **Positive** · ⚪ **Neutral** · ❌ **Negative**
- This labelled dataset was used to:
  - Validate VADER unsupervised predictions
  - Train and test all supervised ML models

| Class | Manual Count | % Share |
|---|---|---|
| ✅ Positive | 1,327 | 47.5% |
| ❌ Negative | 1,315 | 47.1% |
| ⚪ Neutral | 151 | 5.4% |

> ⚠️ **Class Imbalance Warning:** Only 5.4% Neutral reviews. All models
> struggled most with this class due to limited training samples.

---

### 6️⃣ 🤖 Sentiment Analysis — Unsupervised (VADER)
> Rule-based lexicon approach, no labelled data required

**Pipeline Steps:**

| Step | Detail |
|---|---|
| ⚙️ Setup | `SentimentIntensityAnalyzer()` initialized |
| 📐 Scoring | Compound score generated per review (−1 to +1) |
| 🏷️ Labelling | `≥ 0.05` → Positive · `-0.05 to 0.05` → Neutral · `≤ -0.05` → Negative |
| 🗂️ Topic Segmentation | 6 topics assigned per review |

**📊 VADER Sentiment Results (2,793 reviews):**

| Sentiment | Count | % Share |
|---|---|---|
| ✅ Positive | 1,552 | **55.6%** |
| ❌ Negative | 949 | **34.0%** |
| ⚪ Neutral | 292 | **10.4%** |

**📂 6 Topic Segments & Distribution:**

| Topic | % of Reviews | Dominant Sentiment |
|---|---|---|
| 🌟 General Satisfaction | **48.0%** | Mostly Positive |
| 💳 Transaction & Refund Services | **22.3%** | Mixed → Negative |
| 🛎️ Customer Support | **12.6%** | Negative |
| 🚚 Delivery Services | 8.6% | Negative |
| 📱 App Features & Livestream | 6.1% | Mixed |
| 🔧 Technical Features | 2.4% | Negative |

**📈 Visualisations Produced:**
- 🥧 **Pie Chart** — Overall sentiment distribution (Positive / Negative / Neutral)
- 📊 **Horizontal Bar Chart** — Review count by topic
- 📊 **Stacked Bar Chart** — Sentiment mix broken down by topic

**🎯 VADER Validation Against Manual Labels:**

| Class | True Count | Correctly Predicted | Error Rate |
|---|---|---|---|
| ❌ Negative | 1,315 | 924 | 29.73% |
| ⚪ Neutral | 151 | 52 | **65.56%** 🚨 Highest |
| ✅ Positive | 1,327 | 1,185 | 10.70% |
| 🏆 **Overall Accuracy** | | | **77.37%** |

---

### 7️⃣ 🏷️ Sentiment Analysis — Supervised (ML)
> Training classifiers on manually labelled data for higher precision

**Data Split:** 80% Train (2,234 samples) · 20% Test (559 samples)

**3 Models Tested:**

| Model | Vectorisation | Approach |
|---|---|---|
| 📏 Logistic Regression | TF-IDF | Term frequency × importance weighting |
| 🔵 Naive Bayes | Count Vectorizer | Raw word frequency counts |
| 🧠 DistilBERT | Contextual Embeddings | Deep learning — understands word meaning in context |

**🏆 Model Performance Results:**

| Model | Accuracy | Negative F1 | Positive F1 | Neutral F1 |
|---|---|---|---|---|
| 📏 Logistic Regression | 87.48% | ~0.90 | ~0.90 | 0.39 |
| 🔵 Naive Bayes | 87.30% | good | good | **0.00** ❌ |
| 🧠 **DistilBERT** | **90.70%** ⭐ | **0.93** | **0.92** | 0.36 |

**Confusion Matrix Summary:**

| Model | Negative ✅ | Positive ✅ | Neutral ✅ |
|---|---|---|---|
| Logistic Regression | 243/263 | 230/266 | 15/30 |
| Naive Bayes | 241/263 | 248/266 | **0/30** ❌ |
| **DistilBERT** | **253/263** | **246/266** | **8/30** |

> 💡 **Why DistilBERT wins:** It tokenises text into *contextual embeddings*,
> understanding how words relate to each other, not just counting them. This was
> critical for Malaysian *Manglish* reviews where context completely changes meaning.

---

### 8️⃣ ⚖️ Comparison — VADER vs Supervised Models

| Dimension | 🤖 VADER (Unsupervised) | 🏷️ Supervised ML |
|---|---|---|
| Labels Required? | ❌ No | ✅ Yes |
| Accuracy | 77.37% 🟡 | Up to 90.70% 🟢 |
| Speed | ⚡ Instant | 🐢 Requires training |
| Neutral Detection | ❌ 65.56% error | 🟡 Partial (best: 0.39 F1) |
| Mixed-language handling | ❌ Struggles | ✅ DistilBERT handles well |
| Best use case | Quick brand health check | Precise classification & risk detection |

**Key Finding:**
> VADER overestimates positive sentiment by **~13%** compared to manual labels
> (55.6% vs 47.5%). Relying only on VADER would cause Shopee to **miss nearly
> 1 in 8 critical negative reviews** shows a dangerous blind spot for brand health monitoring.

---

### 9️⃣ 💬 Discussion — Key Themes

**What users LOVE about Shopee ✅**
- 💰 Wide product selection + competitive pricing
- 🎟️ Frequent vouchers and discount events
- 🚀 Fast order processing when SPX works correctly

**What users HATE about Shopee ❌**

| Issue | Theme | Severity |
|---|---|---|
| 📺 App defaults to Live & Video on launch | App UX / TikTok-ification | 🔴 High |
| 📦 SPX Express fake delivery attempts | Logistics Failure | 🔴 High |
| 🤖 AI chatbot gives copy-paste replies | Customer Support Wall | 🔴 High |
| 💸 Refund process takes weeks or months | Transaction & Refund | 🔴 High |
| 🌙 No native Dark Mode in 2026 | App Feature Gap | 🟡 Medium |

---

### 🔟 💡 Strategic Recommendations
> Based on sentiment findings and focused on **Social Listening Strategy**

| # | Recommendation | Problem It Solves |
|---|---|---|
| 1️⃣ | 🏠 **"Home Page Toggle"** — Let users choose their default landing page instead of forced Livestream | Stops loyalty erosion to Lazada & TikTok Shop |
| 2️⃣ | 📍 **GPS-Verified Photo System** — Mandatory proof for all "unsuccessful delivery" attempts | Eliminates fake delivery attempts by SPX Express |
| 3️⃣ | 🌙 **Native Dark Mode** — Simple UI update addressing the #1 General Satisfaction complaint | Improves the 48% "General Satisfaction" topic score |
| 4️⃣ | 👤 **Tiered Human Support** — Auto-escalate refunds > RM100 to human agents | Breaks the AI chatbot wall for high-value disputes |

---

### 🏁 Conclusion

> Shopee Malaysia is a market leader but its dominance is under pressure
> from **self-inflicted UX friction**, not competition.

- 🏆 **DistilBERT** is the recommended production model at **90.70% accuracy**
- 📊 **1,327 Positive vs 1,315 Negative** — sentiment is nearly perfectly split
- 🚨 The data shows users aren't leaving Shopee — they're just *frustrated* and being *ignored*
- 💡 The fix isn't a major rebuild — it's **listening to the data Shopee already has**

---

