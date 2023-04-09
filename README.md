# PromptCrunch - Chained, Compressed Prompts for Querying Large Language Models

PromptCrunch is a method for querying large language models (LLMs) using shorthand notation. The goal is to optimize and simplify interactions with language models while retaining their powerful reasoning capabilities.

This repo contains compressed prompts for common text-to-text applications such as summarization, translation, question-answering, and generation. These components are designed to be composable, allowing multiple compressed prompts to be chained together for more complex and conditional queries.

# Table of Contents
- [PromptCrunch - Chained, Compressed Prompts for Querying Large Language Models](#promptcrunch---chained-compressed-prompts-for-querying-large-language-models)
   * [Quick Start](#quick-start)
   * [Examples](#examples)
   * [How It Works](#how-it-works)
   * [Limitations](#limitations)
   * [Further Directions](#limitations)
   * [Motivation](#motivation)
   * [Contributing](#contributing)

## Quick Start

To compress a prompt: use `CmprsPrmpt|GPT4Lng`:  

```
CmprsPrmpt|GPT4Lng:`{Your Prompt Text}`
```

## Examples

Summarize this text in 30 words:
```
Summarize|GPT4Lng:30words`{Your Text}`
```

Recommend a recipe based on specific dietary preferences or restrictions:
```
RcmndRecipe|GPT4Lng:Vegan
```

Generate text conditioned on key information. This example demonstrates compressing a prompt from the OpenAI Codebook, "Write an email to a colleague named Jill congratulating her on her promotion. The tone should be warm yet professional. Mention how you admire the work she's been putting in. Include a joke about how her pet lizard Max enjoys eating grasshoppers. Mention how you're looking forward to the team off-site next week":
```
EmlColleague|GPT4Lang:`Jill,promotion,warm_professional,admire_work,lizard_joke,offsite_next_week`
```

These components are designed to be composable, allowing multiple compressed prompts to be chained together for more complex and conditional queries.




## Motivation

Help developers building applications on LLM APIs to reduce the number of tokens required while improving the overall performance of their interactions with LLMs.

In preliminary testing, using compressed prompts achieved token savings of ~25% and reduced latency by ~1.5 seconds. (More formal benchmarks and paper to come.)


## How It Works

PromptCrunch uses a shorthand notation with some similarities to SQL. But unlike SQL, it specifies the required format of the output at the beginning of the query. This provides the LLM with a stronger signal on the user's intent.

`CmprsPrmpt|GPT4Lng:Can you tell me the smallest 5 US states by geographic size, in ascending order, and format the output as a table?`
```
Table|GPT4Lng:smallestUSstates|5|ascending|geoSize
```

## Limitations

Developed and tested with ChatGPT-4. Some of the compressed prompts work with earlier models but I haven't yet tested backwards compatability.

## Further Directions

You can make the queries parameterized, replacing the constants (e.g., `Summarize`) with parameters.

You can break complex tasks into components and then orchestrate the matching of tasks to APIs to further optimize token usage and latency.

## Motivation

Help developers building applications on LLM APIs to reduce the number of tokens required while improving the overall performance and end-user experience.

## Contributing

Make your own c

## Example: **Summarize|GPT4Lng:30words**: Summarize this text in 30 words.

```Summarize|GPT4Lng:30words```

It can also be used for generating text conditioned on key features.

# Example: **RcmndRecipe|GPT4Lng**: Recommend a recipe based on specific dietary preferences or restrictions.

```
RcmndRecipe|GPT4Lng:Vegan
```

# Example: **EmlColleague|GPT4Lang:`Jill,promotion,warm_professional,admire_work,lizard_joke,offsite_next_week`** : Write an email to a colleague named Jill congratulating her on her promotion. The tone should be warm yet professional. Mention how you admire the work she's been putting in. Include a joke about how her pet lizard Max enjoys eating grasshoppers. Mention how you're looking forward to the team off-site next week.

```
EmlColleague|GPT4Lang:`Jill,promotion,warm_professional,admire_work,lizard_joke,offsite_next_week`
```

This format can also be used for generating text  
# Example


The components are designed to be composable, allowing multiple compressed prompts to be chained together for more complex and conditional queries.

# Examples:
1. **StepByStep|GPT4Lng**: Break down complex reasoning problems into smaller steps, allowing the model to perform logical operations such as selection, deduction, induction, and inference.

Example:

    StepByStep|GPT4Lng:Question|GPT4Lng:```what is emily afraid of?```_SelectInfo|GPT4Lng:```Context: wolves are afraid of mice. sheep are afraid of wolves. emily is a wolf. mice are afraid of wolves. winona is a wolf. cats are afraid of sheep. jessica is a cat. gertrude is a sheep.```_Inference|GPT4Lng:_FinalInferenceOnly|GPT4Lng:

2. **ChainSummarizeTranslate|GPT4Lng**: Summarize a text and then translate the summary to another language, all within a single query.

Example:

    ChainSummarizeTranslate|GPT4Lng:Original text in English_Summary|GPT4Lng:TranslateTo|GPT4Lng:Spanish

With PromptCrunch, you can create modular, efficient, and powerful queries for your language model, reducing the number of tokens required and improving the overall performance of your interactions with LLMs.
