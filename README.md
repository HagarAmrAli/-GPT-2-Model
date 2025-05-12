# Motivational Quote Generator with GPT-2 and BERTScore Evaluation

## Overview

This project implements a Python notebook that uses the GPT-2 language model to generate motivational quotes based on five distinct prompt types. The generated quotes are compared to a human-written reference using BERTScore to evaluate semantic similarity. The project fulfills the requirements of an assignment to explore prompt engineering, text generation, and evaluation metrics.

### Objectives
- **Part 1**: Load the GPT-2 model and tokenizer.
- **Part 2**: Design five unique prompts (Direct, Scenario-based, Persona-based, Keyword-based, Conversational) and generate three outputs per prompt (15 total).
- **Part 3**: Provide a human-written motivational quote as a reference, with its source.
- **Part 4**: Compute BERTScore to measure the similarity between generated quotes and the human reference.
- **Part 5**: Summarize results in a table and save them to a CSV file.

### Features
- Generates 15 motivational quotes using GPT-2 with varied prompt structures.
- Addresses `attention_mask` and `pad_token_id` warnings for reliable GPT-2 generation.
- Evaluates generated quotes using BERTScore for semantic similarity.
- Outputs a results table with prompt types, output numbers, generated texts, and BERTScore F1 scores.
- Saves results to a CSV file for further analysis.

## Prerequisites

- **Python**: Version 3.8 or higher.
- **Hardware**: CPU is sufficient; GPU recommended for faster processing.
- **Internet**: Required for downloading GPT-2 and BERT models.

### Required Libraries
- `transformers`: For GPT-2 model and tokenizer.
- `torch`: For PyTorch backend.
- `bert-score`: For BERTScore evaluation.
- `pandas`: For creating and saving the results table.

Install the dependencies using:
```bash
pip install transformers torch bert-score pandas
```

## Project Structure

- `motivational_quotes_notebook.ipynb`: The main Jupyter Notebook containing the implementation (or equivalent `.py` script).
- `motivational_quotes_results.csv`: Output CSV file containing the results table (generated after running the script).
- `README.md`: This file, providing project documentation.

## Setup Instructions

1. **Clone or Download the Project**:
   - Clone the repository or download the notebook file to your local machine.

2. **Set Up a Virtual Environment** (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install transformers torch bert-score pandas
   ```

4. **Verify Setup**:
   - Ensure Python 3.8+ is installed (`python --version`).
   - Confirm internet access for downloading models.

## Usage

1. **Open the Notebook**:
   - Launch Jupyter Notebook:
     ```bash
     jupyter notebook
     ```
   - Open `motivational_quotes_notebook.ipynb` in your browser.

2. **Run the Notebook**:
   - Execute the cells sequentially to:
     - Load GPT-2 and tokenizer.
     - Generate 15 motivational quotes (3 per prompt).
     - Compute BERTScore against the human reference.
     - Display and save the results table.
   - Alternatively, run the script as a `.py` file:
     ```bash
     python motivational_quotes_notebook.py
     ```

3. **Expected Outputs**:
   - **Console Output**:
     - List of 5 prompts.
     - 15 generated quotes (3 per prompt).
     - Human-written reference quote with source.
     - Results table with Prompt Type, Output Number, and BERTScore F1.
   - **File Output**:
     - `motivational_quotes_results.csv`: Contains the full results table, including generated texts and BERTScore F1 scores.

4. **Customization**:
   - Modify the `prompts` dictionary to experiment with different prompt styles or content.
   - Replace the `human_reference` and `reference_source` with another motivational quote (ensure proper sourcing).
   - Adjust `max_length` in the `generate_quote` function for shorter or longer outputs.

## Implementation Details

### Prompts
The five prompt types are:
- **Direct**: "Write a motivational quote about overcoming fear."
- **Scenario-based**: "Imagine you’re helping a friend who failed a test. Write something encouraging."
- **Persona-based**: "As a wise monk, write a quote about inner strength."
- **Keyword-based**: "Using the words 'growth', 'struggle', and 'hope', write something inspiring."
- **Conversational**: "User: I feel like giving up. GPT-2: Here's a quote for you:"

### Human Reference
- Quote: "The greatest glory in living lies not in never falling, but in rising every time we fall."
- Source: [BrainyQuote - Nelson Mandela](https://www.brainyquote.com/quotes/nelson_mandela_378967)

### Technical Notes
- **GPT-2 Configuration**:
  - Explicitly sets `pad_token_id` to `eos_token_id` (50256) to avoid warnings.
  - Generates `attention_mask` during tokenization and passes it to `model.generate`.
  - Uses `do_sample=True`, `top_k=50`, and `top_p=0.95` for diverse outputs.
- **BERTScore**:
  - Computes F1 scores for semantic similarity between generated quotes and the human reference.
  - Uses the `bert-score` package with default settings (`lang='en'`).
- **Error Handling**:
  - Fixes `NameError: name 'max_length' is not defined` by ensuring `max_length` is passed correctly in the `generate_quote` function.

## Troubleshooting

- **Warnings about `attention_mask` or `pad_token_id`**:
  - Ensure the code includes the `tokenizer.pad_token` and `attention_mask` settings as shown.
  - Update `transformers` to the latest version (`pip install --upgrade transformers`).
- **NameError for `max_length`**:
  - Verify that the `generate_quote` function is used as provided, with `max_length` defined in the function signature.
- **Memory Issues**:
  - Use `gpt2-small` instead of `gpt2` by changing `from_pretrained('gpt2')` to `from_pretrained('gpt2-small')`.
  - Run on a machine with sufficient RAM or a GPU.
- **BERTScore Errors**:
  - Ensure `bert-score` is installed (`pip install bert-score`).
  - Verify internet access for downloading BERT models.
- **Long Prompts**:
  - If outputs are truncated, reduce prompt length or increase `max_length` in the `generate_quote` function.

## Submission Checklist

- [x] **5 Prompts**: Defined in the `prompts` dictionary.
- [x] **15 GPT-2 Outputs**: Generated (3 per prompt) by the `generate_quote` function.
- [x] **Human-Written Reference**: Included with source link.
- [x] **BERTScore Output Table**: Created and saved to `motivational_quotes_results.csv`.

## License

This project is for educational purposes and uses open-source libraries under their respective licenses (e.g., MIT for `transformers`, Apache 2.0 for `torch`). The human-written reference quote is sourced from BrainyQuote and used for non-commercial purposes.

## Contact

For questions or issues, please open an issue in the repository or contact the project maintainer.

-
