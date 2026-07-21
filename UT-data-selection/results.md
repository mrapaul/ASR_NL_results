[**Back to homepage**](../index.md)

<h2>Training Data Selection for Low-Resource ASR Adaptation</h2>

This study is part of the Ph.D. of Dragos Balan at University of Twente. This is a preliminary version of the page, with more detailed information about the data and setup to be published later. As soon as the accompanying conference paper submission gets accepted/rejected, a link will also be published.

The evaluation has been conducted for 2 use-cases: **non-native** and **children** speakers of Dutch. JASMIN-CGN is used for training and evaluation for both use cases, whereas CHOREC is used as an out-of-corpus evaluation set only for the children's speech use-case.

For more details about JASMIN-CGN, please click [here](/OH-SMArt/JASMIN/jasmin.md).

We evaluate our methods using 3 fixed budgets to be met when selecting training data: 5, 10, and 20 hours of speech. We additionally test the performance of models with unrestricted data budgets: the pre-trained version of the ASR model, fine-tuning using the full JASMIN-CGN corpus (excluding the dev and test sets), and fine-tuning using only what is labelled in the corpus as being non-native or children speech respectively.

We evaluate 2 types of speech embeddings extracted using self-supervised learning models: **phonetic** embeddings (represented in the matrix as **XLSR**) and **speaker** embeddings (represented in the matrix as **ECAPA**). In terms of selection methods, 3 have been compared, all based on cosine similarity:
- MaxSim: using global maximum cosine similarity ranking of candidate embeddings to any of the target speaker centroids;
- MMR: Maximal Marginal Relevance, a criterion optimizing diversity of the selection with the relevance of the selected samples to our target space (see the paper [Which Data Matter? Embedding-Based Data Selection for Speech Recognition](https://arxiv.org/abs/2603.05819)).
- TSCDS: Target Speaker Coverage Data Selection, the novel approach proposed where we allocate an equal duration cap to each target speaker centroid and select the highest-scoring
candidates per speaker, based on cosine similarity.

<br>

Here is the matrix with the WER results observed for the **non-native speakers** use case:

|Method\Budget|5 hours|10 hours|20 hours|
|---|---|---|---|
|Random|30.03% ± 1.63%|23.17% ± 1.10%|22.58% ± 0.64%|
|Metadata|29.15% ± 0.73%|22.90% ± 1.97%|22.21% ± 1.02%|
|XLSR-MaxSim|27.47%|28.68%|20.05%|
|XLSR-MMR|30.19%|20.67%|20.23%|
|XLSR-TSCDS|**20.93%**|22.25%|**19.27%**|
|ECAPA-MaxSim|33.34%|23.10%|19.67%|
|ECAPA-MMR|35.90%|23.52%|19.72%|
|ECAPA-TSCDS|25.21%|**20.04%**|21.91%|

|Method\Budget|Amount of train|JASMIN test|
|---|---|---|
|Pre-trained ASR|0 hours|38.44%|
|JASMIN Non-natives|25 hours|19.00%|
|Full JASMIN-CGN|71 hours|**18.17%**|

<br>

The matrix with the WER results observed for the **children speakers** use case:

|Method\Budget||JASMIN test|||CHOREC||
|---|---|---|---|---|---|---|
||5 hours|10 hours|20 hours|5 hours|10 hours|20 hours|
|Random|17.56% ± 0.56%|16.60% ± 1.30%|15.91% ± 0.63%|20.86% ± 3.00%|18.65% ± 3.75%|19.45% ± 3.12%|
|Metadata|16.98% ± 0.97%|14.57% ± 0.42%|**14.00% ± 0.77%**|17.22% ± 2.88%|**14.35% ± 0.39%**|14.41% ± 0.96%|
|XLSR-MaxSim|29.87%|19.79%|15.46%|23.40%|22.99%|**14.28%**|
|XLSR-MMR|22.37%|19.15%|15.82%|26.85%|18.71%|16.91%|
|XLSR-TSCDS|18.55%|**13.91%**|14.40%|16.68%|15.36%|17.05%|
|ECAPA-MaxSim|22.85%|15.39%|**14.08%**|18.77%|21.21%|14.57%|
|ECAPA-MMR|19.99%|15.53%|14.33%|**15.44%**|23.36%|14.74%|
|ECAPA-TSCDS|**14.58%**|15.76%|15.61%|21.48%|16.03%|15.52%|

|Method\Budget|Amount of train|JASMIN test|CHOREC|
|---|---|---|---|
|Pre-trained ASR|0 hours|23.54%|17.54%|
|JASMIN Children|33 hours|11.00%|**10.95%**|
|Full JASMIN-CGN|69 hours|**10.34%**|**10.95%**|

<!-- ### Preprocessing, setup, and postprocessing
For more details, click [here](./setup.md). -->