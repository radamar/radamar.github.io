---
layout: post
title:  "52°North WPS; Rich Data Interface for Copernicus missions"
categories: blog mission gsoc
---

## Description:
The aim of this project is to provide higher level data products and the ability to extend the WPS by adding new process chains using the SNAP framework provided by ESA. This can be accomplished in three steps, 1) making use of SNAP library to handle and process Copernicus data directly without any user-side intervention or processing. This will involve integrating senbox-org/sen2proc python library which already provides the logic to convert L1C to L2A and then L3; this can be done using Jython. 2) The second part is to implement two algorithms based on senbox-org/snap-gpf framework; Ndvi index can be easily implemented using the snap-ndvi package in snap-engine. Moreover a second one can be implemented using the Operator class of snap-gpf which can be used to implement new algorithms. 3) This part of the project will be to make this processing available to the user in the form of OGC WPS standards, i.e. XML RPC. That may include modifying the annotation system in Operator class to make it compatible with WPS AbstractAlgorithm To ensure that everything fits together later; functional paradigms and type theory can be used to reason about the program and program logic.

_This document is also available at "http://rocketsblazing.online/blog/mission/gsoc/2018/03/20/Rich-Data-Interface-for-Copernicus.html" in a much better format, and working inline links. But there is no guarantee the website won't change!._

## A little about me
Amar Matharu Singh; born October 5, I am enrolled in a Bachelors course at IGNOU. I am a freelance designer and a Youtuber. I started the channel "Xtremists Death Gaming" with my friend Arunabha Basak. I have designed photo and video effects for "GJ Chill" and "Nier Clan". I received scholarship in National Talent Search Exam under NCERT, years 2012-15.

## Why am I interested in open source?
It's all about freedom. Better software is complimentary. I think of open source software repositories as being similar to the great Library of Alexandria. It's better if this knowledge is shared widely. Two key aspects i like about the 'Bazaar' model, so to speak, is the ability to build on top of other's projects and the ability to learn from other's works. 

## Preliminary Schedule (milestones and deliverables, planned working hours, and potential other commitments)
The project can be further divided into two parts, 
1. To have access to higher level Copernicus data products. Important to remove the user-intervention when processing the products. One of the key issues discussed in the proposal was the need to manually download and pre process the data to get higher level products. So, to remedy this the project will begin with implementing a direct WPS to Copernicus data interface which can produce the Level2A products and beyond that.
  
2. To expand the Processing Capabilities of WPS, implement new algorithms based on SNAP framework. There are some ready to go algorithm's already present in the SNAP-engine repository. It is only a matter of implementing them in the WPS. More importantly integrating these processes well with the rest of the capabilities of WPS.

## Milestones & Deliverables
Check Scrum [Backlog][8].

## Schedule:
Check Sprint [Schedule][10].


## Working hours:
As part of GSOC we are expected to put out atleast 30 hours of work per week. For simplicity i will assume 6 hours of work a day will suffice. Since Indian timezone is ahead of German timezone by approx 5 hours i will be able to complete my work during the day and it would be available for my Mentor B. Pross and A. Dewall during their daytime to review and make suggestions.

## Why 52°North?
52°North is doing some great work. I am interested in working in bringing the innovations in data to a larger set of users, and in a software that is free and open source. I think it's important that people understand the value of remote sensing and sensor web to better manage our resources on this planet. There is a huge store of data but it won't be of any use if no one can understand it or it's very hard to analyse it. I want to help make this data easier to access, whether it be to run on small computers or low technical skill. So, that there is a foundation for others to work on. I think it's important that the best environment experts can get the data they need to analyse the effects we as a species have on the rest of the biosphere and the global weather.

## Why this project? 
I like the challenge of it. This project is challenging but not too challenging that it can't be done.

## Why are you suited to carry the project?
I don't think I am the only person for the job. But not very many people are working on it and we could definitely use more. Still, I will say that I have good experience with computers and I have used a variety of software on OSGeo disc. I have some experience with servers, one time, making a Nextcloud instance on Google Cloud Platform so that me and my friends don't have to use propreitary cloud services. I have done some hobby projects on java like calculators, submitting some code to AdAway. I'll be a good fit for this project bacause I am confident in working alone, I won't care if very few people use it, but I care that those who use it are satisfied.

