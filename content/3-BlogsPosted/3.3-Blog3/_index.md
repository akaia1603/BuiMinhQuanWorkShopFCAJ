---
title: "Blog 3"
date: 2026-09-15
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# EXTRACT GRANULAR SENTIMENT IN TEXT WITH AMAZON COMPREHEND TARGETED SENTIMENT

Extracted from an AWS Machine Learning Blog announcement of **Amazon Comprehend Targeted Sentiment** — a feature that goes beyond whole-document sentiment to identify the sentiment expressed towards each specific entity (person, product, brand, attribute) mentioned in the text.

### Key Concepts:

- **Amazon Comprehend** is a fully managed NLP service that requires no ML expertise, scales to large data volumes, and exposes simple APIs for entities, key phrases, sentiment, document classification, and language.
- **Traditional (full) sentiment:** returns one overall label — `positive`, `negative`, `neutral`, or `mixed` — for the whole document. Getting entity-level insight previously required workarounds such as chunking the text into logical blocks.
- **Targeted Sentiment:** identifies **co-reference groups of mentions** that refer to the same real-world entity, returns the sentiment per mention and per entity group, and classifies each entity against a pre-determined entity list.
- **Rich output:** each result includes `Entities`, `Mentions`, `DescriptiveMentionIndex`, `GroupScore`, `Text`, `Type`, `Score`, `MentionSentiment`, `Sentiment`, `SentimentScore`, plus `BeginOffset`/`EndOffset` for locating mentions in the text.

### Typical Use Cases:

- Marketing teams track sentiment toward their brands, campaigns, or feature launches on social media over time.
- E-commerce merchants understand which specific product attributes were best- or worst-received by customers.
- Contact centers mine call transcripts for escalation issues and monitor customer experience; restaurants and hotels turn broad ratings into rich descriptions of good and bad experiences.

### How It Works:

Create an **Analysis job** in the Amazon Comprehend console with *Analysis type = Targeted sentiment*, point it at the text input in **Amazon S3**, and consume the JSON result — entity groups, each entity's sentiment, and confidence scores — directly from the API.

---

### Architecture/Feature Diagram:

![Amazon Comprehend Targeted Sentiment](/images/3-BlogsPosted/blog3.png)

---

### Links and References:

- **Reference Article:** [Extract granular sentiment in text with Amazon Comprehend Targeted Sentiment](https://aws.amazon.com/blogs/machine-learning/extract-granular-sentiment-in-text-with-amazon-comprehend-targeted-sentiment/)