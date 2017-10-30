---
layout: default
---

# [](#header-1) "Right to be Forgotten" and Search History Code

I am a little confused by the argument against the right to be forgotten. I understand that with this idea comes the potential for the loss of freedom of speech, but I think that in the state it is currently in it seems pretty fine. The fact that all of the information is still accessible just not as easily makes it seem totally fine to me. One could just go through other routes to find this information. It also seems as though it is almost all personal information that is published without permission. I really do not see much of an issue with it at all as it currently is. I think issue does come when talking about deleting it entirely and making it inaccessible. I also find issue in the idea of Google having to remove access to it from all of their sites. Just because it needs to be removed from one country does not mean that it needs to be removed totally. The other thing is I just rarely put trust in the government, so if a human wants something to be taken away from the government and for their information to be hidden and forgotten I find that totally reasonable. I may not be understanding this entirely as it is written, but it seems like something that primarily protects individuals, which I am almost always for. 

In an entirely different vein, I found playing with the search history quite fun. I found that finding specific words yeilded quite an interesting result. I also realized that by adding a space character before and after the word one was looking for you could actually find solely uses of that word, and not get the strings that had words containing that word. For example searing for " love " rather than "love" would yeild all strings with the word hate in them but not ones that would contain a word like glove. 

My python code is as follows:

```
import csv  

search_for = " hate "
replace_with = " love "
term_list = [] 
new_term_list = []
replaced_term_list = []
i = 0

with open ('queries_2017.csv', 'rb') as csvfile:
	reader = csv.reader(csvfile, delimiter = '\t')
	for row in reader:
		term_list.append(', '.join(row))
#Searches through term_list and looks for all strings that include the search_for phrase and puts them into new_term_list		
for i in term_list: 
	if search_for in i:
		new_term_list.append(i)
#Replaces the search_for phrase in new_term_list with the replace_with phrase and puts them into replaced_term_list
for i in new_term_list:
	replaced_term_list.append(i.replace(search_for, replace_with))

print replaced_term_list
```

What this code is doing is searching through the search terms and finding every one that includes the word "hate" and replacing it with the word "love". I thought that switching those two words was very interesting, especially in the current state of the world where hate is nearly omnipresent. The output is as follows

```
['louisiana love crime', 'nation of islam love group', 'medford gang love crime', 'i love you because when you were born, your father s', 'twitter love speech germany', 'twitter love speech germany withheld']
```

I find "love crime" which shows up a lot and "love speech" to be very interesting ideas. I also feel like this runs the risk of being seen as a falsely profound. I really do not think this is profound in any sense, I just think it is kind of interesting.

[Go back](Philosophy-Of-Data).
