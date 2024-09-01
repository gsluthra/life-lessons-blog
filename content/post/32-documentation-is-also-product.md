+++
title = "Your documentation is also the Product"
description = "Lessons from building an open source 1000 page confluence wiki"
author = "Gurpreet Luthra"
date = 2024-08-31T07:30:50Z
images = ["/images/general/doc-product/document-product.jpg"]


tags = [
    "product-management",
    "opensource",
    "software"
]

+++

![Documentation is also the product](/images/general/doc-product/document-product.jpg "Your documentation is also the Product")


## Introduction
I spent over 8 years on Bahmni, an opensource EMR & hospital system. As part of that work, I was involved in introducing Confluence into the product in 2012. The initial focus was to introduce public-facing documentation for implementing organisations (aka Implementors), to understand how to implement, deploy, configure and support Bahmni.

Since then Bahmni Wiki documentation has evolved to over a **1000 pages** comprising of _User Guide_, _Feature Guide_, _Implementer Guide_, _Install Guide_, _Security Guide_, _Developer Guide_, etc. It is pretty impressive and also loved by the Bahmni community of adopters. **These are a few lessons I learned along the way.**

![Bahmni Wiki Landing Page](/images/general/doc-product/bahmni-wiki-home.jpg "Bahmni Wiki Landing Page")


## 1. Are you documenting a Usability / Design Gap?
Whenever you decide to document something, it is important to ask: Is there a product design or a usability gap that is resulting in us requiring to document something? If so, maybe it is an opportunity to improve the usability of the product. Make it more intuitive. The best user-experience requires no documentation. For instance, when you installed WhatsApp, did you need to read a document to learn how to send a chat message?

As a Product leader, it is important to assess WHAT (and WHY) is being documented. Why is it so complicated that it needs documentation?

