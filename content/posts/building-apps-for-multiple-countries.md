+++

title = "Building Applications for Multiple Countries and Languages"
description = "A checklist of things to bear in mind while developing applications for the global audience"
author = "Gurpreet Luthra"
date = 2015-02-14T02:13:50Z
images = ["/images/general/singapore-street.jpg"]
aliases = [
    "/2015/02/14/building-apps-for-multiple-countries.html/",
    "/2015/02/14/building-apps-for-multiple-countries.html"
]


tags = [
    "programming",
    "technical",
    "architecture",
]

+++

![Near Chinatown street in Singapore](/images/general/singapore-street.jpg "Near Chinatown street in Singapore")

Nowadays, many softwares and websites are i18n enabled. If you don't yet understand what is meant by Internationalisation, Globalisation and Localisation in software, then this [Wikipedia link](http://en.wikipedia.org/wiki/Internationalization_and_localization) is your friend.

I  have worked on a couple of projects where we had to make the application multi-country savvy (also called internationalisation or i18n), and I think it would be good to pen down various areas we considered, and the tools we used. Note that, these practices are from the perspective of a Java/Scala project, but can easily be 
adapted to other platforms too -- since the basic requirements are similar.

1. **External Files for String:** Maintain all user visible strings in properties files (not log messages though!). We maintain the English version (messages.properties), and the translation teams maintain translations for other languages (messages_fr_FR.properties, etc). Read about locales [here](http://tutorials.jenkov.com/java-internationalization/locale.html).

2. **No Automated Translations:** Having automated translations does not really work in practice, because the "context" is important, which can't be figured out by just looking at the string. For instance, on one of our projects we had provided a feature in our website (internal version), which allowed translators to hit a url with a key name so that they can see the page where the key will be used -- and get a context of what we are looking at, and how their translation will look on screen. Automated translations usually target tourists wanting to communicate or researchers wanting to understand a particular sentence, and hence are devoid of the subtleties you want in a website / application. Poor translation is also a put-off for the users of the application. Therefore, I'd recommend staying away from Automated Translation tools / websites.

3. **Simple Scripted Tests for Errors:** On one project we wrote a tool for performing basic checks for received translation files against our reference properties file. These error are usually not easy to catch by "humans", and can slip through. For instance:

    - Check if a key has not been translated
    - Check if a key is missing in a file
    - Check if a key is "extra" in a file
    - Check for UTF-8 encoding issues
    - Check if a key is duplicate
    - Check if a key doesn't have a value

    These checks are very easy to code via a script, and can be run by the translation teams themselves. This concept is called "[Poka Yoke](/2012/07/22/poke-yoke-mistake-proofing-software)".

4. **Grammatical considerations:** Also, many UI messages cannot be concatenated, because grammatically nouns/adjectives/verbs come in different positions in different languages. So a message: "Your owe Rs 100" has to be externalized in YAML/properties file as "You owe {0}" (where {0} will be replaced by price+currency), and this context needs to be informed to the translators.

5. **Singular/Plural:** Also singular / plural word construction needs to be different in different languages. So messages change based on whether you are displaying "1" or "more".

6. **Numbers/Dates/UoM:** Besides UI strings, we also need to look out for currencies, dates, time-zones, units-of-measures, etc since they vary by country, and hence need to use formatters appropriately. Same goes for [Numbers](http://en.wikipedia.org/wiki/Decimal_mark#Examples_of_use), where decimal separators are different by country (dot in some, and comma in others). For instance, use "Number" fields to store numbers in DB / Models, and use UTC to store Date/Time values, and then format them appropriately on screen depending on the locale.

7. **Case-insensitive checks:** Case-insensitive code also needs to be written properly, because for instance in Turkish there are 4 'i', and your code may not do the correct comparison for case-insensitive strings, if it doesn't have a "locale". ([Why languages fail with the Turkish I](http://www.i18nguy.com/unicode/turkish-i18n.html)). For this reason, in Java/Scala, the [toUpperCase API](http://docs.oracle.com/javase/7/docs/api/java/lang/String.html#toUpperCase(java.util.Locale)) takes a "locale" as a parameter (and mentions the Turkish I case in documentation).

8. **UTF-8:** Of course, you use **Unicode** character set and **UTF-8** encoding everywhere. For more details read: [The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets (No Excuses!)](http://www.joelonsoftware.com/articles/Unicode.html). For Java/Scala programs on Windows, don't forget to set JAVA_OPTS="-Dfile.encoding=UTF-8".

These are all the points I could think of right now. If more areas strike me, I will post updates to this blog. Meanwhile, if you have practical tips to share in this regard, I'd love to hear.

_Originally posted on my older blog post here: [Building Applications for Multiple Countries and Languages](http://techie-notebook.blogspot.com/2015/02/i18n-building-applications-for-multiple.html)_
