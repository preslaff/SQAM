# **SQAM - Simplified Question Answering Machine**
Here is a [DEMO VERSION](https://www.cdsv.dev)

## Abstract

SQAM - Simplified Question Answering Machine is a light weight service for question answering using predefined question-answer pairs in a json database. The application tokenizes the user question using 768 dimensional SBERT embeddings and finds the first three nearest predefined questions. Then give theit answers. This approach is very usefull for lightweight application where user will have limited number of domain specific questions. The example database consists of around 1000 predefined questions about Data Science, Machine Learning and Deep Learning. 

## Install

Clone the repo `git clone https://github.com/preslaff/SQAM.git` and install the dependencies with `pip install -r requirements.txt`

## How it works

SQAM uses the `app.py ` flask application to embed, calculate the cosine similarity and then serve the most close predefined question-answer pairs.
Start the app with `python app.py` and then you can request answers with a front end of your choice or with curl ex.:

`curl -X POST http://127.0.0.1:5000/get_answers -H "Content-Type: application/json" -d '{"question": "What is Machine Learning?"}'`

## Offline use

You can use the app in offline mode (without Internet connection) if you save the embeddings:

`np.save('question_embeddings.npy', question_embeddings)`

and when the app is initialized and the model is cached load them with:

`question_embeddings = np.load('question_embeddings.npy')`

After this step, the app can operate in offline, standalone local mode.





