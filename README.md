# Search Intent Classification for Google Ads Search Queries / Chen Portsia

## Introduction:
Allocating marketing budgets efficiently in Google Search can be challenging due to the vast number of keywords and the varying user intents behind search queries. This project aims to optimize marketing budget allocation by classifying user search intents using the Google Ads Keyword Planner. By understanding the intent behind each query, marketing analysts can better align their strategies with user needs and improve overall campaign effectiveness.

![image](https://github.com/ChenPortsia/User-intent-classification/assets/108417183/7c963d5f-b44b-4208-b6fb-9213e78268d0)

## Business Question:
How can we classify search queries in Google Ads Keyword Planner to optimize the allocation of marketing budgets based on user search intent?

## Explanation of Search Intent in the Marketing Field:
Search intent refers to the purpose behind a user's query on a search engine. Understanding search intent is crucial for optimizing content to meet users' needs and improve search engine rankings. There are several types of search intent, primarily categorized into four main types:

### Informational Intent:
- **Goal**: The user is seeking information or answers to specific questions.
- **Examples**: "What is the capital of France?", "How to bake a cake", "Benefits of yoga".
- **Content Focus**: Articles, blog posts, tutorials, how-to guides, and educational content.
  
### Navigational Intent:
- **Goal**: The user wants to go to a specific website or find a particular webpage.
- **Examples**: "Facebook login", "YouTube", "New York Times homepage".
- **Content Focus**: Homepages, login pages, specific sections of a website.
  
### Transactional Intent:
- **Goal**: The user intends to make a purchase or complete a transaction.
- **Examples**: "Buy iPhone 13", "Subscribe to Netflix", "Cheap flights to Paris".
- **Content Focus**: Product pages, service pages, pricing information, calls to action, and e-commerce platforms.
  
### Commercial Investigation:
- **Goal**: The user is researching products or services and considering a purchase but hasn't made a final decision.
- **Examples**: "Best laptops 2024", "Nike vs Adidas running shoes", "Top smartphones under $500".
- **Content Focus**: Reviews, comparison articles, product recommendations, and buying guides.

## Google Ads Keyword Planner Example:
![image](https://github.com/ChenPortsia/User-intent-classification/assets/108417183/87e92134-b4c4-4f95-9f34-c75c9acfdab7)

## Methodology:
1. **Data Collection**: Utilize the Google Ads Keyword Planner API to gather keyword data related to a specific search query and, for future use, automate keyword extraction.
2. **Keyword Filtering**: Identify and filter high-volume keywords to focus on the most impactful queries.
3. **Query Shuffling**: Shuffle low-volume queries to generate new, potentially more relevant keywords using bigram extraction and natural language processing (NLP) techniques.
4. **Intent Classification Research**: Apply zero-shot classification models and OpenAI models to classify the search intents of the queries.
5. **Model Evaluation**: Compare the accuracy and efficiency of different models in classifying search intents.
6. **Choose Queries for Investment**: Generate labels using the model with the best performance and return the queries most likely associated with users who have transactional intent.

## Steps Taken:
1. **Google Ads API Integration**: Successfully integrated the Google Ads API to fetch keyword data for the query "Kitchen remodeling service" as a use case.
2. **Keyword Analysis**: Analyzed and filtered keywords based on their monthly search volumes, focusing on high-volume keywords.
3. **Extend the List of Relevant Queries**: Shuffled low-volume queries and applied NLP techniques to find related queries with higher monthly search volumes.  
   - **Bigram Extraction**: Extracted common bigrams to aid in logically shuffling low-volume queries, treating them as one word (e.g., "near me", "kitchen renovations").
   - **Query Shuffling**: Used SpaCy to shuffle low-volume queries and generate new potential keywords, avoiding conjunctions like "and", "of", "on", etc.
   - **Grammatical Filtering**: Implemented TextBlob to ensure the shuffled queries were grammatically correct.
   - **Re-search in Keyword Planner**: Searched for the new keywords in the Keyword Planner and extracted a list of relevant queries with high monthly search volumes.
4. **Zero-Shot Classification**: Tested several zero-shot classification models (e.g., BART, DeBERTa) to categorize queries into search intent categories: Informational, Navigational, Transactional, and Commercial. 
   - Different label formats were tested, and results improved as labels became more specific.
5. **Model Comparison**: Evaluated model performance and identified the best-performing model for search intent classification.
   ![image](https://github.com/ChenPortsia/User-intent-classification/assets/108417183/7d042d98-7b75-4d5d-84d2-51c9155f5476)
6. **OpenAI Model Integration**: Utilized OpenAI models to enhance classification accuracy and efficiency.
7. **OpenAI Model Comparison**: Evaluated the performance of OpenAI models, identifying the best-performing one.
   - Used the following prompt for classification:  
     **System prompt**: "You are a professional SEO expert"  
     **Main prompt**: "Classify the following query into one of the search intent types: 'Informational', 'Navigational', 'Transactional', 'Commercial'. Keep the response short in the format 'Label'."
8. **Choosing Values**: Examined temperature performance in specific cases to improve accuracy.
9. **Generating OpenAI Models**: Applied the classification for various OpenAI models, such as 'gpt-4o', 'gpt-4', 'gpt-4-turbo', and 'gpt-3.5-turbo'.
   ![image](https://github.com/ChenPortsia/User-intent-classification/assets/108417183/9c9a13b5-f370-4d75-8a45-aa08b0899d76)

   The improvement from "gpt-3.5-turbo" to "gpt-4o" resulted in 95% accuracy.
10. **Generating Labels**: Used the chosen model to label all query lists constructed in Step 3.

## Results:
For the query "Kitchen remodeling services", 57 out of 255 queries were identified as frequently searched and associated with transactional intent. Sample chosen queries include:
- 'kitchen replacement countertops near me'
- 'cost kitchen renovation full'
- 'kitchen cabinet remodeling near me'
- 'redo kitchen cabinets'
- 'cost resurfacing cabinet kitchen'
- 'services bathroom complete'
- 'kitchen cabinets remodeling near me'
- 'kitchen remodel near me'
- 'cost to replace kitchen cabinets'
- 'local contractors kitchen near me'

## Remaining Issues and Further Investigation:
- **Ground Truth**: The labeled data is based on a small sample. To improve accuracy, a larger labeled dataset is needed.
- **Query Ambiguity**: Some queries can belong to multiple intent categories, complicating classification. The field and business objectives may influence classification.
- **Scalability**: Query shuffling and filtering processes need optimization for larger datasets.
- **Cost**: To improve cost-efficiency, consider generating labeled data using one-shot classification with gpt-4o and training on the generated data using RNN.
- **Summation**: Design the code so users can input a query and field to generate a list of related queries directly.

## Further Steps:
The next phase of the project is to generate content tailored to each search intent type, beyond selecting the best queries for investment.
