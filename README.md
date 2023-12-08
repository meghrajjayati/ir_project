# 50.045 Information Retrieval Project 
## ChefGpt:Recipe Recommendation 
Finding the perfect recipe online can be a daunting task, especially when one has to browse through countless options and check the availability of ingredients. To address this problem, we have developed a Recipe Recommendation system that generates personalized recipes based on the user’s input of ingredients. The system provides the recipe name, the list of ingredients, the step-by-step instructions, and the source URL for each recipe. In this report, we will present the problem statement, the objectives, the methodology, the results, and the conclusion of our system. This brings us to the problem statement: 

### Data Collection
Our recommedation system is built in accordance to two types of data. 
1.We are using the “Food Ingredients and Recipe Dataset with Image Name Mapping” dataset on Kaggle which was scraped from the Epicurious Website. It contains 13,000 rows of recipes with the recipe name (title), ingredients (Ingredients) and instructions (instructions). We performed preprocessing of the dataset which involved parsing using keyword extraction to get the important keywords describing each ingredient from the original ingredients column to another column of the final set of ingredients for each recipe. This dataset is to provide a large collection of documents for use in the Information Retrieval system in our RAG implementation.
The Kaggle dataset does not contain a source URL for each recipe, so we used our own code to check if the provided source URL by the LLM is valid.
2. Scraped Data from All Recipes

### IR Models Used
We experimented with the follwoing models to construct our recommendation system:
1. Cosine Similarity  (Tf-idf)
2. Doc2Vec  (with query expansion, only with course information data)
3. BM25
4. BM25  (with query expansion)
5. Doc2Vec and BM25  
6. FAISS
7. Ensemble: FAISS + BM25 
8. BM25 and TFIDF (RAG)

### LLM Generation 
We utilised Mistral Instruct LLM. We verified outputs using BERT Score and Bleu Score.

### LLM Generation 
We utilised Mistral Instruct LLM. 

### RAG  
1. BM25
2. Tf-idf Vectoriser + BM25
3. BM25 + FAISS 


### Folder Struture
```
- scripts                                       
        - validation_set.ipynb                        # generate the sample queries for IR 
        - retreival-methods_ir.ipynb                  # All IR methods + MAP, NDCG and MRR  Score 
        - rag-bm25_entfidf.ipynb                      # RAG ensembled (bm25+tf-idf) (includes bleu scores)
        - rag-bm25-only.ipynb                         # RAG bm-25 (includes bleu score)
        - pe-jayat (1).ipynb                          # LLM Generation (basic prompt) and associated bleu score
        - parsing_test.ipynb                          # keyword extraction from database
        - bert_score.ipynb                            # Bert score --llm generation
        - LangChain BM25 + Ensemble.ipynb             # Hybrid Search RAG





    - final_recipes  
        - final_recipes.xlsx                          # parsed and processed dataset
        - validation_set.xlsx                         # sample query for IR methods


    
