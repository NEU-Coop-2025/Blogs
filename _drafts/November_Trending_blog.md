# Mastodon Trending Statuses Interventions

TODO:
- find citations to back up my thoughts

## Introduction

One of the most unique features of Mastodon compared to traditional social media platforms like Twitter (X) is that the default home page for users does not use any special algorithms to display posts that are customized or personalized for that specific user. Instead, in Mastodon, the default setting is for the users to see the posts from their followings in chronological order (i.e., they see the newest post posted or boosted by the people that they follow). One of the biggest criticisms for this is that there is low discoverability. There is a limited chance for this person to see something that is outside of the people that they follow unless it's reposted or boosted by the people that the user is following. This is why in around early to mid 2022, Mastodon has expanded its trending feature to originally just having trending tags to now having trending posts and news.

I was intrigued to explore and analyze how Mastodon has implemented this feature that is meant to improve discoverability. While looking through the codebase for Mastodon, it seems like the main file for trending posts is within this [file](https://github.com/mastodon/mastodon/blob/main/app/models/trends/statuses.rb). Going through the file, it seems like the eligibility parameters for a post to become trending are split into three categories: logical validity, privacy, and algorithmic. I have created a table that sorts each parameter into a category.

### Table of eligibility categories
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
| valid_locale? | Logical Validity |
| status.quote.nil? | Logical Validity |
| quote.acceptable? | Logical Validity |
| quote.quoted_status.present? | Logical Validity |

## What shouldn't be touched by administrators
This categorization reveals a deep tension in Mastodon's design: the tension between a consistent, safe platform and a flexible, federated one. Some of these parameters are clearly invariants, the rules that shouldn't be easily changed by an administrator, if at all.

The logical validity checks, like valid_locale & quote.quoted_status.present, ensures the smooth running of the application itself. These parameters should not be accessible to the administrators to prevent the software from falling into unknown, broken states.

For example, imagine an instance administrator, without knowing what it means, turns of the valid_locale requirement for their instance. This then would allow posts from other ActivityPub software that isn't in a language Mastodon supports to go trending in software, potentially displaying error codes for the users or crashing the software as a whole. This would not be a policy change, instead, it would lead to illogical outcomes. Similarly, quote.quoted_status.present? ensures that a trending quote-post actually has an original post to point to. Disabling this would lead to trending "empty" posts, a poor user experience that looks like a bug.

These checks are baked directly into the code because they are fundamental to the feature's integrity. Changing them would require re-architecting the trending logic, not just tweaking a setting.

The Privacy parameters are even more critical. According to [Kijung Lee and Mian Wang](https://arxiv.org/pdf/2303.01285), privacy is one of the big reasons why people use Mastodon. Checks like status.public_visibility and status.account.discoverable? are not just features, they are the central social contract of Mastodon. Many users choose Mastodon specifically for this level of granular control, and the bilateral trust between users and administrators. They expect a followers-only post to never be shown to the public, non-negotiable.

By hard-coding these privacy rules, Mastodon's developers are making a strong ethical statement. It forces responsibility onto the administrator. If an admin really wants to impose alternative, non-standard privacy settings (like allowing non-public posts to go trending on other people's pages), they can't just click a button in a settings panel. They would have to actively fork the code, patch the software, and maintain that fork, making their decision transparent and auditable. This friction is a powerful, deliberate design choice that protects the entire ecosystem.

## What should be accessible to administrators

Algorithmic choices, on the other hand, should be up to the administrator's to decide.
