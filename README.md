## **NLP based Question-Answering System using SpanBERT and Splinter model**
  
  
## Introduction
Question answering (QA) is a computer science discipline within the fields of information retrieval and natural language processing (NLP), which is concerned with building systems that automatically answer questions posed by humans in a natural language. It's is a critical NLP problem and a longstanding artificial intelligence milestone. In this project we present the use of Splinter and SpanBERT models to showcase and try to solve the question-answering problem both in the closed domain and open domain as well, where the dataset used was (open domain) is SQuAD 2.0 and also a separate dataset (COVID dataset) has been generated by us for the splinter model (closed domain).

## Methodology

### SPLINTER model (span-level pointer)

Splinter is a model that has been pre-trained for few-shot question answering in a self-supervised manner. This implies it was pre-trained on raw texts solely, with no human labelling (which is why it can use so much publicly available data), and then used an automatic method to build inputs and labels from those texts.

![image](https://user-images.githubusercontent.com/53213766/174388862-e8a758b3-88ba-4270-9fdc-6fb5f20e5869.png)

- A pretrained model for few-shot question answering.
- Can leverage recurring spans: n-grams, such as named entities, which tend to occur multiple times in each passage 
- We emulate question answering by masking all but one instance of each recurring span with a special [QUESTION] token and asking the model to select the correct span for each such token.
- To select an answer span for each [QUESTION] token in parallel, we introduce a question-aware span selection (QASS) layer, which uses the [QUESTION] token’s representation to select the answer span.
![image](https://user-images.githubusercontent.com/53213766/174389735-5204564a-2218-42e0-9bdf-356d4b29fe2a.png)


### SpanBERT model
- An Upgraded version of the BERT model. 
- Unlike BERT in SpanBERT we mask random contiguous spans of text, rather than  randomly mask tokens in a sequence. 
- SpanBERT, the only thing the model is trained on is the Span Boundary Objective which later contributes to the loss function.

![image](https://user-images.githubusercontent.com/53213766/174389788-93e09234-7d4d-415d-99bb-856f2303f61e.png)

- #### Dataset for SpanBERT model
 - SQuAD 1.1 contains 107,785 question-answer pairs on 536 articles. SQuAD2.0 (open-domain SQuAD, SQuAD-Open), the latest version, combines the 100,000 questions in SQuAD1.1 with over 50,000 un-answerable questions written adversarially by crowdworkers in forms that are similar to the answerable ones.

## Results

- Code architecture for the BERT model.
![image](https://user-images.githubusercontent.com/53213766/174390071-ecf63589-f44d-490f-abd3-9c8f4e4147bd.png)

- Code architecture for SpanBERT QuestionAnswering system.
![image](https://user-images.githubusercontent.com/53213766/174390143-77181553-bd18-4b8d-8ec5-305087069abb.png)

- Representation of the Closed Domain, preprocessed data (COVID data).
![image](https://user-images.githubusercontent.com/53213766/174390192-82760f88-fbb8-47cf-9845-0e1a975515e6.png)

- Predicted output of the splinter model.
![image](https://user-images.githubusercontent.com/53213766/174390365-2b73b6cf-d097-4227-9211-98375588947a.png)

- Training process representing the training & validation loss
![image](https://user-images.githubusercontent.com/53213766/174390399-bf22bd64-19bf-4a64-925e-da6a0acfdda2.png)

### Conclusion

In this project we tried to build a question-answering system with the acquired data using pre-processing methods and doing data acquisition for the dataset to work for these models Splinter and SpanBERT models. Our approach converts texts into a set of questions that need to be answered simultaneously.

Thank You :)
#### Sai Ganesh N
