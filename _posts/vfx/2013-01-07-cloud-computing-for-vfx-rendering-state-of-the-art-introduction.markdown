---
layout: post
status: publish
published: true
title: Cloud Computing for VFX Rendering - State OF the Art Introduction
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
wordpress_id: 261
wordpress_url: http://www.guoshihui.net/?p=261
date: '2013-01-07 20:18:15 +0800'
date_gmt: '2013-01-07 20:18:15 +0800'
categories:
- VFX
tags: []
comments: []
---
<p>At the beginning of 1900s every factory had a power generator. In the contemporary setting, the same dilemma is faced by the visual effects production industry. Rendering, the most computationally expensive process in the production pipeline, continuously challenges the computing power of production companies. Every facility may house enormous clusters of workstations and render farms, which consume significant energy, money and human resources. The computing and storage requirements of visual effects production of film has already reached an incredible level. For example, 40,000 processors were handling 7 or 8 gigabytes of data per second, running 24 hours a day in the last month for Avatar production. This trend is set to increase. The centralization of power production in the 20th century resulted in significant efficiency savings for the burgeoning industrial sector, and we can predict that the similar revolution on the horizon in visual effects production: Cloud Rendering (short for Cloud Computing in Rendering).</p>
<p>The concept of the “cloud” is not a new idea in VFX industry: production facilities already house individual clusters of renderfarms and data centers, and some plan to unite all the computing powers around the globe. For example, facilities in LA can utilize the unoccupied computing power in London by taking advantage of the difference in timezone.</p>
<h1>Why we need the Cloud Rendering ?</h1>
<p>The emergence of a new technology always comes with a mission to solve existing problems and benefit people in various ways. Therefore, we may ask, what kind of benefits we can receive from cloud rendering ?</p>
<h2>
Money Comes First</h2>
<p>Business is business, and it is typically correct that major technology breakthroughs are driven by business motivations, including the topic we are talking about.</p>
<p>First, cloud rendering could reduce the operational expenses for the production companies, which need a team of professional technicians - System Administrator - to maintain the large scale of machines. Their job includes setting up the work environment, taking care of the render farm etc. With cloud rendering, these troubles are mostly left out to the cloud service providers. Some even declare that their services of cloud rendering is totally technician-free.</p>
<p>Second, cloud rendering could also reduce the investment in the infrastructure. By utilizing the cloud for heavy computation, the companies avoid investment in the expansion of renderfarms. And those cloud services providers also provide some offer, such as Spot Instances by AMAZON service. Spot Instances allow customers to bid on unused Amazon EC2 capacity and run those instances for as long as their bid exceeds the current Spot Price. For customers with flexibility in when their applications can run, Spot Instances can significantly lower their Amazon EC2 costs. Additionally, Spot Instances can also provide access to large amounts of additional capacity for applications with urgent needs.</p>
<h2>Time is Money</h2>
<p>Time is the most precious thing when working towards the deadline. Using large scale of cloud could significantly accelerates the rendering process at this critical moment. It is also fairly flexible to split up the workload among local workstation, renderfarm and the cloud. By optimizing the distribution, customers can maximize their work efficiency while minimize the expenses.</p>
<h2>“Technically” Small Is Big</h2>
<p>By deploying cloud computing, it is flexible to scale up and down the “cloud” according to the demand of ongoing project. It is of vital importance for small companies to bid for large projects without worrying about their limitations on computing capability. However, we need to mention that infrastructure is also one part of the limitations, out of which talents are more crucial.</p>
<h1>How does Cloud Rendering affect the whole production pipeline ?</h1>
<p>As is aforementioned, cloud rendering will help empower the small production company to carry out large project without the worry of computation limitation. However, its more profound influence on the whole production pipeline is to bear a new model - Distributed Model of Project Cooperation.</p>
<p>Current visual effects production is mostly company-centered, which means that the project is distributed among companies, who employ large numbers of talents. A new P2P (peer-to-peer) model is being developed by CloudPic company, which allows artist to easily create and collaborate with other people. If the project is based on the cloud, and every people participated in the project gets a copy of part of the project. This is similar to the distributed version control system, GIT. We like to call this future model as artist-centered.</p>
<p>P2P network structure reduces the risk of leaking the whole project, however increases the risk of leaking individual component if the artist has local backup on his/her own hard drive. Though it is preferably a better solution, it adds more pressure and risk on individual artist because they are the direct victim if any hacking incidents happens. Therefore how to set up a reasonably agreement for this model is an problem that we should solve before handing it to artists.</p>
<h1>What Are the Issues Concerned With Cloud Rendering ?</h1>
<p>However, cloud rendering is far more complex than its electrical sibling, which indicates that it has some key issues to be solved before it will be fully accepted by the visual effects community.</p>
<h2>Security</h2>
<p>This is a major concern which blocks companies from adopting cloud rendering in their real production. Most production companies avoid involving third-party in the production process because of the fear of leaking-out.</p>
<p>Although these service providers claim that they have passed (I don’t like this word) numbers of regulations and rules about security, we can never under-estimate this problem. Possibilities, from online hacking to offline human mistakes, still exist and highly threaten the data we uploaded to the web server.</p>
<h2>Privacy</h2>
<p>Threat to the files on the cloud not only comes from the malicious attack, but also from the government as well. American Patriot (Providing Appropriate Tools Required to Intercept and Obstruct Terrorism) Act entitles US authorities the power to access data stored overseas if it is owned by a US company. Since most of cloud service providers are under the regulation of this act, it will have an influential impact on cloud computing. On the other side of the Altantic Ocean, the “European Cloud Computing Act” is also under discussion and aims to be published by this year. Though these laws are designed from a good purpose, they puts lots of threats on clients’ privacy.</p>
<h2>Copyright</h2>
<p>The agreement between the cloud service provider, software vendors and production companies is not yet settled down. The fear of being sued by software vendors for infringing the software copyright is also a concern that worries the production companies. However, I would take this as an opportunity, rather than challenge. Imagine that in the far future, when all the computing is carried out on the cloud and the software is based on the cloud, there is no such issue. And the production companies pay the cloud service provider, rather than directly to the software vendors.</p>
<h1>What difficulties we have currently got to widely implement the Cloud Rendering ?</h1>
<p>Let’s put the troublesome bits aside and say we want to use cloud rendering for visual effects projects, is it ready to use for everyone ? The answer is “Not Necessarily”.</p>
<h2>Price</h2>
<p>Compared with local renderfarm, current price from these cloud providers are not competitive enough to attract companies to abandon their current infrastructure and fully embrace the “cloud”. The reason mainly lies in that cloud computing is still in its early development stage and we fully believe that the price will go down when we have more options to choose from.</p>
<h2>Bandwidth Bottleneck</h2>
<p>To fully and instantly access the cloud, we need high-speed internet, which is not guaranteed at all times and all places. By taking the time spent on the internet connection, it may even take longer time than firing the rendering task on the local renderfarm.</p>
<h2>Global availability</h2>
<p>For most web service provider, they only have tens of data centers spread out around the globe and possibly a correspondingly numbers of contact points. The distance to the data centers at this moment significantly influences the time spent on data transferring between your local machine and data centers. Though tele-communication is a normal approach to provide technical supporting, clients are still faced with inconvenience when any problem occurs.</p>
<h2>The support from the software vendors</h2>
<p>Attitudes of some software vendors are still vague while some intend to charge an incredibly high price on web service providers, which prohibits the development of the web services providers and detriments the end-user’s benefits. Without the support from these software vendors, these web service and its clients are faced with two major problems before actually adopting cloud computing in industry production, one is software lock-in and the other is the potential copyright conflicts with these software vendors.</p>
<h1>Conclusion</h1>
<p>In this article, we introduced an emerging technology of using cloud computing for rendering in visual effects production. This service is economical, efficient and flexible, which will greatly benefit the small production companies. It will also give rise to a new model of project cooperation, transforming from current company-based to artist-based. However, people got worries in the security, privacy and copyrights related with the service of cloud computing. Meanwhile the limitations in network connection and global availability are blocking the interested customers from actually applying this technology to their daily practice. Current price is also not competitive enough attract people to abandon the traditional renderfarm.</p>
