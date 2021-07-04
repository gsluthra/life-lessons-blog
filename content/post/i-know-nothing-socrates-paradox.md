+++

title = "I Know That I Know Nothing"
description = "A model for helping us deal with the Socrates Paradox"
author = "Gurpreet Luthra"
date = 2018-05-12T02:13:50Z
images = ["/images/general/colombo_beach_image_small.jpg"]

aliases = [
    "/2018/05/12/i-know-nothing-socrates-paradox.html/",
    "/2018/05/12/i-know-nothing-socrates-paradox.html"
]

tags = [
    "learning",
    "technical",
    "thoughtworks",
    "self-help",
    "career",
]

+++

In this blog I introduce a model for helping us articulate unknowns in our knowledge and in projects.

![Beach side in Colombo, Sri Lanka](/images/general/colombo_beach_image_small.jpg "Beach side in Colombo, Sri Lanka")



## Introduction to the Model

Some months ago, while attending a ThoughtWorks Leadership training program, I encountered a very fascinating awareness model (** It’s inspired from the Johari Window model. See notes at the end of the blog). I was captivated by its implications. 

This is how it looks:

![The Awareness-Knowledge Model](/images/general/AEModel_The_Model.png "The Awareness-Knowledge Model")


You interpret this model as follows: 

**Quadrant 1:** _I know_ what _I know_ (or, I am aware of what I know)

**Quadrant 2:** _I know_ what _I don’t know_ (or, I am aware of what I don’t know)

**Quadrant 3:** _I don’t know_ what _I don’t know_ (or, I am unaware of what I don’t know)

**Quadrant 4:** _I don’t know_ what _I know_ (or, I am unaware of what I know)


Let us simply call this the **Awareness-Knowledge** Model. 

I find this model to be a very fascinating introspection & risk management tool. In the following sections, let us apply this model first to Domains and then to Projects, and see what we might be able to learn. 


## Awareness-Knowledge Model applied to Domains

One can apply this model to any body of knowledge, or area of expertise, like Computer Science, Medicine, Political Science, Movies, Jazz Music, Computer Games, etc. One can choose to be narrow, and just apply it to Artificial Intelligence or Weight Training, or one can choose to be broad, and apply it to Spirituality or Arts. 

As an example, let’s apply this model to my knowledge in the domain of “_Computer Science / Programming_”, and see how it works.


**Quadrant 1 (IK-what-IK):** I am mostly aware of what I know -- I know Java programming, I know React.js, I know Postgres, I know the importance of clean code and how to refactor, I know what is a CPU, a RAM, and what is Computer Architecture, and REST, and so on. This affirms a sense of confidence for me, and helps me in estimating how long certain things will take, or how complex they might be. This is what I know I know.

**Quadrant 2 (IK-what-IDK):** It is said, that “_the more experience one gains, the less knowledgeable one feels_”. I believe this happens because over time as I encounter new problems, and stumble upon inexplicable bugs, I start realising that there are nuances within many topics and areas that I don’t really understand. I also encounter people who are experts in certain tools, techniques, systems or platforms, and realise how much I don’t know. This awareness helps me remain humble, and also motivates me to learn and explore. So, I search on google for things like: “How does Two phase commit work?” or “What is the difference between Non Blocking IO and Asynchronous IO?”, or “What is a Promise?”, etc. I know what I don’t know, and I spend time reading blogs and books in those areas to help me gain a better understanding. 

