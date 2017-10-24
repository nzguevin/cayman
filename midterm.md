### ~~YOU ARE WHAT YOU EAT~~
### ~~YOU ARE WHAT YOU READ~~
# YOU ARE WHAT YOU GOOGLE

## What does our Google search data say about us? Not much. Or at least not much of what we expected, according to our project.

Two weeks ago, we decided to look at Google Searches of individuals and analyze them. We were curious about the things we would be able to learn from ourselves (and others) if we looked at our searches. Inspired in Seth Stephens-Davidowitz’ Everybody lies: how Google search reveals our darkest secrets, we wanted to look at what Google could tell us about ourselves as individuals and not as members of the cluster of a region. There were many initial concerns we knew we’d hit from the beginning. We knew that it would be difficult to find enough people who trusted us with their search data, and we knew there would be 1000 different ways of analysing it. We ultimately decided to look at the most repeated words in the searches of a year, and analyze from there if we saw any parallels or connections. 

### THE CODE

In order to analyze the files, we needed to translate them out of .json format. We also needed for them to be sorted and counted, and then presented to us in a .txt file. This is all illustrated in the code.

### DIFFICULTIES

Breaking the words out the “event”, “query” and “query_text” was difficult. Nate, being the expert programmer he is, managed to solve the issue by using variables and the ‘append’ command. 
Lali struggled finding close friend’s who googled in English exclusively. This lead to some interesting questions about the project as a whole and the potential impact it could have if it were fully developed//expanded. 

### CONCLUSIONS

After looking into our most googled words and our friend’s, we came to the conclusion that it might be more difficult for Google (or anyone that can access this data) to draw some sound conclusions on who we are as individuals just from our searches. Looking at them made some things clear (like which TV shows we watch, or the cities we regularly visit/live in), but also revealed terms that could have ambiguous meanings. For instance, one of the subjects we used had googled the word “Trump” over 2000 times! The real question would be whether the subject is a supporter or avid opposer to the US president - either way, it would be impossible to tell (at least from how we analyzed the data). When looking at our personal data, we both felt that there was much about our personalities that was missing. Things we think about often but don’t Google Search, questions we answer in different ways, secrets that are too private (even for a browser). 

However,  there is still much potential to this project. The possibilities are endless - looking at matches within searchers, doing linguistic analysis on the phrasing and wording, finding recurring themes of search, looking at behavioural patterns, trains of thought, etc. 



