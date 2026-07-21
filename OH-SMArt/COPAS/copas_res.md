[**Back to homepage**](../../index.md)

<h2>Dutch <b>C</b>orpus <b>O</b>f <b>PA</b>thological and Normal <b>S</b>peech (COPAS) </h2>

The Dutch <b>C</b>orpus <b>O</b>f <b>PA</b>thological and Normal <b>S</b>peech (COPAS) contains data collected from speakers who suffer from various pathological speech disorders, as well as speakers without any speech disorders or "normal" speakers.

The evaluation has been conducted per speaker group. The speaker groups are the following:
- Normal (N)
- Dysarthria (D)
- Hearing impairment (H)
- Laryngectomy (L)
- Cleft (C)
- Voice disorder (V)

The type of speech varies between plain read-out texts to carefully selected words and sentences that test the intelligibility or naturalness of speech. Within the dataset, these can be found under Dutch intelligibility assessment (DIA), Text (T), Text Marloes (TM), Sentence 1 (S1), and Sentence 2 (S2).

For more details about the corpus, click [here](https://taalmaterialen.ivdnt.org/wp-content/uploads/documentatie/copas_manual.pdf).

<br>

Here is an **initial** matrix with **WER** results of the baseline model, Kaldi_NL, as well as different end-to-end models tested on this corpus:

|Model\Dataset|Normal|Dysarthria|Hearing imp.|Laryngectomy|Cleft|Voice dis.|
|---|---|---|---|---|---|---|
|[Kaldi_NL](https://github.com/opensource-spraakherkenning-nl/Kaldi_NL)|47.4%|78.0%|78.7%|86.8%|94.8%|56.3%|
|[faster-whisper v2](https://github.com/SYSTRAN/faster-whisper/)|15.6%|**44.7%**|51.8%|**44.8%**|64.0%|30.3%|
|[faster-whisper v3*](https://github.com/SYSTRAN/faster-whisper/)|54.6%|75.2%|74.7%|88.4%|127.2%|72.0%|
|[faster-whisper turbo](https://github.com/SYSTRAN/faster-whisper/)|21.0%|46.9%|50.6%|52.7%|65.9%|23.2%|
|[**faster-whisper v2 w/ VAD**](https://github.com/SYSTRAN/faster-whisper/)|**15.4%**|45.9%|**45.7%**|51.4%|63.4%|**18.1%**|
|[faster-whisper v3 w/ VAD*](https://github.com/SYSTRAN/faster-whisper/)|53.5%|75.0%|71.5%|71.0%|118.1%|68.1%|
|[faster-whisper turbo w/ VAD](https://github.com/SYSTRAN/faster-whisper/)|20.0%|46.9%|49.0%|58.4%|**60.7%**|23.2%|
|[XLS-R FT on Dutch](https://huggingface.co/jonatasgrosman/wav2vec2-xls-r-1b-dutch)|38.3%|64.7%|70.5%|73.7%|96.7%|50.4%|
|[MMS - 102 languages](https://huggingface.co/facebook/mms-1b-fl102)|39.3%|71.5%|76.4%|80.5%|96.5%|50.4%|
|[MMS - 1162 languages](https://huggingface.co/facebook/mms-1b-all)|34.4%|65.8%|75.3%|77.4%|97.1%|56.7%|

\* The timestamps of Whisper large-v3 do not align well with the reference. Thus, there is a significant number of insertions and deletions in cases where the word predicted was correct. Therefore, **the final matrix with WER results** after manually re-aligning timestamps of Whisper large-v3 can be found below:

|Model\Dataset|Normal|Dysarthria|Hearing imp.|Laryngectomy|Cleft|Voice dis.|
|---|---|---|---|---|---|---|
|[Kaldi_NL](https://github.com/opensource-spraakherkenning-nl/Kaldi_NL)|47.4%|78.0%|78.7%|86.8%|94.8%|56.3%|
|[faster-whisper v2](https://github.com/SYSTRAN/faster-whisper/)|15.6%|**44.7%**|51.8%|**44.8%**|64.0%|30.3%|
|[faster-whisper v3](https://github.com/SYSTRAN/faster-whisper/)|20.1%|49.4%|46.3%|52.7%|69.6%|29.5%|
|[faster-whisper turbo](https://github.com/SYSTRAN/faster-whisper/)|21.0%|46.9%|50.6%|52.7%|65.9%|23.2%|
|[**faster-whisper v2 w/ VAD**](https://github.com/SYSTRAN/faster-whisper/)|**15.4%**|45.9%|**45.7%**|51.4%|63.4%|**18.1%**|
|[faster-whisper v3 w/ VAD](https://github.com/SYSTRAN/faster-whisper/)|19.8%|50.1%|47.0%|54.7%|65.5%|26.8%|
|[faster-whisper turbo w/ VAD](https://github.com/SYSTRAN/faster-whisper/)|20.0%|46.9%|49.0%|58.4%|**60.7%**|23.2%|
|[XLS-R FT on Dutch](https://huggingface.co/jonatasgrosman/wav2vec2-xls-r-1b-dutch)|38.3%|64.7%|70.5%|73.7%|96.7%|50.4%|
|[MMS - 102 languages](https://huggingface.co/facebook/mms-1b-fl102)|39.3%|71.5%|76.4%|80.5%|96.5%|50.4%|
|[MMS - 1162 languages](https://huggingface.co/facebook/mms-1b-all)|34.4%|65.8%|75.3%|77.4%|97.1%|56.7%|

<br>

A matrix with the **time** spent in total by each model **to evaluate** the respective subset will be published in the near future.

### Preprocessing, setup, and postprocessing
For more details, click [here](./copas_setup.md).
