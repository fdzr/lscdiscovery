The shared task on Lexical Semantic Change Discovery (LSCDiscovery) in Spanish will be carried out at the [3rd International Workshop on Computational Approaches to Historical Language Change 2022 (LChange'22)](https://languagechange.org/events/2022-acl-lchange/).

## Description task

The task will have two phases:
1. discovery, and
2. detection.


### Phase 1

Similar to Kurtyigit et al. (2021), we define the task of graded lexical semantic change
discovery as follows:

    Given a diachronic corpus pair C1 and C2, rank the intersection of their (content-word)
    vocabularies according to their degree of change between C1 and C2.


The participants will be asked to rank the set of content words (N, V, A) in the lemma vocabulary intersection of C1 and C2 according to their degree of semantic change between C1 to C2.
The true degree of semantic change of a target word w will be given by the Jensen-Shannon
distance (Donoso & Sanchez, 2017; Lin, 1991) between w’s word sense frequency distributions
in C1 and C2 (cf. Schlechtweg, McGillivray, Hengchen, Dubossarsky, & Tahmasebi, 2020). 

The two word sense frequency distributions will be estimated via human annotation of word usage
samples for w from C1 and C2. Participants will be asked to predict a ranking of all target
words according to their degree of semantic change where a higher rank means stronger change.
Participants’ predictions will not be evaluated on the full set of target words, as these would be
unfeasible to annotate, but on an (unpublished) random sample of ≈100 words from the full
set of target words. The predictions will be scored against the ground truth via Spearman’s
rank-order correlation coefficient (Bolboaca & J ̈antschi, 2006)


### Phase 2

This phase contains two subtasks:
  1. Binary Change Detection, and
  2. Graded Lexical Semantic Change.


**Binary Change Detection** subtask is defined similar to Schlechtweg et al. (2020), as follows:

    Given a target word w and two sets of its usages U1 and U2, decide whether w lost or
    gained senses from U1 to U2, or not.

Besides, in this subtask will be considered two more binary tasks, *gain vs no gain* and *loss vs no loss*.

**Change vs no change** will be considered the primary binary task and the metrics to be reported are:
  - F1 (main metric)
  - Precision
  - Recall

The other binary tasks *gain vs no gain* and *loss vs no loss* will be considered secondary tasks and the metrics to be reported are:
 - F1
 - Precision
 - Recall


**Graded lexical Semantic Change** subtask is defined similar to the previous phase. The participants will be asked to rank a set of target words instead of the set of content words in the lemma vocabulary intersection.




<!-- **Binary Change Detection** subtask is a classification task that is a mix of a binary and multi-label problem,
with 3 possible labels (change/no change, gain sense/no gain sense, loss/no loss). For this task, participants are asked
to provide predictions only for the annotated target words. The task has 3 possible labels, but the main evaluation metric
will be F1 and only change vs no change will be considered, similar to Schlechtweg et al. (2020), Precision and Recall
will also be reported. For gain sense vs no gain sense and loss vs no loss will be considered as experimental tasks and
F1, Recall and Precision will be reported. -->


<!-- **Hard Detection** subtask is a classification task which is a mixture of a binary and multi-label problem,
with 3 possible labels (change/no change, gain sense/no gain sense, loss/no loss). For this task, participants are asked to provide predictions only for the annotated target words. The task has 3 possible labels but the main evaluation metric will only consider change vs no change similar to Schlechtweg et al. (2020), 3-level classification performance will be considered as a secondary metric. The true change labels will be derived straightforwardly from the annotated word sense frequency distributions as described above. We will publish the annotated usages without human annotation as model input. Predictions will be scored against the ground truth via F1, Precision and Recall.  -->

<!-- (no change/sense gain/sense loss) -->


<!-- Similar to Schlechtweg et al. (2020), we define the task of binary change detection as follows:
    
    Given a target word w and two sets of its usages U1 and U2, decide whether w lost or
    gained senses from U1 to U2, or not.


For this task, participants are asked to provide binary predictions only for the annotated target
words. The true binary change labels will be derived straightforwardly from the annotated word
sense frequency distributions as described above. We will publish the annotated usages without
human annotation as model input. Predictions will be scored against the ground truth via F1,
Precision and Recall. -->


## Papers

Shared task participants are invited to submit a system description paper to be included in the proceedings of LChange'22. Papers will have a maximum length of 4 pages (excluding acknowledgements/bibliography/appendices). System description papers will be peer-reviewed, so review is mandatory for all who submit a paper.


## Important dates

- **January 10**: The shared task is announced. Practice phase starts.
- **January 21**: Development phase starts. Development set is released.
- **January 30**: Evaluation phase starts. Corpora and target words (depending on the subtask) are released.
- **February 20**: Evaluation phase and submission period ends.
- **February 22**: Shared task results announcenment.
- **March 14**: Paper submission deadline
- **March 29**: Notification of paper acceptance
- **April 10**: Camera-ready papers due


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
