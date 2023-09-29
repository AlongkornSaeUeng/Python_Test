import gazpacho
import requests
url = "https://www.imdb.com/search/title/?groups=top_100&sort=user_rating,desc"
html = requests.get(url)
imdb = html.text
imdb = gazpacho.Soup(imdb)

c_titles = []
c_ratings = []
c_genres = []
c_certificates = []
c_runtimes = []
c_gross = []

titles = imdb.find("h3",{"class":"lister-item-header"})
for title in titles:
    c_titles.append(title.strip())
print(c_titles)

ratings = imdb.find("div",{"class":"inline-block ratings-imdb-rating"})
for rating in ratings:
    c_ratings.append(float(rating.strip()))
print(c_ratings)

genres = imdb.find("span",{"class":"genre"})
for genre in genres:
    c_genres.append(genre.strip())
print(c_genres)

#get age certificate of the movie
certificates = imdb.find("span",{"class":"certificate"})
for certificate in certificates:
    c_certificates.append(certificate.strip())
print(c_certificates)

#get lenght of the movie
runtimes = imdb.find("span",{"class":"runtime"})
for runtime in runtimes:
    c_runtimes.append(runtime.strip())

#delete "min" string in list
i = 0
while i < c_runtimes.__len__():
    c_runtimes[i] = c_runtimes[i].split(" ")  
    c_runtimes[i] = (c_runtimes[i])[0]
    i+=1
print(c_runtimes)

#get gross,votes,top250 (nv) of the movie
gross =  imdb.find("span",{"name":"nv"})
for gross in gross:
    c_gross.append(gross.strip())

#filter gross from nv.list
y=0
for x in range(1, c_gross.__len__(), 3): 
    c_gross[y] = c_gross[x]
    y+=1
print(c_gross)


