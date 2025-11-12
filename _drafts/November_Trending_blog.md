# Mastodon Trending Statuses Interventions

### Mastodon Trending

One of the most unique features of Mastodon compared to traditional social media platforms like Twitter (X) is that the default home page for users does not use any special algorithms to display posts that are customized or personalized for that specific user. Instead, in Mastodon, the default setting is for the users to see the posts from their followings in chronological order (i.e., they see the newest post posted or boosted by the people that they follow). One of the biggest criticisms for this is that there is low discoverability. There is a limited chance for this person to see something that is outside of the people that they follow unless it's reposted or boosted by the people that the user is following. This is why in around early to mid 2022, Mastodon has expanded its trending feature to originally just having trending tags to now having trending posts and news.

I was intrigued to explore and analyze how Mastodon has implemented this feature that is meant to improve discoverability. While looking through the codebase for Mastodon, it seems like the main file for trending posts is within *app/models/trends/statuses.rb*. Going through the file, it seems like the eligibility parameters for a post to become trending are split into four categories, logistics, logical validity, privacy, and algorithmic. I have created a table that sorts each parameter into a category.

| Parameter | Category |
| ----- | ----- |
| status.created_at_past? | Logical Validity |
| status.public_visibility | Privacy |
| status.account.discoverable? | Privacy |
| status.account.silenced? | Privacy |
| status.account.sensitized? | Algorithmic |
| status.spoiler_text.present? | Algorithmic |
| status.sensitive? | Algorithmic |
| !status.reply? | Algorithmic |
| valid_locale? | Logistics |
| status.quote.nil? | Logical Validity |
| quote.acceptable? | Logical Validity |
| quote.quoted_status.present? | Logistics |
