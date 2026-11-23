# Course FAQ Chatbot (NLP + Dash)

A simple question-answering chatbot that answers questions about a data-science course. It learns from a small
question/answer dataset, uses classic NLP preprocessing and a TF-IDF + Naive Bayes model, and runs as a web app
built with Dash.

Built as the chatbot project of the CipherSchools *Python, Data Science & Machine Learning* programme (2024).

## What it does

You type a question such as *"What is data science?"* into a web page and the bot replies with the best matching
answer from its knowledge base (48 question/answer pairs covering the course lectures).

## How it works

1. **Dataset**: `chatbot_dataset (1).csv` has two columns, `Question` and `Answer`.
2. **Preprocessing**: each question is lower-cased and tokenised with NLTK.
3. **Model**: a scikit-learn pipeline of `TfidfVectorizer` (turns text into word-importance vectors) and
   `MultinomialNB` (a Naive Bayes classifier where each answer is a class).
4. **Prediction**: a new question goes through the same preprocessing and the model predicts the most likely answer.
5. **Web app**: a Dash page with a text box and a Submit button; a callback sends the question to the model and
   shows the conversation.

```
User question -> lower-case + tokenise (NLTK) -> TF-IDF vector -> Naive Bayes -> answer -> Dash web page
```

## Files

| File | Purpose |
|---|---|
| `Chatbot_Project_Complete_Code.ipynb` | Full walkthrough: NLP basics (tokenisation, stemming, lemmatisation, stop words), library overview (NLTK, spaCy, TextBlob, ChatterBot, Rasa), training the bot, and integrating it with Flask and Dash |
| `Chat_bot_app.ipynb` | The compact working app: load data, train the model, launch the Dash interface |
| `chatbot_dataset (1).csv` | Question/answer knowledge base |

## Tech stack

Python · pandas · NLTK · scikit-learn (TF-IDF, Multinomial Naive Bayes) · Dash

## Run it

```bash
pip install pandas nltk scikit-learn dash
jupyter notebook Chat_bot_app.ipynb
```

The notebooks were written in Google Colab and read the CSV from `/content/`. When running locally, change the
path to `chatbot_dataset (1).csv`. Recent Dash versions use `app.run(debug=True)` instead of `app.run_server(...)`.

## What I learned

- The standard NLP preprocessing steps and why each one helps
- Treating a FAQ bot as a text-classification problem
- Wiring a model into a small web interface with Dash callbacks

## Ideas to improve

- Use cosine similarity on sentence embeddings so the bot can match questions it was never trained on
- Add a confidence threshold with an "I don't know" fallback
- Keep a full chat history instead of only the latest exchange

## Author

Tannu Kumari · [GitHub](https://github.com/TannuRajput77) · [LinkedIn](https://linkedin.com/in/tannu-singh1)
