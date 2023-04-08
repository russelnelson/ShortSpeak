# PromptCrunch - Chained, Compressed Prompts for Querying Large Language Models
PromptCrunch is a method for querying large language models (LLMs) using shorthand notation, inspired by MapReduce. The goal is to optimize and simplify interactions with language models while retaining their powerful capabilities.

PromptCrunch demonstrates common text-to-text applications such as summarization, translation, and question-answering. 

# Example: **RcmndRecipe|GPT4Lng**: Recommend a recipe based on specific dietary preferences or restrictions.

Example:
```RcmndRecipe|GPT4Lng:Vegan```


The components are designed to be composable, allowing multiple compressed prompts to be chained together for more complex and conditional queries.

# Examples:
1. **StepByStep|GPT4Lng**: Break down complex reasoning problems into smaller steps, allowing the model to perform logical operations such as selection, deduction, induction, and inference.

Example:

    StepByStep|GPT4Lng:Question|GPT4Lng:```what is emily afraid of?```_SelectInfo|GPT4Lng:```Context: wolves are afraid of mice. sheep are afraid of wolves. emily is a wolf. mice are afraid of wolves. winona is a wolf. cats are afraid of sheep. jessica is a cat. gertrude is a sheep.```_Inference|GPT4Lng:_FinalInferenceOnly|GPT4Lng:

2. **ChainSummarizeTranslate|GPT4Lng**: Summarize a text and then translate the summary to another language, all within a single query.

Example:

    ChainSummarizeTranslate|GPT4Lng:Original text in English_Summary|GPT4Lng:TranslateTo|GPT4Lng:Spanish

With PromptCrunch, you can create modular, efficient, and powerful queries for your language model, reducing the number of tokens required and improving the overall performance of your interactions with LLMs.
