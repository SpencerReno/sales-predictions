# sales-predictions
With this project, I used sales [data](https://drive.google.com/file/d/1syH81TVrbBsdymLT_jl2JIf6IjPXtSQw/view) from [datahack.analytics](https://datahack.analyticsvidhya.com/contest/practice-problem-big-mart-sales-iii/) to compare data and complete assigned tasks. Below shows the data comparing the outlets with their sales, the fat contents sold from each outlet, and the prices of each item. Also, I show different machine learning models for predicting the sales and which models have the best outcome for the data. 

## Comparing Outlet Sales
First, we can look at each type of outlet that is in the data. We have four types of outlets grocery store, supermarket type 1, supermarket type 2, and supermarket type 3. In the graph below we can see how the outlet types stack up based on their sales. As shown supermarket type 1 is the highest in the sales total compared to the rest. 

![totaloutletsales](https://user-images.githubusercontent.com/88803320/135890482-071755ab-0501-4047-a686-d36e0577a85a.png)

## Fat Contents Sold From Each Outlet
Next, we'll take a look at the number of items sold based on their fat contents. In this graph, we are still comparing based on the three outlet types. Only this time with the data separated based on the fat contents of items they've sold. Across the board we can see that more low-fat items are sold at every outlet over regular items. For most of the outlets the difference is only by a few hundred. However, for supermarket 1 it's by 1500. Evidently, this is because they have the most in sales as seen in the graph before. Having more sales allows for a wider gap between the two fat contents.

![fatcontentsSold](https://user-images.githubusercontent.com/88803320/135890534-2262b7e2-1a60-405e-b622-378c2422fdd2.png)

## Prices Of Items From Each Store
Here we are comparing the different average prices that each store has for each item they sell. At first glance with this graph, we can see that supermarket type 2 has the highest average prices for most of the items. Taking the information we have gathered from the other graphs we can look at supermarket type 1 and their average prices. Now comparing those prices to the other outlets they don't have the highest nor the lowest prices. This could be a good reason as to why their sales do so well. It's a one-stop-shop to get all the items for the best average prices. 

![differentprices](https://user-images.githubusercontent.com/88803320/135890569-5bbbdbcb-835c-4912-8113-8816febaea5e.png)


## Machine Learning Models
For our machine learning models lets first take a look at all the r2 scores, rmse, and mae of all models used. Looking at the four models none of them really performed well.


![scores](https://user-images.githubusercontent.com/88803320/136480698-bfb375ca-f08a-43a4-9ebf-e8ee0810fb2b.JPG)


Here in this graph shows the r2 score split between the test and train data based on the max_depth parameter for the decision tree model. The train line as shown splits apart from the test after an r2 score of .6 based on how high you go with the max_depth.


![decisiontreee](https://user-images.githubusercontent.com/88803320/136480714-b495e0ee-389a-4680-9b15-6849dd1321fa.png)


Similarly, the graph above this shows the separation for the random forest model. However, with this graph, it's a little different. To get a better test score you have to have a higher max depth parameter. So here starts at 15 and ends at 22 the lines never come close like the other graph. 


![randomForestRegressorMax_depth](https://user-images.githubusercontent.com/88803320/136480702-ab4bd32d-b55f-4260-b8f7-fbf4ed78089e.png)


 So, I did some research based on the dataset and found that going to the [site](https://datahack.analyticsvidhya.com/contest/practice-problem-big-mart-sales-iii/) that the data was obtained from there are other submissions based on this dataset. [Here](https://github.com/Ragha93/Analytics-Vidhya---Big-mart-Sales-prediction) is the repository for the 138th rank submission to the site as of 10/7/21. looking through their ipynb file it's clear they are more focused on scoring for better mean absolute error rather than r2 scores. I ran their latest Random Forest model to check for its scores. When comparing my scores with the Random Forest model mine does slightly better regardless of the r2 score.

Training
r2: 0.5128513018943901\
mae: 892.3420527867046\
rmse: 1200.70603961225

Testing
r2: 0.5162120844553713\
mae: 858.6349565217126\
rmse: 1155.3180822193317

Just looking at one example wouldn't be enough so let's take a look at another.[This](https://github.com/dalwindr/AV_ML_Notebooks) submission is rank 23 on the leaderboard as of 10/7/21. Looking at the av_bigdata file inside is a linear regression model however they do use cross-validation they still have similar results as above. For this one the test and train scores a slightly better than the one before, but remain in the 50's and lower 1000's. As it's shown it's pretty consistent through mine and both of these models that getting good r2 scores is tough with this limited data set. I think if the data had a little bit more data it would be easier to get better testing scores.

train_r2 =0.57\
test_r2 =0.56\
train_rmse =1118.83\
test_rmse =1131.04

## Final Recommendations 

Finally, with using  all the info gathered based on the data and models I would personally recomend useing either the decision tree or random Forest models. With the Decision Tree model it has a lower rmse score than all other models. This means it can predict the prices closer than the other models within range of 1000 dollars. However, it base r2 scores are well lower than the bagged regression and random forest model. Being that it has lower r2 scores this means it didnt learn as well as the other models did. Now, the reason why I give it the choice is because of the differeance in r2 scores and rmse. The random forest model has a better r2 training score than the Decision tree, but a slightly worse rmse. The advantage with the random forest model is that it has properly learned from the data. The disadvantage being that the predictions are within range of 1105. Personally i would choose the Random forest model since it has learned from the data better and in the case of the predictions only being outlet sales an extra 105 isnt an enormus differance.


