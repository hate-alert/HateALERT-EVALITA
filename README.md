# AMI-EVALITA2018
Code for replicating results of team 'hateminers' at EVALITA-2018 for AMI task. We have explained the model details in our paper ``Hateminers : Detecting Hate speech against Women''

##Directory structure

root
|
|-----AMI_data (data needs to be kept here) 
|
|-----CLASSIFIER
		|
		|-----taskA(models and feature selection methods for task A- misogynous or not)
		|
		|-----taskB1(models and features selection methods for task B1- misogyny category )
		|
		|-----taskB2(models and features selection methods for task B2- misogyny category )
		




## Predicitons


```
###loading the tfidf word vectors
with open('tfidf_word_vectorizer.pk', 'rb') as fout:
         word_vectorizer=pickle.load(fout)
###loading the tfidf char vectors
with open('tfidf_char_vectorizer.pk', 'rb') as fout:
        char_vectorizer=pickle.load(fout)


clf_task1=joblib.load('taskA/'+model_for_taskA)
clf_task2=joblib.load('taskB1/'+model_for_taskB1)
clf_task3=joblib.load('taskB2/'+model_for_taskB2)
select_task1=joblib.load('taskA/'+select_featue_for_taskA)
select_task2=joblib.load('taskB1/'+select_featue_for_taskB1)
select_task3=joblib.load('taskB2/'+select_featue_for_taskB2)

```