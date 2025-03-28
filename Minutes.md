Minutes for HP-WAN IETF122 side meeting (20th March 18:00~19:30pm Bangkok)
--------------------------------------------------------------------------

Participants: 

Colin Perkins, Gorry, Zahed, Jordi, David Lou, Hesham, Yamato, Adrian,Michael Welzl,
Antoine Fressancourt, Lius, Andrew, David Guzman, Julien Maisonneuve,Daniel King,
Daniel Huang,Quan Xiong, Kehan Yao, Junfeng Zhao, Ran Chen, Chumeng Wang,Sandy Zhang,
Chuanyang Miao, Yao Liu, Zhengxin Han, Cancan Huang, Huiyue Zhang, Hang Shi,Xueyan Song,
Teng Liang, Huijuan Yao, Peng Liu, Zhiqiang Li, Liuqi, Yangyang Wang, Xing Zhao,Yuexia Fu,
Lei Zhou,Tianji Jiang,WZY, Cheng Zhou.
 
The primary agenda is shown as below.

1,Note well, welcome statements, introduction and agenda bash. Daniel Huang, 5mins

2,Use cases and requirements from public operators' view, Kehan Yao, 10min

3,Problems and gap analysis for HP-WAN, Daniel Huang, 10min

4,Scenarios and deployment considerations for HP-WAN, Junfeng Zhao,10min

5,Technical soulutions and applicable technologies for HP-WAN, Quan Xiong, 10min

6,Open Issues Discussion, 45min

Presentation Highlights:
------------------------
*Use cases and requirements for HP-WAN  (Kehan Yao, 10 mins).

Colin Perkins:

- Requested clarification on whether listed requirements have priorities or are absolute.

Daniel Huang:

- Highlighted the need for increased signaling between host and network, emphasizing differences between shared public networks and dedicated networks like ESnet.

Kehan Yao:

- Emphasized host-to-network signaling and traffic scheduling as top priorities.

- Noted congestion control as important but secondary, considering existing solutions like BBR.

Colin Perkins:

- Distinguished fundamental requirements from those arising from TCP characteristics, such as low packet loss necessary for high TCP throughput.

Kehan Yao:

- Affirmed high throughput as the fundamental requirement and packet loss reduction as an essential consideration for current TCP usage.

Zehad:

- Clarified low loss as a link/path issue rather than transport protocol. Recommended exploring enhanced congestion control or smart routing information strategies.

*Problems and gap analysis for HP-WAN (Daniel Huang, 10 mins).

Colin Perkins:

- Suggested traffic enforcement at network edges to minimize flow completion times.

Daniel Huang:

- Confirmed ongoing efforts to specify host and network functionalities, leveraging existing technologies and edge devices.

*Scenarios and deployment considerations for HP-WAN (Junfeng Zhao,10 mins).

Gorry:

- Questioned necessity of "gateway" terminology, preferring layered or protocol encapsulation approaches.

Junfeng Zhao:

- Explained gateways might be necessary for protocol translation and data buffering.

Gorry:

- Cautioned against complexity of protocol translation and encouraged clarity about specific translation functions required.

Daniel Huang:

- Acknowledged Gorry's concerns, agreeing that transport translation provides benefits but also poses challenges.

*Technical solutions and applicable technologies for HP-WAN (Quan Xiong,10 mins).

Open Issues Discussion (45 mins).
---------------------------------

Kehan Yao:

- Summarized options: forming a new working group for developing new transport mechanisms or distributing work across existing groups.

- Identified key considerations: scope within IETF, clarity of use cases, and fundamental requirements.

Daniel Huang:

- Expressed caution about introducing new transport protocols. Recommended exploring existing signaling methods first.

Xing Zhao:

- Requested clarification on metrics defining "timely" end-to-end traffic scheduling.

Kehan Yao:

- Clarified goals of timely transmission relating to flow completion time and improved throughput.

Daniel King:

- Raised geographic considerations for protocol deployment and questioned vendor support globally.

Daniel Huang:

- Confirmed multi-vendor interest and support for HP-WAN initiatives.

Colin Perkins:

