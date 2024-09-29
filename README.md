# Twitter Response Analysis on BSI Ransomware Incident (2023)
In 2023, BSI Bank experienced a nationwide disruption due to a ransomware attack, which garnered significant attention from the public. Many users took to Twitter (now known as X) to express their opinions, frustrations, and discussions surrounding the incident. This project aims to model and analyze these tweets to understand the discussions and personas related to this event.

The project includes clustering and topic extraction approaches to provide a comprehensive analysis of user conversations on Twitter, giving insights into how the public responded to the BSI ransomware attack.

## Dataset Description
The dataset contains tweets related to the BSI ransomware incident and includes the following columns:
Column  | Description
------------- | -------------
Index  | Original index of the tweet
URL  | URL link to the original tweet
Date  | Date and time when the tweet was posted
Tweet  | The content of the tweet
ID  | Unique tweet identifier
Username  | Username of the person who posted the tweet
Replies  | Number of replies the tweet received
Reetweets  | Number of retweets
Likes  | Number of likes the tweet received
Quotes  | Number of quote retweets
conversationId  | ID of the conversation thread the tweet belongs to
Language  | Language of the tweet (e.g., 'in' for Indonesian)
Links  | Any links shared in the tweet
Media  | Media content in the tweet (if any)
Retweeted Tweet  | Whether the tweet is a retweet
Bookmarks  | Number of bookmarks

## Methodology
The project is structured into four key tasks:
1. **Clustering (k-Means)**
   - **Objective:** Group tweets into clusters based on their similarities.
   - **Approach:** Apply k-Means Clustering to categorize tweets into groups. Different values of k are tested to identify the optimal number of clusters.
   - **Evaluation:** The silhouette score is calculated for different k values to determine the optimal number of clusters. However, this method is limited to providing clusters of similar tweets without further analysis of their content.

2. **Persona Analysis for Clusters**
   - **Objective:** Perform persona analysis based on the clusters obtained from k-Means.
   - **Approach:** Examine the key characteristics of each cluster (e.g., recurring themes in tweets, sentiment) and derive user personas such as “Concerned Customers” or “Critics.”

3. Topic Extraction (LDA)
   - **Objective:** Extract the hidden topics discussed within the tweet dataset using Latent Dirichlet Allocation (LDA).
   - **Approach:**
       - LDA assumes each tweet is a combination of several topics, and each topic is defined as a distribution of words.
       - By applying LDA, we can uncover the latent themes or topics discussed by users, such as “Frustration with BSI,” “Security Concerns,” or “Banking Service Feedback.”
   - **Justification:** The LDA approach goes beyond simple clustering. While k-Means assigns tweets to clusters based solely on content similarity, LDA provides detailed insights into the topics being discussed, revealing the nuanced themes in user conversations.

4. **Persona Analysis for Topics**
   -  Objective: Compare and contrast the personas discovered through topic extraction with those from clustering.
   -  Approach:
      - After extracting topics using LDA, we can perform persona analysis to understand what types of users are associated with each topic.
      - For example, users discussing "Security Concerns" might belong to a persona of technical experts, while those discussing "Service Issues" could be regular banking customers.

## Comparison of Clustering and Topic Modeling:
1. **k-Means Clustering:**
    - Strength: Provides well-defined clusters based on the similarity of tweet content.
    - Limitation: The analysis stops at the level of clustering, where only the number of clusters can be defined. No deeper information about the content within each cluster is provided.
2. **LDA Topic Extraction:**
    - Strength: LDA allows for a more detailed analysis of the topics being discussed within the dataset. Each tweet is treated as a mix of several topics, which gives deeper insights into what users are talking about.
    - Advantage: Unlike k-Means, LDA can define the specific topics discussed in each cluster, enabling further analysis of the subject matter within each group of tweets.

By comparing the two methods, LDA offers a more comprehensive approach for understanding the content of tweets. While k-Means is useful for grouping similar tweets, LDA goes a step further by identifying the key topics within those clusters.



## Requirements
- Python 3.x
- Libraries:
  - `Pandas`
  - `NumPy`
  - `Scikit-learn`
  - `NLTK`
  - `Gensim`
  - `Matplotlib`
  - `Seaborn`
 
## Results
**Clustering (k-Means)**
- k-Means provides a predefined number of clusters based on content similarity.
- Optimal k is selected based on silhouette scores, with each cluster representing groups of similar tweets. However, further insights into the content are limited with this method.

**Topic Modeling (LDA)**
- LDA uncovers hidden topics within the dataset. For example:
    - **Topic 1:** Security and Privacy concerns after the ransomware attack.
    - **Topic 2:** Complaints about customer service and banking issues.
    - **Topic 3:** Positive responses regarding BSI’s recovery efforts.
- These topics help reveal deeper insights about the discussions, going beyond simple clustering.

**Persona Analysis**
- **Clustering Personas:** Clustering reveals general groups of users, such as those criticizing BSI, concerned customers, or unaffected observers.
- **Topic-Based Personas:** Topic extraction allows for more refined personas, such as "Security Experts," "Casual Bank Users," and "Financial Professionals."

## Conclusion
The comparison of k-Means Clustering and LDA Topic Extraction shows that while k-Means is effective in grouping tweets based on content similarity, LDA provides a richer and more nuanced understanding by revealing specific topics discussed within each cluster.
  - k-Means: Useful for defining groups, but limited to superficial analysis.
  - LDA: Offers a deeper dive into the content, uncovering the hidden topics and their importance within the dataset.
