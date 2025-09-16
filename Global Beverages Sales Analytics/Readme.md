# About the Market #
    The global beverage market was valued at USD 207 billion in 2023.

    It is forecasted to grow to USD 459 billion by 2027, with an average annual growth rate of 14.22%.

    Beverage products include soft drinks (sodas, juices) and alcoholic drinks (beer, wine, spirits).

    Growth is driven by changing consumer tastes and lifestyles, increasing drink consumption.

    Soft drinks serve non-alcohol consumers, while alcoholic beverages include beer, wine, and spirits.

    Rising demand for convenient and healthier beverage options encourages innovation in flavors and packaging.

    This expanding market presents strong opportunities for companies to develop and sell popular drinks.

# Dataset #

# Tables #
**Sales Information**
| Column Name   | Data Type | Unique Values | Description                                   |
|---------------|-----------|---------------|-----------------------------------------------|
| SalesChannel  | String    | 11            | The platform or method through which the sale was made. |
| ChannelType   | String    | 4             | Categorizes the sales channel (e.g., Online, Retail). |
| OrderQty     | Integer   | 250           | The quantity of items ordered in the transaction. |
| SalesValue   | Float     | 2481          | The total value of the sales transaction.    |
| Discount     | Float     | 4             | The discount amount offered on the MRP for the transaction. |
| Country      | String    | 13            | The country where the transaction occurred.  |

**Product Information**
| Column Name            | Data Type | Unique Values | Description                                         |
|------------------------|-----------|---------------|-----------------------------------------------------|
| ProductItemID          | String    | 153           | Unique identifier for the product.                  |
| Category               | String    | 2             | The category to which the product belongs.          |
| Brand                  | String    | 16            | The brand of the product.                            |
| SpecificProductName    | String    | 39            | The specific name of the product.                    |
| Packaging Type         | String    | 5             | Details about the product's packaging (type, quantity, category). |
| Packaging Quantity     | Integer   | 23            | Details about the product's packaging (type, quantity, category). |
| Packaging Category     | String    | 2             | Details about the product's packaging (type, quantity, category). |
| PackagingQty_N_ml      | Integer   | 23            | Product quantity in milliliters for standardized comparison. |
| MRP_UnitPrice          | Float     | 16            | Maximum Retail Price per unit of the product.       |
| Product_Launch_Date    | Date      | 152           | The date when the product was launched in the market. |
| IsNewProduct           | Boolean   | 2             | Indicator whether the product is new (True or False). |

**Finance Information**
| Column Name      | Data Type | Unique Values | Description                      |
|------------------|-----------|---------------|----------------------------------|
| CostPerUnit      | Float     | 23            | The cost incurred per unit of the product. |
| MarginPercentage | Float     | 3             | The percentage of margin made from the transaction. |
| Profit           | Float     | 2272          | The profit earned from the transaction. |

**Retailer Information**
| Column Name   | Data Type | Unique Values | Description                                   |
|---------------|-----------|---------------|-----------------------------------------------|
| RetailerId    | String    | 650           | Unique identifier for the retailer.           |
| RetailerName  | String    | 263           | The name of the retailer.                      |
| State        | String    | 53            | The geographical location of the retailer (State, City). |
| City         | String    | 57            | The geographical location of the retailer (State, City). |
| Lat          | Float     | 206           | Latitude coordinate of the retailer's location. |
| Long         | Float     | 205           | Longitude coordinate of the retailer's location. |

**Transaction Information**
| Column Name      | Data Type | Unique Values | Description                           |
|------------------|-----------|---------------|-------------------------------------|
| SrNo             | Integer   | 25000         | Serial number of the transaction.   |
| TransactionDate  | Date      | 1492          | The date when the transaction occurred. |

# Approach #

### **Step 1: Identify stakeholders**

| Section         | Details                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------|
| **User Persona** | Sales Manager                                                                                                   |
| **Role**        | Leads sales team to meet revenue targets and grow market share.                                                |
| **Responsibilities** | - Analyze market trends, competitor strategies, and industry dynamics for decision-making.<br>- Provide insights and recommendations from data analysis.<br>- Evaluate risks and opportunities.<br>- Develop and implement strategic growth initiatives.<br>- Collaborate across teams to align and execute strategies. |
| **Needs**       | - Comprehensive, up-to-date market data.<br>- User-friendly analytics tools and dashboards.<br>- Advanced analytics to spot trends and opportunities.<br>- Insights on emerging markets, threats, and disruptions.<br>- Timely, relevant information for strategic planning. |
| **Challenges**  | - Keeping up with fast-changing markets and competition.<br>- Balancing short-term and long-term goals.<br>- Managing large data volumes to gain insights.<br>- Securing alignment and buy-in from stakeholders.<br>- Adapting strategies for unforeseen challenges and market shifts. |

