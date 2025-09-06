# Unlocking User Loyalty: A Deep Dive into Weekly Cohort Analysis for Retention and Churn at MyOnlineShop
I recently completed an advanced cohort analysis project during my internship at MyOnlineShop, a subscription-based e-commerce platform. This two-week endeavor (Weeks 7-8 of the program) focused on weekly retention and churn trends, providing critical insights into user behavior. Conducted as part of Team Ace's internship curriculum, the analysis was performed as of February 7, 2021, using historical subscription data from late 2020 to early 2021. This project not only honed my skills in SQL querying, data visualization, and storytelling but also highlighted how granular metrics can drive long-term business growth.
I'll walk you through the project's objectives, my step-by-step process, key insights, and forward-looking recommendations. This work showcases my ability to handle real-world data challenges and deliver value-driven narratives—skills I'm eager to bring to my next role in data analytics or business intelligence.

<h2>Project Objectives</h2>
The primary goal was to shift from high-level monthly metrics to a more agile weekly view of user retention and churn. By grouping users into cohorts based on their subscription start week, we aimed to:
<ul>
<li>Track Engagement Over Time: Measure how many users remained active from Week 0 (sign-up) through Week 6, revealing patterns in loyalty and drop-offs.</li>
<li>Identify Churn Hotspots: Pinpoint where and why users were leaving, enabling targeted interventions.</li>
<li>Support Data-Driven Decisions: Provide visualizations and insights to help product managers, marketers, and growth teams optimize user experiences, reduce churn, and boost lifetime value.</li>
<li>Quantify Business Impact: Link retention trends to financial metrics, such as total value rate, to underscore the economic importance of user stickiness.</li>
</ul>
These objectives were crucial because, in a competitive e-commerce landscape, retaining users is often more cost-effective than acquiring new ones. Studies show that a 5% increase in retention can boost profits by 25-95%, making this analysis a cornerstone for sustainable growth.

<h2>Step-by-Step Process: From Data Exploration to Actionable Insights</h2>
I approached this project methodically, blending technical execution with narrative clarity. Each step built on the last, ensuring accuracy and relevance. Here's how I did it, including the importance of each phase.

<h2>Step 1: Understanding the Data</h2>
I started by diving into the subscriptions table in BigQuery, focusing on key columns: user_pseudo_id (unique user identifier), subscription_start_date, and subscription_end_date. Using exploratory SQL queries, I checked for data quality issues like missing values, duplicates, or anomalies (e.g., end dates before start dates).
This revealed a clean dataset spanning November 2020 to January 2021, with no major invalid entries but some null end dates indicating active subscriptions.
Importance: Data quality is the foundation of any analysis. Skipping this could lead to skewed retention rates (e.g., overestimating churn due to duplicates). This step ensured reliable cohorts and built confidence in downstream calculations.

<h2>Step 2: Analyzing a Single Cohort</h2>
To build intuition, I focused on one cohort: users subscribing between January 4-11, 2021. I truncated start dates to the week level using SQL's DATE_TRUNC function and calculated activity status for Weeks 0-6 by checking if the subscription end date was after each week's end.
This output showed retention dropping from 100% in Week 0 to around 93% by Week 6 for this cohort.
Importance: Starting small allowed me to debug logic and validate assumptions (e.g., handling ongoing subscriptions). It prevented errors when scaling, saving time and ensuring the full analysis was robust.

<h2>Step 3: Scaling to Multiple Cohorts</h2>
I expanded the query to all weekly cohorts from October 2020 to January 2021, using conditional aggregation to compute retention rates across Weeks 0-6 for each.
This produced a pivoted table with cohorts as rows and weekly retention percentages as columns.
Importance: Multi-cohort analysis reveals trends across time (e.g., seasonal effects), which single-cohort views miss. It enables comparative insights, like how holiday-acquired users (e.g., Black Friday) retain differently from off-season ones.

<h2>Step 4: Exporting the Data</h2>
I exported the results as a CSV from BigQuery and imported it into Google Sheets for further manipulation.
Importance: Exporting bridges the gap between querying and visualization, allowing non-technical stakeholders to access raw data for validation or custom views.