- Supported incremental approach to addressing problems through smaller working groups or existing groups, rather than forming a large overarching group.

Kehan Yao:

- Advocated a core group to coordinate a unified framework despite splitting tasks among existing working groups.

Colin Perkins:

- Reiterated flexibility in organizing work either via an overarching group or coordinated efforts among smaller groups.

Daniel King:

- Recommended incremental and focused protocol enhancements over large-scale simultaneous modifications.

Daniel Huang:

- Agreed on the importance of clear frameworks and coordination across groups.

Colin Perkins and Daniel King:

- Recommended further discussions and consensus-building post-meeting through mailing lists and follow-up documents.

Conclusion:

- Looks to be a problem that a small community is willing to work on. Agreement to continue discussions and consolidate feedback on mailing lists to identify optimal method for organizing and advancing HP-WAN solutions discussion.

A full transcription of meeting is below. 
-----------------------------------------

Colin: Those requirements are sort of nice to have. Is there like a priority list?
Or is it simply sort of absolute? 

Daniel Huang: From the previous discussion, we think that we need more signaling between the host to network.
We want to solve the problems within a public operators network where the network is shared. So this might not be, 
this is very different from the network like ESnet. They have the network like all the topologies and other 
jobs and the workflows are well scheduled. So this is a fundamental difference I think. So we need to ensure that
 the traffic Scheduling in the public operator networks. So we want to see that how the traffic can be 
 efficiently scheduled in this kind of networks. So I think the signaling between host and network may be a priority.

Kehan Yao: If this can be done within the WIT, like host to network or like scheduling about the traffic within the
routing area. So I think these will be the very top requirement, but also like a congestion control, they're also 
important because we see the results like BBR, they have influence in the end to handle transport and have effects
on the throughput. We can rely on the mechanisms already defined by the CCWG and other congestion control algorithms. 
So congestion control, they might not be the very top requirement for HP WAN.

Colin:W hich of these requirements are fundamental and which are related to your suggested solution.
For example, it seems there is a requirement to have very fast TCP downloads. Which would suggest that if 
you're using TCP in its current form, you need low packet loss rates. But the fundamental requirements is high
performance TCP and low packet loss rates are an artefact of the way TCP is currently built, so what are the 
fundamentals requirements relate to your current suggested solution? Why there is a requirement for low packet loss?

Kehan Yao: The basic requirement for high throughput and to reach high throughput over a large distance.
So we need to ensure the packet loss to be very low if you're using TCP in its current form. 
We've been identifying the root cast of the transport throughput is the packet loss, I do believe there's 
not simply packet loss, but so we will put in some solutions mechanisms in place to reduce the packet lost as 
low as possible but I do have the concern if we put packet loss to itself. So I would say the high throughput 
is the the HPWAN fundamental requirements.

Zahed: Thanks for this presentation. So I have been giving input and trying to help you, this is the first time
I see the relationship, the problem then you're describing and relationship to the transport protocol aspects. 
So thanks for doing that. The second thing is like I was exactly thinking like what Colin knows asking. We need 
to understand one thing like if we need low loss, that's a requirement of the link on the path, not on the transport
protocol. We cannot change the link or path behavior because you have no control over it. We have shared traffic 
and we really want to have high throughput. Then this transport protocols maybe. We can update TCP condition control
or think about like taking from ingress routing information to take do the some smart backup or like fill in the buff
like link city, this kind of behavior. That could be something with the transport product and currently I don't see
like any transport protocol in a sense like condition control algorithms actually do that, but I heard like the 
admission control, this kind of things could be done and the the requirement then is like basically if you're doing
trying to solve this problem, they're trying to get the throughput high on a transport protocol layer, then we need
to split up whether we need to improve the congestion control, whether we need to improve some other kind of behavior
on the transport protocol like how we react, all these things and we need to have like new kind of information. 
Cross layer information taking when you're sending when your sender or when you're receiver of the data. So those
kind of things I think we need to go a bit more farther looking into this one because the moment you say like, we
 need to have low loss at the transport protocol I don't know what I do need to do. Because that's the path and link 
 characteristic. You can have very bad engineered path or link or route that's losing packet, I cannot do anything 
 about it just back off because to me it's confused. So just as a follow on to that we had a similar discussion I 
 guess in the early two thousands when Protocols such as TCP Cubic were introduced and the the change from TCP Reno 
 to TCP cubic allowed TCP to achieve higher throughput with the same packet loss rates. So I'm trying to understand 
 if the issue is, can you make TCP go faster or if the real issue is, can you make the packet loss Lower? Because 
 there that's not necessarily the same problem. Not all of the case depend on TCP to be transferred data especially
 for the new case. So, and go back for TCP itself that we did see that there was some progress. Not only like TCP 
 plus cubic, but also like TCP plus PBR, we have that TCP can achieve a very good throughput performance. So 
 we see that cubic is twenty years old now, of course, the things are better. So your pro you want to make sure that
 if we do want to improve the performance of TCP. I think it's within the scope and but the difference is that TCP, 
 they can achieve very good effects. Like plus PBR in the well scheduled network we have clear like they can grab 