## CODE 


	import json
	import io
	import re
	import operator
	from collections import Counter
	
	def parse_json(file_path, file_name, append):
		with open(file_path) as data_file:    
			data = json.load(data_file)
	
		x = []
		y = []
		z = []
	
		data = data['event']
		for item in data:
			x.append(item)
	
		for item in x:
			item = item['query']
			y.append(item)
	
	
		for item in y:
			item = item['query_text']
			z.append(item)
	
		if append:
			with io.open (file_name, "a", encoding = 'utf-8') as f:
				for item in z:
					item = item.upper()
					f.write(item)
					f.write(u'\n')
		else:
			with io.open (file_name, "w", encoding = 'utf-8') as f:
				for item in z:
					item = item.upper()
					f.write(item)
					f.write(u'\n')
	
	def word_counts(file_path, file_name):
		with open (file_path) as f:
			file = f.read()
	
		words = re.findall(r'\w+', file)
		word_count = Counter(words)
		sorted_words = sorted(word_count.items(), key=operator.itemgetter(1))
		sorted_words.reverse()
	
		with open (file_name, "w") as f:
			for item in sorted_words:
				f.write(str(item))
				f.write("\n")
			print("Wrote new file: " + file_name)
	
	parse_json("DrewSearches/2016-01-01 January 2016 to March 2016.json", "Drew.txt", False)
	parse_json("DrewSearches/2016-04-01 April 2016 to June 2016.json", "Drew.txt", True)
	parse_json("DrewSearches/2016-07-01 July 2016 to September 2016.json", "Drew.txt", True)
	parse_json("DrewSearches/2016-10-01 October 2016 to December 2016.json", "Drew.txt", True)
	parse_json("DrewSearches/2017-01-01 January 2017 to March 2017.json", "Drew.txt", True)
	parse_json("DrewSearches/2017-04-01 April 2017 to June 2017.json", "Drew.txt", True)
	parse_json("DrewSearches/2017-07-01 July 2017 to September 2017.json", "Drew.txt", True)
	parse_json("DrewSearches/2017-10-01 October 2017 to December 2017.json", "Drew.txt", True)
	
	parse_json("NateSearches/2016-01-01 January 2016 to March 2016.json", "Nate.txt", False)
	parse_json("NateSearches/2016-04-01 April 2016 to June 2016.json", "Nate.txt", True)
	parse_json("NateSearches/2016-07-01 July 2016 to September 2016.json", "Nate.txt", True)
	parse_json("NateSearches/2016-10-01 October 2016 to December 2016.json", "Nate.txt", True)
	parse_json("NateSearches/2017-01-01 January 2017 to March 2017.json", "Nate.txt", True)
	parse_json("NateSearches/2017-04-01 April 2017 to June 2017.json", "Nate.txt", True)
	parse_json("NateSearches/2017-07-01 July 2017 to September 2017.json", "Nate.txt", True)
	parse_json("NateSearches/2017-10-01 October 2017 to December 2017.json", "Nate.txt", True)
	
	parse_json("DylanSearches/2016-01-01 January 2016 to March 2016.json", "Dylan.txt", False)
	parse_json("DylanSearches/2016-04-01 April 2016 to June 2016.json", "Dylan.txt", True)
	parse_json("DylanSearches/2016-07-01 July 2016 to September 2016.json", "Dylan.txt", True)
	parse_json("DylanSearches/2016-10-01 October 2016 to December 2016.json", "Dylan.txt", True)
	parse_json("DylanSearches/2017-01-01 January 2017 to March 2017.json", "Dylan.txt", True)
	parse_json("DylanSearches/2017-04-01 April 2017 to June 2017.json", "Dylan.txt", True)
	parse_json("DylanSearches/2017-07-01 July 2017 to September 2017.json", "Dylan.txt", True)
	parse_json("DylanSearches/2017-10-01 October 2017 to December 2017.json", "Dylan.txt", True)
	
	parse_json("LaliSearches/2016-01-01 January 2016 to March 2016.json", "Lali.txt", False)
	parse_json("LaliSearches/2016-04-01 April 2016 to June 2016.json", "Lali.txt", True)
	parse_json("LaliSearches/2016-07-01 July 2016 to September 2016.json", "Lali.txt", True)
	parse_json("LaliSearches/2016-10-01 October 2016 to December 2016.json", "Lali.txt", True)
	parse_json("LaliSearches/2017-01-01 January 2017 to March 2017.json", "Lali.txt", True)
	parse_json("LaliSearches/2017-04-01 April 2017 to June 2017.json", "Lali.txt", True)
	parse_json("LaliSearches/2017-07-01 July 2017 to September 2017.json", "Lali.txt", True)
	parse_json("LaliSearches/2017-10-01 October 2017 to December 2017.json", "Lali.txt", True)
	
	parse_json("MaryAliceSearches/2016-01-01 January 2016 to March 2016.json", "MaryAlice.txt", False)
	parse_json("MaryAliceSearches/2016-04-01 April 2016 to June 2016.json", "MaryAlice.txt", True)
	parse_json("MaryAliceSearches/2016-07-01 July 2016 to September 2016.json", "MaryAlice.txt", True)
	parse_json("MaryAliceSearches/2016-10-01 October 2016 to December 2016.json", "MaryAlice.txt", True)
	parse_json("MaryAliceSearches/2017-01-01 January 2017 to March 2017.json", "MaryAlice.txt", True)
	parse_json("MaryAliceSearches/2017-04-01 April 2017 to June 2017.json", "MaryAlice.txt", True)
	parse_json("MaryAliceSearches/2017-07-01 July 2017 to September 2017.json", "MaryAlice.txt", True)
	parse_json("MaryAliceSearches/2017-10-01 October 2017 to December 2017.json", "MaryAlice.txt", True)
	
	word_counts("Drew.txt", "DrewWords.txt")
	word_counts("Nate.txt", "NateWords.txt")
	word_counts("Dylan.txt", "DylanWords.txt")
	word_counts("Lali.txt", "LaliWords.txt")
	word_counts("MaryAlice.txt", "MaryAliceWords.txt")
	
[Go Back](index).