# Lab Report Template for CIS411_Lab1 
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Matthew Coates
GitHub: [slycatm2](https://github.com/YOUR_HANDLE)
(if appropriate) Collaborators: [Names of colleagues you worked with on this assignment]


# Step 0: Reviewing Architectural Patterns
See the [lecture / discussion](https://docs.google.com/presentation/d/1nUcy63FWPFYO3OJmERJpMjEtdaFtaIBbuUkpmNRVRas/edit#slide=id.g45345bd5ea_0_136) from CIS 411. You'll need to be familiar with the content from this lecture to complete this assignment.

Note: you are free to work with classmates on this assignment. _Good architecture is born out of collaboration - not reclusive mad-scientist behavior._ However, if you work with colleagues:

1. You must specifically note your collaborators by name at the top of your report.
2. You may not completely copy each others work (diagrams and descriptions, even if your solutions are identical).

# Step 1: MVC Architecture
Review the proposals for the Serve Central project. Let's imagine that the project has been granted (relatively) unlimited resources if they can deliver a version 1 release in 120 days. As a result, the team decides to implement an MVC architecture for its version 1 release, delivering functionality through a [responsive web application](https://en.wikipedia.org/wiki/Responsive_web_design). 

Based on the [this](https://docs.google.com/presentation/d/1UnU0xU0wF1l8pAB8trtLpdM0yuskx66jTFJzd64nsjU/edit#slide=id.g439b9c6866_2_53) and [this](https://docs.google.com/presentation/d/1-VZfAFoBVr6ijNepKAtRA7JoAQsV2Jlbf2l1WPDMhI0/edit) presentation:

1) Document two use cases of your choosing

| Use Case #1 As a volunteer, I want to know if there are any volunteer opportunities that will give me experience in my career field.| |
|---|---|
| Title "Volunteer work and career developement"| |
| Description / Steps 1. Select search radius 2. Discriminate between jobs that are in my career field using categories such as environmental or social support 3. Pick volunteer work | |
| Primary Actor The User | |
| Preconditions Events are loaded into database, the event actually exists, the volunteer must be a trusted person of the community. | |
| Postconditions Volunteer must follow through and take the job, the volunteer job can't be cancelled| |

| Use Case #2 As a volunteer, I want to know if any of my friends are planning to be a part of a future volunteer project.| |
|---|---|
| Title "Volunteer friend finder"| |
| Description / Steps 1. Find friends' profiles 2. Check what those projects those friends are a part of 3. Join the projects that those users are a part of| |
| Primary Actor The user, other users| |
| Preconditions Their friends are already ServeCentral users, the account that represents the user's friend actually represents them and not someone impersonating them, the project actually exists and doesn't contain misinformation on it's existanceS |
| Postconditions Their friends don't quit working on the project, they don't delete their Servecentral accounts so it can't be checked if they still are being a part of the project leading up to it, Servecentral doesn't shut down| |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
| --- | --- | --- |
| Location | Map Page | Get Local Events security gateway/login, area update|
|Location data, account data, jobs in categories, jobs available|map page, job list page, accept/decline page|||

|Location data, account data,  project data|  map page, job list page, accounts page, accept/decline page|security gateway/login, area update|

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

Use Case 1 diagram:

![](2020-03-08-10-34-09.png)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

I think at this stage of developement a Client-server architecture should be considered. It might be slower than a blackboard approach especially since the plan is to use multiple thirdparty source to input and retrieve data, but this way we also don't need to worry about structural mutation. 

2. Using your preferred diagramming tool, generate a diagram of the new Serve  Central architecture that supports these two new requirements.

![](2020-03-08-11-09-18.png)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

I think that the blackboard model will be best for the task, at least for mobile users, since this seems to be where a lot of user traffic comes from on other services. Although it is complex, I feel that Blackboard's use of a diverse group knowledge sources to solve problems would be perfect for trying not to overload servers with more than 1M event registrations per month. 

Since the desktop version also sees a lot of traffic, I think the blackboard model ought to work for it as well, especially since it might get a lot of traffic while the mobile version is down when we're renovating it. It would also be a wise move since our number of users has only increased in the number of years, so changing from a client-server architecture also makes sense from the perspective of needing an architecture to deal with an increasing amount of data. 

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.

The only thing I can think of is limiting the use of numbering within steps to questions only. Sometimes, numbering is used to expand detail, but if it were just used for questions, it might make identifying questions that need to be answered as a part of the lab easier.