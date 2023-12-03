# Music Organizer Overview

# Initial Proposal:
The problem that I am trying to solve with this program is organizing a large amount of music into several playlists. My reasoning for this is that I, like many others, enjoy many different types of music of all different genres and vibes, which can make it very hard to organize as there are so many factors of a song to consider. An example of this would be if I have music of two different genres but that have the same vibe, or music of two different vibes but the same genre, how should I go about organizing them. Typically this would lead to me attempting to make some playlists then getting overwhelmed and flustered to the point where I just give up. In order to combat this, the program will evaluate each some, and then group the songs together based on their stats within each category. This then would result in a playlist that all flows together and can be played on shuffle without there being a dramatic change in music half way through. 
How I would go about implementing this is first, similar to my first choice, is that I would find a model which is able to evaluate music and break it down into different statistics. Then based on how many statistics I decide to have for each song, let's say 10, I would then graph the songs in a 10D space which could then be divided into how many playlists we would like. The program would do this by prompting the user for stats they want for the songs to share and then how many playlists would be created where the songs would then be sorted by those stats and then divided into several groups. The program could then also create a playlist given certain “tags”  so if you want sad pop songs it could pull all the songs that are considered both sad and pop. This could also be implemented via simply applying filters to a database in order to create a playlist with certain “tags”. What method I end up going with would probably be determined by the tools already created, whichever is easier to implement. 

# Progress Report 1:
Much of my time so far has been spent figuring out how to use the different tools I discussed in my project proposal. First of all I have been watching videos and reading articles about how to not only find ML models on HuggingFace but then also use them for your own project. Next I began researching the Spotify API in order to get a better understanding of how to get a database of music to reference from. With this research being done I figured I would go with my method of applying filters to a database in order to generate certain playlists. This I figured would be much easier with my experience in my Databases class and not having to figure out how to graph these attributes in a multi-dimensional space. Now I am beginning to look more into how to connect the Spotify API to the ML algorithm in order to pull songs from the Spotify database that I would like to classify. After that I plan on creating some sort of data structure myself in which I will store each song with their classification.
Once I have figured out how to do that I will need to figure out how I would want the playlist creation to go as I am not sure how I want to go about doing that as I am stuck between two options. First organize each song into a non-distinct playlists, such that some songs may appear in multiple playlists. Or second if I should ask the user for attributes in which it then pulls songs and creates a playlist which follows those tags. I am leaning more towards the second option but I am going to have to figure out how to match keywords with the tag on the actual songs.

# Progress Report 2:
I began coding this project by linking my personal spotify using the spotify api, this however was made easy with the research thatI did t I did prior to progress report one. Where I ran into trouble however was finding a model I could use on HuggingFace. This was because the model I thought I would be using did use the same classifiers as the spotify api. This resulted in the api and model not being able to work together leading me to find a new model. This again did not go to plan as every model that I found that used the same features as the spotify api was private and thus I couldnt use it. This then led me finally to bite the bullet and create my own neural network to train on.
That Then led me to first find data that I wanted to train on. This Resulted in me googling pre-classified music based on mood as well as their corresponding spotify features. This resulted in me finding a data set on Kaggle, which I linked in the notebook, that I then cleaned up and used as testing/validation data. Once I had this data loaded into the notebook I had to create the model to classify the data. I began this progress using a mix of both pytorch and sklearn which are both very popular machine learning python libraries. The initial model that I created was a single dimension model, which although very simple, was also very inaccurate with an accuracy below 60%. This I found very underwhelming which led me to aim for a model which had at least 80% accuracy. This was obtained using a multidimensional model which was much more complicated and much more accurate. Once this model was trained and validated, I loaded in the playlist from my spotify account and had it classify the songs. Then from this I added the songs into a dictionary where the song_id was the key and then the song name, artist name, and mood which I then plan to grab from when making a new playlist.
Now in terms of where I want to go from here, first I want to possibly tweak the model and make it more accurate, possibly approaching 90%, and then also possibly add more training data with possibly some more possible moods. The reason I want to do this is that the current model is only trained to organize based on 4 moods; happy, sad, calm, and energetic, which I may want to bump to 5 moods if I can find one that I would want to add. Then I also want to add some more modern music as the training data seemed to be older music. Then from there I want to add a simple user interaction in which they pick one of the moods and then the program lists all the songs which are classified under that mood.

# Progress Report 3:
Because I have been very busy the past week I have to stray a bit away from the plans that I made during the last progress report. Instead of fine tuning the model this week I decided to instead just implement a simple interactive menu in which it’ll display the songs with the moods of your choice. So now the program does actually organize the music based on moods but there are still more features that I would like to implement. First of all I obviously still want to fine tune the model to possibly get it up to 90% accuracy and then also add some more modern music to the database. Then in the actual music recommendation, I would like to implement a feature which could add the selected songs to a playlist within your spotify account if prompted to do so. I feel like this could ultimately streamline the process which I feel like could be a very useful feature, especially if you agree with the models suggestions. So although I strayed away from my plans, goals were still accomplished and with Thanksgiving break approaching I should have plenty of time to make up for work from my busy schedule last week.

# Final Report:
Within this final stretch of this project I made the majority of the adjustments I said I was going to make. The first change was the impproved accuracy of the model, I made it so the training ends once the accuracy fails to increase resulting a accuracy that reaches up to 85%. Next the feature that I implimented was the abilty to add the playlist to your spotify account. This now stream liines the process of organizing your music and then given you the abiliy to access and listen to the new organized playlist. Finally the change the I desided not to go thorugh with was the addition of my own classifyed saongs to the training/validation data. My reasoning for this is the bias this would impliment. This is because I would no longer be able to organize my own playlists as the model was trained on some of the sonsg thus would have a bias and thus not be able to properly organize the songs from an "unbiased" view.
