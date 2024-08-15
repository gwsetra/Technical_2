## Table of Contents

1. [Understanding Business Goals and Expectations](#understanding-business-goals-and-expectations)
2. [Defining Technical Architecture](#defining-technical-architecture)
3. [Architecture Diagram](#architecture-diagram)
4. [Explanation of Architecture](#explanation-of-architecture)
5. [Design Advantage & Disadvantage](#design-advantage--disadvantage)


## Understanding Business Goals and Expectations

Before diving into technical details, it may be important to start by defining the Business Objective and Key Results (OKRs). Establishing these can guide decisions about technical requirements during the design process. Below is an example of Business OKRs:

#### Objective 1: Enhance Understanding of Consumer Behaviour
- ***Key Result 1:*** Conduct user journey mapping for 80% of app users by the end of Q3.
- ***Key Result 2:*** Identify and document the top 5 pain points in the booking process within 60 days.

#### Objective 2: Improve Conversion Rate through Data-Driven Insights
- ***Key Result 1:*** Analyse booking funnel data to identify a 10% drop-off at each stage within the next quarter.
- ***Key Result 2:*** A/B test 3 different user flow optimizations and select the most effective one based on a 5% improvement in booking completion rates.

#### Objective 3: Optimize User Experience Across Platforms
- ***Key Result 1:*** Reduce the average booking time by 20% on both mobile and web platforms by the end of Q4.
- ***Key Result 2:*** Increase the number of repeat bookings by 25% through targeted user journey improvements within the next 2 quarters.

By this, we can reasonably conclude that the Product Manager and Business Analyst will have bi-weekly meetings to review progress on the consumer journey analysis and assess the effectiveness of implemented strategies.

## Defining Technical Architecture

To store event data in the data warehouse and analyze events such as successful payments, barcode scans, or items added to the cart, we need to prepare the facts and questions to guide the technical architecture decisions.

### Facts:
1. Event logs are expensive.
2. Tracking new events or modifying existing events is costly.

### Questions:
1. Has the backend team ever produced events before?
2. What is the event streaming platform currently being used by the backend team? (e.g., Kafka, Pub/Sub, Kinesis)
3. What is the cost comparison between utilizing existing events and having the backend team create new events for the data engineers?
4. What type of database is used for the data warehouse? (OLAP, OLTP, which vendors?)
5. Should we store raw events in a data lake, NoSQL DB, or Relational DB?
6. How granular do we want to track the events?
7. What is the budget allocated for the project?
8. What is the data retention policy, and does it involve PII data?
9. How proficient is the team in using the tools and technologies in use?

For this scenario, let’s assume Kafka is the event streaming platform, Snowflake is used for the data warehouse, Amazon S3 is used for the data lake, the backend team has the capacity to create new events for data engineers, PII data is involved, and it is necessary to store the data for up to 2 years. In parallel, based on OKRs and business expectations, we can estimate that real-time data is not required, and batch-processing is adequate to track relevant metrics for the business.

## Architecture Diagram
End-to-end Diagram
User Action Diagram![image](https://github.com/user-attachments/assets/a21b8197-f3f3-4900-a4a7-b861355c8eeb)
Sample of event message![image](https://github.com/user-attachments/assets/8e3d5c40-c000-4776-9f7e-bd4b6633c129)