One could argue, that being “_in the grip of_” Quadrant 2, is one of the reasons people experience the [Imposter Syndrome](https://en.wikipedia.org/wiki/Impostor_syndrome). I experience this myself from time and time, and I discovered a rather cheeky yet meaningful lens through which to alleviate the discomfort (see tweet below):


![Imposter Syndrome Tweet](/images/general/AEModel_Imposter_Syndrome_Tweet.png "Imposter Syndrome Tweet")


Source: [https://twitter.com/ThisIsJoFrank/status/988048711937748992](https://twitter.com/ThisIsJoFrank/status/988048711937748992)


**Quadrant 3 (IDK-what-IDK):** This one is interesting. _I don’t know what I don’t know._ Another way to look at this is _What are my blind spots?_ This one is very tricky. I may believe that after having seen so many microservices based projects, I am good at identifying when to introduce a new microservice, or when to update an existing one -- but in reality, I _might_ still be poor at it. I _might not know_ that I am actually _not_ proficient at detecting the right Microservices split. It’s possible that I have a blind spot in this scenario. But the moment I acknowledge this fact, this moves into Quadrant 2, and then I can work on it. And that’s what is fascinating about this quadrant. Things in this quadrant are out of grasp. The moment you grasp them, they move to Quadrant 2!

It’s also quite likely that in my case, 95% (a significant chunk), of all Computer Science knowledge is in this quadrant --- i.e. the knowledge whose existence itself I am unaware of.  For instance: What did all the folks in the world who did a PhD in Computer Science related areas, really uncover and write about? I have no idea!

![The size of Unknown](/images/general/AEModel_Knowledge_size.png "The size of Unknown")


**How do I deal with this situation?** What measures do I take to mitigate the risk of not being aware of my blind spots -  my knowledge black holes? How do I become aware of what I don’t know? And more importantly, which blind spots do I need to focus on? Which ones are relevant? 

The hope is that once we become aware of what we don’t know, we move that piece of knowledge into Quadrant 2 (IK-w-IDK), and from there we can learn more about the relevant pieces, and move into Quadrant 1 (IK-w-IK).  

So what do I do? I read books on broad topics, listen to podcasts - software related and non-software related, have random conversations with colleagues, subscribe to twitter feed of experts and luminaries in various areas, etc. This exposes me _accidentally_ to information that tells me what I don’t know. This uncovers the _unknowns_, and that helps me identify what needs to go into Quadrant 2. 

As an example, when I signed up as an instructor for the Tech Lead training program, that’s when I got introduced to the [Butterfly Model for a well rounded Tech Lead](http://www.engineeringandcareering.co.uk/2013/05/the-well-rounded-technical-lead-model.html) while preparing for the sessions. Until then, I didn’t know that such models existed for Tech Lead roles. 

Another example: a google search for “[Top Kubernetes Tips](http://google.com/#q=top+kubernetes+tips)” or “[Top Git Tips](http://google.com/#q=top+git+tips)”, etc will uncover suggestions and tips that you don’t know about Kubernetes or Git respectively. This is another way to stumble upon things you may not realise exist, but can be very helpful to you. A move from Quadrant 3 to Quadrant 1. 

![Moving across the quadrants](/images/general/AEModel_Moving_across_the_quadrants.png "Moving across the quadrants")



You can do the same while taking an interview for a potential hire. Instead of focussing only on “What _they_ know” and “What _they_ don’t know”, you can focus on “What do _I not_ know?”, and “how can this discussion help me know something I don’t know, yet allow me to also get to know the candidate”. One way to do this is ask them to explain the architecture of their current project, or a topic they love, and then ask them well thought out _WHY_ questions to dig into things that _YOU_ don’t know or don’t understand, and see if the candidate enlightens _YOU_. That is a win-win interview! 

**Quadrant 4 (IDK-what-IK):** _I don’t know what I know!_ To some people, this quadrant might seem counter-intuitive. At first glance, this sounds like a spoiled brats’ response. But, in fact this is an important quadrant. The questions to ask here are: _What skills and knowledge do I bring to the table that I am unaware of? What am I good at or have an intuition of, but am unaware of? What activities can I sign up for without worrying about whether I will be good at them? What is it that other people notice about me, but I am not cognizant or appreciative of?_

This is where people underestimate what skills and knowledge they bring to the table. Having a (respectful) feedback culture in an organisation can help uncover this for individuals. This is also a by-product of long periods of contemplation and hard work, coupled with past events and exposure to different environments & cultures. Part of this is also what people sometimes call: “Expert Intuition” or “Expert Knowledge” or “Gut feeling”. Something that experts find hard to explain. 

An example of this in the programming world is called a “Smell”. I can’t describe it, but I can smell it -- there is something “not nice” about this piece of code, or the design of this set of classes, etc.

Andrew Ng, one of the most influential Computer Scientist in Artificial Intelligence and Deep Learning, who led Google Brain and was a former VP & Chief Scientist at Baidu had once tweeted this:



![Andrew Ng Tweet](/images/general/AEModel_AndrewNG.png "Andrew Ng Tweet - Secret to getting new ideas")


Source: [https://twitter.com/andrewyng/status/793107879557345280?lang=en](https://twitter.com/andrewyng/status/793107879557345280?lang=en)

The more you read, the more experiences you collect, the more time you spend in reflection and honest discussion, the more you _know_ even if you don’t realise it yet. 

#### A Classroom Joke

**Economics Professor:** _Dear Class, now that you have heard a 45 min summary on the complex area of trade surplus and deficit, how many of you feel that you have understood this topic?_

..._The class is very silent. The Professor patiently waits for someone to speak up..._

**One Student:** _Mam, I fear that I don’t know whether I have understood exactly what you wanted us to understand, but I did like it a lot!_

## Awareness-Knowledge Model Applied to Projects

One can also look at a new project, or a new program of work, and try to apply this model to it. For instance, here are some questions and thoughts that one can have while walking through each quadrant for a particular project: 

**Quadrant 1 (IK-what-IK):**

  1. What is it that we know for sure? If so, can we confirm this with our clients to ensure that our understanding is correct. 
  2. Is that piece of information squarely in Quadrant 1? Or does it have parts that we don’t realise?

**Quadrant 2 (IK-what-IDK):**

  1. What are the areas that we are not sure of? 
  2. What spikes should we play to better understand that area? 
  3. What PoCs need to be built to better understand what we don’t know? 
  4. Which stakeholders should we talk to to better understand a certain API that we will need to integrate with? 
  5. We need to highlight certain known risks and follow up on them earlier in the lifecycle of the project to mitigate those risks. We must ensure that we report them periodically. 

**Quadrant 3 (IDK-what-IDK):**

This can be a very tricky one, and requires careful consideration. Here are some possibilities:

  1. How do we validate that we have received all the right information about what is needed to be built? 
  2. Is it possible that there is a security related activity, or compliance related activity that we aren’t aware of, but it might come back later to bite us, and delay our project? 
  3. How do we mitigate the risk of what we don’t know? This is an example of the risk with “handover” of pre-created requirement documents during the start of an engagement. How do we know what has been completely missed in the requirements? As an example, at ThoughtWorks, we run [inceptions](https://martinfowler.com/articles/lean-inception/) at start of engagements to mitigate the risk that we aren’t building something no one wants, or we aren’t forgetting an important stakeholder or an important compliance step in the process. We don’t know, what we don’t know -- and we need to take steps to uncover it early!

**Quadrant 4 (IDK-what-IK):**

  1. Are we adding too much buffer to our estimates? 
  2. Are we playing spikes / PoC unnecessarily, when we can easily reach out to someone within our organisation, and get the answers quickly? 
  3. Are we under-estimating our teams abilities? 
  4. Have we created a team that can together solve most problems we throw their way, in a creative, efficient and cost-effective manner - even if they don’t have any clue right now about it? 

A _unit test_ is an example of something we write based on what we _know_, to catch errors and situations that can arise based on changes in the future that we _don’t know_ or can’t anticipate, but we know that will _likely_ happen.

Teams that follow [mature QA practices](https://martinfowler.com/articles/practical-test-pyramid.html) will usually ensure that any bugs that are uncovered in production, and are likely to therefore occur again, will be automatically detected in the future via automation. We now _know_ about them. Customers will rarely be forgiving to the same bugs occurring repeatedly in production. QAs will also focus their _manual efforts_ towards _exploratory testing_, so that bugs (requirement, design or implementation bugs) that we _don’t know exist_ are uncovered, since automation can only test for _known_ behaviors.

A [Threat Modelling](https://www.owasp.org/index.php/Category:Threat_Modeling) exercise is an attempt to build a shared context to uncover what we don’t know, and then use the new knowledge to prioritise security threats, create [Attack Trees](https://en.wikipedia.org/wiki/Attack_tree), identify possible countermeasures, etc. The [Rugged manifesto](https://www.ruggedsoftware.org/) has a statement that I think is pertinent to this discussion: “_I recognize that my code will be used in ways I cannot anticipate, in ways it was not designed, and for longer than it was ever intended_”. 

The philosophy of Agile is rooted in embracing change. It acknowledges that new information is uncovered gradually, and we know that we don’t know a lot, and iteratively we will discover it.

At ThoughtWorks we try to establish high performing, cross-functional teams comprised of smart, passionate and diverse technologists; whilst supporting them with a respectful environment and a learning culture. The hypothesis is, that this will help our teams to be capable enough to deal with unexpected situations (Quadrant 3); humble enough to recognise & address gaps in their knowledge (Quadrant 2 & Quadrant 1); and diverse enough to discover what they already know but don’t realise right now that they do.

Machine Learning has recently become a mainstream conversational topic because it _apparently_ promises that given large datasets, it will likely be able to find insights that will be useful for us, but _we don't know_ what these insights will likely be. 

## In Conclusion

I hope you found the Awareness-Knowledge model fascinating. It can help you decide how confident you feel about a domain, area of expertise or project by brainstorming & introspecting on each of the four quadrants. You can put in mitigation strategies to help shape events and unknowns eventually towards Quadrant 1.

> “I know that I know nothing” --- Socrates Paradox. 

![Calvin & Hobbes - Bridges Comic Strip](/images/general/Calvin_Bridge.jpg "Calvin & Hobbes - Bridges Comic Strip")


(c) Calvin and Hobbes. Source: [https://www.pinterest.com/pin/155374255872428173/](https://www.pinterest.com/pin/155374255872428173/)


####  Notes:

  1. I came across a variation of this model recently in Chapter 3. of Sriram Narayan’s excellent book: [Agile IT Organisation Design](https://www.amazon.com/Agile-Organization-Design-Transformation-Continuous/dp/0133903354), where he wrote about Software Development being a learning journey, and how software development teams encounter Unknown Unknowns that can surprise them and often invalidate existing estimates. 
  2. Some people may point out that this model is likely the same as [Johari Window](https://en.wikipedia.org/wiki/Johari_window) for self-awareness in the field of cognitive psychology. But I felt its explanation & application is quite different from how I perceived it above. I am happy to be told otherwise, as I am no expert in the field of psychology. The whole field of psychology is definitely in my Quadrant 2 and Quadrant 3. I know nothing about it! 
  3. Read more on the Socates Paradox [here](https://en.wikipedia.org/wiki/I_know_that_I_know_nothing).

_Disclaimer: All thoughts and opinions in this blog are my own, and do not represent the stance or opinion of my employer (ThoughtWorks)._ 