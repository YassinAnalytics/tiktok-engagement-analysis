# TikTok Engagement Analysis  
🔍 Identifying key drivers of video performance (likes, shares, views)  
📊 Python + SQL + PowerBI | Kaggle Dataset | 19K videos analyzed  

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data_Cleaning-green)
![PowerBI](https://img.shields.io/badge/PowerBI-Visualization-yellow)

*What drives engagement on TikTok? A data dive into 19K videos*  

## 🔍 Key Findings  
- Likes account for 82% of total engagement  
- Video duration doesn't impact performance  
- Shares are the #2 engagement driver (16%)  

## 🛠️ Tech Stack  
- Python (Pandas, Seaborn, matplotlib)  
- SQL (pandasql)  
- Power BI  

## 📂 Dataset  
[Kaggle TikTok Video Metrics](https://www.kaggle.com/datasets/yakhyojon/tiktok)  
[Kaggle TikTok Video Metrics](https://www.kaggle.com/datasets/raminhuseyn/dataset-from-tiktok )

## Data cleaning
![image](https://github.com/user-attachments/assets/037f5264-ff52-455f-a5c0-b033d7820933)

![image](https://github.com/user-attachments/assets/3d025e10-b21b-460e-93bf-e9287f9c274c)

![image](https://github.com/user-attachments/assets/64c325c2-2927-4954-a997-7005ec1d6292)

There are 298 rows empty. They will be deleted. The cleaning will be done with  dropna function

![image](https://github.com/user-attachments/assets/793b487f-efb0-401a-b7df-241c0f0fd27f)

Check again: 

![image](https://github.com/user-attachments/assets/13959df5-2a0e-4b86-82e4-07c2c4157327)

![image](https://github.com/user-attachments/assets/8cca1c20-f8c2-40b5-928e-f9e3157197af)

Save the file and import the second one.
I noticed that second file contains the exact same data as the one we just cleaned. We keep only the first file.

Now the file is cleaned, let’s do some analysis.

## Analysis
![image](https://github.com/user-attachments/assets/394768ef-c3fd-4a98-b031-76c4c3969533)

Let’s first see the distribution: 

![image](https://github.com/user-attachments/assets/a7d7a661-ed16-4c05-85e4-5afc7f2719c3)

The biggest repartition is with the views and the likes. Is it possible to find some extreme values. It’s same for the share count but with a lower gap.
Let’s see the histograms for the repartition of each metrics:

![image](https://github.com/user-attachments/assets/52528f98-8234-4bd9-b763-35f47c716582)

![image](https://github.com/user-attachments/assets/a7fea7d7-f8bd-4485-914a-4ddba28702a4)

We can observe that the big majority of the videos have a very low number of views. And that’s view videos have a large number.
It’s the same trends for all the other metrics. The only difference is that a progressive decrease is visible.

![image](https://github.com/user-attachments/assets/0a0534c4-1933-41cb-b2bd-8a41696c9b35)

![image](https://github.com/user-attachments/assets/01a15168-7406-4e1a-80c5-994d37845e72)

![image](https://github.com/user-attachments/assets/cf31dff2-bab8-46f6-bd36-3f2a3de2abb2)

![image](https://github.com/user-attachments/assets/dc39d181-d83a-4d54-bb24-9e445ed2e6b1)

![image](https://github.com/user-attachments/assets/5b5a7e11-b326-46b3-8d3f-311f889b281b)


For the duration repartition, we can observe that the peak of number of videos are at 5 seconds, 16 seconds, 28 seconds, 38 seconds, 50 seconds and 60 seconds for similar numbers. Then for the rest of the duration in the between it’s more or less the same numbers. 

Now let’s see the correlation:  

![image](https://github.com/user-attachments/assets/b8526f30-9d62-4770-ba48-44310d71ff80)


It’s possible to observe that some correlations are strong and other are weak:
-	Duration has very low correlation with all metrics
-	The view count has medium correlation with the number of comments, of download, share and strong correlation with the likes
-	The like has strong correlation with the view, share and download. And a correlation with comment.
-	The share has strong correlation with the likes, and correlation with view, download and comment
-	The download has a strong correlation with the likes and comment and a correlation with view and share
-	The comment has strong correlation with the download and correlation with share, likes and view

Now let’s calculate the engagement rate: (all metrics added and divided by the number of view)

![image](https://github.com/user-attachments/assets/2e17afea-0e44-4a5d-ad8c-1136371fef00)

Let’s observe how the duration and view numbers are represented:

![image](https://github.com/user-attachments/assets/c55b29d6-a9a8-43cf-ab64-dbfc985bfa36)


We can see that for all duration there is many views numbers. So, the duration of the video doesn’t impact it.

## Analysis with SQL

Now that we have saw some trends thanks to python. Let’s do an exploration using SQL.
Firstly, install pandasql.

![image](https://github.com/user-attachments/assets/e3c1fdcb-b4b7-498d-8714-1772c2e7d0fa)

Then the exploration can start. 
Top 10 most viewed video:

![image](https://github.com/user-attachments/assets/3840721f-8755-4665-91b5-ec01c0d0313f)

Global average engagement rate:

![image](https://github.com/user-attachments/assets/72defa17-8da2-4cc3-80a9-2d1b94036cd5)

The global average engagement rate is 34%.


Average length of video:

![image](https://github.com/user-attachments/assets/5e456bdb-2e78-4612-b545-ff2858e411fe)

The average length of video is 32.42 seconds.

Number of videos with more than million views: 

![image](https://github.com/user-attachments/assets/cc799724-fa06-4301-b21f-f28b49e63437)

There are no video above 1 million views in this dataset.

Top 5 video with best engagement rate:

![image](https://github.com/user-attachments/assets/33a84ecd-27f1-4128-a5d1-10a0089cdb6d)

Some vide have 93/94% of engagement rate which is extremely high.

Average length of video per slice of views:

![image](https://github.com/user-attachments/assets/f74aac15-add0-4ae9-be78-a4a4fb148837)

No matter the view range, the average duration is similar.

Average engagement rate per slice of views:

![image](https://github.com/user-attachments/assets/e17b9697-34ec-4268-9dc0-591939c47dcf)

Above 10 000 views the engagement rate is similar 39/40%. When less, it’s a bit less, around 27%. But there is more video with less views than the other, so this is lowering the global average



#Key finding
- Likes	: 82% of total engagement. Strong correlation
- Shares: 	16% of total engagement,	Moderate correlation
- Comments:	2% of total engagement,	Weak correlation
- Duration:	No significant impact, 	Negligible correlation

Now let’s visualize on Power BI

## PowerBi vizualisation

![image](https://github.com/user-attachments/assets/30ca9f57-33dc-42db-81ca-cd19047cd2d4)

Delete “# “column, for the count, change type to who number, 
Creation of the following measures:
-	Engagement Rate
-	Average Video Duration
-	Total Views
-	Total Likes
-	Total Comments
-	Total Shares
-	Total Downloads
-	Average Engagement Rate per Video
-	View Category
-	Top Viewed Videos
-	Engagement by View Range
-	Total Video Duration
-	Total Videos
-	Top Engaged Videos
-	Average Share Rate

![image](https://github.com/user-attachments/assets/c73478cb-b3a9-4f31-a9a4-df253e99f29d)

## Insights
In this visualization, at the top of it, the main data are displayed: number of videos, the average view, average duration of the video, the engagement rate (any engagement) and the total of views. In the dataset there was 19 000 videos for a total of 5 billion views.
Then, we can see that in terms of engagement, the ratio view/like is 25% (the likes being the engagement KPI the most used). 82% of the total engagement is from the likes, which is followed by the shares at 16%. The download and comments are a very low indicator for the engagement.
We can see the duration of the video has not really an impact about the engagement. The engagement rate is similar at any duration of videos, even for the shortest and longest ones.

The top 10 video, have more or less the same number of views and like. But differ greatly in terms of comment, shares and downloads. The duration is also totally different, from short (7s) to average (30s) to long (almost a minute. This confirms the trend we mentioned before.
And in terms of view by duration, there is not a specific impact because the views can be high or low no matter the duration of the video.

## Conclusion

Likes (82%) are the KPI which impacts the most the engagement, followed by the shares (16%). 
The duration of the video doesn’t have impact for the views or the engagement rate
Limits and next steps:
The dataset is a small sample of 19k videos
No creator data or music data or category data
Next steps could be to link the results with datasets containing creators’ data, and determinate the virality of video, Integrate with TikTok API for real-time data



## Files included
- tiktok_viz.pdf :  PowerBi vizualisation in PDF
- tiktok_viz.pbix :  PowerBi vizualisation in PBIX
- tiktok_dataset : dataset Kaggle not used
- tiktok_dataset2 : dataset Kaggle used
- tiktok_dataset_cleaned : data set cleaned
- tiktokdata.ipynb : Jupyter notebook






