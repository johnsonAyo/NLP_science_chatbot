# NLP Chat Bot Trained on science-related Questions

API service

## Deployment Options
- Download the needed packages by running `pip install -r requirements.txt`

The application can be executed in two different ways:
- locally by running the `start.sh`
- on in a docker container using `Dockerfile`

## API Docs
There is an automatically generated API documentation when the server is running. the API can be viewed at `<your_env_url>:<port>/swagger-ui`. For example, if you are running it locally you can view the API docs at `http://localhost:5000/swagger-ui`

## Chat Bot Brain Setup

Important components of the setup
1. Training Data (Science Questions(features) and answers(label))
2. NLTK Package
3. Tensorflow
4. Numpy

Important Concepts in the Setup
1. Neural Network
2. Bag-of-Words Model
3. Lemmatization


## Background 
The project involves a dataset related to science. This dataset is imported into the system. Then a process known as 'feature engineering' is carried out, where important pieces of information (features) and their corresponding labels are extracted from the dataset.

'Lemmatization' is performed on the data using a tool called NLTK. This is a process where different forms of a word are converted into its base form, such as 'running', 'runs', and 'ran' all becoming 'run'. This step aids in standardizing the data.

The text data is then converted into numbers, a necessary step because the machine learning model, a Neural Network, can only process numerical data.
Further input preprocessing is done using a function called 'clean_text'. This involves removing unnecessary elements from the text like punctuation and extra spaces. A method called 'bag of words' is also used to represent the text data in a way that's suitable for machine learning.

Once these steps are completed, the data is ready to be used by the Neural Network model. This model is trained using an optimization method called 'Adam'. The model takes the processed data and makes predictions.

Finally, a function called 'get_response' is used to interpret the model's predictions and provide a meaningful output.
Below is a Python function used in the project:

```python
############################################################
# Callback function called on each execution pass
############################################################
def execute(request: SimpleText, ray: Ray, state: State) -> SimpleText:
    output = []
    for text in request.text:
        intents = pred_class(text, words, classes)
        response = get_response(intents, data)
        output.append(response)

    return SchemaUtil.create(SimpleText(), dict(text=output))
```

This function, named 'execute', takes in a request, processes each piece of text in the request, makes predictions, gets responses based on these predictions, and returns the responses


## Future Improvement 
Data Expansion and Quality: a model is only as good as the data it's been trained on. The model's performance is directly tied to the quality and diversity of the training data.

Contextual Understanding: The model can be enhanced to understand better and interpret various contexts, leading to more informed and accurate predictions.

Bias Reduction: Reinforcement Learning from human feedback can be integrated into the training process to detect and correct biases, ensuring the model's decisions are more equitable.

