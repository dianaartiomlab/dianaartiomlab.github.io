---
layout: default
title: History of Computers
---
# Greatest Software Bugs

<div class="custom-image"><img src="/images/bug-software.png" /></div>

Software development is a very interesting process. Despite that, a programmer should be very careful while writing programs. Applications are developed in almost every domain of our life, including education, medicine, government, etc. A programmer’s fate is to cover as many devices and OS versions as possible, and to assure its compatibility on other versions, i.e. to make sure it works well not only on his own machine.  Moreover, it might appear to run well on some machine, but it will better be tested on multiple machines to assure the software program works well there. And we already know that. Because we, humans, already faced some serious issues, some serious bugs, that caused extreme consequences, like human deaths, resources wasting, pollution, and, even if at the first sight it might appear not that important, time wasting - also a great resource, people forget to take into account. <br />


As being a computer science student, I had to make a presentation on “Computer History” course. Multiple topics were given, but the one I decided to choose is “The Greatest Bugs in the history of Computer Science.” There is a lot to speak about here, like  Therac-25 bug,  European Ariane 5, NASA’s metric confusion, Millennium bug, etc. All these bugs caused extreme consequences, and therefore made themselves great points in the history of computers. The one I was really impressed about was the Y2K problem.

####Y2K problem
Millennium bug (aka Y2K bug) was a problem related to the transition between millennia. The problem is, back in times, programmers used to store the date value using the following format: DDMMYY. Yes, programmers stored the value for the current year, using only two digits, instead of four. Problems arose, because this made the year 2000 indistinguishable from 1900. In fact, various errors were caused, such as the incorrect display of dates bugs and errors in computing app, etc. This topic was the one of interest for me, because, as many of us also thought, I asked myself: “Why would one save the value for the current year using only two digits?”. The answer is simple. The storage was expensive, from as low as $10 per kilobyte, to in many cases as much as or even more than US$100 per kilobyte, and storing only two digits for the year was a solution. It was therefore very important for programmers to reduce usage as much as possible. The “genius” solution they thought is to simply use prefix "19" to the year of a date. Most programs internally used, or stored on some external memory, data files where the date format was six digits, using the format MMDDYY, where MM stands for the two digits for the month, DD -for the two digits for the day, and YY for the two digits in order to show the year. As space on the memory used(discs and tapes) was also expensive, this also saved money by reducing the size of stored files and databases.<br />

Whether is this life threatening or not, bugs means always danger. The most terrible happens when using these data for calculation, In fact, no actual problems could be caused if the time&date values weren’t used in calculations. <br />

Related to the Y2K problem, which dealt specifically with the transition between the millennia, there was also another issue - the leap years. Mostly, according to the Gregorian calendar, a year is considered to be leap year if it is evenly divisible by four. However, a year divisible by 100 is not a leap year. It also has to be divisible by 400 to follow the rule. For example, 1600 was a leap year, while 1700, 1800 and 1900 were not. And here’s where the issue of storing only two digits arise. Some programs could have misunderstood when the rule that a year divisible by four is a leap year actually does occur. Yes, maybe that’s not a direct y2k bug related problem, because it works fine for the year 2000 (being a leap year). Unfortunately it becomes a problem by reaching 2100, when older legacy programs definitely will be affected. I know what one might think: “Come one, how can a program live that much?” Well, no one knows. :) But I’m pessimistic too.<br />


So what bugs what actual bugs did then happen? After a small “radiography” of the internet and the pages related to this topic I found some of the resulting issues. <br />

#####Here are a few of them:
<ul>
  <li>US - Official timekeeper, the Naval Observatory, reported the date as 19100 on its website</li>
  <li>Japan - system collecting flight information for small planes failed</li>
  <li>Australia - bus ticket validation machines failed</li>
  <li>US - over 150 slot machines at race tracks in Delaware failed</li>
  <li>Spain - worker was summoned to an industrial tribunal on 3 February, 1900</li>
  <li>South Korea - district court summoned 170 people to court on the 4 January, 1900</li>
  <li>Italy - Telecom Italia sent out bills for the first two months of 1900</li>
</ul>


Now, after so many bugs lived, it would be naturally to think that engineers took their lesson. Unfortunately, this is false. Engineers are humans too. They also make mistakes. Being punished or not for their bad work, some consequences are irreversible. It is impossible to revive those who paid with their life for others to learn that the code should be tested, or to be truly attentive while applying their engineering knowledge. That’s why, while developing any kind of app, we better make sure it performs well, subject to the given requirements, and to test it. We all know, that exhaustive testing is not possible, but one better makes sure the found bugs are solved, rather than assuming the software works well the way it is. Are you and me meant to work for NASA or SpaceX or not, we should be aware of our code, of our engineering skills and the way we apply our knowledge. <br />




