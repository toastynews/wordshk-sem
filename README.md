# wordshk-sem

*Licensed under the Non-Commercial Open Data License (https://words.hk/base/hoifong/)*

This dataset is obtained by scraping [words.hk](https://words.hk/) for word definition pairs commonly used in Hong Kong. Formatted to use with BERT. The entries are not limited to vernacular or slang usage. It can be used to test how much a model understands general language usage in Hong Kong.

## Description
The task is structured as a binary classification task (0=incorrect, 1=correct) of a word(text_a) against a dictionary definition(text_b). Each correct entry would have two corresponding incorrect entires. One with an incorrect definition, another with an incorrect word. 

Example:

|label|text_a|text_b         |
|-|---|----------------------|
|1|客氣|有禮貌；講究禮數；保持距離|
|0|客氣|檢查資料係咪符合紀錄、規則|
|0|儐相|有禮貌；講究禮數；保持距離|

Random guess would give 33% accuracy, and a model that always predicts 0 will give 67% accuracy.

The entries are filtered so that no characters from the word would appear in the definition, as these are strong hints that the word matches the definition. One such example is 
* word: 烈火
* definition: 熾熱、猛烈嘅火焰

This task can be thought of as an intrinsic evaluation of the model's knowledge about words. The word is given without any context, there is no way to guess by the definition. Finetuning is just to get the model to understand what we want. 