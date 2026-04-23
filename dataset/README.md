# Predicting the Memorability of Brand Slogans

## Dataset – Codebook

This dataset folder contains memorability scores, memorability factors, and embeddings for brands and slogans, enabling prediction of cued recall and recognition memory performance. The memorability factors include measures from human ratings, natural language processing derived features, and large language model-derived features across multiple memorability dimensions.

The slogan data is in three files: 

- final_dataset_raw.csv

- final_dataset_imputed_z_and_embeddings.csv

- level1_mean_z.csv

In the first two files the slogan is in column 'index' and the brand in column 'brand'. The file level1_mean_z.csv has the same order of slogans as in the first two files.

The file final_dataset_raw.csv contains the memorability factor measurements for each slogan from a combination of human ratings and natural language processing (some of which require a large language model). 

The column names include "(HR)" if a measure is from human rating studies or RA coders, "(NLP)" if the measure is computed using natural language processing, and "(LLM)" if the measure required a large language model. Note that some of the non-human measures have missing data.

The file final_dataset_imputed_z_and_embeddings.csv contains imputed values for the missing data. All factors were z-scored after any necessary imputation.

The file level1_mean_z.csv contains the 25 factor values, which are obtained by taking the mean of the factor's measures. A dictionary given at the end of this codebook maps the columns to the memorability factors. 

### final_dataset_imputed_z_and_embeddings.csv

Contains the data needed to train predictive models of memorability:

#### Memorability measures 

The same column names as **final_dataset_raw.csv**. These columns have now been z-scored with missing data imputed.

#### Dependent variables for the recall memory task

• **sum_correct_recall** — Number of times the slogan was correctly recalled.

• **sum_incorrect_recall** — Number of times the slogan was not correctly recalled.

• **recall_percentage** — Proportion of recall attempts in which the slogan was correctly recalled.

#### Dependent variables for the recognition memory task

• **hit_count** — Number of correct "old" responses when the slogan was old.

• **false_alarm_count** — Number of incorrect "old" responses when the slogan was new.

• **correct_rejection_count** — Number of correct "new" responses to new slogans.

• **miss_count** — Number of "new" responses to old slogans.

• **hit_rate** — hit_count / total_old.

• **false_alarm_rate** — false_alarm_count / total_new.

• **correct_rejection_rate** — correct_rejection_count / total_new.

• **miss_rate** — miss_count / total_old.

• **overall_accuracy** — Proportion of all recognition decisions that are correct.

• **hits-fas** — Raw hits minus false alarms.

• **d_prime** — Signal detection sensitivity index.

• **accuracy_correct** — Number of correct responses.

• **accuracy_incorrect** — Number of incorrect responses.

#### Brand-Level Popularity & Fame from YouGov

• **fame** — Brand fame score from YouGov.

• **popularity** — Brand popularity score from YouGov.

#### Embeddings

The 1536 dimensional representation of the slogans and brands using Ada embeddings. These are given in **ada_embeddings_no_** and **brand_embeddings_ada_embedding_no_**.

## Dictionary mapping column names to memorability factors

```python
factors = {
	'frequency': ["Frequency (NLP)"],
	'length': ['Length'],
	'arousal': ['Arousal (NLP)', "Arousal (HR)"],
	'valence': ["Valence (NLP)", 'Valence (HR)'],
	'dominance': ['Dominance (NLP)', "Dominance (HR)"],
	'concreteness': ['Concreteness (NLP)', "Concreteness (HR)"],
	'humor': ['Humor (NLP)', "Humor (HR)"],
	'imageability': ['Imageability (NLP)', "Imageability (HR)"],
	'prevalence': ['Prevalence (NLP)'],
	'readability': ['Automated Readability Index (NLP)', 'Flesch Reading Ease (NLP)',
                	'Flesch Kincaid Grade Level (NLP)', 'Coleman Liau Index (NLP)',
                	'Type Token Ratio (NLP)'],
	'surprise': ['Surprise (NLP)'],
	'pronouns': ['Pronoun We (HR)', 'Pronoun You (HR)'],
	'creativity': ['Creativity (HR)'],
	'liking': ['Liking (HR)'],
	'brand fit': ['Slogan Brand Personality Fit (HR)', 'Slogan Brand Functional Fit (HR)',
             	'Slogan Brand Fit 1 (LLM)', 'Slogan Brand Fit 2 (LLM)'],
	'distinctiveness': ['Distinctiveness in General (HR)', 'Distinctiveness Within Category (HR)',
                   	'Distinctiveness (LLM)', 'Closest Semantic Density (LLM)',
                   	'Closest Slogan Similarity (LLM)'],
	'closest brand similarity': ['Closest Brand Similarity (LLM)'],
	'wordplay': ['Wordplay (HR)'],
	'metaphor': ['Metaphor (HR)'],
	'alliteration': ['Alliteration (HR)'],
	'hyperbole': ['Hyperbole (HR)'],
	'age of acquisition': ['Age of Acquisition (NLP)'],
	'ease_of_spelling': ['Ease of Spelling (LLM)'],
	'phonological': ['Phonological Neighborhood Size (NLP)', 'Phonological Levenshtein Distance (NLP)'],
	'orthographic': ['Orthographic Neighborhood Size (NLP)', 'Orthographic Levenshtein Distance (NLP)']
}
```
