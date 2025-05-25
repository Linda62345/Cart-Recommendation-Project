# Cart-Recommendation-Project
This project is a session-based recommendation system based on real-world e-commerce data provided by 91APP. It focuses on understanding consumer behavior during the add-to-cart phase, and builds a category-level co-occurrence recommendation engine.
## Dataset Overview
- Source: 91APP SalePage + session01 behavior logs  
- Time Range: 2023/09/01 – 2023/12/31  
- Total Records: 72,734 SalePage titles  
- Filtered Unique Products (Sept–Dec): 37,909  
- User Behavior Logs (Add to Cart): 1,236,664 mapped entries
## Preprocessing
- Excluded products with keywords like "贈品", "限時", "預購", "solone", etc.
- Removed volume units like ml, g, kg, 入, 包, etc.
- Applied **Chinese word segmentation + TF-IDF vectorization** on SalePageTitle
- Clustered into **150 KMeans groups** using elbow method
## Idea
We simulate cart-level co-purchasing decisions by building a co-occurrence matrix of categories.
If users who added Category A also frequently added Category B, we recommend B when A is added.
## Implementation
- Combine user session identifiers via:**SessionId = FullVisitorId + "_" + HitTime**
- Group items by SessionId to form a cart cluster
- Count pairwise category co-occurrence
- For each category, recommend Top-N associated categories
## Output
- The recommendation system identifies related product categories based on session-level co-occurrence.