topologies, they can schedule traffic like Google's Effingo systems or ESnat use SDN controller 
or orchestrator to orchestrate different workflows. And then they can do some capacity planning for different
traffic, they can use TCP for the transport protocol and then use some algorithm like BBR to achieve very 
good throughput performance. But they have some scenarios cannot be achieved. For example, in scenarios like networks,
 you cannot precisely measure the bandwidth and the network is not that stable, so they will not behave very good 
 for TCP plus PBR. That is probably correct, but I think if we need to understand what are the fundamental 
 requirements and what are derived requirements because of limitations of current protocols. Because that may affect 
 the way you build a solution because there maybe several different ways of building a solution and if you're assuming
 you're starting from here, you end up in this place, but if you don't assume you start from the current things you
 may end up somewhere else.

3,Problems and gap analysis for HP-WAN, Daniel Huang,10min

Colin: I wonder whether you would consider solutions like traffic enforcement at the edge
to be able to Schedule flows and achieve the. The goal of minimizing flow completion time, 
etc is that what kind of solution do you think we have in the network that we can use and whether.

Daniel Huang: Enforcement would be one of them and among others or just just as a random question actually.
Yeah, actually we will have presentations about framework under which details is going to be some specified 
functionality in both the the end host as well as the network devices. We believe we have to get the clear.
Boundary between a routing network, the routing error of the technology and transport error networks.
That's why we get an edge network devices involved. There will be there will be some, a brief coordination 
between the hosted network, but when when it comes to the the Traffic scheduling. Within the network, I believe.
The existing technologies to not technology will apply for those scenarios.

4,Scenarios and deployment considerations for HP-WAN，10min

Gorry: Why we had gateway there rather than encapsulating or tunnel or something because to me gateway is
quite as scary term. Does it have to be a gateway?

JunFeng Zhao: It could be function like maybe we can translates protocols. And they need to buffering catching 
some data.

Gorry: Protocol translators are interesting but fairly complicated beats pieces of machinery. What real 
functions you need in that because this has come to become one of the areas where maybe the IETF doesn't
tend to specify things like protocol translation. It's very difficult to translate two arbitrary versions
of a protocol into each other and even more so when one is perhaps not under IETF congestion control, if 
we're talking about RDMA here. So, just wondering whether it has to be a full gateway protocol translation
function or whether you can actually Layer something to solve the problem.

Daniel Huang: I generally agree Gorry's points and I believe they're going to be quite hard balanced to
to strike when it comes to approximate gateway, particularly the transport translation because transport 
translation will work in some way to help us to to achieve the high throughput, but it has cost. It has to
quite maybe it will raise the we raised some other performance.

Gorry: I'm not saying it's impossible to do or anything that crazy like that. I'm just saying this is an area
where you need to think carefully about how much you need and whether one of those could just be a standard 
protocol or whether you can use standard interfaces and whether that helps or doesn't help. 
If you were to translate RDMA to an FSB four and translate from TCP to running quick, you have a lot of things 
to match. So maybe the bad choice isn't good choices, but it would be interesting to know which IETF protocols were.
useful in this context and which ones would need to be changed and what you're trying to map from and to. So,
they're all just questions and I'm not I'm not saying anything's bad, anything's good, just saying that be 
worth their dragons here.

