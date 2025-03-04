**Introduction**


The traditional view of knowledge estimation suggests that we acquire static facts about what others know through interactions with others. As we gain experience in interacting with others about specific ideas, we develop an understanding of others’ knowledge. In this theory, our estimates of others’ knowledge should not be affected by the contexts or conditions under which the judgments are elicited, but should change as others reveal novel evidence about their knowledge [4]. 
The view of knowledge estimation as static knowledge has a strong history in education research, in which it is theorized that teachers’ ability to predict students’ knowledge improves through direct teaching experience and interactions with students [4]. Knowledge tracing is the task of modelling student knowledge over time so that we can accurately predict how students will perform on future interactions. Improvement on this task means that resources can be suggested to students based on their individual needs, and content which is predicted to be too easy or too hard can be skipped or delayed. Already, hand-tuned intelligent tutoring systems that attempt to tailor content show promising results. One-on-one human tutoring can produce learning gains for the average student on the order of two standard deviations [5]. Machine learning solutions could provide these benefits of high quality personalized teaching to anyone in the world for free. With advances in data science and the increasing availability of Interactive Educational Systems, data-driven models that learn the complex nature of student behaviours from interaction data have become a common recipe for knowledge tracing. However, the AIEd research community currently lacks a large-scale benchmark dataset which reflects the wide variety of student behaviours available through modern IESs [6]. They are not large enough to leverage the full potential of data-driven models. Furthermore, the data they collect is limited to question-solving activities. The knowledge tracing problem is inherently difficult as human learning is grounded in the complexity of both the human brain and human knowledge. Thus, the use of rich models seems appropriate. 
The current education system needs to be redesigned in terms of attendance, engagement, and individualized attention. This was done by taking up digital teaching. To know where the students stand, a model should be created, which will predict the students’ understanding on a particular topic, on the basis of the analysis made by his/her past performance and the correctness of the questions answered by them. The availability of the massive dataset of students’ interactions facilitates for predicting student’s performance and providing meaningful feedbacks with the help of data mining and machine learning.  The competition “Riiid! Answer Correctness Prediction” hosted on “Kaggle” [11], a data science and machine learning platform, is a part of this project. In this competition, the challenge is to create algorithms for "Knowledge Tracing" i.e., the modeling of student knowledge over time. The goal is to accurately predict how students will perform on future interactions.

**1.1.	Motivation**

In 2018, 260 million children weren't attending school. At the same time, more than half of these students didn't meet minimum reading and math standards [11]. Education was already in a tough place when COVID-19 forced most of the countries to temporarily close schools. Desperate needs call for desperate measures, this thought was put into action during this pandemic to continue and maintain the education of students. Computer-assisted education promises open access to world class instruction and a reduction in the growing cost of learning. We can develop on this promise by building models of large scale student trace data on popular educational platforms.



















**2.	 Problem Statement**

Analyse the information a complete education app would have i.e. a student's historic performance, the performance of other students on the same question, metadata about the question, etc. and predict whether students are able to answer their next questions correctly.






































**3.	Methodology**

The methodology provides framework that includes data understanding, data pre-processing, modelling and evaluation which can be repeated with the aim to review and refine the forecasting model.

**3.1.	KDD 1**

The knowledge discovery process is iterative and interactive, comprising nine steps. The   process is iterative at each stage, implying that moving back to the previous actions might be required. The process has many imaginative aspects in the sense that one can’t present one formula or make a complete scientific categorization for the correct decisions for each step and application type. Thus, it is needed to understand the process and the different requirements and possibilities in each stage. The process begins with determining the KDD objectives and ends with the implementation of the discovered knowledge.

**3.1.1.	 Data Pre-processing**

Data pre-processing is a data mining technique that involves transforming raw data into an understandable format.

**a)	Data Cleaning**

The missing values in prior_question_elapsed_time were filled with a global constant -1 as the values were missing for the first question of each user and there is no prior question before the first question. The missing values in prior_question_had_explanation were filled with False as the values were missing for the first question of each user and there is no prior question before the first question. The missing tag value in questions was filled with the 6 most frequent tags that appear with part 6 as the part number of the missing tag was 6.

**b)	Data Transformation**
The datatype of prior_question_had_explanation was changed from boolean to int, True was replaced with 1 and False with 0 as the machines represent data internally as numbers. 

**c)	Data Reduction**
Entire lectures data was dropped along with some features from train such as user_answer, row_id and content_type_id as these features had less importance and did not contribute significantly to the overall score.


**d)	Data Integration**

  We have merged the train and question data.

