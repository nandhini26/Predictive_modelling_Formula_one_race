
Predictive Modelling of Singapore Grand Prix race

Problem Space:

The Marina Bay Street Circuit, also known as the “Singapore Street Circuit” is a street circuit around Singapore’s Marina Bay, which has been hosting the Singapore Grand Prix every year since 2008. Due to Singapore’s yearly high temperatures, its humidity, and the uneven nature of the street track and the heavy braking zones, the Singapore Circuit represents a physical challenge for both the drivers and cars and it is probably the most demanding race on the F1 calendar. Moreover, it is the longest race of Formula One Grand Prix season, taking up to two hours to complete.

The objective of this project is to find the potential drivers for the upcoming Singapore F1 season.
        
Key Technologies Used:

Tableau (Visualization software)

Scikit python

Flask python

Visual Code

Workflow pipeline:

1. Deployed a web scraper to gather practice time (Singapore race) from the official F1 auto-sport website. ( https://www.formula1.com/)

2.Data pre-processing

A.	Data cleaning
B.	Exploratory Data Analysis
C.	Weather API
D.	Feature Engineering

3. Machine learning Logistic Regression model (Best suited for my binary classification problem)

4. Tested with different machine learning algorithms and compared the performance.


Background

Getting inspired by watching Netflix F1 documentary movies with my son, I decided to start my journey to do my data analysis and predictive modeling for the upcoming F1 race in Singapore. This will cover the challenges faced during data analysis, learning outcomes from the project, and the results from the machine learning models and predictions. The project started with 6 sections — data mining, data processing and exploration, feature engineering, model building, the final results, and the visualizations. It leads us to questions such as which strategy works well for the fastest driver for every circuits since every circuit has different characteristics like altitude, weather, turns, and curves in the circuits. Every driver has to undergo practice season before their qualifying season. Every final race starting grid depends on their qualifying season position. It is most likely that the starting pole position is highly demanding to secure a podium position.

![Figure-1 project flow Diagram](images/Picture1.png)


Part1: 

1. Driver standings for only the Singapore race all through the 10 years.
2. Constructor standings for Singapore race all through the 10 years.
3. Results for Singapore races all through the 10 years
4. Qualifying season time for Singapore races all through the 10 years
5. Average pit stop time for Singapore races all through the 10 years

Part-2:

1. Writing a web scraping script for weather data from postman API
2. Writing a web scraping script for practice session time in Singapore race 2019

Part-3:

Merging the information appropriately without losing any vital characteristics of the race.

Since there were 10 years of Singapore Grand Prix data, and each race has ~20 drivers each, which gives me 200 rows. As we know, machine learning models work well with large data sets, which goes minimally to around 1000 k rows/observation. I supplemented my data sets with weather data, practice time. This would help us to do more feature engineering rather than an increase in data points suitable for more machine learning models. I have started my analysis with simple machine learning algorithms such as logistic regression, decision trees, K-nearest neighbors, which handles small datasets.


Feature Engineering

The primary consideration here for feature engineering is the values for missing qualification 1, qualification 2, and qualification 3 timings. The way qualification stages in Formula One work is that everyone will be racing for the fastest lap in each stage, and the slowest few will be cut off from the next stage. This session will determine the running order at the beginning of the race. This is often called setting the grid. The qualifying session is split into three parts, called Q1, Q2, and Q3. Q1 is 20 minutes long, followed by a seven-minute break. Q2 is 15 minutes long, followed by an eight-minute break. Q3 is 10 minutes long. During each part of qualifying, the fastest lap time set by a car is recorded. Drivers may run as many or as few laps as they wish.
After Q1 is complete, the eight slowest cars are eliminated (removed from) the qualifying session. This would include any cars that did not set a qualifying time. The remaining 18 car advance (move on to) Q2. The eight cars eliminated are placed in the last eight start positions, based on their fastest time from Q1. The procedure is repeated for Q2. The eight slowest cars from Q2 are placed in the 11 through 18 starting positions on the grid.

The top ten cars remain for Q3. After this final part of qualifying, the top ten starting positions on the grid are set. The fastest qualifier is placed in the first position, which is known as the pole position. This car will have an advantage at the start because they do not need to follow any other cars.

Q3 will then be left with 10 of the 20 drivers, and they will be racing for pole position. Hence, there will be missing values for Q2 and Q3 timings. The issue now is how to deal with them. I copied the Q2 round position holders’ timings to the Q3 column before copying Q1 round last 7 position drivers timings.

Machine Learning Model building

Finally, we had our data ready to feed into the model. My total dataset will be split into 2 parts, training set and testing set. 80% will be kept and trained on, to help with hyper-parameter of the top few machine learning models that perform well on this current dataset. 20% will then be kept for the testing phase, which will help me decide on the final model to use. I decided to test the model with 2019 Singapore race details. I compared the actual winning to predicted winning percentage. The best performing ML algorithms for the regression problem are tree-based algorithms, such as xgboost, and gradient boosted machines. This is expected given the small dataset we have. Gradient boosting seems to work much better. However, overfitting happened. Best algorithms for classification seem to be generative parametric models such as Gaussian Naive Bayes and plain old logistic regression due to the small dataset. However, the classification algorithm is best suited that the output will be probabilities, and thus give us a level of confidence in our predictions. Simple models are preferred in this case over complex ones like neural networks or support vector machines, given the small data set.

Results

However, the logistic regression shows the predicted probability of the drivers to get more level of confidence.

Conclusion: 

As shown in the above model prediction, Lewis Hamilton, Max Verstappen, has a 100 % probability of winning in the 2019 Singapore race, whereas Nico, Pierre have 99 % to win in the 2019 Singapore race. Antonio has a 95 % probability of winning. We can repeat this exercise for upcoming races to predict the winning probabilities for future races. COVID-19 has postponed all the future F1 races indefinitely as of now. Let us wait and see whether the predicted results come true.

Challenges:

1.	Data points are race-specific, not cumulative over the years.
2.	Weather Data collection is very challenging over the years over the different races across 35 years
3.	Practice season time has been collected for only one year, and Singapore race makes the Singapore race prediction modeling overfitting. (20 rows of information)

Future extension:

1. Implementing all the practice times, and compare final time with practice time, qualifying season time to find more insights. This will improve model training to achieve better test accuracy results.

2. Driver statistics such as Total lifetime points, lifetime winning, winning percentage, total races participated makes the model overfitting when the currently active drivers are filtered for the predictive modeling. Naive base algorithm will be tested with more driver-specific parameters.

3. Hypothesis will be derived for more analysis. Ex: Overtaking in the race affects the race points.