Daniel Huang: We do not specify a specific transport to be refined HP WAN, we will not invent a new transport 
protocol. We will simply trying to get some additional input for the existing transport transport port host
to address to the problems of HP WAN.  

Gorry: Would love to see more feedback about how this works out this evening.

Gorry:Would you please to specify the the specific products that you you mentioned that the particle optimization 
for the packet lost and tolerant. How packet loss tolerance is for the product? The average packet lost in the 
public network now is roughly about 0.1%.

Junfeng Zhao: The average of 0.1% is presumably highly variable depending on the environment. It would expect quite 
high packet loss rates in wireless networks and much lower than 0.1% in high quality backbones network. 

5,Technical solutions and applicable technologies for HP-WAN, 10min
6,Open Issues Discussion, 45min

Kehan Yao: Thank you all for attending the meeting today. So I wanna summarize some recent progress and also we try
to narrow down the scope and go further. So the options for HP WAN, one is that if we can form a new working group
and to design some new transport mechanism or protocols and then another is that if the current defined a protocols 
or ways to solve HP WAN service problems and then we can split the work to existing working groups. So there there 
are some basic questions. We get a consensus on whether to form a working group, we need to ask, are these IETF care,
are these use cases that within the IETF scope and are they clear enough to derive the requirements, and also other
problems space narrowed down and also then for the requirement I just thanks calling for raising out the question 
and and modify the question here that what's the fundamental requirement for HP WAN. So maybe we can have some open 
discussions for the spacing three basic question here.

Daniel Huang: When it comes to a new protocol. I'm quite a little bit concerned about the new protocol involved into the 
transport area. So I believe we firstly the first phase it will be necessary for us to investigate the existing 
signaling or protocol in place, which could be, exploited and refined to address to the issues but
nevertheless, a new signaling protocol would be beneficial if the existing mechanisms to come out to satisfy the 
requirements of HP WAN.

Xing Zhao: Just one question about the timely. I'm wondering how to define timely. Is there a specific metric for 
the time you you mentioned that the timely end to the traffic scheduling? So, is there any metric for the time.

Kehan Yao: I mentioned about four use cases, they use different transport protocol, and then we want to define
a transport protocol to realize timely end to end transmission with completion time and traffic scheduling to 
improve throughput performance. Compared to traffic scheduling, under well controlled networks like ES network
or cloud networks. 

Daniel King: Compared to sort of where we've had previous discussions, I felt that there was more detail and I
 think the observation earlier was that we're narrowing sort of the discussion and therefore the search space 
 for potential protocol solutions. There's still sort of several unknowns to me at this stage and considering 
 that we're hearing this requirement from a particular region, a geographic region in China, for example, 
 I do wonder if the problem is geographically specific because other networks around the world have this dedicated
 infrastructure in the UK we have Janet across Europe we have Dante, the US ESnet, and others. So is this really
 something that if we were to build or modify some existing protocol would have a very limited deployment. Because 
 other regions don't use it currently?

Kehan Yao: Not just China specific, it is internet problem, want to transfer across different networks from provided
 by different providers. 

Daniel King: What is actually implemented? Is that going to be function on the ingress. Typically is owned and and 
managed and operated potentially even built by the provider itself? So cause this is sort of an OTT type environment,
 very big, you essentially can take white box components and and put them together and implement a stack that performs
 this function. And there's sort of the intermediate hop. Across the network to the other side, is that a multi vendor
 network? It's applicable worldwide across public internet infrastructure. Are there enough vendors who actually want
 to support it?
 
Daniel Huang: There will be many vendors, when it comes to the vendor supporting, I actually I made a couple of 
short conversations with other colleagues from the other vendors. Generally the they agree with the use cases of 
HP WAN and they believe they the general mechanisms we described within our draft is quite necessary for the 
requirements so I believe we have kind of multi vendor supporting for the functionalities.

