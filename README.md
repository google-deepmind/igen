# igen

This is the dataset collected as part of the project described in Help Me Write
a Story: Evaluating LLMs' Ability to Generate Writing Feedback.

## Usage

This repository contains two sets of data: `generated_feedback.jsonl` and `human_ratings.jsonl`.

- `generated_feedback.jsonl`: The full set of generated feedback from all
  models. Each entry in the dataset contains the following fields:
    - `story_id`: An ID indicating which original story the input story is based
    on
    - `noise`: The corruption method that was applied to the original story
    - `prompt`: The prompt type that was used to generate the feedback
    - `nshot`: Whether it was a zeroshot or twoshot prompt
    - `model`: The model that generated the feedback
    - `story`: The input story
    - `gold_story`: The original story (before corruption)
    - `feedback`: The generated feedback
    - `example_id`: A unique identifier for the piece of generated feedback
    - various automatic metrics: The remaining fields are automatic metrics describing the feedback

- `human_ratings.jsonl`: A subset of the generated feedback that has human annotations. In addition to the above fields, it contains:
    - `sanity`, `is-perfect-as-is`, `perfect-agree`, `correctness`, `error-detection`, `specificity`, `relevance`: The scores for the multiple choice questions from the human evaluation (aggregated over 3 annotators). See section 6.1 in the paper for a full description of each dimension and figure 4 for the possible paths through the questions. (Note: `is-perfect-as-is` is referred to as "feedback-type" in the paper.)
    <!--- - `free_resp`: A list with the human-authored feedback for the story from each annotator --->

> Here's an example of an entry from `human_ratings.jsonl`
> ```json
> {
>   "story_id": 209,
>   "noise": "random_sentence_swap",
>   "prompt": "one_sentence",
>   "nshot": "zeroshot",
>   "model": "gemma9b",
>   "story": "Thankfully, we solved it in the end. I was stuck for hours with this problem, but Sarah came by, and we could brainstorm together.",
>   "gold_story": "I was stuck for hours with this problem, but Sarah came by, and we could brainstorm together. Thankfully, we solved it in the end.",
>   "feedback": "The sentence lacks a clear subject for the \"we solved it\" action, making it slightly ambiguous.",
>   "story_length_num_characters_all": 95,
>   "story_length_num_words": 18,
>   "story_length_num_trigrams": 16,
>   "story_length_num_sentences": 1,
>   "story_length_num_paragraphs": 1,
>   "trigram_stats_trigram_vocab_size": 16,
>   "trigram_stats_ratio_trigram_vocab_size_to_num_trigrams": 1.0,
>   "trigram_stats_ratio_unique_trigrams": 1.0,
>   "trigram_stats_intra_story_trigram_repetition": 0.0,
>   "nonunique_trigram_ratio": 0.0625,
>   "nonunique_trigram_ratio_no_pai": 0.0625,
>   "nonunique_trigram_ratio_vs_story": 0.0,
>   "contains_perfect_as_is": false,
>   "is_one_sentence": true,
>   "example_id": "209-randomsentenceswap-zeroshot-onesentence-gemma9b",
>   "sanity": 1.0,
>   "is-perfect-as-is": 0.0,
>   "perfect-agree": NaN,
>   "correctness": 1.0,
>   "error-detection": 0.6666666666666666,
>   "specificity": 1.0,
>   "relevance": 0.6666666666666666
> }
> ```

## Citing this work

If you use this work, please cite the following paper:

```latex
@inproceedings{rashkin-etal-2025-help,
      title={Help Me Write a Story: Evaluating {LLM}s' Ability to Generate Writing
      Feedback},
      author={Hannah Rashkin and Elizabeth Clark and Fantine Huot and Mirella
      Lapata},
      year={2025},
}
```

## License and disclaimer

Copyright 2025 DeepMind Technologies Limited

All software is licensed under the Apache License, Version 2.0 (Apache 2.0);
you may not use this file except in compliance with the Apache 2.0 license.
You may obtain a copy of the Apache 2.0 license at:
https://www.apache.org/licenses/LICENSE-2.0

All other materials are licensed under the Creative Commons Attribution 4.0
International License (CC-BY). You may obtain a copy of the CC-BY license at:
https://creativecommons.org/licenses/by/4.0/legalcode

Unless required by applicable law or agreed to in writing, all software and
materials distributed here under the Apache 2.0 or CC-BY licenses are
distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
either express or implied. See the licenses for the specific language governing
permissions and limitations under those licenses.

This is not an official Google product.
