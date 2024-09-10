
there are three ways of using a KG for the retrieval part of RAG:
* Vector-based retrieval: Vectorize your KG and store it in a vector database. If you then vectorize your natural language prompt, you can find vectors in the vector database that are most similar to your prompt. Since these vectors correspond to entities in your graph, you can return the most ‘relevant’ entities in the graph given a natural language prompt. Note that you can do vector-based retrieval without a graph. That is actually the original way RAG was implemented, sometimes called Baseline RAG. You’d vectorize your SQL database or content and retrieve it at query time.
      * no explainability 
* Prompt-to-query retrieval: Use an LLM to write a SPARQL or Cypher query for you, use the query against your KG, and then use the returned results to augment your prompt.
      * explainability, but need to write SPARQL query 
* Hybrid (vector + SPARQL): You can combine these two approaches in all kinds of interesting ways. Using the vector database for the initial search and then the KG for filtering provided the best results. 


Steps:
* Vector-based retrieval
    * ![image](https://github.com/user-attachments/assets/b92a3048-c513-452c-bfef-918411fe287d)
    * define schema
    * vectorize the data into the vector database (veaviate cluster can be used here)
    * semantic search using vector database (the vector takes the context of the terms into consideration. For example, if the term Mark Twain is mentioned many times near the term Samuel Clemens in the training data, the vectors for these two terms should be close to each other in the vector space. Likewise, if the term Mouth Cancer appears together with Mouth Neoplasms many times in the training data, we would expect the vector for an article about Mouth Cancer to be near an article about Mouth Neoplasms in the vector space.)
    * Similarity search using vector database: Similarity is calculated as distance in the vector space.
    * Retrieval-Augmented Generation (RAG) using a vector database: use the vector database to retrieve results which are then sent to an LLM for summarization
*  use a knowledge graph for data retrieval
    * ![image](https://github.com/user-attachments/assets/d90ca73c-531e-4a47-b00d-a7e62c9bc7ea)
    * turn data into RDF format
    * semantic search: find articles with tags
    * similarity search: rely on the tags associated with articles (Jaccard Similarity, computational efforts)
    * RAG using a knowledge graph: We already have a list of articles about mouth neoplasms saved as results from the semantic search above. To implement RAG, we just want to send these articles to an LLM and ask it to summarize the results.
        * First we combine the titles and abstracts for each of the articles into one big chunk of text called combined_text,
        * We then set up a client so that we can send this text directly to an LLM
        * Then we give the context and the prompt to the LLM:
* use a vectorized knowledge graph to test data retrieval
    * ![image](https://github.com/user-attachments/assets/c9df5911-ccdb-4046-a5ee-a79bac7d8efe)
    * We will add a URIs to each article in the database and then create a new collection in Weaviate where we vectorize the article name, abstract, the MeSH terms associated with it, as well as the URI. The URI is a unique identifier for the article and a way for us to connect back to the knowledge graph.
    *  create a new schema for the new collection with the additional fields
    *  vectorize the data into the new collection
    *  Semantic search / similarity search: vector-based retrieval + KG filter
    * RAG using a knowledge graph : results which are then sent to an LLM for summarization


### Reference
* https://towardsdatascience.com/how-to-implement-knowledge-graphs-and-large-language-models-llms-together-at-the-enterprise-level-cf2835475c47
* https://towardsdatascience.com/how-to-implement-graph-rag-using-knowledge-graphs-and-vector-databases-60bb69a22759
