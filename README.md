# Evalita2026_MultiPRIDE

Identity, Toxicity, or Complexity? A Language-Specific Feature Selection Approach to Reclamatory Intent Detection

Houman Rajabi · Fatemeh Ghavidel · Kourosh Ghahremani

Paper submitted to [EVALITA 2026](https://www.evalita.it/2026/) , Bari, Italy.

## Research Problem

The central objective  was to **distinguish between offensive and reclamatory uses of slurs in LGBTQ+ discourse** in a multilingual setting ( Italian, Spanish, and English).

In standard NLP systems, slurs are treated as inherently **hate speech and toxic lexical items**. 

However, within marginalized communities, the same terms may be reappropriated to express **solidarity, pride, or identity affirmation**. 

The meaning of these expressions depends on **who's speaking and why, discourse context, and sociolinguistic cues**. 

This is **the reclamation paradox**: the word is toxic, but the intent is empowering.

When models treat slur words as offensive, they may **misinterpret in-group reclamation** and **produce false positives** and **silences the community**.



## Methodology

We implemented a hybrid modeling framework with two parallel components:

- **Stream A:** Monolingual BERT encoders (bert-base-uncased, dccuchile/bert-base-spanish-wwm-uncased, dbmdz/bert-base-italian-uncased) for contextual semantic representations.
  
- **Stream B:** 61 handcrafted sociolinguistic features, including morphosyntactic metrics, sentiment–toxicity dynamics, and identity markers.

A Random Forest model was used to rank features independently for each language, enabling language-specific feature selection.



## Results

The Italian model achieved first place in the official [ranking](https://multipride-evalita.github.io/rankings/). Spanish and English performances remained below baseline.

Findings indicate that language-specific feature selection is effective when sociolinguistic signals are structurally salient (e.g., syntactic complexity in Italian), but less effective when reclamation relies on implicit pragmatic cues.

In English, reclaimed usage proved particularly difficult to model. Low recall suggests that surface-level lexical and identity features are insufficient to capture irony, role ambiguity, and socially situated meaning.




## Cross-Linguistic Insight

Reclamation is language- and culture-specific; each language relies on different sociolinguistic cues.

- **Italian:** Reclamation often appears in longer, structured, argumentative texts that explicitly defend identity.
- 
  *Failure mode:* the model sometimes confuses formal reports of hate speech with reclamation, learning a writing style rather than true intent.

- **Spanish:** Reclamation frequently co-occurs with community markers (hashtags, LGBTQ+ terms) that mitigate perceived toxicity.
- 
  *Failure mode:* when a slur appears at the beginning of a sentence, its positional salience may override supportive context.

- **English:** Reclamation tends to rely on implicit irony and in-group signaling that surface features struggle to capture.
- 
  *Failure modes:* models misinterpret first-person pronouns (confusing victims with reclaimers) or over-weight the toxicity of the slur itself.
