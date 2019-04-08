# AMI-EVALITA2018
Code for replicating results of team 'hateminers' at EVALITA-2018 for 'Automatic Misogyny Identification' task. We have explained the model details in our paper ''[Hateminers : Detecting Hate speech against Women](https://arxiv.org/abs/1812.06700)''.
We came **First for the English Subtask A and Fifth for the English Subtask B.**

## Please cite our paper in any published work that uses our model.

> Saha, P., Mathew, B., Goyal, P. & Mukherjee, A., (2018). Hateminers: Detecting Hate speech against Women. _arXiv preprint arXiv:1812.06700_.
```
@article{saha2018hateminers,
  title={Hateminers: Detecting Hate speech against Women},
  author={Saha, Punyajoy and Mathew, Binny and Goyal, Pawan and Mukherjee, Animesh},
  journal={arXiv preprint arXiv:1812.06700},
  year={2018}
}
```

## Directory structure
```
root
|
|-----AMI_data (data needs to be kept here) 
|
|-----Classifier
	|
	|-----taskA(models and feature selection methods for task A- misogynous or not)
	|
	|-----taskB1(models and features selection methods for task B1- misogyny category )
	|
	|-----taskB2(models and features selection methods for task B2- misogyny category )
		
```
## Predicitons
In order to make the predicition feature vector consisting tfidf-vectors , glove embeddings , google-universal-encoding should be prepared.

```
clf_task1=joblib.load('taskA/'+model_for_taskA)
clf_task2=joblib.load('taskB1/'+model_for_taskB1)
clf_task3=joblib.load('taskB2/'+model_for_taskB2)
select_task1=joblib.load('taskA/'+select_featue_for_taskA)
select_task2=joblib.load('taskB1/'+select_featue_for_taskB1)
select_task3=joblib.load('taskB2/'+select_featue_for_taskB2)
```
Assuming x to be a feature vector.Models of Task B are only used when Task A model predicts the given text as misogynous. 
```
x=x.reshape(1,-1)
temp=x
temp=select_task1.transform(temp)
predict1=clf_task1.predict(temp)

if(int(predict1[0])!=0):
	temp1=x
	temp1=select_task2.transform(temp1)
	predict2=clf_task2.predict(temp1)
	temp2=x
	temp2=select_task3.transform(temp2)
	predict3=clf_task3.predict(temp2)
else:
	list_2.append(0)
	list_3.append(0)
```
More details can be found in [here](Classifier/Submit_test.ipynb)


## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
