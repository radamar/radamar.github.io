---
layout: post
title:  "52°North WPS; Rich Data Interface for Copernicus missions"
categories: blog mission gsoc
---

## Description
The project is a natural evolution from the idea "Rich Data Interface for Copernicus Data" after discussion with the mentors. The aim of this project is to enable graph processing framework for WPS, which will make it easier for researchers to process geo data. Directed Acyclic Graphs(DAG) are a tree like structure in discrete mathematics. Graph processing allows the user to define arbitrary sequence of operations, which makes the program more powerful, easier to implement new algorithms, and more autonomous. SNAP is viable candidate to use for the GPF because it works well with Copernicus data and has an active community of contributors. A process could be implemented to convert Level1C data to L2A, using sen2cor and sen2three.

## My Proposal
1. The project will extend WPS to support graph processing but otherwise retain compatibility with old WPS operations. It can be extended to accept and parse the XML for SNAP's graphs. The 'GraphIO' object in snap-gpf can be used to do that.
1. I will begin by integrating NDVI algorithm into WPS, calling the process on Copernicus product via XML post to WPS, to familiarize myself with the source. And full featured snap-gpf implementation should be able to accept snap's 'Graph' objects which are in XML format and execute the graph on Copernicus product. The graph itself could be arbitrary length(no. of operations) and there are a many 'Operator' implementations available. I can use them to test the Application. I can use rainwater catchment area calculation to really test the framework.
1. The benefit? Getting SNAP-gpf integrated into WPS allows for a great degree of freedom to work on Copernicus data. There are several 'Operator' present in snap-gpf package and they will be available immediately as the WPS is able to parse 'Graph' XML objects. Combined with ability to perform arbitrary sequence of calculations quickly and expressively with guarantee of reproducibility, that will make testing new processes and theories much more fun and quick, quick not only in the time it takes to execute a sequence of processes, but how long it takes to define new algorithms, and how long it takes to write a new complex process(Graph).
1. The key will be to maintin all existing WPS features as were but when this project is done there will be a new more efficient way to operate on Copernicus data.

## A little about SNAP
1. To implement new algorithms, SNAP-gpf has SPIs 'Operator' and 'OperatorSpi' which can be extended to implement new algorithms, this makes sure that new algorithms are compatible 'Node' of the graph. Operators can be called or more accurately, added to the graph, by commands like 'gpf.createProduct("operatorName",Map parameters, sourceProduct)'.
2. All the 'Operators' in SNAP-gpf can be thought of as nodes in a directed acyclic graph, all nodes have same type of input(Products) and output(Product). So, these nodes can be linked together in any sequence of arbitrary length, the only requirement is to have a 'ReadOp' which marks the start of the graph and 'WriteOp' marks the end. Researchers have complete freedom between to add operators as they please between these two nodes. 
3. And 'Operator' are really cool, they are private, so they can only be called in a graph. A node(Operator) is linked to the node that goes before it. So, a graph won't execute if it's not complete. These features provide 1. guarantee of reproducibility 2. The nodes can be connected very flexibly i.e. given a certain graph(XML), a certain version of software and a certain input(product) the output(resulting Product) will always be the same.

_So, i have done some work and familiarized myself with SNAP_

## A little about me
Amar Matharu Singh; born October 5, I am enrolled in a Bachelors course at IGNOU. I am a freelance designer and a Youtuber. I started the channel "Xtremists Death Gaming" with my friend Arunabha Basak. I have designed photo and video effects for "GJ Chill" and "Nier Clan". I received scholarship in National Talent Search Exam under NCERT, years 2012-15.

## Why am I interested in open source?
It's all about freedom. Better software is complimentary. Software source repositories are similar to the great Library of Alexandria. It's better if this knowledge is shared freely. I like the ability to build on top of pre-existing projects and ability to learn from prior works. I love it when my software is useful to someone!

## What other features I wish were present in WPS 
1. There should be a single unix shell command to install 52°N WPS.
2. Graphs! they are awesome. Ability to modify the operations at runtime is pretty cool!
3. Some useful processes, like rainwater catchment. It would be great to have some predefined set of processes that can calculate useful things(for users that are not technical in geo).
4. An OGC standard for graph processing on WPS.

## Milestones & Deliverables
Check Scrum [Backlog][8].

## Schedule
Check Sprint [Schedule][10].

## Working hours
As part of GSOC we are expected to put out atleast 30 hours of work per week. I will assume 6 hours of work a day will suffice. Since my home, 77°E is ahead of 7°E by 5 hours i will be able to complete my work during the day and it would be available for my mentors Benjamin Proß and Arne de wall during their daytime to review and make suggestions.

## Why 52°North?
52°North is doing some great work. I am interested in working in bringing the innovations in data to a larger set of users, and in a software that is free and open source. I think it's important that people understand the value of remote sensing and sensor web to better manage our resources on this planet. There is a huge store of data but it won't be of any use if no one can understand it or it's very hard to analyse it. I want to help make this data easier to access, whether it's to be run on small computers or by people with low technical skill. So, that there is a foundation for others to work on. I think it's important that the best environment experts can get the data they need to analyse the effects we as a species have on the rest of the biosphere and the global weather.

## Why this project? 
I think geo science is very important. Where do we find the minerals? Where do we get energy? Where is it prone to earthquakes? It answers the questions "Where?". If this really is the decade we see extra-planetry missions to Mars and the Moon, we will need to answer these types of questions. And geo processing and web processing service are a natural continuation of the geo science into the 21st century.

## Why are you suited to carry the project?
I don't think I am the only person who can do the job. But not many people are working on it and we could definitely use more. Still, I will say that I have good experience with computers and I have used a variety of software on OSGeo disc. I have some experience with servers, one time, making a Nextcloud instance on Google Cloud Platform so that me and my friends don't have to use propreitary cloud services. I have done some hobby projects on java like calculators, submitting a patch to [AdAway][4]. I'll be a good fit for this project bacause I am confident in working alone, I understand discrete maths and I like research.

## Relation of project to ongoing studies
[It's never unrelated.][6]

## Report on programming challenge
I am growing familiar with SNAP-engine API. I used 'NdviOp' operator from SNAP-engine to calculate the NDV Index. The 'ReadOp' operator reads the product from a file and the 'WriteOp' operator writes to the disk in "BEAM-DIMAP" format. Here is my Github [repository][7]. 

## Do you understand this as a serious commitment equivalent to a full-time paid job?
I understand.

## Do you have any known time conflicts in the programming period? 
I'll try contributing to other open source projects too, including other 52°North projects, this won't interfere with the work on WPS. Apart from my studies, I don't see my work for Summer of Code to be distracted by something else.

## Open Source Experience
1. Submitted a [pull request][4] to AdAway/AdAway on Github.

2. Designed application with SQL backend for school elections.

3. Bug reports to GNU guix.

## Programming Level:
Intermediate, I think I can write 50 lines worth of programs a day.

## Work experience
Freelance graphics and effects designer.
Youtube [channel][9] where we did reviews of computer parts.
But i guess that doesn't count.

## Academic experience and performance
I scored 9.2 GPA out of cumulative 10 in grade tenth/high school(2013). Participated and won many quizes; received a credit against admission at Triumphant Institute of Management Education for winning a team quiz event(2016). Participated in Tech quizzes across schools and won many. Recieved the Scientific Inclination award twice in high school. Received a certificate for building a voting application for the school council.

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
[10]: https://rocketsblazing.online/2018/03/25/Sprint-Schedule.html
