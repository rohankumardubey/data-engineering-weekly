# What exactly is the Graviti Data Platform?
I am [Edward Cui](https://www.linkedin.com/in/yunkai-edward-cui-411a0563/), the founder of [Graviti Data Platform](http://www.graviti.com), the next-generation cloud data platform. To define what the next generation is, we need to understand the current generation’s emergence, use cases and limitations. The demand for the next-generation data platform inevitably comes from a series of changes in the world. Understanding these changes can help us to better understand how people use data platforms and the trade-offs that need to be made when designing our product.
Here is a quick walkthrough of the topics covered in this article. Feel free to drop at the part you are most interested in.
## Topics Discussed
1. [Database VS Data Platform](#database-vs-data-platform) 
* Data-driven decision making
* The difference in data access frequency and latency
* Different user groups
2. [Why you need a next-generation data platform](#why-you-need-a-next-generation-data-platform)
* The rapid accumulation of unctructured data
* Features of unstructured data platforms
3. [Write at the end](#write-at-the-end)

## Database VS Data Platform
Let’s begin with the birth of the current generation of data platforms, which include leading companies such as Snowflake and Databricks. I’ll start with the following two questions:
* Why were companies like Snowflake and Databricks born around 2012?
* What happened at the macro level that laid the foundation for their birth?
I will share my answers in the following chapters and the reasons behind them.

**Data-driven decision making**</br>
***The foundation of a data platform*** 

Imagine you are the CEO of a company that has several business units including marketing, sales, finance and human resources. If the current goal of the company is to increase business ROI as well as shorten the sales cycle, you need to find the most effective marketing channel to obtain high-quality customers with higher revenues and excellent salespeople who can close the deals the fastest while maintaining the size of the sales team.
To make the right decisions, you will need to gather and analyze data from various business units. However, data is usually scattered across BUs. When data volume is small, it is still easy to handle such data in a large spreadsheet imported from each BU. This large table is the earliest form of a data platform, and its emergence demonstrates that businesses start to transition into a data-driven decision-making process, instead of going with their “gut” or instinct.
Since the dot-com bubble arrived in the early 2000s, database technology has become more and more popular. Following that, many software companies were born to better manage big data and perform business analytics, the backbone of which is a relational database. With the ability to handle a large variety of data, databases enable businesses to scale, and more people to collaborate efficiently. 
As of 2012, about 2.5 exabytes of data are created each day,  and a better data platform product is needed to process the volume, which can automatically pull data (ELT or ETL) from various databases and put the data into a bigger table. It should be stored on the hard disk rather than RAM, where you can quickly filter data through the SQL interface and get results. This was the opportunity for the current-generation data platform, generated by data explosion over 12 years and how Snowflake and Databricks came into being.

**The difference in data access frequency and latency**</br>
***The nature of the product***

As data accumulates rapidly, the demands of transactional data and analytical data lead to the two directions of product development.
Transactional data are those that support the day-to-day running of a business. Users might  access or write at the same time with expectations of an excellent user experience. The database needs to respond to your request quickly without waiting. Therefore, the transactional data systems require two features:

* High-frequency read and write data, especially read.
* Low latency (Milliseconds for a query).

The database is designed for this purpose, especially relational databases.
On the other side, analytical data are used to provide the necessary information to support business decisions. The process is designed for internal users with a relatively low access frequency. However, making decisions requires huge volumes of data for business analytics. It requires a low-price storage solution and efficient processing. In summary, an analytical data system should have the following features:

* Low-frequency read and write data.
* High latency for queries (seconds, even at minute-level).
* More data will be piped in while the business grows. High scalability is a must.
* Low price for data storage and appropriate acceleration for some use cases.

When we get to know the use cases and business requirements, it is not difficult for us to understand why we need two completely different data products.
To achieve low latency and high frequency for transactional data, it often chooses to use more memory and CPU power. However, the tradeoff is the price (you will find the price of RDS is often 10 times the price of object storage.) Similarly, it also needs sharding and partitioning data if a dataset is too large to be stored in a single database.
For analytical purposes, low latency is not strictly required while data volume is particularly large. Object storage is often the option with better scalability and affordability.
Only when an access is made, memory and CPU would be used for acceleration. 
These features are in line with Databricks and Snowflake's product marketing, which is leveraging object storage for high scalability, lower pricing, and better data processing parallelization, which should also be universal features when designing a data platform.

**Different user groups**</br>
***Differentiation in user experience***

The different purposes mentioned in the previous chapter also result in different user groups and bring great differences in user experience between transactional and analytical data processing products.
Transactional data products, which are also known as databases, are developed for software engineers, database administrators(DBA) and infrastructure engineers who use databases in their daily work. As an engineer-oriented product, a database often gives users more control over the product and plenty of room for adjustment and optimization to achieve higher performance.
Analytical data products, which are also known as data platforms, are tailored for data scientists. Data scientists are good at using statistics and prediction models to interpret data, but they may not have as much experience in programming as software developers. Therefore, a data platform tends to be low code or no code with efficient performance. This explains the success story of  Snowflake, which the ease of using Snowflake fulfills the needs of its user group.

## Why you need a next-generation data platform?
Embracing a data-driven approach enables enterprises' fact-based decision-making. Current data platforms were born for that. What would trigger the arrival of the next-generation data platform?

**The rapid growth of unstructured data**</br>
***The critical driver for the next-generation data platform***

Ten years ago, I was still using an LG flip phone with a rear SD camera, and the online websites we visited the most were web-based forums. The websites on the mobile end were mainly text and links.
Smartphones we use today generally have 3-4 cameras on the back, and possibly an in-depth camera on the front. The increasing use of smartphones has greatly reduced the cost of sensors, not only on the consumer side but also on the enterprise side. Advanced telecommunication technology makes information exchange based on unstructured data possible. Today, your major channels of obtaining information now became Tiktok, Yelp, and Instagram, which consist of unstructured data such as pictures and videos. Unstructured data is accumulated rapidly on both personal devices and enterprises, and scattered everywhere. Managing and extracting insights from these data becomes the competitive advantage of enterprises, while the rapid growth of data has become a new challenge to the architecture of such data systems.

**Features of an unstructured data platform**</br>
***AI is the cornerstone to harnessing the power of unstructured data***

The biggest difference between [structured and unstructured data](http://www.graviti.com/article/difference-between-structured-unstructured-data) is that it is almost impossible to use unstructured data directly. People are analyzing with statistical models on structured data platforms for decision-making purposes while the results, which are numbers, exist in structured data. But unstructured data is just a binary block for a machine. If you want to extract its meaning, you’ll have to use AI. So what would be the use cases and characteristics of an [unstructured data platform](https://www.graviti.com/platform)?
The first question we would naturally ask is about the frequency of using the unstructured data platform and the requirements of latency.Then what is the high-frequency use case for AI with unstructured data? It is prediction applications at a large scale in fact and they are almost happening on the edge at low latency. For example, the prediction algorithm of [autonomous driving](https://gas.graviti.com/open-datasets?usedScene=Autonomous+Driving) occurs on the vehicle. The beauty camera app occurs on the mobile and the algorithm of a smart camera occurs on its processing chip. Almost all AI applications that require low latency do not transfer data through the network as it is hard to control the network delay. If high-frequency prediction and primitive data accumulation occur on the edge, unstructured data will be scattered everywhere.
Our product is a data platform in [cloud](http://www.graviti.com/data-hosting), where most of the offline processing tasks happen. These offline processing tasks include, but are not limited to, model training, large-scale model prediction, algorithm evaluation, temporary analysis, etc. They often do not require high performance on frequency and latency. These features are very similar to structured data platforms. Despite these similarities, the structured and unstructured data platforms still have a few major differences in terms of data types, data complexity, and scenarios.
To deal with these differences, we provide the below features,

1. Applied in most offline processing scenarios with large-scale I/O. Low requirements on latency and frequency.
2. Applied in AI scenarios, where there are a large number of interactions for model prediction and training.
3. Adaptable with the sum of data on the edge at a large scale and considering data collection in distributed edges.
4. As data is continuously collected by sensors in time series, whether it is audio, video, or point clouds data, there will be a large number of searching, splitting and merging based on time series.

Processing unstructured data generates results of AI predictions which are often not just the final results. The storage of intermediate results and the lineage between intermediate results and original data has become particularly important. Processing unstructured data is often in multi-steps and large volumes. It is necessary to allow end-users to define each step and schedule enough [computing power](http://www.graviti.com/advantages) for data processing. Unlike structured data which has a lot of standard processing operators, processing unstructured data is often not standardized and customized for the business. The platform should allow users to integrate their models and algorithms with our system.
Now we have a few more features,

5. Data lineage and consistency have a significant impact on long-term storage, management, and use of data.
6. The data platform should allow users to customize [workflows and pipelines](https://www.graviti.com/solutions/workflow-automation) easily, as well as schedule compute at a large scale.

Another feature we need to pay attention to is our user interface. Different from the users of structured databases and data platforms, our users are algorithm engineers. Therefore, we need to take care of the user experience in iterating data and model training. The capabilities of the platform should be encapsulated into an easy-to-use interactive experience. In the meantime, the unstructured data platform is a supplement to a structured data platform rather than a substitute.

7. Provide data abstraction for users and make the user experience as simple as possible.

## Write at the end
In this article, I systematically explained my recent thoughts about Graviti as a next-generation data platform, by walking you through the trade-offs when designing our product. It not only provides me with a better understanding of our data platform in the entire ecosystem, but also helps me digest the knowledge of structured data products design and trade-offs. When we stand on the shoulders of giants to carry out innovations, such thinking clears things up for us to explore independently in the direction of scalability of data processing and query.

What I haven't discussed deeply in this article is the function of data version control, which is worthy of an in-depth discussion in a separate article.

You're welcome to comment and leave a message. Thank you all for reading.