<h2>Step 5: Visualizing Retention Trends</h2>
Using Power BI, I created:
<ul>
<li>Retention Heatmap: Rows for cohorts (e.g., "2020-10-26"), columns for Weeks 0-6, with green-to-red gradients (100% green, low retention red). This showed early cohorts retaining better long-term.</li>
<li>Churn Table: Complementary view with churn percentages, highlighting progressive increases (e.g., from 0% in Week 1 to 12.81% by Week 6 in some cohorts).</li>
<li>Funnel Chart: Illustrated average dropout vs. retention, showing a 42% cumulative dropout by Week 6, with the steepest drop (36%) in Week 5.</li>
<li>Line Charts: Tracked individual cohort trends, revealing stabilization around 58-85% retention by Week 6.</li>
</ul>
Overall metrics included a 91.34% average retention, 35.32% dropout, and 8.66% churn, contributing to a $1,217,741 total value rate.
Importance: Visuals make complex data digestible, turning numbers into stories. Heatmaps spot patterns quickly, while funnels emphasize drop-off urgency, aiding stakeholder buy-in.

<h2>Step 6: Interpreting Insights and Summarizing</h2>
I compiled a 1-2 page document detailing methodology, trends (e.g., sharper declines in 2021 cohorts), and recommendations.
Importance: Interpretation bridges data to action, ensuring insights don't sit unused. It demonstrates analytical thinking beyond technical skills.

<h4>Key Insights</h4>
<ul>
<li>Drop-Off Patterns: Retention decreased from 100% in Week 1 to 58% by Week 6 on average, with critical dropouts of 11% (Week 2), 19% (Week 3), 27% (Week 4), 36% (Week 5), and 42% (Week 6). Week 5's 36% spike suggests onboarding or feature gaps.</li>
<li>Cohort Variations: Early 2020 cohorts (e.g., 2020-10-26) retained 87.19% by Week 6, while later ones (2021-01-25) dropped to 94.58% in early weeks but showed potential for decline. Holiday cohorts had higher initial churn (up to 15.43%) due to promotional sign-ups.</li>
<li>Churn Trends: Progressive rise from 0% to 12.81% by Week 6 in late 2020 cohorts, stabilizing at 3.97%-5.42% in 2021, indicating improved strategies.</li>
<li>Financial Tie-In: High churn correlated with lost value, emphasizing retention's role in the $1.2M total rate.</li>
</ul>

<h2>Recommendations for Improvement</h2>
<h4>Short-Term (Next 2 Years)</h4>
<ul>
<li>Enhance Onboarding: Implement personalized tutorials in Weeks 1-3 to combat early dropouts (11-27%), potentially reducing churn by 10-15%.</li>
<li>Targeted Re-Engagement: Use email/SMS campaigns for Week 5 risks, focusing on features like loyalty rewards.</li>
<li>A/B Testing: Test pricing or promotions on cohorts to isolate factors like Black Friday impacts.</li>
</ul>
<h4>Long-Term (2-10 Years)</h4>
<ul>
<li>AI-Driven Personalization: By 2027, integrate machine learning to predict churn and automate interventions, aiming for 95%+ retention through dynamic content.</li>
<li>Expand Metrics Integration: By 2030, combine cohort data with usage logs and feedback for holistic views, enabling predictive analytics to forecast lifetime value and reduce churn to under 5%.</li>
<li>Sustainability Focus: Invest in community-building (e.g., user forums) and eco-friendly incentives to foster loyalty, aligning with evolving consumer values and supporting 20-30% growth in subscriber base.</li>
<li>Scalable Infrastructure: Upgrade to real-time dashboards by 2035, allowing weekly (or daily) monitoring to adapt to market shifts like economic downturns.</li>
</ul>
These strategies could elevate MyOnlineShop from a reactive to a proactive player, potentially increasing revenue by 50% through sustained engagement.

<h2>Conclusion</h2>
This cohort analysis project was a pivotal experience, blending SQL prowess, visualization expertise, and storytelling to uncover hidden user trends. It reinforced that data isn't just numbers, it's the key to building lasting customer relationships. As I seek opportunities in data analytics, I'm excited to apply these skills to help organizations thrive. Connect with me on LinkedIn to discuss how we can turn your data into stories!
Note: Visualizations and datasets available upon request. Project completed as part of MyOnlineShop Internship, Team Ace.