Colin: There are clearly looked to be reasonable problems to be solved here. And I think we've had similar 
discussions in the IETF a number of times in the past at different performance levels. Back in the early two 
thousands, for example, when the various high speed TCP variants were developed, it was in response to a similar 
set of problems and they haven't come up with a particular solution which worked in the environment we had twenty
 five years ago, but it was a similar type of Requirements which were being addressed. So the requirements 
 certainly seems like a reasonable one to solve. There's also obviously several different ways you could build
 technologies which could solve this problem. I I can imagine several different technical solutions for addressing
 this problem. And I can also imagine several different ways of organizing the work in the IETF. I would suggest 
 that this the work can probably be split into separable pieces. There's some parts of it which is congestion 
 control, there's some part of it which is talking to a proxy, there's some part of it which is QoS signaling, 
 there's some part of it which is traffic engineering and so on. My impression is that the IETF has done a better
 job at building small building blocks than it does at building systems. And I would therefore suggest that perhaps
 a way of organizing the work that would maximize chances of success is to take each piece to the relevant working 
 group or research group or a boss or whatever is needed. And address each piece individually. Rather than to try 
 and create a working group to do the overarching problem. Because such large scale working groups have historically 
 not been as successful in the IETF as small focused attempts to build individual pieces, which the company had then
 turns into a product which solves the overarching problem.
 
Kehan Yao: If HP WAN touched many pieces that are relevant to existing working groups, but the problems can be 
splited into too many working groups to solve individually. We think that forming the core group for overall 
framework to better understand the problem space or the fundamental requirement.

Colin: Certainly we have had working groups which have been structured like that in the IETF before.
Sometimes they have succeeded, sometimes they have not. I don't think there is a requirement in the IETF to have
 such an overarching group. So you could certainly organize the work that way and it would be a reasonable way 
 of organizing the work. You could also take each piece separately and then standardize the necessary building
 blocks and not standardize the overarching problem. And that would also be a reasonable way of doing the work. 

Daniel Huang: I agree there's different trade offs obviously. It's quite necessary for us to leverage the existing
technologies in the relevant working groups but I think it will also be quite necessary to have overall description
 and specification of of what the requirements as well as the problem is and as well as the general framework rather
 than a standard a standard track and yeah, there's going to be quite a lot of coordination among multiple existing
 working groups. It would be quite hard if we do not have overall framework and coordination.

Colin: Clearly someone has to coordinate the work. That coordination could happen in the form of an IETF working 
group or it could happen in the form of a company which is interested in the work. Organizing its engineers to go 
to particular working groups and work on particular pieces. But both ways work, what they have different challenges 
in terms of organization in the IETF and my suggestion would be that, you know, in, in my experience. The approach
 of standardizing the building blocks in the IETF but not the overarching system tends to work more effectively, 
 but I have seen people do it both ways. 
 
Daniel King: It's the balance of probabilities. If you are trying to modify several things at the same time, it has 
a much higher risk of failure. And if you consider that there is one specific capability that is a highest priority,
which was kind of the point I was making earlier, and that then becomes a soluble problem, ideally in an existing 
working group. And then the other factors that are required or need to be addressed can be sort of incremental updates. 
If we're dealing with produce significant protocol change or multiple protocols, that's potentially a difficult path 
to follow. You could potentially create a working group and try to coordinate that. If there are sort of multiple 
 technologies that need to be worked on almost simultaneously rather than sequentially, but you could also just 
 have the coordination done through an internet draft, it maybe a framework and it may refer to other documents 
 that kind of feed the framework. And then use that framework in one or two existing working groups
 as a way to coordinate. It's probably worth post this meeting kind of going through these different scenarios,
 talking about them on the list cause clear. There are other people who are interested in this, but for whatever 
 reason, they weren't able to attend the site meeting today, so when when we publish some sort of conclusions, we
 can continue this discussion on the list.
 
Daniel Huang: Thank you, we will be open for multiple options to raise debate at you, We'll have 
summarization of our discussion and to put it posted on the list and gather more people's interest to the
comments involved.
 
 
 
