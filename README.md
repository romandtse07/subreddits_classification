# Subreddit Classification - Identifying Harmful Content

**Profanity is not censored from data**

In this series of notebooks, we explore the idea of potentially creating an automated NLP based model that can learn what constitutes behavior worthy of a subreddit ban and apply this to future posts and communities.  There are two goals in this project, though only the first is expected to succeed: 

1. Training a machine learning model to correctly classifying a comment as belonging to either a parent subreddit or its banned child, using as little forum-specific vocabulary as possible.
2. Possibly extrapolating the model to classify the banned subreddit versus any other subreddit with no further information, possibly gaining some insight as to what generally constitutes a bannable offense.  

We attempt to acheive this by limiting the forum specific vocabulary as well as other words that are assumed unhelpful in detecting offensive text.  The hopes are not high for the second goal, since it is expected that most other threads are not like either thread.  The project is more an exploration into what we can possibly do to reach this goal using certain techniques - here, we use a Naive Bayes model and a Random Forest model.  Note that we limit our attention to r/incels and r/foreveralone comments at present with the assumption that if we can get high accuracy predicting comments between these two threads, we expect better accuracy comparing incels to an unrelated subreddit.  The simplifying assumptions are that r/incels is only filled with toxic comments, r/foreveralone never crosses the line, and that r/foreveralone shares its inoffensive language with other unbanned subreddits.

The first notebook restates most of this introduction and provides the code needed to pull data from the pushshift API, from which we obtain data.  Not all the data is used currently, notably the submissions.

The second notebok uses a count vectorizer to gain an intuitive understanding of the comments in each subreddit.  The data is then modelled using a multinomial Naive Bayes classifier.

The third notebook introduces several changes to the second, including rescaling of our numerical representation of words as well as using a different classification method.  Though it is therefore difficult to determine if it is the rescaling or the new classifier that is responsible for the change in result, we simply note the increased accuracy in distinguishing the two groups and continue the discussion from there.