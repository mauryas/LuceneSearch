Information Retrieval
Programming Task 1
Command Line Information Retrieval system using Apache Lucene.

How to run the code :
Programme is coded in a way that it can be run just by passing the path of the directory having the files to be indexed. There is no need to look into the code or change any parameter for the code.
Code can be run in following mannar :
		java -jar IR_P01.jar [path to document folder]

Working of the Code :
The code will parse and index all the HTML files(.html) or the plain text files(.txt) , and even the subfolders if any present. A separate folder will be created which will have all the indexes of the files.
Porter Stemmer is used to stem the contents of the page even the query that is being passed . 
For eg - If we search for Fuzzy , then documents will be searched for the term and its stemmed version i:e Fuzzi.
When starting the program user will be prompted with option to re-use the already made indexes or create new. Even if the users chooses not to create a new index and there does exist any prior index then , program creates new index on its own.
If any query term is included in more that one document then all the documents are listed based on their ranks for the searched query. The output contains
	Name of the file.
	Rank of the document
	Path of the document
	Last modified time-stamp

For eg:
		"
			Searching Documents for query= fuzzy 
            1 documents found. Time :9
            Rank(Score):1(0.014279323) File Name:IR_P01_Documentation.txt File Path:/Users/apple/Documents/luceneTest/IR_P01_Documentation.txt   Time Stamp:11/30/2016 15:51:44
            Enter Search Query or press exit
				
				
Structure of the code :
Code consist of following classes , structure and working of classes will be discussed accordingly.
	LuceneMain.java (Main Class)
	FileTypeFilter.java
	Indexer.java
	LuceneConstants.java
	Searcher.java
	
LuceneMain.java (Main Class) : 
	This is the main class which will in turn call the other class for the respective functions.This class will have basic validations for the query searched and path provided .On the basis of the input from user(Exit/Indexin/Search) respective class will be called and corresponding function will be preformed.Ranking of the documents will be done on the rank score and will be listed according to the rank.
	
FileTypeFilter.java :
	This file will return a boolean value on the basis of the file format. Valid file formats accepted by program is .txt/.htm/.html , if any other format is places , a False value will be returned by the class.

Indexer.java :
	This class is used to stem the search query and index the respective files.Index will consist of file name, path and its content.After the contents of the file are stemmed using porter stemmer , files are then fed to indexer handled by Apache Lucene , to preform the indexing. Indexes are created in a subfolder where the files are placed.
In this class property tags of the html files are removed so that they do not alter the document search results.

LuceneConstants.java
	This class defines the constants used by the Apache lucene libraries.

Searcher.java
	This class will return the score of the documents corresponding to the searched query.Standard Analyzer (Part of Lucene) is used for analysing the query.

