+++

title = "Bahmni - Open Source EMR with 1 Million Lines of Code"
description = "An analysis of Bahmni AngularJS exposure and strategy to migrate to React"
author = "Gurpreet Luthra"
date = 2021-02-25T02:13:50Z
images = ["/images/general/Bahmni-friendsWithoutBorders.jpg"]


tags = [
    "design",
    "technical",
    "health",
    "opensource",
    "india",
    "programming",
    "frontend"
]

+++

![Bahmni Hospital Management System](/images/general/Bahmni-friendsWithoutBorders.jpg "Image courtsey: Friends without borders")


### Bahmni Codebase - Moving out of AngularJS

Bahmni, an open source hospital management system and EMR has over 1 Million lines of code (LoC)! Out of that over 164,000 LoC are in AngularJS (Angular 1.x). AngularJS is going to be end-of-life in Dec-2021, with no likely SLAs around fixes after Dec-2021.

In this article, I would like to shed some light into what parts of Bahmni depend on AngularJS, what parts are already in React; and suggest some steps forward to remove dependence on AngularJS. Some of this feedback has come from the Bahmni community and we continue to be on the lookout for creative means to move away from AngularJS.

> This is also another reminder of how a technology that shines today — could be forgotten and left behind in the future!

**Read my full writeup on Bahmni Medium Blog here:** [Bahmni EMR— 1 Million lines of Open Source Code](https://medium.com/bahmni-blog/bahmni-emr-1million-lines-of-open-source-code-87e610e9a4ec)

![Bahmni Code Analysis](/images/general/Bahmni_FrontendCode_analysis.png "Frontend Code Analysis for Bahmni")
