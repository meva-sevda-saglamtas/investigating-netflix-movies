# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt

# Start code
netflix_df = pd.read_csv('netflix_data.csv')
netflix_subset = netflix_df[netflix_df["type"]=="Movie"]
netflix_movies = netflix_subset[['title', 'country', 'genre', 'release_year', 'duration']]
short_movies = netflix_movies[netflix_movies.duration<60]
colors=[]
for index, movie in netflix_movies.iterrows():
    genre = movie['genre']
    if genre == 'Children':  
        colors.append('red')
    elif genre == 'Documentaries':
        colors.append('blue')
    elif genre == 'Stand-Up':
        colors.append('green')
    else:
        colors.append('black')
colors[:10]
fig=plt.figure(figsize=(12,8))
plt.scatter(netflix_movies.release_year, netflix_movies.duration, c=colors)
plt.xlabel("Release year")
plt.ylabel("Duration (min)")
plt.title("Movie Duration by Year of Release")
plt.show()

print("Are we certain that movies are getting shorter?")
answer= 'no'
print(answer)
