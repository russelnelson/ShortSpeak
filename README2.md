# ShortSpeak

## Table of Contents

* [Introduction](#introduction)
  * [Overview of ShortSpeak](#overview-of-shortspeak)
  * [End-to-End SS Approach](#end-to-end-ss-approach) 
* [Getting Started](#getting-started)
  * [Installation](#installation)
  * [Requirements](#requirements)
* [Components of ShortSpeak](#components-of-shortspeak)
  * [Input Transformation and Recursive Prompting](#input-transformation-and-recursive-prompting)
  * [Optimizing Shorthand Notation and Performance](#optimizing-shorthand-notation-and-performance)
* [Datasets](#datasets)
  * [Publicly Downloadable Datasets](#publicly-downloadable-datasets)
  * [Dataset Usage Guidelines](#dataset-usage-guidelines)
* [Example Use Cases](#example-use-cases)
  * [Domain-Specific Applications](#domain-specific-applications)
  * [Cross-Domain Adaptability](#cross-domain-adaptability)
* [Performance Evaluation](#performance-evaluation)
  * [Performance Metrics](#performance-metrics)
  * [Benchmarking Results](#benchmarking-results)
* [Contributing](#contributing)
  * [Code Contributions](#code-contributions)
  * [Bug Reports and Feature Requests](#bug-reports-and-feature-requests)
* [License](#license)
* [Acknowledgements](#acknowledgements)

## Introduction

ShortSpeak is a shorthand notation system that allows users to input complex commands and queries with minimal keystrokes. This repository provides an overview of ShortSpeak, its end-to-end approach, and its various components. Additionally, it includes instructions for installation and requirements, descriptions of publicly downloadable datasets, example use cases, and performance evaluation metrics.

### Overview of ShortSpeak

ShortSpeak (SS) is a prompt-compression strategy designed to enable efficient communication with language models using shorthand notation. The primary goal of SS is to reduce the input size while maintaining the context and meaning of user queries, thereby allowing faster interaction and reducing computational overhead.

### End-to-End SS Approach

The end-to-end SS approach comprises two main components:

1. Recursively using the language model to transform the user's input and prompt.
2. Optimizing the balance between shorthand notation and language model performance for diverse use cases.

This repository includes code for both components, along with pointers to the publicly downloadable datasets.

## Getting Started

### Installation

To install ShortSpeak, please follow these steps:

```bash
git clone https://github.com/yourusername/ShortSpeak.git
cd ShortSpeak
pip install -r requirements.txt
```

### Requirements

ShortSpeak requires Python 3.8 or higher. Additional dependencies are listed in [requirements.txt](./requirements.txt).

## Components of ShortSpeak

### Input Transformation and Recursive Prompting

The input transformation component of ShortSpeak first recursively employs the Language Model (LM) to convert tasks and prompts from natural language to shorthand notation. The transformation is performed using ***compressed-prompt-chains***, which consist of a sequence of shorthand symbols and abbreviations representing the original user input in a more concise form. This component also prompts the user for any missing information, ensuring that the LM receives a complete and contextually relevant input.

### Optimizing Shorthand Notation and Performance

This component deals with optimizing the balance between shorthand notation and language model performance. It ensures that the use of shorthand notation does not negatively affect the quality of generated responses while still maintaining efficiency. The code for this component is located in the [shorthand_optimization](./shorthand-optimization/) directory. caching

## Datasets

### Publicly Downloadable Datasets

The datasets used for training and evaluating the ShortSpeak strategy can be found in the [datasets directory](./datasets/).

### Dataset Usage Guidelines

Guidelines for using ShortSpeak datasets can be found in the [dataset usage guide](./dataset-usage.md).

## Example Use Cases

### Domain-Specific Applications

ShortSpeak can be effectively applied to a variety of domain-specific applications, such as customer support, medical consultations, and legal advice. The [examples](./examples/) directory contains several pre-built examples demonstrating how ShortSpeak can be adapted for these specific use cases.

### Cross-Domain Adaptability

In addition to domain-specific applications, ShortSpeak is designed to be adaptable across multiple domains. This adaptability allows users to leverage the benefits of shorthand notation across a wide range of language model applications. The [examples](./examples/) directory also includes examples that showcase the cross-domain capabilities of ShortSpeak.

## Performance Evaluation

### Performance Metrics

To measure the effectiveness of ShortSpeak, we use several performance metrics, including:

* Compression Ratio: The ratio of the original input size to the compressed input size.
* Response Quality: A subjective measure of the relevance and coherence of language model-generated responses.

Detailed information on these metrics and the evaluation process can be found in the [evaluation](./evaluation/) directory.

### Benchmarking Results

ShortSpeak has been benchmarked against several popular language models to evaluate its performance. The benchmarking results, along with a detailed analysis, can be found in the [evaluation](./evaluation/) directory.


## Contributing

### Code Contributions

Instructions for contributing code can be found in the [contributing guide](./contributing.md).

### Bug Reports and Feature Requests

If you encounter any bugs or have suggestions for new features, please create an [issue](https://github.com/user/repo/issues). We appreciate your feedback and will address your concerns as soon as possible.

## License

The ShortSpeak repository is licensed under [Apache License 2.0](./LICENSE.md).

## Acknowledgements

This project is made possible by our contributors, collaborators, and users. We are grateful for your valuable feedback and suggestions.