**e)	 Feature Extraction and Generation**

The “tags” column in questions.csv was split into 6 columns Tag1, Tag2, Tag3, Tag4, Tag 5 and Tag6 as some of the questions had as many as 6 tags and three additional features user_acc, ques_acc and part_acc were generated.

**3.1.2.	 Learning Models **


**a)	  CatBoost- Categorical Boosting**

CatBoost is designed to work on categorical data flawlessly. It requires minimal data preparation. It handles missing values for numeric variables, and non-encoded categorical variables.
AUC Score obtained: 0.7683

**b)	LightGBM – Light Gradient Boosting Machine **

LightGBM is an open source distributed gradient boosting framework for machine   learning. It is based on decision tree algorithms and used for ranking. It can handle large size of data and takes lower memory to run. Also, it focuses on accuracy of results.  

**AUC Score obtained: 0.77**


**c)	XGBoost - Extreme Gradient Boosting**

XGBoost is an optimized distributed gradient boosting library designed to be highly efficient and flexible. The beauty of this powerful algorithm lies in its scalability, which drives fast learning through parallel and distributed computing. 

**AUC Score obtained: 0.7667**





**d)	AdaBoost- Adaptive Boosting**

AdaBoost was first successful boosting algorithm developed for binary classification. AdaBoost combines multiple weak classifiers into single strong classifier. AdaBoost works by putting more weight on difficult to classify instances and less on those already handled well. 

**AUC Score obtained: 0765**


**e)	K-Nearest Neighbors**

K-Nearest Neighbors works by finding distances between test points and all the examples in the data. Then it selects the specified number of examples(K) which are closest to the test points. After that it votes for most the frequent label

**AUC Score obtained: 0.594**

**f)	 Naïve Bayes**

Naive Bayes classifiers are a family of simple probabilistic classifiers based on applying Bayes' theorem with strong independence assumptions between the features. They are among the simplest Bayesian network models, but coupled with kernel density estimation, they can achieve higher accuracy levels.
  **    AUC Score obtained: 0.5622**

**g)	Logistic Regression**

       Logistic regression is a supervised classification algorithm, used when the value of the target variable is categorical in nature. Logistic regression is most commonly used when the data in question has binary output i.e. when it belongs to one class or another, or is either a 0 or 1.
   **    AUC Score obtained: 0.5543**






**3.1.3.	Performance Evaluation**



<img width="716" alt="image" src="https://github.com/user-attachments/assets/307840aa-0f05-4baa-9421-f14f448d11a0" />

As can be seen from table 1, the LightGBM model performed better than all the other models in KDD1.

3.2.	KDD 2

In KDD1, satisfactory results were not obtained so another iteration of KDD was performed.

3.2.1.	 Data Pre-processing

In KDD2 cleaning, transformation and reduction of the data was done once again.

a)	Data Cleaning

The missing values in prior_question_elapsed_time were filled with mean of that column as it is more appropriate to fill the mean rather than a global constant as most users had values in same range.
b)	Data Transformation

The timestamp values and prior_question_elapsed_time values are converted into seconds from milliseconds as the values in milliseconds were too large and data had to be standardized.

c)	Data Reduction

Tag4, Tag5 and Tag6 were dropped as these attributes weren’t contributing to the overall score.

d)	Feature Extraction and generation

The features extracted from the given train, lectures and questions data were timestamp, Tag1, Tag2, Tag3, Part, content_id, user_id, task_container_id, prior_question_elapsed_time, prior_question_had_explanation, bundle_id and timestamp. The features generated from the given train, lectures and questions data were user_acc, part_acc, ques_acc, lagtime, lagtime2, lagtime3, Attempt_no, q_exp_correct, q_exp_count, q_exp_acc, user_correct_ratio, ques_correct_ratio and part_correct_ratio. 


3.2.2.	Learning Models

Since in KDD1 the CatBoost, XGBoost and LightGBM models gave the best scores, in KDD2 focus was given was training these three models.

a)	LightGBM - Light Gradient Boosting Machine 

AUC Score obtained: 0.790

b)	CatBoost – Categorical Boosting

   AUC Score obtained: 0.788

c)	XGBoost – Extreme Gradient Boosting 

                AUC Score obtained: 0.785










3.2.3.	Performance Evaluation 


<img width="738" alt="image" src="https://github.com/user-attachments/assets/3aface9f-71f0-4ed4-8132-489430e860ca" />





As can be seen in Table 2, the LightGBM model performed better than the other 2 models in KDD2.
