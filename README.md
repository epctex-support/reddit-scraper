[https://apify.com/epctex/reddit-scraper](https://apify.com/epctex/reddit-scraper?fpr=yhdrb)

# Actor - Reddit Scraper

## Reddit scraper

Reddit, the popular social media platform, is home to a vast array of discussions, communities, and user-generated content. From thought-provoking discussions to entertaining memes, Reddit offers a wealth of information and engagement. However, extracting data from Reddit programmatically can be a complex task due to the platform's structure and limitations.

Introducing our Reddit scraper, a versatile tool designed to extract valuable data from Reddit effortlessly. Our scraper can fetch posts, subreddits, comments, and user information, enabling you to access and analyze the content and interactions happening on Reddit.

Since Reddit's official API can be prohibitively expensive to use for many individuals and organizations, our super-fast scraper provides an affordable solution for fetching Reddit data without breaking the bank.

The Reddit data scraper supports the following features:

-   **Fetch anything** - Our scraper allows you to retrieve data from any Reddit URL. Whether it's a search query, a specific subreddit, a post, a user profile, or even the Reddit homepage itself, you can utilize our scraper to scrape the desired data. Simply input the URL, and our scraper will gather the relevant information for your analysis.

-   **Search** - With our scraper, you can perform advanced searches on Reddit using various parameters. You have the flexibility to specify keywords, search modes, sorting options, and time frames to refine your search results. This feature enables you to extract specific content from Reddit based on your criteria.
  
-   **Scrape homepage** - Our scraper can extract data from Reddit's homepage, allowing you to gather the latest and most popular content from across the platform. Stay up to date with trending topics, viral posts, and engaging discussions by scraping Reddit's homepage effortlessly.

-   **Scrape popular posts** -  If you're interested in fetching popular posts, our scraper provides the functionality to extract the most upvoted and widely discussed content on Reddit. By leveraging this feature, you can gather a curated collection of highly engaging posts for further analysis or exploration.

-   **Scrape subreddits** - Our scraper enables you to fetch entire subreddits along with all the posts they contain. This capability allows you to gather comprehensive data from specific communities on Reddit, providing insights into their discussions, trends, and user interactions.

-   **Scrape users** - Extracting user information is made easy with our scraper. You can retrieve data related to Reddit users, including their comments and posts. Analyze user behavior, track their contributions, and gain a deeper understanding of the Reddit community through comprehensive user data scraping.

-   **Scrape any post** - Our scraper gives you the flexibility to fetch any specific post of your choice. Simply provide the URL of the desired post, and our scraper will extract the content, comments, and other associated data for your analysis.

## Bugs, fixes, updates, and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/reddit-scraper/issues).


## Input Parameters

The input of this scraper should be JSON containing the list of pages on Reddit that should be visited. Required fields are:

- `search`: (Optional) (String) Keyword that you want to search on Reddit.

- `startUrls`: (Optional) (Array) List of Reddit URLs. You should only provide a news list, jobs list, or detailed URLs.

- `searchMode`: (Optional) (String) Type of search you want to make at Reddit. (`Posts`, `Communities`, `People`)

- `sort`: (Optional) (String) Specifies how you want to sort your results. (`Relevance`, `Hot`, `Top`, `New`, `Most Comments`)

- `time`: (Optional) (String) Specifies the time range for sorting your results. (`All Time`, `Past Year`, `Past Month`, `Past Week`, `Past 24 Hours`, `Past Hour`)

- `includeComments`: (Optional) (Boolean) Specifies whether to include comments or not within the posts.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. The default is `Infinite`. This applies to all `search` requests and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as an argument and returns an object with data.

- `customMapFunction`: (Optional) (String) Function that takes each object's handle as an argument and returns the object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that is explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor is optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detailed requests. If the actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.03-0.05 compute units.

### Reddit Scraper Input example

```json
{
  "startUrls": [
    "https://www.reddit.com/",
    "https://www.reddit.com/hot",
    "https://www.reddit.com/best",
    "https://www.reddit.com/rising",
    "https://www.reddit.com/r/popular",
    "https://www.reddit.com/r/popular/hot",
    "https://www.reddit.com/r/popular/new",
    "https://www.reddit.com/r/popular/top",
    "https://www.reddit.com/r/popular/rising",
    "https://www.reddit.com/new",
    "https://www.reddit.com/top/?t=hour",
    "https://www.reddit.com/r/crypto",
    "https://www.reddit.com/r/crypto/hot",
    "https://www.reddit.com/r/crypto/new",
    "https://www.reddit.com/r/crypto/top/?t=week",
    "https://www.reddit.com/subreddits",
    "https://www.reddit.com/subreddits/new",
    "https://www.reddit.com/users",
    "https://www.reddit.com/user/nationalgeographic",
    "https://www.reddit.com/user/lukaskrivka/comments",
    "https://www.reddit.com/user/lukaskrivka/comments/?sort=new",
    "https://www.reddit.com/user/lukaskrivka/comments/?sort=hot",
    "https://www.reddit.com/user/lukaskrivka/comments/?sort=top&t=day",
    "https://www.reddit.com/user/lukaskrivka/submitted",
    "https://www.reddit.com/user/lukaskrivka/submitted/?sort=new",
    "https://www.reddit.com/user/lukaskrivka/submitted/?sort=hot",
    "https://www.reddit.com/user/lukaskrivka/submitted/?sort=top&t=week",
    "https://www.reddit.com/r/redditisfun/comments/13wxepd/rif_dev_here_reddits_api_changes_will_likely_kill"
  ],
  "search": "",
  "searchMode": "user",
  "sort": "top",
  "time": "year",
  "endPage": 2000,
  "maxItems": 10000,
  "includeComments": true,
  "proxy": {
    "useApifyProxy": true
  }
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with a failure state and output an explanation of what is wrong.

## Reddit Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any language (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Reddit actor.

## Scraped Reddit Properties

The structure of each item on Reddit looks like this:

### Community

```json
{
  "type": "community",
  "id": "2qh13",
  "url": "https://www.reddit.com/r/worldnews/",
  "title": "World News",
  "icon": "https://styles.redditmedia.com/t5_2qh13/styles/communityIcon_pldiwqvsyns91.png?width=256&amp;v=enabled&amp;s=3088f291b089bb5bc15599d429a759b258c6cbd5",
  "subscribers": 32018938,
  "bannerImage": "https://styles.redditmedia.com/t5_2qh13/styles/bannerBackgroundImage_5q0f5lsk6pu01.png?width=4000&amp;v=enabled&amp;s=bdfa7d8903b848b0f7885868e8228652a1d3ee9d",
  "subredditType": "public",
  "headerTitle": "News from Planet Earth",
  "publicDescription": "A place for major news from around the world, excluding US-internal news.",
  "publicDescriptionHTML": "&lt;!-- SC_OFF --&gt;&lt;div class=\"md\"&gt;&lt;p&gt;A place for major news from around the world, excluding US-internal news.&lt;/p&gt;\n&lt;/div&gt;&lt;!-- SC_ON --&gt;",
  "description": "&gt;&gt;&gt; - **Other Subs:**\n\n&gt;&gt;&gt; - [Related](http://goo.gl/ztbbza)\n&gt;&gt;&gt;     - /r/News\n&gt;&gt;&gt;     - /r/PoliticalDiscussion\n&gt;&gt;&gt;     - /r/WorldEvents\n&gt;&gt;&gt;     - /r/GeoPolitics\n&gt;&gt;&gt;     - /r/IntheNews\n&gt;&gt;&gt;     - /r/GlobalTalk \n&gt;&gt;&gt;     - /r/Breakingnews \n&gt;&gt;&gt;     - /r/Business\n&gt;&gt;&gt;     - /r/Economics\n&gt;&gt;&gt;     - /r/Environment\n&gt;&gt;&gt;     - /r/History\n&gt;&gt;&gt;     - /r/HumanRights\n&gt;&gt;&gt;     - /r/Features\n&gt;&gt;&gt;     - /r/UpliftingNews\n&gt;&gt;&gt;     - /r/NewsOfTheWeird\n&gt;&gt;&gt;     - /r/FakeNews\n&gt;&gt;&gt;     - /r/ID_News \n\n&gt;&gt;&gt; - [N. America](https://goo.gl/dkfVnB)\n&gt;&gt;&gt;     - /r/Politics\n&gt;&gt;&gt;     - /r/USA\n&gt;&gt;&gt;     - /r/USANews\n&gt;&gt;&gt;     - /r/Canada\n&gt;&gt;&gt;     - /r/CanadaPolitics\n&gt;&gt;&gt;     - /r/OnGuardForThee\n&gt;&gt;&gt;     - /r/Cuba\n&gt;&gt;&gt;     - /r/Mexico\n&gt;&gt;&gt;     - /r/PuertoRico\n\n&gt;&gt;&gt; - [S. America](https://goo.gl/DDaqmY)\n&gt;&gt;&gt;     - /r/Argentina\n&gt;&gt;&gt;     - /r/Brasil\n&gt;&gt;&gt;     - /r/Chile\n&gt;&gt;&gt;     - /r/Colombia\n&gt;&gt;&gt;     - /r/Ecuador\n&gt;&gt;&gt;     - /r/Guyana\n&gt;&gt;&gt;     - /r/Nicaragua\n&gt;&gt;&gt;     - /r/PanAmerica \n&gt;&gt;&gt;     - /r/Suriname \n&gt;&gt;&gt;     - /r/Uruguay\n&gt;&gt;&gt;     - [/r/Venezuela](/r/vzla)\n\n&gt;&gt;&gt; - [Europe](https://goo.gl/ZF5rou)\n&gt;&gt;&gt;     - /r/Armenia\n&gt;&gt;&gt;     - /r/Austria\n&gt;&gt;&gt;     - /r/Azerbaijan\n&gt;&gt;&gt;     - /r/Belgium\n&gt;&gt;&gt;     - [/r/Bosnia](/r/BiH)\n&gt;&gt;&gt;     - /r/Bulgaria\n&gt;&gt;&gt;     - /r/Croatia\n&gt;&gt;&gt;     - /r/Denmark\n&gt;&gt;&gt;     - /r/Europe\n&gt;&gt;&gt;     - /r/Finland\n&gt;&gt;&gt;     - /r/France\n&gt;&gt;&gt;     - [/r/Georgia](/r/sakartvelo)\n&gt;&gt;&gt;     - /r/Germany\n&gt;&gt;&gt;     - /r/Greece\n&gt;&gt;&gt;     - /r/Hungary\n&gt;&gt;&gt;     - /r/Ireland\n&gt;&gt;&gt;     - /r/Italy\n&gt;&gt;&gt;     - /r/Moldova\n&gt;&gt;&gt;     - /r/TheNetherlands\n&gt;&gt;&gt;     - /r/Poland\n&gt;&gt;&gt;     - /r/Polska\n&gt;&gt;&gt;     - /r/Portugal\n&gt;&gt;&gt;     - /r/Romania\n&gt;&gt;&gt;     - /r/Scotland\n&gt;&gt;&gt;     - /r/Serbia\n&gt;&gt;&gt;     - /r/Spain\n&gt;&gt;&gt;     - /r/Sweden\n&gt;&gt;&gt;     - /r/Switzerland\n&gt;&gt;&gt;     - /r/Turkey\n&gt;&gt;&gt;     - /r/UnitedKingdom\n&gt;&gt;&gt;     - /r/UKPolitics\n&gt;&gt;&gt;     - /r/Ukraina\n&gt;&gt;&gt;     - /r/Ukraine\n&gt;&gt;&gt;     - /r/UkrainianConflict\n\n&gt;&gt;&gt; - [Asia](https://goo.gl/az3Ygk)\n&gt;&gt;&gt;     - /r/Afghanistan\n&gt;&gt;&gt;     - /r/Bangladesh\n&gt;&gt;&gt;     - /r/China\n&gt;&gt;&gt;     - /r/India\n&gt;&gt;&gt;     - /r/Kazakhstan \n&gt;&gt;&gt;     - /r/Malaysia\n&gt;&gt;&gt;     - /r/Myanmar\n&gt;&gt;&gt;     - /r/Nepal\n&gt;&gt;&gt;     - /r/NorthKoreaNews\n&gt;&gt;&gt;     - /r/Pakistan\n&gt;&gt;&gt;     - /r/Philippines\n&gt;&gt;&gt;     - /r/Singapore\n\n&gt;&gt;&gt;     - /r/Thailand\n&gt;&gt;&gt;     - /r/Turkey\n\n&gt;&gt;&gt; - [Middle East](https://goo.gl/Ut3syV)\n&gt;&gt;&gt;     - /r/Assyria\n&gt;&gt;&gt;     - /r/Iran\n&gt;&gt;&gt;     - /r/Iranian\n&gt;&gt;&gt;     - /r/Iraq\n&gt;&gt;&gt;     - /r/Israel\n&gt;&gt;&gt;     - /r/Kurdistan\n&gt;&gt;&gt;     - /r/LevantineWar\n&gt;&gt;&gt;     - /r/MiddleEastNews\n&gt;&gt;&gt;     - /r/MideastPeace\n&gt;&gt;&gt;     - /r/Palestine\n&gt;&gt;&gt;     - /r/Syria\n&gt;&gt;&gt;     - /r/Yemen\n&gt;&gt;&gt;     - /r/YemeniCrisis\n\n&gt;&gt;&gt; - [Africa](https://goo.gl/FgJ4Na)\n&gt;&gt;&gt;     - /r/Africa\n&gt;&gt;&gt;     - /r/Namibia \n&gt;&gt;&gt;     - /r/SouthAfrica\n\n&gt;&gt;&gt; - [Oceania](https://goo.gl/5pz9uS)\n&gt;&gt;&gt;     - /r/Australia\n&gt;&gt;&gt;     - /r/Fijian\n&gt;&gt;&gt;     - /r/NewZealand\n&gt;&gt;&gt;     - /r/Oceania\n&gt;&gt;&gt;     - /r/Westpapua\n\n## **Filter out dominant topics:**\n\n[Display COVID-19 submissions](http://www.reddit.com/r/worldnews#nc)\n\n[Filter COVID-19](http://nc.reddit.com/r/worldnews#www)\n\n[Display Russia/Ukraine submissions](http://www.reddit.com/r/worldnews#nr)\n\n[Filter Russia/Ukraine](http://nr.reddit.com/r/worldnews#www)\n\n[Display North Korea submissions](http://www.reddit.com/r/worldnews#nk)\n\n[Filter North Korea](http://nk.reddit.com/r/worldnews#www)\n\n[Display Afghanistan submissions](http://www.reddit.com/r/worldnews#nh)\n\n[Display Israel/Palestine submissions](http://www.reddit.com/r/worldnews#ni)\n\n[Filter Israel / Palestine](http://ni.reddit.com/r/worldnews#www)\n\n[Display all submissions](http://www.reddit.com/r/worldnews#iu)\n\n[Filter all dominant topics](http://iu.reddit.com/r/worldnews#www)\n\n#### [](#h4-green)\n&gt;# Welcome!\n&gt;\n&gt; /r/worldnews is for major news from around the world except US-internal news / US politics\n\n&gt; [See all of our AMA events here] (http://www.reddit.com/r/worldnews/wiki/ama)\n\n###### [](#h6-red)\n&gt;#Worldnews Rules\n&gt;\n&gt;\n&gt;### **Disallowed submissions**\n&gt;\n&gt; * US internal news/US politics\n&gt; * Editorialized titles\n&gt; * Misleading titles\n&gt; * Editorials, opinion, analysis\n&gt; * Feature stories\n&gt; * Non-English articles\n&gt; * Images, videos or audio clips\n&gt; * Petitions, advocacy, surveys\n&gt; * All caps words in titles\n&gt; * Blogspam (if stolen content/direct copy)\n&gt; * Twitter, Facebook, Tumblr\n&gt; * Old news (≥1 week old) articles\n\n&gt;[See the wiki](/r/worldnews/wiki/rules#wiki_disallowed_submissions) for details on each rule\n\n&gt;### **Disallowed comments**\n&gt;\n&gt; * Bigotry / Other offensive content\n&gt; * Personal attacks on other users\n&gt; * Memes/GIFs\n&gt; * Unlabeled NSFW images/videos\n&gt; * URL shorteners\n&gt; * Celebrating death/Advocating violence\n&gt; * Genocide denial/downplaying genocide\n&gt; * Disinformation/misinformation\n&gt; * Health disinformation/misinformation\n\n&gt;[See the wiki](/r/worldnews/wiki/rules#wiki_disallowed_comments) for details on each rule\n\n&gt;[Guidelines for the media](/r/worldnews/wiki/media)\n\n&gt; Violation of our rules may result in a ban from this subreddit. Untimed bans may be lifted when the moderators are confident that you will not continue to infringe on the community rules.\n\n&gt;\n&gt;----\n&gt;\n&gt;**Please don't ever feed the trolls.**    \n&gt;Downvote, report and move on.\n&gt;\n&gt;----\n&gt;\n&gt;* [**What moderators do and can't do**](/r/worldnews/wiki/whatmodsdo)\n&gt;* [**Message the moderators**](http://www.reddit.com/message/compose?to=%2Fr%2Fworldnews)\n\n#### [](#h4-green)\n&gt;# Sticky Posts\n\n&gt; • [A list of all recent stickied posts.](/r/worldnews/search?q=author%3AWorldNewsMods+OR+title%3A%22worldnews+live+thread%22+OR+self%3Ayes&amp;restrict_sr=on&amp;sort=new&amp;t=all)\n\n&gt; • **[Daily Live Threads](https://www.reddit.com/user/WorldNewsMods/submitted/?sort=new)**\n&gt;",
  "submitText": "###### [](#h6-red)\n&gt;# DISALLOWED SUBMISSIONS\n&gt;\n&gt; * US internal news/US politics\n&gt; * Editorialized titles\n&gt; * Feature stories\n&gt; * Editorials, opinion, analysis\n&gt; * Non-English articles\n&gt; * Raw images, videos or audio clips\n&gt; * Petitions, advocacy, surveys\n&gt; * No all caps words in titles\n&gt; * Blogspam (if stolen content/direct copy)\n&gt; * Twitter, Facebook, Tumblr\n&gt; * Old news (≥1 week old) articles",
  "createdAt": 1201231119,
  "submissionType": "link",
  "allowedMediaInComments": [
    "expression"
  ],
  "hideCommentScoreForMins": 90
}
```

### Post

```json
{
  "type": "post",
  "id": "t3_13wxepd",
  "url": "https://www.reddit.com/r/redditisfun/comments/13wxepd/rif_dev_here_reddits_api_changes_will_likely_kill/",
  "title": "RIF dev here - Reddit's API changes will likely kill RIF and other apps, on July 1, 2023",
  "flair": null,
  "flairs": [],
  "subreddit": "redditisfun",
  "subredditId": "t5_2rfi7",
  "author": "talklittle",
  "authorId": "t2_39mle",
  "authorFlair": "RIF Dev",
  "text": "I need more time to get all my thoughts together, but posting this quick post since so many users have been asking, and it's been making rounds on news sites.\n\nSummary of what Reddit Inc has announced so far, specifically the parts that will kill many third-party apps:\n\n1. The Reddit API will cost money, and the pricing announced today will cost apps like [Apollo $20 million per year to run](https://old.reddit.com/r/apolloapp/comments/13ws4w3/had_a_call_with_reddit_to_discuss_pricing_bad/). RIF may differ but it would be in the same ballpark. And no, RIF does not earn anywhere remotely near this number.\n\n2. As part of this they are blocking ads in third-party apps, which make up the majority of RIF's revenue. So they want to force a paid subscription model onto RIF's users. **Meanwhile Reddit's official app still continues to make the vast majority of its money from ads.**\n\n3. Removal of sexually explicit material from third-party apps **while keeping said content in the official app**. Some people have speculated that NSFW is going to leave Reddit entirely, but then why would Reddit Inc have recently [*expanded* NSFW upload support on their desktop site](https://old.reddit.com/r/modnews/comments/13evueo/bringing_image_uploads_to_parity/)?\n\nTheir recent moves smell a lot like they want third-party apps gone, RIF included.\n\nI know some users will chime in saying they are willing to pay a monthly subscription to keep RIF going, but trust me that you would be in the minority. There is very little value in paying a high subscription **for less content** (in this case, NSFW). Honestly if I were a user of RIF and not the dev, I'd have a hard time justifying paying the high prices being forced by Reddit Inc, despite how much RIF obviously means to me.\n\nThere is a lot more I want to say, and I kind of scrambled to write this since I didn't expect news reports today. I'll probably write more follow-up posts that are better thought out. But this is the gist of what's been going on with Reddit third-party apps in 2023.",
  "textHTML": "&lt;!-- SC_OFF --&gt;&lt;div class=\"md\"&gt;&lt;p&gt;I need more time to get all my thoughts together, but posting this quick post since so many users have been asking, and it&amp;#39;s been making rounds on news sites.&lt;/p&gt;\n\n&lt;p&gt;Summary of what Reddit Inc has announced so far, specifically the parts that will kill many third-party apps:&lt;/p&gt;\n\n&lt;ol&gt;\n&lt;li&gt;&lt;p&gt;The Reddit API will cost money, and the pricing announced today will cost apps like &lt;a href=\"https://old.reddit.com/r/apolloapp/comments/13ws4w3/had_a_call_with_reddit_to_discuss_pricing_bad/\"&gt;Apollo $20 million per year to run&lt;/a&gt;. RIF may differ but it would be in the same ballpark. And no, RIF does not earn anywhere remotely near this number.&lt;/p&gt;&lt;/li&gt;\n&lt;li&gt;&lt;p&gt;As part of this they are blocking ads in third-party apps, which make up the majority of RIF&amp;#39;s revenue. So they want to force a paid subscription model onto RIF&amp;#39;s users. &lt;strong&gt;Meanwhile Reddit&amp;#39;s official app still continues to make the vast majority of its money from ads.&lt;/strong&gt;&lt;/p&gt;&lt;/li&gt;\n&lt;li&gt;&lt;p&gt;Removal of sexually explicit material from third-party apps &lt;strong&gt;while keeping said content in the official app&lt;/strong&gt;. Some people have speculated that NSFW is going to leave Reddit entirely, but then why would Reddit Inc have recently &lt;a href=\"https://old.reddit.com/r/modnews/comments/13evueo/bringing_image_uploads_to_parity/\"&gt;&lt;em&gt;expanded&lt;/em&gt; NSFW upload support on their desktop site&lt;/a&gt;?&lt;/p&gt;&lt;/li&gt;\n&lt;/ol&gt;\n\n&lt;p&gt;Their recent moves smell a lot like they want third-party apps gone, RIF included.&lt;/p&gt;\n\n&lt;p&gt;I know some users will chime in saying they are willing to pay a monthly subscription to keep RIF going, but trust me that you would be in the minority. There is very little value in paying a high subscription &lt;strong&gt;for less content&lt;/strong&gt; (in this case, NSFW). Honestly if I were a user of RIF and not the dev, I&amp;#39;d have a hard time justifying paying the high prices being forced by Reddit Inc, despite how much RIF obviously means to me.&lt;/p&gt;\n\n&lt;p&gt;There is a lot more I want to say, and I kind of scrambled to write this since I didn&amp;#39;t expect news reports today. I&amp;#39;ll probably write more follow-up posts that are better thought out. But this is the gist of what&amp;#39;s been going on with Reddit third-party apps in 2023.&lt;/p&gt;\n&lt;/div&gt;&lt;!-- SC_ON --&gt;",
  "gallery": [],
  "score": 33998,
  "upvoteRatio": 1,
  "isOriginal": false,
  "createdAt": 1685565699,
  "editedAt": 1685565933,
  "isOver18": false,
  "removedByCategory": null,
  "commentCount": 6265,
  "awards": [
    {
      "id": "award_3dd248bc-3438-4c5b-98d4-24421fd6d670",
      "name": "Coin Gift",
      "description": "Give the gift of %{coin_symbol}250 Reddit Coins.",
      "icon": "https://i.redd.it/award_images/t5_22cerq/cr1mq4yysv541_CoinGift.png",
      "count": 1
    },
    {
      "id": "award_19860e30-3331-4bac-b3d1-bd28de0c7974",
      "name": "Heartwarming",
      "description": "I needed this today",
      "icon": "https://i.redd.it/award_images/t5_22cerq/v1mxw8i6wnf51_Heartwarming.png",
      "count": 1
    },
    {
      "id": "award_88fdcafc-57a0-48db-99cc-76276bfaf28b",
      "name": "Press F",
      "description": "To pay respects.",
      "icon": "https://i.redd.it/award_images/t5_22cerq/tcofsbf92md41_PressF.png",
      "count": 1
    },
    {
      "id": "award_b92370bb-b7de-4fb3-9608-c5b4a22f714a",
      "name": "Tree Hug",
      "description": "Show nature some love.",
      "icon": "https://i.redd.it/award_images/t5_22cerq/fukjtec638u41_TreeHug.png",
      "count": 2
    },
    {
      "id": "award_2ae56630-cfe0-424e-b810-4945b9145358",
      "name": "Helpful (Pro)",
      "description": "Thank you stranger. Gives %{coin_symbol}100 Coins to both the author and the community.",
      "icon": "https://www.redditstatic.com/gold/awards/icon/Animated_Helpful_512.png",
      "count": 2
    },
    {
      "id": "award_4ca5a4e6-8873-4ac5-99b9-71b1d5161a91",
      "name": "Argentium",
      "description": "Latin for distinguished, this award shimmers like silver and is stronger than steel. It’s for those who deserve outsized recognition. Gives 2,500 Reddit Coins and three months of r/lounge access and ad-free browsing.",
      "icon": "https://www.redditstatic.com/gold/awards/icon/Mithril_512.png",
      "count": 1
    },
    {
      "id": "gid_2",
      "name": "Gold",
      "description": "Gives 100 Reddit Coins and a week of r/lounge access and ad-free browsing.",
      "icon": "https://www.redditstatic.com/gold/awards/icon/gold_512.png",
      "count": 12
    },
    {
      "id": "gid_3",
      "name": "Platinum",
      "description": "Gives 700 Reddit Coins and a month of r/lounge access and ad-free browsing.",
      "icon": "https://www.redditstatic.com/gold/awards/icon/platinum_512.png",
      "count": 4
    },
    {
      "id": "award_02d9ab2c-162e-4c01-8438-317a016ed3d9",
      "name": "Take My Energy",
      "description": "I'm in this with you.",
      "icon": "https://i.redd.it/award_images/t5_q0gj4/p4yzxkaed5f61_oldtakemyenergy.png",
      "count": 3
    },
    {
      "id": "award_58ef8551-8c27-4f03-afa5-748432194e3d",
      "name": "Defeated",
      "description": "The process of taking a painful L",
      "icon": "https://i.redd.it/award_images/t5_22cerq/ooo0r2cq7q161_Defeated.png",
      "count": 3
    },
    {
      "id": "award_9583d210-a7d0-4f3c-b0c7-369ad579d3d4",
      "name": "Mind Blown",
      "description": "When a thing immediately combusts your brain. Gives %{coin_symbol}100 Coins to both the author and the community.",
      "icon": "https://i.redd.it/award_images/t5_22cerq/wa987k0p4v541_MindBlown.png",
      "count": 1
    },
    {
      "id": "award_43c43a35-15c5-4f73-91ef-fe538426435a",
      "name": "Bless Up (Pro)",
      "description": "Prayers up for the blessed. Gives %{coin_symbol}100 Coins to both the author and the community.",
      "icon": "https://i.redd.it/award_images/t5_22cerq/xe5mw55w5v541_BlessUp.png",
      "count": 1
    },
    {
      "id": "award_abcdefe4-c92f-4c66-880f-425962d17098",
      "name": "Burning Cash",
      "description": "I don't need it, I don't even necessarily want it, but I've got some cash to burn so I'm gonna get it.",
      "icon": "https://i.redd.it/award_images/t5_22cerq/kqr00h8b7q161_BurningCash.png",
      "count": 1
    },
    {
      "id": "award_31260000-2f4a-4b40-ad20-f5aa46a577bf",
      "name": "Timeless Beauty",
      "description": "Beauty that's forever. Gives %{coin_symbol}100 Coins each to the author and the community.",
      "icon": "https://www.redditstatic.com/gold/awards/icon/Timeless_512.png",
      "count": 1
    },
    {
      "id": "award_28e8196b-d4e9-45bc-b612-cd4c7d3ed4b3",
      "name": "Rocket Like",
      "description": "When an upvote just isn't enough, smash the Rocket Like.",
      "icon": "https://i.redd.it/award_images/t5_q0gj4/35d17tf5e5f61_oldrocketlike.png",
      "count": 1
    },
    {
      "id": "award_8352bdff-3e03-4189-8a08-82501dd8f835",
      "name": "Hugz",
      "description": "Everything is better with a good hug",
      "icon": "https://i.redd.it/award_images/t5_q0gj4/ks45ij6w05f61_oldHugz.png",
      "count": 1
    },
    {
      "id": "award_b4ff447e-05a5-42dc-9002-63568807cfe6",
      "name": "All-Seeing Upvote",
      "description": "A glowing commendation for all to see",
      "icon": "https://www.redditstatic.com/gold/awards/icon/Illuminati_512.png",
      "count": 10
    }
  ]
}
```

### Comment

```json
{
  "type": "comment",
  "id": "j2hu3o9",
  "url": "https://www.reddit.com/r/keto/comments/zzzv8m/expectations_too_high/j2hu3o9/",
  "author": "lukaskrivka",
  "authorId": "t2_4y22fmn1",
  "authorFlair": null,
  "isSubmitter": false,
  "body": "It has to be individual because when I tried keto 7 years ago, my anxiety and depression almost disappeared after like 1 week, it was totally magical and unexpected. I guess it depends on your body and what is the main cause of your condition.\n\nI want to try it again this year as my mood got worse again over years.",
  "bodyHTML": "&lt;div class=\"md\"&gt;&lt;p&gt;It has to be individual because when I tried keto 7 years ago, my anxiety and depression almost disappeared after like 1 week, it was totally magical and unexpected. I guess it depends on your body and what is the main cause of your condition.&lt;/p&gt;\n\n&lt;p&gt;I want to try it again this year as my mood got worse again over years.&lt;/p&gt;\n&lt;/div&gt;",
  "createdAt": 1672575589,
  "editedAt": false,
  "score": 2,
  "parentId": "t3_zzzv8m",
  "postUrl": "https://www.reddit.com/r/keto/comments/zzzv8m/expectations_too_high/",
  "postTitle": "Expectations too high?",
  "postId": "t3_zzzv8m",
  "subreddit": "keto",
  "subredditId": "t5_2rske",
  "awards": []
}
```

### User

```json
{
  "type": "user",
  "id": "129jlh",
  "url": "https://www.reddit.com/user/MikeMikeGaming",
  "name": "MikeMikeGaming",
  "title": "Opanic",
  "publicDescription": "",
  "icon": "https://styles.redditmedia.com/t5_bqe06/styles/profileIcon_snoo-nftv2_bmZ0X2VpcDE1NToxMzdfYTMzOTZhZjIwY2U1MmJkM2M3YWI2ZDcwNDZiZTYxNzI1N2Y2MGViOV80NjA0_rare_e94a979b-b6ad-489a-8b25-87226fc848bd-headshot.png?width=256&amp;height=256&amp;crop=256:256,smart&amp;v=enabled&amp;s=41b559dbf2ba43f05b8c483d54b220266f5dd873",
  "commentKarma": 16543,
  "linkKarma": 16132,
  "createdAt": 1476985743,
  "isGold": false,
  "isMod": true,
  "isOver18": false,
  "isVerified": true,
  "hasVerifiedEmail": true,
  "isEmployee": false,
  "acceptsFollowers": true
}
```

## Contact 
Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
