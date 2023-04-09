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

A compressed prompt uses the format `{Expected Response}|{Target Model}:{Condition}`

Summarize this text in 30 words:
```
Summarize|GPT4Lng:30words`{Your Text}`
```

Recommend a recipe based on specific dietary preferences or restrictions:
```
RcmndRecipe|GPT4Lng:Vegan
```

You can further adjust the response formatting by prepending the instruction to the compressed prompt.

Bullet points:
```
ListBullets|GPT4Lng:`Explain the benefits of exercise`
```

Numbered list:
```
ListNumbered|GPT4Lng:`List the steps to create a successful engagement proposal`
```

Table format:
```
TableFormat|GPT4Lng:`Compare apples and oranges in terms of nutritional content and taste`
```

Generate text conditioned on key information: 
Compressing an example prompt from the [OpenAI Codebook](https://github.com/openai/openai-cookbook/blob/main/text_writing_examples.md), "Write an email to a colleague named Jill congratulating her on her promotion. The tone should be warm yet professional. Mention how you admire the work she's been putting in. Include a joke about how her pet lizard Max enjoys eating grasshoppers. Mention how you're looking forward to the team off-site next week":
```
EmlColleague|GPT4Lang:`Jill,promotion,warm_professional,admire_work,lizard_joke,offsite_next_week`
```


These components are designed to be composable, allowing multiple compressed prompts to be chained together for more complex and conditional queries. Here's an example: 

Let's say we have two compressed prompts:
1. `QA|capitalFrance`: For the capital of France
2. `QA|famousLandmark`: For a famous landmark in a city

To chain them together, you can create a compressed prompt like this:
```
Chained|GPT4Lng:QA|capitalFrance_QA|famousLandmark
```

Chained compressed prompts can be designed to work with various retrieval methods. Here are a few examples:
1. `Summary|GPT4Lng`: Summarize a given piece of text
2. `Translate|GPT4Lng`: Translate a given text to a specified language
3. `ExplainConcept|GPT4Lng`: Provide a simple explanation of a given concept
4. `Rephrase|GPT4Lng`: Rephrase a given sentence or paragraph while maintaining its meaning
5. `Analogies|GPT4Lng`: Generate analogies for a given concept or term

You can also do conditional chaining, which involves chaining prompts based on the output of a previous prompt. For instance, suppose you want to ask about famous landmarks in France that are outside of Paris:
1. `QA|cityFrance`: For cities in France
2. `QA|famousLandmark`: For a famous landmark in a city

Now, let's create the chained compressed prompt with a conditional marker `IF_NOT_PARIS`:
```
Chained|GPT4Lng:QA|cityFrance_IF_NOT_PARIS_QA|famousLandmark
```


Finally, you can use compressed prompts to provide structure to reasoning tasks. Here's a question from [bAbi QA](https://huggingface.co/datasets/facebook/babi_qa).
Input:
```
wolves are afraid of sheep 
sheep are afraid of wolves
emily is a wolf
mice are afraid of wolves
winona is a wolf
cats are afraid of sheep
jessica is a cat
gertrude is a sheep
Question: what is emily afraid of?
```
Compressed prompt:
```
Chained|GPT4Lng:Question|GPT4Lng:```what is emily afraid of?```_SelectInfo|GPT4Lng:```Context: wolves are afraid of sheep. sheep are afraid of wolves. emily is a wolf. mice are afraid of wolves. winona is a wolf. cats are afraid of sheep. jessica is a cat. gertrude is a sheep.```_InferenceOnly|GPT4Lng:
```
This prompt first provides the question "what is emily afraid of?" and then instructs GPT-4 to select the relevant information from the provided context. Finally, it performs inference based on the selected information and returns only the inferred result.


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

Extended Results:
```
CmprsPrmpt|GPT4Lng:`Use the following clues to answer the following multiple-choice question.
 
Clues:
1. Miss Scarlett was the only person in the lounge.
2. The person with the pipe was in the kitchen.
3. Colonel Mustard was the only person in the observatory.
4. Professor Plum was not in the library nor the billiard room.
5. The person with the candlestick was in the observatory.
 
Question: Was Colonel Mustard in the observatory with the candlestick?
(a) Yes; Colonel Mustard was in the observatory with the candlestick
(b) No; Colonel Mustard was not in the observatory with the candlestick
(c) Unknown; there is not enough information to determine whether Colonel Mustard was in the observatory with the candlestick
 
Solution:`
```

```
CmprsAns|GPT4Lng:`Clues:1.Scarlett-lounge,2.pipe-kitchen,3.Mustard-observatory,4.Plum-!library-!billiard,5.candlestick-observatory_Q:Mustard+candlestick-observatory?_A:a)Yes`
```
