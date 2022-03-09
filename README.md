The shared task on Lexical Semantic Change Discovery (LSCDiscovery) in Spanish will be carried out at the [3rd International Workshop on Computational Approaches to Historical Language Change 2022 (LChange'22)](https://languagechange.org/events/2022-acl-lchange/).

**You can participate in the competition following this [link](https://codalab.lisn.upsaclay.fr/competitions/2243).**

## Task description

The task will have two phases:
1. graded change discovery, and
2. binary change detection.


### Phase 1 (Graded Change Discovery)

Similar to Kurtyigit et al. (2021), we define the task of graded lexical semantic change
discovery as follows:

    Given a diachronic corpus pair C1 and C2, rank the intersection of their (content-word)
    vocabularies according to their degree of change between C1 and C2.


The participants will be asked to rank the set of content words (N, V, A) in the lemma vocabulary intersection of C1 and C2 according to their degree of semantic change between C1 to C2.
The true degree of semantic change of a target word *w* will be given by the Jensen-Shannon
distance (Donoso & Sanchez, 2017; Lin, 1991) between w’s word sense frequency distributions
in C1 and C2 (cf. Schlechtweg, McGillivray, Hengchen, Dubossarsky, & Tahmasebi, 2020) (Schlechtweg et al., 2020). 

The two word sense frequency distributions will be estimated via clustering of human semantic proximity judgments of word usage samples for w from C1 and C2 (Schlechtweg et al., 2020). Participants will be asked to predict a ranking of all target words according to their degree of semantic change where a higher rank means stronger change.
Participants’ predictions will not be evaluated on the full set of target words, as these would be
unfeasible to annotate, but on an (unpublished) random sample of ≈80 words from the full
set of target words. The predictions will be scored against the ground truth via Spearman’s
rank-order correlation coefficient (Bolboaca & Jäntschi, 2006).


### Phase 2 (Binary Change Detection)

Similar to Schlechtweg et al. (2020), we define binary change detection as follows:

    Given a target word *w* and two sets of its usages U1 and U2, decide whether *w* lost or
    gained senses from U1 to U2, or not.

<!-- Besides, in this subtask will be considered two more binary tasks, *gain vs no gain* and *loss vs no loss*. -->

The participants will be asked to classify a pre-selected set of content words (N, V, A) into two classes, 0 for no change and 1 for change. The true binary labels of word *w* will be inferred from *w*’s word sense frequency distributions
in C1 and C2 (see above). Participants' predictions are scored against the ground truth with the following metrics:
  - F1 (main metric)
  - Precision
  - Recall

The only difference compare to  Graded Change Discovery is that the target words correspond exactly to the hidden words on which we evaluate. Also, we will publish the annotated word usages (without annotations). Hence, participants can work with the exact annotated data.

For details on how word sense frequency distributions are inferred from the annotated data and how the change scores are calculated (including noise thresholds *n* and *k*) see the [WUG repository](https://github.com/Garrafao/WUGs).

Participants' submission files only need to include those values correponding to the obligatory tasks in order to get a valid submission.


## Optional tasks

**Graded Change Detection** subtask is defined similar to Graded Discovery. The only difference is that the target words correspond exactly to the hidden words on which we evaluate. Also, we will publish the annotated word usages (without annotations). Hence, participants can work with the exact annotated data. Participants will be scored with Spearman correlation.

**Sense Gain Detection** is similar to Binary Change Detection subtask. However, only words which gained (not lost) senses will receive label 1. Participants will be scored with F1, Precision and Recall.

**Sense Loss Detection** is similar to Binary Change Detection subtask. However, only words which lost (not gained) senses will receive label 1. Participants will be scored with F1, Precision and Recall.

**COMPARE** subtask asks participants to predict the inverse DURel COMPARE metric (Schlechtweg et al., 2018). This metric is defined as the average of human semantic proximity judgments of usages for *w* between C1 and C2.[^1] Participants will be scored with Spearman correlation.

[^1]: Contrary to the original metric we first take the median of all annotator judgments for each usage pair and then average these values. For details see the [WUG repository](https://github.com/Garrafao/WUGs). Participants will be scored with Spearman correlation.


## Submission format

Participants will submit a Zip file named *answer* for both phases with the following structure:
	
	answer/
		submission.tsv

The format of *submission.tsv* file for the *pase 1* is defined as follows:
	
	word	change_graded   COMPARE

	word1	score           score
	...     ...              ...   

Note that *change_graded* column corresponds to the obligatory task, and the other column labeled *COMPARE* corresponds to the other optional task. 

It's important to say that the binary subtasks were excluded from this phase because the participants need to use the full corpora for discovery and we don't know how well the binary scores obtained on small annotated samples generalize the full corpora.

The format of *submission.tsv* for the *phase 2* file is defined as follows:

	word	change_binary	change_binary_gain	change_binary_loss	change_graded	COMPARE
	word1	0|1    		0|1    			  0|1    		  score    	score
	...    ...    		...    			  ...    		    ...    	...

Note that *change_binary* column correponds to the obligatory task, and the other columns correspond to the other optional tasks.


## Baselines


Starting kit for both phases of the shared task is provided, you can download it from [here](https://github.com/fdzr/lscdiscovery/files/8106552/starting_kit.zip). 

The code draws mainly from the [LSCDetection repository](https://github.com/Garrafao/LSCDetection).

Under `code/` is provided an implementation of two baselines for both phases of the shared task:
1. skip-gram negative sampling + orthogonal procrustes + cosine distance.
2. normalized frequency difference (FD)

For more details, please read de the `Readme` file inside the starting_kit folder.

**The submissions will be made through Codalab, following this [link](https://codalab.lisn.upsaclay.fr/competitions/2243)**.


## Corpora

In this shared task there are two corpora available, corresponding to different time periods.

| Corpus | Time period  | Size|
| ------ | -----------  | ----|
| Old corpus| 1810 - 1906 | ~13 M|
|Modern corpus| 1994 - 2020 | ~ 22M|

**Old corpus** was created using different sources freely available from [Project Gutenberg](https://www.gutenberg.org/browse/languages/es).

**Modern corpus** was created using different sources available from the [OPUS project](https://opus.nlpl.eu/). 

Each corpus contains four version of the original dataset (raw, tokenized, lemmatized and post-tagged).

Annotated development data with sampled uses, clusterings, change scores, visualizations, and more stats are available [here](https://zenodo.org/record/6300105). 

## Target words

- Development Phase 1 (Graded Discovery): The [target words](https://github.com/fdzr/lscdiscovery/files/8138960/population_restricted.txt) correspond to the content word (adjectives, adverbs, verbs and nouns) vocabulary intersection between the two lemmatized corpora above a frequency threshold. The frequency threshold is 40 and 73 for corpus 1 and 2 respectively. Uploaded submissions will be scored against 20 hidden words from the full target word list which were annotated for semantic change.
- Development Phase 2 (Binary Detection): The [target words](https://github.com/fdzr/lscdiscovery/files/8209314/target_words_development_phase2.txt) correspond to the 20 hidden words from Phase 1. Participants get access to the annotated usages (20+20 from each corpus), human annotations and gold change scores for development. Uploaded submissions will be scored against the 20 target words. The evaluation script for phase 2 ignores additional words other than the target words as input in phase 2. 
- Evaluation Phase 1 (Graded Discovery): The [target words](link) correspond to the content word (adjectives, adverbs, verbs and nouns) vocabulary intersection between the two lemmatized corpora above a frequency threshold. The frequency threshold is 40 and 73 for corpus 1 and 2 respectively. Uploaded submissions will be scored against 60 hidden words from the full target word list which were annotated for semantic change.
- Evaluation Phase 2 (Binary Detection): The [target words](link) correspond to the 60 hidden words from Phase 1. Participants get access to the annotated usages (20+20 from each corpus). Uploaded submissions will be scored against the 60 target words. The evaluation script for phase 2 ignores additional words other than the target words as input in phase 2.

<!--  -->


## Lemmatizer-related issues

In this research, spacy was used as a lemmatizer for the Spanish text. This library did not produce good results for some words, especially those from the old corpus. 

**Example**:
    "Decidióse ésta por Teresa la expósita, y así se vio a la vagamunda tomar bajo su amparo a la pobre desheredada como ella."

**After running the lemmatizer**:
    Decidióse este por Teresa el expósita , y así él ver a el vagamunda tomar bajo su amparo a el pobre desheredado como él .

As can be seen, the lemma of the word *Decidióse* was not found, nor was the word converted to lowercase.

**Note**: Spacy version 3.1.1 was used and the Spanish model used was es_core_news_md (3.1.0).


## Papers

Shared task participants are invited to submit a system description paper to be included in the proceedings of LChange'22. Papers will have a maximum length of 4 pages (excluding acknowledgements/bibliography/appendices). System description papers will be peer-reviewed, so review is mandatory for all who submit a paper.


## Important dates

- **February 28**: Development phase 1 (Discovery) starts. It will be published the annotated data for development.
- **March 9**: Development phase 2 (Detection) starts.
- **March 14**: Evaluation phase 1 (Discovery) starts. 
- **March 19**: Evaluation phase 2 (Detection) starts.
- **March 26**: Results are announced.
- **April 1 (preliminary)**: Paper submission deadline.
- **April 6 (preliminary)**: Notification of paper acceptance
- **April 10 (preliminary)**: Camera-ready papers due


## Organizers

- Frank D. Zamora-Reina  -  fzamora dot reina at gmail dot com
- Felipe Bravo-Marquez   -  fbravo at dcc dot uchile dot cl
- Dominik Schlechtweg    -  schlecdk at ims dot uni-stuttgart dot de


### Contact
Communication between the participants and the organizers will take place on a Telegram channel. Write to Frank Zamora to access our channel.


### Bibibliography

```
@inproceedings{kurtyigit-etal-2021-lexical,
    title = "Lexical Semantic Change Discovery",
    author = "Kurtyigit, Sinan  and
      Park, Maike  and
      Schlechtweg, Dominik  and
      Kuhn, Jonas  and
      Schulte im Walde, Sabine",
    booktitle = "Proceedings of the 59th Annual Meeting of the Association for Computational Linguistics and the 11th International Joint Conference on Natural Language Processing (Volume 1: Long Papers)",
    month = aug,
    year = "2021",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    abstract = "While there is a large amount of research in the field of Lexical Semantic Change Detection, only few approaches go beyond a standard benchmark evaluation of existing models. In this paper, we propose a shift of focus from change detection to change discovery, i.e., discovering novel word senses over time from the full corpus vocabulary. By heavily fine-tuning a type-based and a token-based approach on recently published German data, we demonstrate that both models can successfully be applied to discover new words undergoing meaning change. Furthermore, we provide an almost fully automated framework for both evaluation and discovery.",
}

@inproceedings{schlechtweg-etal-2020-semeval,
    title = "{S}em{E}val-2020 {T}ask 1: {U}nsupervised {L}exical {S}emantic {C}hange {D}etection",
    author = "Schlechtweg, Dominik and McGillivray, Barbara and Hengchen, Simon and Dubossarsky, Haim and Tahmasebi, Nina",
    booktitle = {{Proceedings of the 14th International Workshop on Semantic Evaluation}},
    year = "2020",
    address = "Barcelona, Spain",
    publisher = "Association for Computational Linguistics",
    url = {https://www.aclweb.org/anthology/2020.semeval-1.1/},
    slides = {publications/201027-semeval-slides.pdf},
}

@inproceedings{DonosoS17,
  author    = {Gonzalo Donoso and
               David Sanchez},
  title     = {Dialectometric analysis of language variation in Twitter},
  booktitle = {Proceedings of the Fourth Workshop on {NLP} for Similar Languages,
               Varieties and Dialects},
  pages     = {16--25},
  year      = {2017},
  address      = {Valencia, Spain}
}

@article{Lin91divergencemeasures,
    author = {Jianhua Lin},
    title = {Divergence measures based on the Shannon entropy},
    journal = {IEEE Transactions on Information theory},
    year = {1991},
    volume = {37},
    pages = {145--151}
}

@article{bolboaca2006pearson,
  title={Pearson versus Spearman, Kendall’s tau correlation analysis on structure-activity relationships of biologic active compounds},
  author={Bolboaca, Sorana-Daniela and J{\"a}ntschi, Lorentz},
  journal={Leonardo Journal of Sciences},
  volume={5},
  number={9},
  pages={179--200},
  year={2006}
}
```


### Acknowledgements
This task is funded by ANID FONDECYT grant 11200290, U-Inicia VID Project UI-004/20 and ANID - Millennium Science Initiative Program - Code ICN17 002.

This task also was supported by  [SemRel Group (DFG Grants SCHU 2580/1 and SCHU 
2580/2)](https://www.ims.uni-stuttgart.de/en/institute/team/Schulte-im-Walde-00001/).
