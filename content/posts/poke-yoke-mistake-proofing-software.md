+++

title = "Poka Yoke - Applying Mistake Proofing to Software"
description = "A technique for reducing mistakes in software"
author = "Gurpreet Luthra"
date = 2012-07-22T02:13:50Z
images = ["/images/general/orange-evening.jpg"]
aliases = [
    "/2012/07/22/poke-yoke-mistake-proofing-software.html/",
    "/2012/07/22/poke-yoke-mistake-proofing-software.html"
]


tags = [
    "programming",
    "technical",
    "quality",
    "architecture",
]


+++

![Near the Norbulingka Institute, Dharamshala, India](/images/general/orange-evening.jpg "Near the Norbulingka Institute, Dharamshala, India")


**Note:** *This has been one of my highest read blog posts ever with over 100,000 views. I am humbled. Thank you!*

For years, automobile companies have utilized "Mistake Proofing" as a technique for ensuring high quality,
high speed manufacturing -- especially in cases of mass scale production.
This is also known as [Poka-Yoke](http://en.wikipedia.org/wiki/Poka-yoke) (in Japanese) and was adopted and formalized as part of the Toyota Production System.
This blog attempts to raise awareness (with examples) for the need of Poka Yoke in Software Design and
within the Software Development process.

## What is Poka Yoke?

The essential idea of Poka Yoke is to Mistake Proof the manufacturing process so that workers in a plant cannot make mistakes easily, or if a mistake is made, it is detected and corrected quickly.

There are two types of Poka Yokes:

**Control Poka Yoke:** A Control Poka Yoke is one where the process is designed in such a manner that one cannot make a mistake.

For instance, a car manufacturer might want to put special heat resistant bolts in the engine assembly. For this, the bolts can be made to be of a certain dimension such that it only fits the engine assembly, and nowhere else. Therefore, one cannot use the special bolts in any place except the engine assembly, and one can also not inadvertently put the wrong (non-heat resistant) bolt in the engine assembly.

This is a form of control poka yoke, where one cannot go wrong, or make a mistake.

Another interesting example of a control poka yoke are the Gas connections in an Emergency Room at the hospital. To ensure that someone doesn't connect the wrong gas pipes to the wrong outlets, the Pin configuration of the connections are designed to be unique for each Gas outlet (a standard called the *Pin Index Safety System*).

![Mistake Proofing via different Pin Configurations](/images/general/poka-yoke/medical-gas-valves.jpg "Mistake Proofing via different Pin Configurations")

**Warning Poka Yoke:** A warning Poka Yoke is one where the moment someone makes a mistake, the person is quickly notified of the mistake, so that corrective action can be taken.

An example of a Warning Poka yoke is the Car Seatbelt Warning indicator. If one forgets to put on the Seat Belt, then it will beep to warn you of the fact that you forgot to put it on.

Check out the following catalog of Poka Yoke examples from John Grout's website: [http://www.mistakeproofing.com/](http://www.mistakeproofing.com/)

## The Need For Poka Yoke in Software

There are very compelling reasons to use Poka Yokes in Software Design for the benefit of end users, and also in Software Development Teams for creating high quality software in shorter time-frames.

**In Software Design**

*Beautiful software* is designed in a manner that it is intuitive and transparent to the user. It meets the need in a fluid manner, assisting the user to do just what he/she would like to do with it, without making the user jump through hoops and millions of clicks. It should be like an extension of the body, which one uses sub-consciously.

To create such Beautiful software, it is imperative that it is designed with the user behavior, psychology and needs at the core of all thought. When the user naturally moves through the software with ease, we can perceive it as a form of Control Poke Yoke, that ensures that one doesn't make costly mistakes while using the software. For instance, a simple control Poka Yoke feature is the "Auto Save" feature of Gmail, which ensures that a user's email is auto-saved every few minutes, so that loss of the internet connection doesn't make the user lose his/her data. This is an indication of detailed thought gone into understanding the users behavior and needs.

We will look at few more examples of Poka Yoke in software design in the following sections.

**In Software Development Teams**

The need for Poka Yoke in Software Development teams is higher than ever before. It is quite well established in the industry that the cost of fixing a defect amplifies 10 to 100 times depending on how far the defect has gone unnoticed in the development process. Couple that with the need for integrating with tens of systems nowadays, and the problem gets compounded manifold. Delegating software development to large number of mediocre or inexperienced developers, isn't helping the cause. Introducing a poka yoke, that catches defects early, makes Discovery and Diagnosis of a defect ridiculously easy. Of course, to design a Poka Yoke, one needs to be aware of possible mistakes that could potentially occur -- and that comes from feedback, retrospectives and burnt fingers across a project or multiple projects.

The point of a Poka Yoke is: *Making mistakes is OK, just don't make the same mistake again and again*.

Quite frequently on large projects, or long running projects, or on projects with multiple and remote teams -- communication becomes a severe issue. In such projects it is very difficult to keep all folks "on the same page". One finds people sending emails in BOLD, or writing and maintaining huge Wiki pages with FAQ and ToDos on how to perform a certain task. Unfortunately, no one has the time to read or maintain these documents, and errors slip through the cracks.

For instance, on one of my Travel projects, to perform test bookings, we had to use live GDS inventory. So we were given instructions on attributes of a test booking. These went something like: Make bookings at least 6 months in advance, and don't book during Christmas, or New Year season, don't book ABC and XYZ airlines, cancel the ticket within 20 minutes of doing the bookings, etc.

Now, even though people followed these rules, quite a few folks would forget to follow at least one or more of these rules. As a result, one time a large airline sent our Travel booking agency a huge bill for messing up with their ticket prices because apparently some test program did a huge number of bookings & cancellations for their flights -- and caused their ticket prices to go up, resulting in shooing away of "real" customers. Now, this can be easily avoided by putting a Poka yoke that would reject any bookings sent via our service that didn't meet the criteria. And -- that's really quite easy in software!

In today's world, the array of tools and techniques available to us are immense. We must use these tools smartly, so that we concentrate on more pressing issues, and let poka yokes, automation scripts and smart checks catch common, and well understood project issues.

Instead of sending multiple BOLD font emails, create a Poka Yoke -- to ensure things don't break again, and mistakes and errors don't slip through.

## Qualities of a Good Poka Yoke

A good Poka Yoke must meet the following qualities:

- **Early:** A good poka yoke must be early in the process, so that it can provide quick feedback -- and help in detecting mistakes the moment they occur.
- **Precise:** It should be precise, so that it is easy to diagnose and identify what mistake occurred.
- **Simple:** The poka yoke should be simple -- to develop and maintain. This is quite important since one doesn't want to spend time and effort in maintaining poka yokes, and complex poka yokes will have a fairly high chance of becoming erroneous. Having a buggy poka yoke is worse than having no poka yoke at all.
- **Light:** The poka yoke needs to be unobtrusive and transparent. If a poka yoke itself becomes an overhead to the process, then it will drive the developers/users crazy, and they will find ingenious ways to avoid it all together. For instance, think about how a developer will feel if he/she has to run a 70 minute pre-commit script before each and every check-in!

## Examples of Poka Yoke in Software Design (for End Users)

1. [Gmail Attachment Check](http://npxp.com/gmail-please-find-the-attached-file): If one uses the words "I have attached", but does not attach any document to the email, Gmail will give a warning saying you used the words I have attached, but didn't really attach any document. Are you sure this isn't a mistake?
2. [Wrong Bob/ Missed Bob Check in Gmail](http://gmailblog.blogspot.in/2011/04/dont-forget-bob-and-got-wrong-bob.html): Depending on which set of people you commonly email together, Gmail will warn you (or offer suggestions) to include the folks you may have missed. This will ensure you don't mistakingly leave out someone, or add someone you didn't want to email.
3. [Password Strength Indicators](http://googleenterprise.blogspot.in/2009/01/new-layer-of-data-access-security-for.html): When you sign up for an account on most websites, you are nowadays displayed a password strength indicator - which gives you feedback on the quality and strength of your chosen password. You may think that "Passw0rd" is an awesome password, but that's a mistake you are making! Websites have data collected over millions of users which can tell them things like what are common and easy to break passwords. They utilize this data, along with sophisticated software to create Password Strength indicators so that naive users don't mistakingly set simple, easy to guess passwords.
4. [Cmd-Q Warning In Chrome](http://www.macstories.net/news/prevent-accidental-quit-in-google-chrome/): Quite often Mac users make a mistake of pressing Cmd+Q to close a TAB instead of Cmd+W. Google Chrome on Mac can warn users when they press Cmd+Q, to help them from inadvertently closing all their windows.
5. [Spelling suggestions in Google suggest](http://www.designvsart.com/blog/2009/10/29/poka-yoke-design/): Google will auto-suggest spelling corrections depending on what you might be searching. Helps users from making inadvertent mistakes.
6. **Undo Feature** is nowadays present in most production quality successful software. Undo as a way of quickly "fixing" mistakes has become second-nature for most software users, that without this feature, most of us operate with a Save-paranoia. Gmail provided an [Undo Send](http://mashable.com/2010/08/22/how-to-undo-send-in-gmail/) feature to provide a safety net for times when someone clicks Send by mistake.
7. **Double Entry Box**: Most websites & software where one needs to enter a critical bank account number, or a password create option, users will notice that they are asked to enter the same value twice (with paste option disabled). This is to ensure people haven't made a mistake while entering the value, and that both boxes hold the same value.

## Examples of Poke Yoke in Software Development

1. [Unit Tests + Pre-commit + CI + Build Radiators](http://soyouthinkyouneedtorewrite.com/build-radiators-love-them-long-time/): Unit Tests are one of the strongest and most effective means of Mistake Proofing software development. They are precise and early in the development stage. They catch regression mistakes during refactoring, or bug fixing immediately. Unit Tests, coupled with a Continuous Integration Server (like [Go](http://www.thoughtworks-studios.com/go-agile-release-management), [Jenkins](http://jenkins-ci.org/), etc), a pre-commit script, and a Build Radiator are an excellent poka yoke mechanism to inform developers quickly about a mistake having occurred.
2. **IDEs and Compilers**: IDE's indicate issues in code while you code. They will catch mistakes around incorrect type casting, generics, exception handling and provide you with possible fix options. Compilers will act as strict control mechanisms and will disallow any code that doesn't meet the syntax requirements (especially in case of Statically typed languages).
3. **Architectural Controls [ACs]**: Some architectural poka yoke control examples in software:
    1. **[AC] Hiding HttpSession**: In some web projects folks would create a custom framework for development teams where a potential-to-misuse object like an HttpSession would be made unavailable. Instead, a custom "Session" object would be available which only has specific methods exposed like the getSessionID() method, so that application code could use the Session for its original purpose -- which was to identify the user's session, and not to act as a bag of data for passing around to pages and methods. It also ensures that there isn't much overhead in keeping session data synchronized across multiple machines in a cluster - since the ability of developers to stuff anything they like in the session object has been taken away. This will force the developers to look for data structures appropriate to their need for storing user specific application data.
    2. **[AC] Context aware injections**: Custom frameworks can also be written to explicitly ensure that people don't perform an operation which is incorrect / invalid in the current application context. For instance, we would not like to perform updates during a GET Request (remember [REST](http://en.wikipedia.org/wiki/Representational_state_transfer)?). In such cases, the framework can inject appropriate implementations which do not support update method calls, so that a developer doesn't make a modifying call in the GET context.
    3. **[AC] Running Under Least Privilege (RUPL)**: The paradigm of Running Under Least Privilege is popular at many levels in Software Development. Operating Systems now create processes which operate at Lowest Level of Privilege, so that processes cannot inadvertently wipe out a memory area which doesn't belong to them, or they do not mistakingly come under a virus attack and wipe out system secure space. Database connections at application level are given only read/update/delete row access on tables, rather than dba / admin access to ensure that the application cannot overwrite/drop tables by mistake. RUPL ensures that a process or a program is given only as much control as they need to avoid costly screw-ups.
    4. **[AC] Circuit Breaker**: Michael T. Nygard introduces this concept as a programming pattern in his masterpiece book [ReleaseIt!](http://pragprog.com/book/mnee/release-it) The essential idea is similar to an electric current circuit breaker which trips open whenever the current load is high. The Circuit Breaker trips open whenever it detects that the call to an external web-service, database, etc took too long to respond, or timed-out. Once a circuit breaker is in Open State, it will immediately return an exception to any caller that attempts to connect to the external service. This has the advantage of protecting the external service from an overload of requests while it is attempting to recover, and also prevents the caller application threads from getting blocked. For more details read the [concept](http://www.dalnefre.com/wp/2011/06/circuit-breaker-stability-pattern/) and a sample Java AOP based [implementation](http://code.google.com/p/jianwikis/wiki/CircuitBreakerDesignPattern) here. Circuit breaker acts as a poka yoke by preventing both the callee and the caller from unknowingly blowing up in case of a failure.
    5. **[AC] Types with Immutability**: Passing a type (like a Money object), instead of passing primitives (like numbers) gives developers control over what can happen to the data as its passed along the various software layers, and what kind of operations can be performed on the data. Adding immutability to these types also ensures that an intermediate layer cannot inadvertently modify an internal data element while it is passing the type around.
4. **Password Log Check**: To ensure that someone has not mistakingly logged sensitive user information like Credit Card Number, CVV or user password to a log file one can write a script to scan log files on the automation test machines. In automation tests, teams usually use only a small set of username/password/accounts/test-data, and hence checking for these accounts in log files, can help uncover if someone has mistakingly left a debug statement in code that prints sensitive data to the log. This would be a Warning Poka Yoke. A control poka yoke would be one where somehow the log API would disallow logging any variable/string which contained the words "credit card number" or "password" or "pwd", etc.
5. **Localization Test for Menu-Keyboard Shortcuts**: Quite a few desktop softwares have menu options with Keyboard Shortcut keys (accelerators) which are shown underlined. The idea being that when someone presses "Alt+Character", then that menu option will get pressed. There are 2 requirements of these shortcut characters: First, the character must be present in the menu item, and Second, it must be unique in the menu. This is all fine when its designed, but quite often the keyboard shortcuts get messed up when they go through a localization process for other languages. Quite often translators will assign shortcuts which will clash with other menu options, since they don't fully understand which all menu options are shown together (especially in the case where menu changes dynamically based on roles). The solution in such cases is to write a poka yoke script that will check all menu options in a particular language to ensure there isn't a clash. This kind of bug detection is very cumbersome manually.
6. **Localization Message Bundle Checks**: Localization in Java for instance is done through message bundlers (or properties file). Quite often translated files can have errors like translation of a specific line missed, or key misspelled, or key missing, etc. Such errors cannot be quickly caught through language testing. Instead a simple script that compares English Locale properties file against each Language property file can easily catch most of these errors through simple comparisons, and save precious heart aches later. These scripts can be run as part of the localization check-in to catch translation file errors immediately. Use of good translation tools can also eliminate these problems quite effectively, acting therefore as control poka yokes.
7. **Hiring the Right People**: A very effective poka yoke to mistake proof your software. Something only few companies like [ThoughtWorks](http://www.thoughtworks.com/) get right :)

## Pragmatic Mistake Proofing

One needs to be pragmatic about mistake proofing to ensure it is effective, and doesn't irritate the hell out of its users. The guideline to deciding whether a Poka Yoke is needed is to look at feedback from the field. If an issue occurs quite frequently, and people seem to stumble upon it too often, then its most likely a candidate to apply a Poka Yoke. Also, if the blast radius of an issue going out in the field is very high, like logging passwords in clear text, then too, it makes sense to mistake proof the issue.

## Conclusion

Poka Yoke techniques have been in software for sometime. The point to keep in mind, is to be aware of the fact that whenever there is something to warn to people -- instead of writing long emails, and bold font Wiki documents, one should pause and introspect. Ask the question: Can I re-design the system/ component/process such that mistakes cannot be made. Or, can I put in a check in software, such that if mistakes occur, then they can be caught quickly. If yes, then consider the Poka Yoke.

*Note: The idea of Poka Yoke in Software was presented by [Dhaval Doshi](http://blog.doshi.info/?tag=thoughtworks) and me in ThoughtWorks Bangalore xConf (July 2012). Based on positive reviews at the xConf we decided to write a blog on this topic since we could not find good enough resources on the Internet that spoke of Poka Yoke in Software. Thanks to fellow ThoughtWorkers [Unmesh Joshi](http://in.linkedin.com/pub/unmesh-joshi/5/763/948) and [Chirag Doshi](http://in.linkedin.com/in/chiragdoshi) for providing feedback and few suggestions on this topic.*

You can watch the video of my talk on YouTube here: [Poke Yoke - Youtube - Gurpreet Luthra](https://www.youtube.com/watch?v=vOsfPJ4Vok4)

Slides are [here](https://www.slideshare.net/gsluthra/poka-yoke-the-science-of-mistake-proofing-for-slideshare).

_Originally posted on my older blog post here: [Poka Yoke -- Applying Mistake Proofing to Software](http://techie-notebook.blogspot.com/2012/07/poka-yoke-applying-mistake-proofing-to.html)_
