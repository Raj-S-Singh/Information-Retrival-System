# Vector Space based Information Retrieval System

The objective of this project is to build an Information Retrieval System based on the Vector Space Model.  The  IR  system  runs  on  a  corpus  of  unstructured  documents  obtained  from  the  English Wikipedia. It will makean end-to-endsystem that reads and processes the HTML text corpus andcreates an easy-to-use index on them. This index is further used to query the corpus for relevant documents through single or multi-term queriesandreturns a list of top K documents that it finds most relevant. Different  heuristics  such  as  searching  for  synonyms,  making  champion  lists  and zone indexing have been applied to improve the search results and thus better the performance of the search engine. 

## Corpus:
English  Wikipedia  in  partially  processed  form  and  divided  into  approx  1500  files  is  available  athttps://drive.google.com/drive/folders/1ZsnuEm7_N6aUwhjFpv-TZXFt4DiYex4t?usp=sharing. For this assignment, 20 wikis are chosen from the list of available wikis.  A single file in the corpus contains multiple documents.  These documents have a start and the end tag as:
start−tag:<  doc  id=  ”Document  id” url=  ”Wikipedia  URL” title=  ”Document  title” >end tag:< /doc>
All the text present in between the start and the end tag is associated with the same document.

1. In the same directory that contains the 'test_queries.py' and 'build_index.py' files, create a directory called 'wikis' and paste the relevant wiki files to be used as the corpus for the system. For the results in the report, the wikis used are "AA - wiki_10 to wiki_29 (20 files)".
2. Run the 'build_index.py' file once. This will create two pickle files, namely 'index.pickle' and 'modified_index.pickle' in the same directory as of 'build_index.py'. The index has been created. If you change the corpus, this file has to be run again to change the pickle files.
	Command: 	python3 build_index.py
3. Run the test_queries.py file to test the queries. This file can be run multiple times for different queries, as long as the corpus is fixed.
	Command: 	python3 test_queries.py
   Input query, path of index(default or new), whether to consider improvements or not and value of k needs to supplied as and when asked in program.