### **Step 2: Empathy Map**
| Quadrant      | Content                                                                                                  |
|---------------|----------------------------------------------------------------------------------------------------------|
| **Thinks**    | - "How do I hit or exceed revenue targets this quarter?"<br>- "Which team members are performing well, and who needs coaching?"<br>- "Are we capturing enough of the market compared to competitors?"<br>- "Is our pipeline healthy, or are we at risk of missing future targets?"<br>- "Are my reports and dashboards giving me the right insights, or am I missing blind spots?" |
| **Feels**     | - Pressured by leadership expectations and market competition.<br>- Frustrated when data is fragmented, late, or incomplete.<br>- Motivated by wins and recognition.<br>- Concerned about team morale if targets seem unrealistic.<br>- Conflicted balancing short-term revenue pushes and long-term growth. |
| **Says**      | - "I need better visibility into the pipeline."<br>- "We’re closing deals, but not fast enough."<br>- "I can’t manage what I can’t measure—where’s the data?"<br>- "Our competitors are moving faster than us."<br>- "We need to celebrate wins to keep the team motivated." |
| **Does**      | - Reviews dashboards, CRM reports, KPIs regularly.<br>- Holds team meetings and coaching sessions.<br>- Escalates pipeline or target risks to leadership.<br>- Pushes team on activity metrics.<br>- Requests new insights or reports from analysts. |
| **Sees**      | - CRM tools with varying adoption and accuracy.<br>- Dashboards showing lagging indicators.<br>- Competitor campaigns and market shifts.<br>- Team members struggling with objections or lead quality.<br>- High leadership scrutiny on results. |
| **Hears**     | - Leadership demanding aggressive growth.<br>- Sales reps frustrated with leads and quota pressure.<br>- Customers expressing objections or delays.<br>- Analysts explaining KPIs and new dashboards.<br>- Industry chatter about changing customer needs and economic uncertainty. |
| **Pains**     | - Inaccurate, delayed, or non-actionable data.<br>- Difficulty linking sales activities to outcomes.<br>- Pressure affecting team morale.<br>- Blind spots on competitor and market positions.<br>- Team turnover or low morale due to missed targets. |
| **Goals**     | - Grow revenue consistently and expand market share.<br>- Clear, reliable view of sales performance.<br>- Identify leading success indicators.<br>- Improve forecast accuracy.<br>- Keep sales team motivated and focused. |

### **Step 3: Identify KPIs**

| KPI Name               | Columns Used                      | Formula                                                  | Description                                                        |
|------------------------|---------------------------------|----------------------------------------------------------|--------------------------------------------------------------------|
| Sales Volume           | OrderQty                        | Sum(OrderQty)                                            | Total units sold, reflecting market demand.                        |
| Market Penetration Rate | IsNewProduct, OrderQty          | (Sum(OrderQty of New Products) / Sum(OrderQty)) * 100   | % of new products sold out of total, indicating launch success.   |
| Discount Impact        | Discount, SalesValue, Profit    | Average(Discount), Correlation(Discount with SalesValue and Profit) | Average discount and its effect on sales & profitability.          |
| Product Mix Diversity  | ProductItemID, OrderQty         | Count(Distinct ProductItemID), Sum(OrderQty) per ProductItemID | Variety and volume of products sold, showing market reach.         |
| Geographic Market Share| State, City, SalesValue         | Sum(SalesValue) per State/City                           | Sales distribution across regions, showing market dominance.       |
| Sales Channel Effectiveness | SalesChannel, OrderQty, Profit | Sum(OrderQty) and Sum(Profit) per SalesChannel          | Performance of sales channels by volume and profitability.         |
| Sales Growth          | SalesValue, TransactionDate     | ((Current Period Sales - Previous Period Sales) / Previous Period Sales) * 100 | Growth in sales value over time.                                    |
| Average Deal Size     | SalesValue, OrderQty            | SalesValue / Count of Deals                              | Average revenue per deal, indicating deal size trends.             |
| Pipeline Health       | Number of leads, OrderQty       | Count(Active Leads), Conversion Rate                     | Measures strength and potential of sales pipeline.                 |
| Customer Acquisition Cost (CAC) | Sales and Marketing Costs, New Customers | Total Sales & Marketing Costs / Number of New Customers  | Average cost to acquire a new customer.                             |


### **Step 4: Goals and Objective**

| Section   | Details                                                                                                      |
|-----------|--------------------------------------------------------------------------------------------------------------|
| Objective | - Provide strategic insights and recommendations through comprehensive market analysis and data-driven insights.<br>- Identify emerging trends and evaluate market opportunities.<br>- Support strategic decision-making to foster business growth and create competitive advantage. |
| Goals     | - Enhance organizational performance and market competitiveness.<br>- Deliver actionable insights and recommendations for key strategic initiatives.<br>- Analyze market trends and assess competitive dynamics.<br>- Identify and prioritize growth opportunities to guide strategic planning and execution.<br>- Collaborate with cross-functional teams to align objectives and ensure effective implementation of strategic initiatives. |

### **Step 5: Business questions**

    1. Sales over the years
    
    2. Top 5 countries by sales and profit
    
    3. Packaging imacpt on sales in India
    
    4. Product by sales and cost per unit

### **Step 6: Insights**
