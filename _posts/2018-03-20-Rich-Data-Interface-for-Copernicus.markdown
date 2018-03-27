---
layout: post
title:  "52°North WPS; Rich Data Interface for Copernicus missions"
categories: blog mission gsoc
---

## Description
The aim of this project is to enable graph processing framework for WPS, which will make it easier for researchers to process geo data. ESA's SNAP looks like a viable candidate to use for the GPF because it works well with Copernicus data and makes writing new graph processes easier. SNAP's strength that it is designed to be used for geodata from Sentinel satellites is also it's weakness, when say, in future Copernicus is not the most prominent source of geodata. Further, the internal standards for SNAP-gpf rely on XML-RPC for providing node name and parameters, their compatibility with OGC WPS standards will have to be explored. But the heart of the matter is the GPF implementation. SNAP has a rich API to read, write and operate on Copernicus geodata. OpenHub Level2A products have been announced but only with Euro-mediterranean region at first, and other limitations. A process could be implemented to convert Level1C data to L2A.

## What approach?
I've discussed some ideas with my mentors Benjamin Pross and Arne de Wall, what i understood was there is a strong need for a WPS that can execute a sequence of processes without user intervention and in-memory, so that the operations are faster and more autonomous. SNAP-gpf has an Operator SPI which can be extended to implement new algorithms. Along with ability to define new operators there are many already available with SNAP, which are growing. All the operators in SNP-gpf can be thought of as nodes in a directed acyclic graph, The nodes have can have multiple sourceProducts but return a single object of type Product. These nodes can be linked together in any sequence of arbitrary length, the only requirement is to have a 'ReadOp' which marks the start of the graph and 'WriteOp' marks the end. Researchers have complete freedom between these two nodes. Since the operators themselves are protected or private, A graph execution cannot be spoiled by an out of order call to any operator. A graph will not execute if the graph is not complete i.e. there is broken links. The nodes are linked starting from the end i.e. Operators look for their source or Node that goes before them, the graph will not evaluate if any of the operator is missing and there will be no disk write. These features provide 1. guarantee that if the graph ran, then the product is what you told it to do, 2. The nodes have the same input and output so they can be connected very flexibly and 3. this guarantees reproducibility of graphs i.e. given a certain graph(XML), a certain version of software and a certain input(product) the output(resulting Product) will always be the same. These are concepts of functional programming languages applied to an imperative language so the source looks unusual but it's the same.

These graphs are created using the 'GPF' class in snap-gpf, this class has methods to describe new instances of Operators or nodes in the graph. It cannot be called to do ad-hoc processes(write stuff to memory, or change it's contents), the graph has to be complete. This is a safety feature. The resulting benefits from giving up more of the stateful nature of the program is more reliable applications.

There is a tool GPT which can execute graphs in XML format, it could be very useful for batch operations, like executing a set of predefined operations to transform Level1C products to Level2A. Again, the XML representation of a graph in snap-gpf may not be compatible with WPS standards which will need to be verified. The graphs have hard rules, graphs cannot be relied upon if the underlying operators are public, graphs won't be flexible if the nodes don't have the same input and output etc. I've looked at some algorithm source of the WPS, i don't think it is compliant with any of those rules. But all the tooling is already there on SNAP to make WPS work on graphs and thrive!

## A little about me
Amar Matharu Singh; born October 5, I am enrolled in a Bachelors course at IGNOU. I am a freelance designer and a Youtuber. I started the channel "Xtremists Death Gaming" with my friend Arunabha Basak. I have designed photo and video effects for "GJ Chill" and "Nier Clan". I received scholarship in National Talent Search Exam under NCERT, years 2012-15.

## Why am I interested in open source?
It's all about freedom. Better software is complimentary. Software source repositories are similar to the great Library of Alexandria. It's better if this knowledge is shared freely. I like the ability to build on top of pre-existing projects and ability to learn from prior works. I love it when my software is useful to someone!

## What features do I want to see?
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
52°North is doing some great work. I am interested in working in bringing the innovations in data to a larger set of users, and in a software that is free and open source. I think it's important that people understand the value of remote sensing and sensor web to better manage our resources on this planet. There is a huge store of data but it won't be of any use if no one can understand it or it's very hard to analyse it. I want to help make this data easier to access, whether it be to run on small computers or low technical skill. So, that there is a foundation for others to work on. I think it's important that the best environment experts can get the data they need to analyse the effects we as a species have on the rest of the biosphere and the global weather.

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
