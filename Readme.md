# Vector Space based Information Retrieval System

The objective of this project is to build an Information Retrieval System based on the Vector Space Model. The IR system runs on a corpus of unstructured documents obtained from the English Wikipedia. It will make an end-to-end system that reads and processes the HTML text corpus and creates an easy-to-use index on them. This index is further used to query the corpus for relevant documents through single or multi-term queries and returns a list of top K documents that it finds most relevant. Different heuristics such as searching for synonyms, making champion lists and zone indexing have been applied to improve the search results and thus better the performance of the search engine. 

The IR system is built with the following characteristics:
1. The vector space model is used for computing the score between document and query.
2. lnc.ltc scoring scheme (based on SMART notation) is implemented for scoring.
3. The system supports free-text queries.

## The following packages need to be installed

    nltk
    bs4
    collections
    pyspellchecker
    pickle
    numpy
    requests

## Corpus:
English  Wikipedia  in  partially  processed  form  and  divided  into  approx  1500  files  is  available  at https://drive.google.com/drive/folders/1ZsnuEm7_N6aUwhjFpv-TZXFt4DiYex4t?usp=sharing. For this assignment, 20 wikis are chosen from the list of available wikis.  A single file in the corpus contains multiple documents.  These documents have a start and the end tag as:
start−tag:<  doc  id=  ”Document  id” url=  ”Wikipedia  URL” title=  ”Document  title” >end tag:< /doc>
All the text present in between the start and the end tag is associated with the same document.

## Structure
There are 2 functionalities:

   1. build_index
   2. test_queries

### build_index

This file creates an inverted index for documents in the folder wikis and stores it in a pickle file for further processing.

For lemmatization, WordNetLemmatizer from nltk is used.
### test_queries

It takes as an input a query and gives as output the top K documents. This file never reads the text corpus.

## User Interface

	Load index file from default location enter 0 else enter 1: 0

	Loading indices....

	Options:
	1. Normal search based on lnc.ltc scoring scheme
	2. Improvement using synonyms only
	3. Improvement using champion list
	4. Improvement using zone indexing
	5. Improvement using synonyms, championship list and zone indexing

	Main Menu

	Enter the query: tv

	Enter your choice (either 1, 2, 3, 4 or 5): 1

	Enter No. of documents to retrieve: 10
	['tv']
	Time:  0.0003894120000040857

	Number of retrieved documents: 10

	score = 0.1500, document_id = 26399, title = rms laconia
	score = 0.1132, document_id = 27344, title = telecommunications in slovenia
	score = 0.0915, document_id = 17056, title = kiyoshi atsumi
	score = 0.0891, document_id = 12114, title = telecommunications in greece
	score = 0.0878, document_id = 13039, title = gordon michael woolvett
	score = 0.0871, document_id = 27846, title = sorious samura
	score = 0.0862, document_id = 23875, title = phoenix (tv series)
	score = 0.0823, document_id = 12073, title = telecommunications in ghana
	score = 0.0803, document_id = 21813, title = naked news
	score = 0.0783, document_id = 20659, title = mv blue marlin

	Enter 1 to go back to main menu else 0 to quit: 1

## Implementation Details

For lemmatization, WordNetLemmatizer from nltk is used. Weighting scheme for ranked retrieval is lnc.ltc:

   1. Before asking any queries the system pre-calculates term-document weights, using the formula 1 + log10(term_frequency) and normalizes it by document vector's length (for cosine similarity). Results are stored in a Dictionary for fast future accesses. Also, inverse document frequency (idf) is computed for all terms.

   2. When free-text query is typed, the system computes term-query weights using formula (1 + log10(term_frequency_in_query)) * idf(term) and normalizes them. It requires linear time depending on the query length.

   3. To efficiently calculate document scores, term-at-a-time approach (bag of words) is used for query terms:

	for term, query_weight in term_query_weights.items():
		for doc_id, doc_weight in term_doc_weights[term].items():
			doc_id_score[doc_id] += query_weight * doc_weight

4. Time complexity will linearly depend on the number of term-document pairs for query terms.

    Documents are sorted by their scores in (O(N log N), where N is the number of documents, containing query terms) to show top relevant.





## Guidelines to run the project 
1. Run the 'build_index.py' file once. This will create two pickle files, namely 'index.pickle' and 'modified_index.pickle' in the same directory as of 'build_index.py'. The index has been created. If you change the corpus, this file has to be run again to change the pickle files.
	Command: 	python3 build_index.py
2. Run the test_queries.py file to test the queries. This file can be run multiple times for different queries, as long as the corpus is fixed.
	Command: 	python3 test_queries.py
   Input query, path of index(default or new), whether to consider improvements or not and value of k needs to supplied as and when asked in program.
## For more details look into REPORT.pdf 