## Relation of project to ongoing studies. 
[It's never unrelated.][6]

## Report on code challenge
I read through the SNAP-engine classes and found some to do my work. Thankfully, the NDVI index is not very hard to calculate. [Github][7]. 

## Do you understand this as a serious commitment equivalent to a full-time paid job?
I understand.

## Do you have any known time conflicts in the coding period? 
I'll be contributing to other open source projects to which i think are important, approx. 10 hours a week. Apart from my studies, I don't see my work for Summer of Code to be distracted by something else.

## Open Source Experience
Submitted a Pull Request to AdAway/AdAway on Github. [Open]
Designed application with SQL backend for school elections.
## Programming Level:
Intermediate, I think I can write 50 lines of code a day.
## Work experience
Freelance graphics and effects designer.
Youtube [channel][9] where we did reviews of computer parts.
But i guess that doesn't count.
## Academic experience and performance
I scored 9.2 GPA out of cumulative 10 in grade tenth/high school(2013). Participated and won many quizzes, recieved a credit against admission at Triumphant Institute of Management Education, for winning a team quiz event(2016). Participated in Tech quizzes across schools and won many. Recieved the Scientific Inclination award twice in high school. Received a certificate for building a voting application for the school council.

## Personal Details
# Name: Amar Singh
# Country: India
# E-mail: radamar@protonmail.com
# Phone: +91 9910229366
# Timezone: UTC +5:30
# University and Degree: Indra Gandhi National Open University, Bachelor in Science

  [1]: https://kraft-de-paper.blogspot.in/
  [2]: https://www.flickr.com/photos/amar_znzi
  [3]: https://radamar.github.io/
  [4]: https://github.com/AdAway/AdAway/pull/1001
  [5]: https://rocketsblazing.online 
  [6]: https://www.bostonglobe.com/arts/music/2016/09/18/six-degrees-hungarian-mathematician-paul-erdos/mE8BVQp2vXQMSBQLPuLOzN/story.html
  [7]: https://github.com/radamar/52n-wps-algorithm-ndvi
  [8]: http://rocketsblazing.online/2018/03/25/Scrum-Backlog.html
  [9]: https://youtube.com/xtremistsdeathgaming
  [10]: https://rocketsblazing.onine/2018/03/25/Sprint-Schedule.html

## Scrum Backlog

# Features

__1. Integrate the Ndvi Algorithm with WPS.__

__2. Make WPS able to accept and handle Copernicus data.__

__3. Use org.esa.snap.gpf.Operator class to define new 'MyOp' that is compatible with 52N WPS and OGC WPS standards.__

__4. Implement a useful algorithm based on 'MyOp'.__

...

# User stories:

__1. WPS process to get Level 2A data from Copernicus Level 1C.__

...


## Sprint Schedule


__April 23rd, Community Bonding: Tasks__
1. Week of regular talks to discuss backlog ideas and suggest new ones.
2. Integrate the Ndvi Algorithm you implemented for the challenge into the WPS.
3. Get your doubts cleared
4. Align goals with organisation's.

__May 14th, Start work on Project: Tasks__
1. Add process 'copernicus-import-product' to import Copernicus Data into WPS.
2. Make the process compliant with OGC WPS standards. User should be able to interactively tell the server to download the data, or load it from the disk.
3. Integrate the Ndvi Algorithm with import 'copernicus-import-process' to generate Ndvi band on WPS.
4. Weekly blog update on progress and daily mail updates to mentors.

__June 11th, First Evaluations: Tasks__
1. Complete the evaluations
2. Make a demo of the running application, posts about useful features for the blog.
3. Update Sprint Schedule if necessary

__June 15th, Continue Programming: Tasks__
1. Start work on the second algorithm implementation using the Operator class in org.esa.snap.gpf. (Discuss in the Community bonding period which one)
2. Generalise the algorithm class to form the basis for 'myoperator' which will be extended to implement future algorithms.
3. Make a process for the 2nd algorithm for WPS

__July 9th, Second Evaluations: Tasks__
1. Complete the evaluations
2. Extensive blog articles, tutorials detailing the features of the project.
3. Update the Sprint Schedule as necessary. After discussing backlog and new ideas.

__July 13th, Continue Programming__
1. Lots of optimizations and annotations in the code, make it easier for the next guy to work on it too.
2. Make the WPS much more capable of handling Copernicus data, higher level data.
3. Resolve the issue of Level2A data for parts other than Europe. If the data is still not available.
4. Make sure the code can be commited upstream to 52North WPS.

__August 6th, Pens down: Hope for the best!__
1. Complete the evaluations.
2. Write a blog post to summarize the experience.

August 21st, You are independent Open Source contributor now!

## Sources and References:
[1] https://kraft-de-paper.blogspot.in/

[2] https://www.flickr.com/photos/amar_znzi

[3] https://github.com/radamar

[4] https://github.com/AdAway/AdAway/pull/1001

[5] https://rocketsblazing.online

[6] https://www.bostonglobe.com/arts/music/2016/09/18/six-degrees-hungarian-mathematician-paul-erdos/mE8BVQp2vXQMSBQLPuLOzN/story.html

[7] https://github.com/radamar/52n-wps-algorithm-ndvi

[8] http://rocketsblazing.online/2018/03/25/Scrum-Backlog.html

[9] https://youtube.com/xtremistsdeathgaming

[10] https://rocketsblazing.onine/2018/03/25/Sprint-Schedule.html

