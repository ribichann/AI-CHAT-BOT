# AI Chatbot

An intent-based chatbot built with Python, NLTK and Scikit-learn. It uses NLP preprocessing and a Logistic Regression classifier to work out what the user is asking, replies accordingly, and shows how confident the model was. Served through a Flask web app with a colorful glassmorphism chat UI.

## Features

- **Intent classification** using TF-IDF features and a Logistic Regression model
- **NLP preprocessing** with NLTK (tokenization and lemmatization)
- **Confidence score** on every reply (green / yellow / red) plus the predicted intent tag, both toggleable
- **Fallback handling** — low-confidence messages get a friendly "I didn't get that" reply instead of a wrong answer
- **Colorful gradient UI** with frosted-glass bubbles, typing animation, timestamps and a message counter
- **Sound effects** for sent and received messages (can be switched off)
- **Quick-reply buttons** for common questions
- **Easy to extend** — add new topics by editing a single JSON file

## What it can talk about

| Category | Examples |
|---|---|
| Small talk | greetings, goodbyes, thanks, "how are you", compliments |
| About the bot | name, creator |
| AI / ML topics | Artificial Intelligence, Machine Learning, Deep Learning, NLP |
| Tools | Python, TensorFlow, OpenCV |
| Fun | jokes, motivation quotes |
| Practice | Python quiz, ML quiz |

## Tech Stack

- **Python** — core language
- **NLTK** — tokenization and lemmatization
- **Scikit-learn** — TF-IDF vectorizer and Logistic Regression classifier
- **Flask** — backend web server and JSON API
- **HTML / CSS / JavaScript** — frontend chat interface

## Project Structure

```
ai-chatbot/
├── app.py              # Flask server (routes: / and /chat)
├── chatbot.py          # NLP preprocessing + intent classifier
├── intents.json        # Training data: tags, patterns, responses
├── requirements.txt    # Python dependencies
├── README.md
└── templates/
    └── index.html      # Chat UI
```

## Getting Started

**1. Clone the repository**
```bash
git clone https://github.com/adhiljabbar23-cmd/ai-chatbot.git
cd ai-chatbot
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Run the app**
```bash
python app.py
```

**4. Open in your browser**
```
http://localhost:5000
```

The required NLTK data is downloaded automatically the first time you run the app.

## How It Works

1. The user types a message in the browser.
2. JavaScript sends it to the Flask `/chat` endpoint as JSON.
3. `chatbot.py` tokenizes and lemmatizes the text with NLTK.
4. The TF-IDF vectorizer converts the text into numeric features.
5. The Logistic Regression model predicts the intent and a probability for it.
6. If the probability is below the confidence threshold, the bot uses the fallback reply; otherwise it picks a random response from the matched intent.
7. Flask returns the reply, intent tag and confidence score, and the UI displays them.

## Adding New Topics

Open `intents.json` and add a new block:

```json
{
  "tag": "your_topic",
  "patterns": ["example question 1", "example question 2", "another way to ask"],
  "responses": ["Your answer here", "Another possible answer"]
}
```

Give each intent plenty of varied patterns (15–20 is a good target). More examples mean higher model confidence and fewer fallback replies. Restart the app and the model retrains automatically.

## Possible Improvements

- Context memory across multiple messages
- Sentiment analysis on user input
- Larger intent dataset and a neural network classifier (TensorFlow/Keras)
- Voice input and output
- Deployment to Render or Hugging Face Spaces

## Author

** Ribn Xavier **
B.Tech in Artificial Intelligence and Machine Learning, Vidya Academy of Science and Technology
