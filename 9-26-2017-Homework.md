---
layout: default
---

# [](#header-1) Web Scraping Code and *Art Against Information*

I worked with Lulu over the past week on creating the following code: 

```
from bs4 import BeautifulSoup
import requests
import csv

result1 = requests.get("http://www.msnbc.com/")
content1 = result1.content
msnbc = BeautifulSoup(content1, "html.parser")

result2 = requests.get("http://www.foxnews.com/")
content2 = result2.content
fox = BeautifulSoup(content2, "html.parser")

result3 = requests.get("http://www.cnn.com/")
content3 = result3.content
cnn = BeautifulSoup(content3, "html.parser")

def get_text(soup, org):
	text = (soup.get_text().encode('utf-8'))
	with open(org+".txt", "w") as f:
		 f.write(text)
	#print "Created text file!"	

get_text (msnbc, "msnbc")
get_text (fox, "fox")
get_text (cnn, "cnn")

def trump_count(file_name):
	count = 0
	with open (file_name + ".txt", "r") as f:
		for line in f:
			count += line.count("Trump")
	print (file_name)
	print (count)

trump_count("msnbc")
trump_count("fox")
trump_count("cnn")
```

What the code is doing is going through three major news sources' websites to find how many times the homepage of each uses the word "Trump". It then prints out the name of the news source and the number of times it found said string. We were hoping this would show a trend of which news sources talk about him more. It did do that much of the time with CNN using it the most, however there is something more interesting that I noticed when running it again today. As you are aware, tragically there was a mass shooting last night. Because this is most likely dominating the news right now, as it probably should, there are exponentially less mentions of Trump across the board. Additionally Fox News which (surprisingly) usually mentioned Trump the least, is now mentioning him the most. This is a strange trend. 

This trend implies to me that Fox News is still talking about Trump in the scope of the shooting. Trump and the white house have commented on pieces of the shooting within the past 24 hours, and Fox News, a traditionally conservative news source, is probably reporting more on that than the two other less conservative sources. 

In terms of the article *Art Against Information: Case Studies in Data Practice* I found myself very drawn to the Spam Architecture Series and the Spam Plants Series. The 3D models of this abstract data really blows me away. I find it incredibly beautiful, and knowing that there is another layer to it makes it all the more special. 

I also love the layer to these two pieces specifically that is taking something as frustrating and ugly as spam, and turning it into these beautiful forms. The artists took one of the most prevelant parts of the internet, especially in 2006, and turned it into these beautiful forms. I really have no idea how these things are made, and have always wondered, which is one reason why they are so beautiful to me. 

[Go back](Philosophy-Of-Data).
