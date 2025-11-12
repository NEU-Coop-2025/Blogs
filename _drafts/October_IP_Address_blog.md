# The IP Address Dilemma

TODO: add suitable subtitles

For decades, and for the forseeable years to come, the internet has ran on a simple exchange: provide your IP address, and you get to proceed/use the service. This exchange of information is essential for routing traffic, but it's also a foundational tool for security, moderation, and analytics.

The problem? That same IP address is a serious privacy risk. As technology and privacy laws evolve, the practice of logging raw IPs is becoming a significant liability.

## What is an IP Address?

An IP address, on its own, may not have your name on it, but it is legally considered personal data in many key jurisdictions. Take the GDPR in Europe for example, automatically treats IP addresses as Personally Identifiable Information (PII). "Natural persons may be associated with online identifiers provided by their devices, applications, tools and protocols, such as internet protocol addresses, cookie identifiers or other identifiers such as radio frequency identification tags." [GDPR Recital 30](https://gdpr-info.eu/recitals/no-30/). In the case of CCPA from California, IP addresses are only treated as PII if it "identifies, relates to, describes, is reasonably capable of being associated with, or could reasonably be linked, directly or indirectly, with a particular consumer or household." Nonetheless, IP addresses are and should be regulated as it is an important piece of information.

In some cases, IP addresses might not be PII. [Tim Lachance](https://law.unh.edu/sites/default/files/media/2018/08/ip-so-facto.pdf), a JD student at New Hampshpire School of Law, has argued that IP addresses are simply not PII. The three arguments he gave were: dynamicity, indefiniteness, and risk of harm. I will not be going through all of his arguments, but to summarize his paper: "The IP addresses are connected to machines and not people, and although they can be correlated with other data about individuals, that correlation cannot be made with any degree of certainty in order to unmask an individual's identity."

When users are using IP address obfuscation technologies such as Onion Routing and VPNs, it undoubtedly weakens the relationship between IP addresses and the ability for them to identify personal info. Thus, one could argue that IP addresses, with the help of other techniques, simply cannot be considered to be PII under the fact that it is difficult to identify actual personal information from protected IP addresses. In practice, while these technologies are more accessible to regular people on the internet nowadays, it is still hard for some, for certain individuals to be able to protect their IP addresses and for IP addresses to be unable to identify themselves. For example, people in China generally have a very hard time bypassing the Great Firewall.

Let's take a look at Google's argument on this. A software engineer at Google, Alma Whitten, has stated in a [Google Blog](https://publicpolicy.googleblog.com/2008/02/are-ip-addresses-personal.html) that "the IP addresses recorded by every website on the planet without additional information should not be considered personal data, because these websites usually cannot identify the human beings behind these number strings." Paul Ohm further explained this in his book [Broken Promises of Privacy](https://digitalcommons.law.scu.edu/cgi/viewcontent.cgi?article=1016&context=hightechevents) "websites like Google never store IP addresses devoid of context; instead, they store them connected to identity or behavior. Google probably knows from its log files, for example, that an IP address was used to access a particular email or calendar account, edit a particular word processing document, or send particular search queries to its search engine. By analyzing the connections woven throughout this mass of information, Google can draw some very accurate conclusions about the person linked to any particular IP address."

These debates create a conflicting dilemma for companies and social media moderators, as IP addresses are essential to defenses against spam, fraud, and other illegal activites. While taking the introductory cybersecurity course at Northeastern, [Professor Justin Wang](https://www.khoury.northeastern.edu/people/hsiao-an-justin-wang/) talked about the secrets users provide to systems in order to gain access to their accounts, with one of them being IP addresses, or where you are. When a user attempts to commit spam or fraud, the IP address is used to prevent these actions (as much as possible). In the case of harassments, IP addresses are also used to prevent banned users from simply creating a new account and coming back to the platform unharmed.

According to a [report](https://www.pewresearch.org/internet/2023/10/18/how-americans-view-data-privacy/) from Pew Research Center, in the United States, around two-thirds of the population do not understand what companies are doing with their personal data. Around three-quarters of the people believe that they have little to no control over what companies or the government do with their data. This is especially true in traditional social media platforms. Take Twitter for example. Everyone that uses the platform must agree to privacy policies that Twitter has set. For a long time, there were no great alternatives to Twitter. This means that if you want to engage with other people on a social platform, there is virtually no other choice besides agreeing to whatever Twitter says.

In Mastodon, the relationship between the users and the platform is quite different. Since Mastodon has multiple individual instances, often the users will have a stronger relationship and social ties with the administrators of that instance compared to the relationship between users of centralized social media with the company behind that centralized social media platform. According to [Erin Kissane and Darius Kazemi](https://fediverse-governance.github.io/#findings-report-governance-on-fediverse-microblogging-servers): "Fediverse moderation can offer humane, culturally attuned, context-sensitive moderation that far outperforms central platform offerings in its responsiveness to member needs and experiences." This allows the users to be a judge of how each instance is treating the user's data and gives them the freedom to choose which instance based on their preferences and standards. If one instance does not properly treat the user's data, the users will not choose that instance to store the data on.

However, the issue with Mastodon being decentralized is that there are inevitably a large number of instance administrators who want to run their own instance but does not properly understand the privacy policies. In a paper written by [Emma Tosch, Cynthia Li, Luis Garcia, and Chris Martens](https://petsymposium.org/popets/2024/popets-2024-0138.pdf), where they have surveyed and examined how dozens of Mastodon instance administrators handle the instance, it appeared that multiple instance administrators either use the default privacy policies from Mastodon and does not care to modify them, or even worse, does not fully acknowledge what data is being collected from Mastodon. An example of this is where a respondent from the survey stated that “we never collect or share user data” in the privacy policy of their instance. This is simply not true, as the Mastodon software requires the collection and retention of certain user data like IP addresses in order for it to provide a usable experience.

[//]: # (I decided to leave out any legal discussions for this blog)

[//]: # (Looking at the legal laws on data retention of IP addresses, the state is not so great. In the European Union, the GDPR states that the collection of IP addresses must have a clear legal basis and must not hold it for longer than strictly necessary. In the United States, there are no federal data retention laws, and, currently, as far as my knowledge goes, only CCPA has certain laws on the retention of IP addresses. This lack of clarity in the privacy laws regarding IP addresses means that the retention policies of different platforms are all over the place, from services that delete IP addresses after 24 hours to those that potentially hold it for as long as their software runs.)

[//]: # (Obviously, brilliant researchers have been researching about the solutions of how we can solve the issue of IP addresses, and the most complex yet the most seemingly complete solution is homomorphic encryption. Homomorphic encryption is this new innovative technology that empowers zero-trust in any scenario. It encrypts the information before anyone knows what's behind the information. For example, in our case of IP addresses, the server does not gain knowledge of the user's IP address right away. Instead, the IP address is encrypted immediately. Therefore, this encrypted IP address can be shared, analyzed, and stored anywhere without the risk of it being exposed. This way, the server can store a list of blacklisted or fraudulent IP addresses without the risk of it being exposed. Even if it is exposed, it is already encrypted and will not harm anyone's privacy. When administrators try and identify whether a user is fraudulent or blacklisted, they only have to ask whether the encrypted IP address they get matches any of the encrypted IP addresses on their blacklist. If it does, they get an encrypted yes or no address, then they can act upon that result. In this whole process, no one — not the server, not the cloud, not the administrator, not the users — see the actual IP addresses of any users.)

TODO:
- give an example of someone's privacy being violated due to their IP address being retained
    - premilinary idea: Hong Kong protest and China government getting the IP addresses of the protestors
- give a longer, more concrete example of how retaining IP addresses can help with the security of a website

## Ways to protect IP addresses

### Protection from the origin
| Method | How It Works |
| ----- | ----- |
| VPN (Virtual Private Network) | Encrypts connection and routes it through an intermediary server. Websites see the VPN's IP only. |
| Tor (Onion Routing) | Routes connection through multiple, encrypted volunteer relays, making it extremely difficult to trace the origin. |
| Proxy Server | Acts as a simple intermediary that forwards requests. The destination sees the proxy's IP. (Generally less secure than a VPN). |
| IPv6 Privacy Extensions | A feature of IPv6 that periodically generates a new, random interface identifier (the second half of origin IP) to prevent device tracking. |
| NAT (Network Address Translation) | The standard method home routers use to hide all private internal device IPs behind a single public IP. |

### Protection during storage
| Category | Method | Description |
| ----- | ----- | ----- |
| Access Control | Password Protection | The basic layer of securing the system, database, or file with a strong, unique password. |
| Access Control | Access Control Lists (ACLs) | Rules at the file system or network level that define *which* specific users or systems are permitted to access the data. |
| Access Control | Role-Based Access Control (RBAC) | Assigning permissions based on a user's job role, following the Principle of Least Privilege. |
| Access Control | Multi-Factor Authentication (MFA) | Requiring anyone accessing the data to provide more than just a password (e.g., a code from sms or authenticator). |
| Encryption | Local Encryption (At Rest) | Encrypting the hard drive (Full-Disk Encryption) or specific database columns (Transparent Data Encryption) where IPs are stored. |
| Encryption | Encryption in Transit | Using TLS/SSL to encrypt IP data as it moves between internal services (e.g., from a web server to a log database). |
| Encryption | Homomorphic Encryption | An advanced method that allows computations (like analytics) directly on encrypted data without ever decrypting it. |
| Data Minimization | IP Truncation | Storing only a portion of the IP. This is often enough for location data without storing the full, identifiable IP. |
| Data Minimization | Hashing | Running the IP through a one-way function (like SHA-256) with a salt to create an irreversible, anonymous string. |
| Data Minimization | Pseudonymization | Replacing the IP with a random token. The key that maps the token back to the real IP is stored in a separate, highly secure database. |
| Data Minimization | Data Retention Policies | Automatically and permanently deleting logs containing IP addresses after they are no longer needed (e.g., after 30 days). |
| Network Security | Firewalls | Using strict firewall rules to block all unauthorized access to the servers and databases that store IP data. |
| Network Security | Network Segmentation | Placing sensitive log databases on an isolated network segment, separate from public-facing servers. |
| Network Security | Auditing & Logging | Keeping detailed logs of who accessed the IP data and *when* to detect and respond to a breach. |


## Footnotes
- https://gdpr-info.eu/recitals/no-30/
- https://law.unh.edu/sites/default/files/media/2018/08/ip-so-facto.pdf
- https://publicpolicy.googleblog.com/2008/02/are-ip-addresses-personal.html
- https://digitalcommons.law.scu.edu/cgi/viewcontent.cgi?article=1016&context=hightechevents
- https://www.khoury.northeastern.edu/people/hsiao-an-justin-wang/
- https://www.pewresearch.org/internet/2023/10/18/how-americans-view-data-privacy/
- https://fediverse-governance.github.io/#findings-report-governance-on-fediverse-microblogging-servers
- https://petsymposium.org/popets/2024/popets-2024-0138.pdf
