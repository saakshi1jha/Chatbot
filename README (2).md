# FAQ Chatbot (Semantic Search)

A simple chatbot that answers questions by finding the most semantically similar question in a predefined FAQ dataset, using sentence embeddings instead of exact keyword matching.

## How It Works

1. A `sentence-transformers` model (`distiluse-base-multilingual-cased-v1`) encodes each FAQ question into a vector embedding.
2. When the user types a question, it's encoded into a vector too.
3. Cosine similarity (`util.semantic_search`) compares the user's question against all FAQ question embeddings.
4. The chatbot returns the answer linked to the closest matching question.

This means the chatbot can understand questions phrased differently from the exact FAQ wording, since it matches on meaning rather than exact text.

## Tech Stack

- **Python**
- **[sentence-transformers](https://www.sbert.net/)** — for generating text embeddings
- **pandas** — for storing and managing the FAQ dataset
- **Model:** `distiluse-base-multilingual-cased-v1` (multilingual, supports many languages)

## Project Structure

The chatbot logic lives in a single Jupyter notebook (`chatbot_cetpa_.ipynb`) with the following flow:

| Step | Description |
|---|---|
| Install dependencies | `sentence-transformers` |
| Load model | Loads the multilingual sentence embedding model |
| Build FAQ dataset | A sample set of ~50 question-answer pairs stored in a pandas DataFrame |
| Encode FAQs | Converts all FAQ questions into embeddings |
| Chatbot loop | Takes user input, finds the closest FAQ match, and prints the answer |

## Setup

```bash
pip install sentence-transformers pandas
```

## Usage

Run all cells in the notebook, then call the chatbot function:

```python
chatbot()
```

Example interaction:

```
chatbot : Hello! Ask a question or type exit to quit.
You : how do I stay fit?
chatbot : To stay healthy, maintain a balanced diet, exercise regularly...
You : exit
chatbot : Goodbye!
```

## Customizing the FAQ Data

To use your own data instead of the sample FAQs, replace the `faq_data` dictionary with your own `"question"` and `"answer"` lists (both lists must be the same length), then re-run the encoding step so the chatbot picks up the new questions.

## Limitations

- Answers are limited to whatever exists in the FAQ dataset — the chatbot cannot generate new answers, only retrieve the closest existing one.
- Always returns a "best match," even if no FAQ is actually a good match for the input (no similarity threshold/fallback is currently set).
- Runs as a command-line loop within the notebook; there's no web or chat UI.

## Possible Improvements

- Add a similarity score threshold to respond with "I don't know" for irrelevant questions.
- Persist FAQ embeddings (e.g., save/load with pickle) instead of recomputing on every run.
- Load FAQ data from an external file (CSV/JSON) instead of hardcoding it.
- Wrap the chatbot in a simple web interface (e.g., Streamlit or Flask).

## Author

Created by Sakshi Jha
