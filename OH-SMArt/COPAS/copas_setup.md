[**Go back**](./copas_res.md)

## COPAS setup

### Postprocessing

Whisper v3 with or without VAD outputted misaligned timestamps for each word. Thus, there were a significant number of insertions and deletions instead of correct words across all subsets for Whisper large-v3. This was fixed by adjusting the timestamps manually by adding **250ms** for both the start and end timestamps for each word in the transcript. Both results, before and after realignment, are presented, for transparency.

Aside from that, there are other steps applied, such as normalization of numbers and characters or variations of different words that are acceptable spellings in the context of evaluation. For more details, check the [ASR-NL-benchmark](https://github.com/opensource-spraakherkenning-nl/ASR_NL_benchmark) repository, where details about the hypothesis/reference files format can also be found.