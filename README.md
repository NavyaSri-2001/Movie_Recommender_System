Data Import, cleaning and manipulation:
1. Imported 2 datasets namely movies.csv and credits.csv from kaggle.
2. Merged 2 datasets on 'title' column
3. After inspecting the data removed unimportant columns and kept only #genres id, keywords, title,overview, cast, crew columns in the data.
4. Dropped null values and duplicate values
5. Using abstract syntax tree (ast) module created a function called convert and cleaned genres and keywords columns.
6. Wrote another function to fetch only top3 cast members from cast column which initially had a list of many values.
7. Wrote another function to fetch the director from the crew column because we are considering only director as the important technician in the crew
8. Split the overview column which was a string to a list of words
9. Removed spaces between names:
#Problem: to remove spaces between the words in the 4 columns-overview, genres,keywords and cast
#Reason: to give the exact recommendations eg: names
#Eg: "Sam Mendes"----->"SamMendes"
10. Created a new column called tags.
movies['tags']=movies['overview']+ movies['genres']+ movies['keywords']+ movies['cast']+ movies['crew']
11. Created a new data frame with only 3 final columns which are movie_id, title, tags
new_df=movies[['movie_id','title','tags']]
12. Converted the tags column which is a list of words into a string using join method.

Text Vectorization:
problem statement: user enters a movie name and we have to give 5 similar movie names based on the input
similarity is based on the tags
converting texts ino vectors
many techniques-Bag of words

Bag of words
1. Combined all the tags(concatenate all)
2. Took 5000 most common words from that large text
3. Created a data frame of (5000*5000)-each row is a vector here and you give the closest 5 vectors to a row as recommendations
4. stop words are not considered in vectorization. stop words= in, from, at, etc
5. Performed stemming on the tags column. #Stemming-
['loved','loving','love']---->['love','love','love']
6. #4806 movies----->4806 vectors
#each vector has 5000 numbers
#we have to calculate distance for every movie from all other movies
#more the distance, lesser the similarity
#Here we do not calculate Euclidean distance but cosinean distance
#cosinean distance---> angle btw 2 vectors not the point to point distance
#Euclidean distance is not a good measure in higher dimensions
#similarity is the inverse of distance
7. Created a function which outputs 5 similar movies when a movie title is given as input.
8. Created movie_list.pkl and similarity.pkl file using pickle.dump

Website using streamlit:
1. Wrote a function to fetch the poster of movie from the website api
2. using movie_list.pkl and similarity.pkl files wrote a function to fetch the top 5 similar movies.
3. Feteched the posters of those movies

