# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Joe King
GitHub: [jk1551](https://github.com/jk1551)
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

| Use Case #1 |  |
|---|---|
| Title | Serve Central for users. |
| Description / Steps | An application to help users find volunteer service opportunies near their location.  |
| Primary Actor | The primary actor is someone who is interested in volunteering. |
| Preconditions | 1. User must download the application on their phone 2. User must create an account email and password 3. User must allow app to use their location. 4. User must choose events they are interested in |
| Postconditions | 1. The app will take the location and find events around the user 2. It will display these results |
| Invariants | 1. The map will always stay the same because the world never changes 2. New events will be added |

| Use Case #2 | |
|---|---|
| Title | Serve Central For organizations. |
| Description / Steps | An application to help organizations find volunteers for service work. |
| Primary Actor | The primary actor is an organization looking for volunteers.  |
| Preconditions | 1. Organization admin must download the application on their phone 2. Admin must create an account email and password 3. Admin must post location the event will be at 4. Admin must maintain info about events   |
| Postconditions | The app will post the event and show it to the volunteers looking to work. 2. It will show if users sign up for your event  |
| Invariants | Once your event is posted it will constantly be on the until an admin takes it down. Organizations will be able to post events in multiple locations. |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Username and password | Login Page | User Database |
| Username, First name, Last name, Birthday | Profile Page | User Database |
| Locations to click on | Map Page | Event Database |
| Short excerpt on a specific event | Info on a specific event | Event Database (Subsection) |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

[embed](https://docs.google.com/drawings/d/1dx4UXtgw9uGFj_33FojDXoQnCtVw0Ns_nXovB1lXTbI/edit?usp=sharing)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

I believe for an application of this size MCV would be the best architecture to adopt. Because it is an easy to adopt design, it would be perfect as an open source project for anyone who wanted to volunteer to work on the app. It also has a simple design of what the user sees and the info relayed to the database which is all you really need on an app like ServeCentral

One potential issue with this structure could be that it is so simple, if one part of it breaks the rest of the app could be non-functional which would push away users. You would always have to keep a working version of the app running. 

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements. 

[embed](https://docs.google.com/drawings/d/1KSWc-J8n7oOi0Rps1f2sIRDhwnOtTHK2-GKQQF60xEw/edit?usp=sharing)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

For this application, I would use the the blackboard architecture. Because it is used for large data sets it is ideal for the 50Tb of data that is going to be added. It also gives a way for the user to access data within the latency requirements because it leverages communication between the user and the data. 

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).

2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.

Some changes that I made to the lab report were: 

1. Adding invariants to the pre/post conditions because even aspects of the project that never change are important. 
2. Include an extra step in the git instructions because it is not clear for someone who is new to git when they should stop the git commands and work on the assingment. I added step 7 in the 
Lab instructions saying when to start the assignment and when to start pushing to GitHub. 