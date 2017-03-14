# What I want to cook today?

Last Saturday, I had a dream that I was thinking about what recipe is at a cafe.
At that time, I had already planned to go to Bath (I live in Bristol, UK). So I grabbed some articles and papers, then headed to Bath.

<img src="https://pbs.twimg.com/media/C6odvoXWYAEihhR.jpg" width="480">

I'm interested in how people decide what they cook today. I think what I eat is important because it becomes my body directly.

<img src="https://pbs.twimg.com/media/C6odxaKWoAIMR1a.jpg" width="480">

Interestingly, I feel that it might not be a big issue at the same time. I don't die right after I eat something bad.
And I guess most people think so too.

<img src="https://pbs.twimg.com/media/C6odw6IWcAA_XBl.jpg" width="480">

People research/invest something important or something making money. The advance of technology is something like this.

There are many examples which utilize the latest technologies to e-commerce, music stream services, ...
But I've hardly seen such examples in cooking.

I saw a man who has a scrap of paper (should be a shopping list) at a grocery store. Technology doesn't seem to be helping people.

<img src="https://pbs.twimg.com/media/C6odyMtWwAAb8NG.jpg" width="480">

It doesn't mean there is no hope in cooking. Or rather, we could change the current situation.

Anyway, I'm learning recommender systems.

# Recommender system

* What: help people discover diverse, serendipitous, trustable recipes based on users' preferences they might not have found by themselves
* Why: people can't read all recipes in Cookpad because time is finite
* How: technically, there are 2 approaches. Content-based approach and collaborative-based approach. And they are often combined.

# Content-based approach

which recommends **similar recipes**. There are 2 steps; Creating profile and matching them.

How to profile users and recipes is a key. It determines the accuracy of the model. To create a good model, domain knowledge is required.

<img src="https://cloud.githubusercontent.com/assets/883148/23915549/5be85070-08e1-11e7-9128-dcc46deaa548.png" width="480"><img src="https://cloud.githubusercontent.com/assets/883148/23915525/44c09b0a-08e1-11e7-8b95-0551f102b87d.png" width="480">

*User profile and Recipe profile*

The above part is "Understanding users and recipes".
I'm thinking many things when I decide what I cook today. Ingredients, nutritions, tools, cooking time, difficulty, type (breakfast, ...), cuisine (Japanese, ...), color, ...
How can I extract features from users and recipes?

One option would be vectorization. Some colleagues have already been trying to extract features using word2vec.
And I also found an interesting project on the Internet: [food2vec - Augmented cooking with machine intelligence – Jaan Altosaar](https://jaan.io/food2vec-augmented-cooking-machine-intelligence/)

Generally, [tf–idf](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) is used to extract features.
Actually (Briefly), it just counts the frequency of the word in the doc. So "extracting words which characterize the doc" would be more appropriate.

### Advantages
* We can recommend recipes which don't have much information like new recipes or not popular recipes
* We can describe why we recommend this recipe to users

### Disadvantages
* It could recommend recipes that the user liked in the past only (lack of serendipity)
* Domain knowledge is required to create profile

# Collaborative-based approach

which recommends what users will like based on similarity to **other users**.

<img src="https://upload.wikimedia.org/wikipedia/commons/5/52/Collaborative_filtering.gif" width="360">

### Advantages
* We can recommend diverse recipes
* Domain knowledge isn't required

### Disadvantages
* Cold start: a large amount of information on a user is required
* Scalability: there are millions of users and recipes
* Sparsity: users can't rate all recipes
* Clickbait
* Privacy
* ...

# Hybrid recommender systems

There are some ways to convert the 2 approaches.

* Making content-based and collaborate-based predictions separately then combining them
* Adding content-based capabilities to collaborative-based approach (and vice verse)
* Unifying the approaches into one model

# Examples in real world

* [Recommending music on Spotify with deep learning – Sander Dieleman](http://benanne.github.io/2014/08/05/spotify-cnns.html)
* [Deep Neural Networks for YouTube Recommendations (PDF)](http://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45530.pdf)

# What should I do next?

In the first place, what is changed after introducing a recommender system?
I get inspired from recommended recipes? Recommended recipes make me healthy? It's tasty? Or it makes me a better cook? It maximizes my happiness? What is my happiness?

I think there are 2 approaches.

1. Define the goal then break it down into small tasks
2. Anyway, build something

Well, aside from disadvantages, I will build recommender systems in each way and compare the results to see how good or bad.
At least, I can't imagine how recommender systems work now.
