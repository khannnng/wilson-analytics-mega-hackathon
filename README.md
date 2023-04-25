# Wilson Analytics Mega Hackathon

Wilson Analytics Mega Hackathon was a 80 hour hackathon hosted by Great Learning for all learners of the MIT Data Science Programs. 




Problem statement:
- All bank branches across India provide MUDRA loans. Such loans have created the low-cost credit concept for micro and small businesses. One of the leading financial institutions in India wants to leverage Machine Learning techniques to determine the client’s loan repayment abilities and take proactive steps to reduce the magnitude of exposure to default.

Goal: The goal of the problem is to predict whether a client will default on the loan payment or not, given the recent data of all the loan transactions. This can help the institution to distinguish future applicants who might default. For each ID in the Test Dataset, you must predict the “Default” level.

Metrics: Accuracy.

_________________________________________

The main challenge I faced is there's quasi-separation in the data. There's one feature ('ChargeOff_Amount') that can predict 99.4% accuracy by itself. Any attempt to improve the prediction only results in very insignificant improvement. For each new prediction, I had to check kfold cross validation to determine if a model is improving in prediction, like looking at model's performance with microscope.

Next is that there is a lot of string data that are potentially useful, such as the bank issuing the loan. Certain bank has stricter process for approving loan, which can lead to lower chance of default. There are over 80 banks so dummy variables is not a really good idea. 

General approach:
For  categorical with very number of classes, I convert them to the odds of default for each class. At the time I had not known, but this techniques is very similar to what called Weight of evidence, though much simpler.

To deal with quasi-separation, a lot of numerical features were derived to see if they can help negate the effect of ChargeOff_Amount. 

There are also other engineered features that can combine the effect of the loan term, loan amount, debt, and income together, like monthly pay, net income after debt payment, etc. Reason is that for someone who have higher loan amount but with longer term, the loan is more relaxing than someone who has maybe lower loan amount but shorter term and higher monthly pay. Someone has high month loan pay while having a very high salary is also in a much better spot than one with low loan payment but much lower salary.

To quickly experiment with different data preparation and features, I have a data transformation function that can be added more argument as the needs arise without breaking the previous code blocks.

In the end a random forest model had the best accuracy of all, landed me 2nd place on the leaderboard.

![image](https://user-images.githubusercontent.com/112837341/234328772-5b6a885f-952e-4f86-9da3-3b253f92714e.png)
![image](https://user-images.githubusercontent.com/112837341/234328982-9ba1363f-bed3-4322-a755-8d433d965768.png)
