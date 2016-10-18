Thomson Reuters
USA Election Simulation
@ Khaled Ammar

White house run app: pretend to be a candidate, capability score

How did we build this?

data acquisition
- reuters polling explorer
- questions, responses, participants

initial analysis
- data is skewed
- power law distribution
- answers per question vs # of questions

data cleansing
- filter non relevant data
	- recent responses (>2014)
	- popular questions (> 200 responses)
	- valid participants (> 50 responses)
- improving sparse matrix
	- collaborative filtering to fill in missing values, predict values using recommendations
	- didn't work very well, user based model using non negative matrix factorization
	- converts users vs questions to users to topics and topics to questions
	- eigen candidate vector: represent hypothetical candidate for one topic
	- voronoi clustering: matching data points of users to eigenvector similarity

data analysis with a user based model
- computing electability score
	- collect answers to question
	- count supporters
		- cluster population into groups and find popularity of candidate in each group
		- hard to describe each group

data analysis with a questions based model
- use elastic search
- apply TFIDF to find similar questions
	- EX: gun related questions --> marijuana laws? performance good, but not quite optimal
- use deep learning --> question to vec
	- EX: gun ownership --> firearm, automatic weapons, machine guns
- using question to vec for electability score
	- robust, sparse model
	- allows for question diversity, new and different questions
	- can match questions to the model based on their meaning
	- electability per question = # agreement / # answers, where supports agree with candidate on most questions
	- agreement strength

summary of white house run app
- 1 million responses
- understand data
- applied models
- NLP approach to match questions
- build model to score responses
- demographics analysis of candidates