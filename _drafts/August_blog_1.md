---
layout: post
title: "YSocial and Digital Twins"
---

### Introduction to YSocial

Recently, I've been reading about this new technology called digital twins. I found it to be very exciting, so I want to share some of my thoughts and have a bit of discussion around digital twins. The paper I read on digital twins is the one below. I think it's a great introduction, and it's also the one that my research supervisor has recommended to me to read about digital twins.

https://www.nature.com/articles/s43588-024-00603-w.pdf

I had no idea what a digital twin is. I have not heard of this phrase at all, and the first impression of it was that it felt similar to what NFTs are. It's also a digital representation of a real-world physical object, and that was my first impression of what a digital twin could be.

As I continued reading the paper, I found out that no, it's not like that. Digital twins are online objects or online clones of something in the physical world, but there are huge differences. The digital twins are alive, where they gather real-time data from the object or system that it is representing in the real world, so it keeps updating itself. An NFT is an online object, it's something that does not change, and that is one of the key properties of NFTs.

Something that is quite talked about on the internet is how digital twins have a use over regular simulations, which is being heavily used in different areas of the world. They have similar features; they both gather data and they both try to simulate what something in the real world or even in the digital world might do. They try to predict the future. Now they are more similar, I think. They have a similar go down inside the real difference here is simulation is where you feed it the data before it starts and try to predict everything afterwards based on the data you feed it. Whereas the digital twin is more of a progression where the digital twin will evolve as the physical twin progresses in the real world, like a twin where they grow, they evolve, they do everything basically simultaneously. And that's the thing with the Digital Twin, you basically get a realtime, digital clone of something in the real world, whether that is an object, whether that is a system, whether it is anything that has sorts of data that you could replicate in the real world. And basically, that is the real goal of what digital twins are.

On a side note, there seems to be a lot of buzzwords that can be fitted into presenting digital twins in this paper. I've read a lot about AIs, LLMs, machine learning, different models, I've even seen blockchain, security... It seems like potentially could grab the investors' attention one day.

## How digital twin relates to social media - YSocial

When I was reading the paper on digital twins, I was wondering how this technology would be able to fit within the scope of research that I was doing within this co-op, as the paper's examples of digital twins were all manufacturing-related. After reading the paper below, I realized why my research supervisor wanted me to learn about dictionary systems. Why social, which is talked about in the paper below, is a digital trend platform that replicates an online social media environment.

https://arxiv.org/pdf/2408.00818

In short, YSocial allows users to simulate a social media environment using LLMs. Some of the possible use cases for this would be to simulate political discussions on platforms like Twitter. It does this by utilizing LLM agents to mimic how real-world humans discuss, in this case, political discussions on social media. Thanks to the development of AI, this can be done very easily compared to what it was like a decade ago.

It also is a huge playground for researchers to gain insights into how LLMs are actually performing in trying to mimic humans. By using YSocial, it allows researchers to gain huge amounts of data and try out different kinds of settings to play around with to see whether the LLMs we have today can actually human-led environment online would look like and to see what kind of different settings they can address in order to achieve different results on potentially different social media platforms.

For example, on Instagram, it is not strictly the same concept compared to Twitter (where Instagram is more photo and image-based), it is a very distinct platform compared to Twitter (where Twitter is more opportunity for you to express your feelings). Instagram is more of a record, a place where you keep track of what you have done. You can put all of your photos, you can even put your stories (what your recent activities have been) onto Instagram. By adjusting different sliders and adjusting different personalities, the agents on the Why Social platforms behave. It could potentially be a very powerful tool for researchers to dive into.

## Trying out YSocial

I've also tried to play around with YSocial and trying to set it up locally. I have not been too successful with it. I ran across a few problems that I was unable to solve on my own. I am planning to contact the team behind YSocial to see if they would be able to solve any of the problems that I've encountered so wish me luck.

I was able to access the main dashboard of YSocial, but after following the instructions on that page and creating different experiments and agent populations, and actually activating the simulations, I was unable to get any of the results or get any of the posts that I would assume the agents would have created in order to have this simulation off Twitter. Instead, when I enter the simulation, I only get this posting page where I can act as a user of the social media platform and post something myself. It was very strange to me that a tool that would simulate social media doesn't actually give me any posts or any of the data that comes along with a simulation of social media.

On the website, I also saw that there is a "hard way" to do it where I would have to set up my server and my client separately. I presume that it allows for more customization of the setup. I believe that the documentation here is a bit outdated, and I would have to play around and find out a lot more about the tool itself. See where some of the things have fallen out of date and replace them in the code. I was not successfully run my social distro yet, so hopefully in the coming few days I'll be able to find out what is wrong in the documentation or in the code for the "hard way".

A very strange thing I discovered while trying YSocial is that some of the features on the web dashboard does not seem to work offline, even though it was setup locally, and the LLM connected was also through Ollama. When trying to create the "experiments" and "populations", if there is no network connection, the dashboard would not display the already created ones, instead only showing empty tables. A big todo for me to fully go through the codebase, as YSocial is open source, to see where this problem lies.

Looking ahead, something that me and my research supervisor would like to do is try and have YSocial communicate with Mastodon, which is the social media platform that we are focusing on. The goal is to set up a locally run master.instance where we would have Y Social acting as the LLM agent for users on that instance. We would try to figure out various kinds of things that we can play around with. Starting off, we would see what happens when changing some of the factors or configurations on Mastodon, especially related to privacy. These changes might affect how Mastodon is used, but with actual Mastodon, we are unable to simulate the effects of these changes with actual users. With these LLM agents, we can try and simulate the effects of these changes in a less harmful and less dangerous way.

Looking at this tool, I would imagine that it is wildly powerful and useful if being used correctly. Unfortunately, I have not been able to find the correct usage of this tool just yet. As I figure out how some of the features of this platform actually work, and finally being able to correctly use this technology, I believe that I'll be able to simulate and gather a bunch of simulated data about social media and AI, and especially the combination between them. Not only on the AI factor but also the human factor if been configured if configured correctly, this tool allows researchers (as I have mentioned) to simulate human behavior on social media which is a huge benefit for any of the research that they will be doing. I hope I will be able to utilize this tool in various areas, including but not limited to Mastodon.
