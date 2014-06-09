#Loading the File


So first we have to import the url and csv library so python knows what to do with it.

````import url````
````import csv````

and here is the url we are opening using the urlretrieve function built in to python: 

````urllib.urlretrieve("http://jonathansoma.com/lede/dogs.csv","dogs.csv")````

So now that we have retrieved it, we have to tell python to read it in a csv format:
````dog_file = open("dogs.csv", "rb")````
````dogscsv = csv.reader(dog_file, delimiter=',')````

Then we turn it into a list so later we can iterate over that list. We assigned the variable 'rows' to this list so that each individual dog is an item within the larger list. So rows[1] is a dog and rows [2] is a different dog, etc.

````rows = list(dogscsv)````

The first question asked how many dogs there were in New York so first we have to ask how many rows are in the list:

````print len(rows)````

From this list, we subtract 1 to get the actual number of dogs because we don't want to include the 'header' row (i.e. row[0]) in our count.

Next we were asked to asked to find all the dogs in each bourough in New York. We can do this by setting the count to 0 for each borough, then iterating over the whole list and asking the computer to only input the items that match our borough criteria by adding 1 to the original count (which begins at 0. The) code looks like this:

````
with open('dogs.csv', 'rb') as csvfile:
    dogcsv = csv.reader(csvfile, delimiter=',')
    count=0
    for row in dogcsv:
        if row[9] == "Manhattan":
            count=count+1
    print count````

I just did this for each borough but it's easier if you set all the boroughs to = 0 instead of the 'count' variable at the beginning. So instead, Brooklyn = 0, Staten Island = 0, and then iteraring over the whole list for each. Oh well, next time....


Ok, so next we have to find how many dogs named Max are in Bed-Stuy so there are two variables now. The first thing I did was define Bed-Stuy by creating a new list with all the Bed Stuy zipcodes in them. Then, like last time, I set the count to 0 and then did a for loop that says, "if row[10] (i.e. the zipcode 'column') is in the list I created for bedstuy AND row[0] (the name 'column') is equal to Max, then add it to the count. Then I printed the count and it gave me the answer. 
````
with open('dogs.csv', 'rb') as csvfile:
    dogcsv = csv.reader(csvfile, delimiter=',')
    bedstuy_list= ["11205", "11206", "11216", "11221", "11233"]
    count=0
    for row in dogcsv:
        if row[10] in bedstuy_list and row[0] =="Max":
            count=count+1
    print count````

I repeated this for dogs named Max on the Lower East Side:
````
with open('dogs.csv', 'rb') as csvfile:
    dogcsv = csv.reader(csvfile, delimiter=',')
    LES_list= ["10003", "10002", "10009"]
    count = 0
    for row in dogcsv:
        if row[10] in LES_list and row[0] == "Max":
            count = count+1
    print count````


Then we were asked to find all the dogs with the color 'brindle' as their first or second color. Here's what the code looks like:

````
with open('dogs.csv', 'rb') as csvfile:
    dogcsv = csv.reader(csvfile, delimiter=',')
    count=0
    for row in dogcsv:
        if (row[4] == "BRINDLE") or (row[5] == "BRINDLE"):
            count=count+1
    print count````

This is an 'or' rather than 'and' statement because we want both those dogs that have it as either one or the other rather than the dogs that have it listed for both. 