In Bahmni, when we introduced Docker (and docker-compose), we wrote extensive documentation on how to use various docker-compose commands to start various Bahmni services, view service logs, reset database, etc. However, there was still "friction" for many adopters who were unaware of Docker (we target NGOs, Govts and hospital/clinics in low-resource environments). So, we created a script called `run-bahmni.sh` ([github](https://github.com/Bahmni/bahmni-docker/blob/master/run-bahmni.sh#L185)) which wrapped all these functions into an easy-to-use menu-driven command line option. This reduced the need for users to go and read the documentation for the basic tasks and reduced "time-to-first-start" Bahmni! 


![run-bahmni script](/images/general/doc-product/run-bahmni-command.jpg "run-bahmni script menu command line")



## 2. The purpose of documentation is to reduce the time it takes for the user to achieve something.

The reason we write documentation is to help a user understand how to get "something" done easily. The better your documentation, the faster they can get it done. This means, in the end your documentation AND your product, are together helping in "getting-something-done". If that is the case, then your document is also part of your product. 

Imagine you wrote a sucky document, and they could not figure out how to do X -- won't they blame the product? Saying -- it is hard to do X or Y or X with the product. Therefore, poor documentation leads to poor product experience.

## 3. Good documentation is written with the reader in mind. 

One has to think about who the various _readers_ of the documentation can be. In a way, they are the _users_ of the _product_, and hence the _users_ of the _document_. So, for this reason, in Bahmni, we wrote different guides:

a. **Implementor Guide:** For implementors, who install Bahmni for hospitals, and usually understand Linux/Windows, JSON, config files, commands, SQL, some HTML, probably a bit of Java -- but are not programmers. Possibly more like IT operators. Therefore the product configuration features, and the Implementor guide, both have to be designed for this persona. The documentation has to use the _readers_ mindset, their _vocabulary_, to enable them to understand and find the relevant information.

b. **Security Guide:** We extracted a separate Security Guide, containing all the various guidance and tips on Securing Bahmni server, into one place. This is because, the person who is coming to evaluate Bahmni from a security perspective, will want to quickly know what guardrails, configurations and features Bahmni has considered. Scattering these pages across multiple guides will make this persona feel confused or likely disappointed. See the Bahmni Security guide [here]( https://bahmni.atlassian.net/wiki/spaces/BAH/pages/3091300353/Security%2BGuide).

c. **User Guide**: For end-users, to understand how to navigate and use the Bahmni UI. 

d. **Developers Guide**: For developers, coding best practices, architecture, quality practices, etc. 

Also, we added references to useful pages on many pages to ensure that when people landed on a particular page, they are also able to find other related information that is helpful, for example: A training video related to this module, or a public discussion regarding the roadmap of this feature. The idea is to help the reader find the relevant information, and also the corresponding contextual information. This requires a strong understanding of the audience, and also a willingness to evolve pages based on community feedback, support tickets, conversations, etc. For example see the screenshot below where we mention tools to connect to various Bahmni databases, and also provide references to anonymizing databases, etc. on the same page:

https://bahmni.atlassian.net/wiki/spaces/BAH/pages/49545219/Connecting+to+various+databases

![database wiki page](/images/general/doc-product/database-documentation.jpg "Connect to Bahmni Database page with related links on the right side showing how to anonymize the database")

The above mindset of designing documentation with the target personas in mind, and curating and evolving it, to bring related pages together, and easy to find -- is the PRODUCT MINDSET!

## 4. A page that can elicit actionable feedback is better than a perfect page.

We realized that getting feedback on documentation pages is easy. Once a page is put up, with _some_ information, and widely shared, then people comment on what it lacks, how it could be written better, etc. Therefore, it is important to ensure a page for a feature is put up, with basic content, and then allow for team members and community members (or users) to easily drop comments, and provide feedback. This way, the page can quickly evolve to become useful. 

Again, these are principles of modern Product Development -- lightweight, rapid, MVP, quick go-live, and then use feedback cycles to improve the product. The inertia in the team is usually for creating the first version. Helping them do that, as part of Story / Iteration work, helps ensure there is _something_ acceptable out there. Of course, depending on individuals and their skill, some team members do a _great_ job the first time itself! 

## 5. Set the standards with great pages and templates early, and others will follow.

Once good pages are created, with certain templates/structures, it makes is very easy for anyone to just *copy_and_paste* and then modify, and make the new pages also rich and helpful. Hence, the faster we have some good example pages, and we evangelize them across the teams, the easier it gets for everyone else to follow.

For example: The Bahmni [Releases Page](https://bahmni.atlassian.net/wiki/spaces/BAH/pages/70221837/All+Bahmni+Legacy+Releases) has mostly remained the same for last 8 years, because it is easy for someone to copy a row and replicate it for each new release. 

## 6. Over time wikis and documentation evolve and need continuous refactoring.

Imagine how you organize your files & folders on your machine. It didn't happen overnight. As new files and folders get added to your machine, you realize that it gets harder to find a file, or it gets harder to decide _where_ to put a file. This acts as a trigger to reorganise and refactor. The same is true for documentation. And for code files. Make a start, and then continuously refactor and reshape the Wiki. 

Make it easy to decide where to put the new documentation page. If people struggle, then it is a sign that documentation is not well organized, and a re-think might be needed. Creating a high-level information architecture for the documentation is important, and as the product evolves, the documentation also follows along.

## 7. Use popular pages to direct users to other relevant nuggets of gold.

Some pages will be much more popular than others -- for instance: Install Pages. Or some FAQ page, etc. You can see documentation metrics/analytics to figure this out. If so, then put other relevant information, or nuggets of gold page links, on those pages, to guide users to the other pages. For instance, 
 - In our install page, we have put links to the Security Guide, or to the Reporting Tool, to ensure people are aware that these pages & functionalities also exist. 
 - [This page](https://bahmni.atlassian.net/wiki/x/AQBTvQ) is considered a really useful page on Bahmni's support for Global Standards, and we have linked it in various wiki pages, to ensure people stumble onto it.
 - [This page](https://talk.openmrs.org/t/training-on-bahmni/6275/9) shows up on Google search for Bahmni training, so we have linked it to our actual Training Guide. 

## 8. Don't write long answers in chat. Instead, write a short document and share the page link.

For every long answer to a question on a forum or on Chat, see if it is an opportunity for a documentation update or a product improvement. Use questions and support tickets to identify what is missing in the document (or product). Whenever you find yourself writing a paragraph in response to a question, ask if this should go into the documentation, because other users in the future might ask the same thing. If yes, then put it in the documentation (and let technology index it for easy searchability). 


## Conclusion

The documentation is another _user interface_ for your Product. It is not just something that "supplements" your product, but it is an extension of your Product itself. If you apply the principles of product development to your documentation, you will be able to make your documentation (and your product) a delight for your users. 

**Remember: Your documentation is also the Product**.