# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Matt Ly
GitHub: MattLy21(https://github.com/YOUR_HANDLE)
(if appropriate) Collaborators: Leanne Weaver


# Step 0: Reviewing Architectural Patterns
See the [lecture / discussion](https://docs.google.com/presentation/d/1nUcy63FWPFYO3OJmERJpMjEtdaFtaIBbuUkpmNRVRas/edit#slide=id.g45345bd5ea_0_136) from CIS 411. You'll need to be familiar with the content from this lecture to complete this assignment.

Note: you are free to work with classmates on this assignment. _Good architecture is born out of collaboration - not reclusive mad-scientist behavior._ However, if you work with colleagues:

1. You must specifically note your collaborators by name at the top of your report.
2. You may not completely copy each others work (diagrams and descriptions, even if your solutions are identical).

# Step 1: MVC Architecture
Review the proposals for the Serve Central project. Let's imagine that the project has been granted (relatively) unlimited resources if they can deliver a version 1 release in 120 days. As a result, the team decides to implement an MVC architecture for its version 1 release, delivering functionality through a [responsive web application](https://en.wikipedia.org/wiki/Responsive_web_design). 

Based on the [this](https://docs.google.com/presentation/d/1UnU0xU0wF1l8pAB8trtLpdM0yuskx66jTFJzd64nsjU/edit#slide=id.g439b9c6866_2_53) and [this](https://docs.google.com/presentation/d/1-VZfAFoBVr6ijNepKAtRA7JoAQsV2Jlbf2l1WPDMhI0/edit) presentation:

1) Document two use cases of your choosing

| Use Case #1 | |
|---|---|
| Title |Register|
| Description / Steps |The users information is sent to the organization and is processed  |
| Primary Actor |Volunteers |
| Preconditions |The volunteer is able to entering information into the form for an event |
| Postconditions |The volunteer is able to see that they have been approved or denied to the work at said event |

| Use Case #2 | |
|---|---|
| Title |Events |
| Description / Steps |Users are able to look up and register for event by giving information |
| Primary Actor |Organizations |
| Preconditions |The organization enters information to an event and posts |
| Postconditions |The organization gets information about the volunteers that are interested |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| First Name | Events | Edit Profile |
| Last Name | Log In | Upload Event |
| Date of Birth | Settings | Update Map |
| State | Accounts | Adding Admin |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

[Diagram](https://drive.google.com/file/d/19jV1dA3I81Zv1PD6pH9NASATnG243wt6/view?usp=sharing)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

I chose the layer architectural pattern because it allows independent choices per layer meaning that the organization is able to have the local churches website but have Serve Centrals database and logic. They would be able to be a third party admin that they could use and would input information and recieve information by simply changing the logic. One potential issue that over time changes start to happen in layers and differentiating things. It becomes hard to tell which one is which and they start to bleed together and that is when things start to fall apart. 

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

[Diagram](https://drive.google.com/file/d/11pXyQd5GWv9A6tvtal-QoCtdSvVhp3wc/view?usp=sharing)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

The archictural pattern I chose was the Microservice. I chose this because it is able to have fast reliable delivery of large/complex applications. By having multiple API's working you would be able to service the 10k+ volunteers in less than 15 secs. It would then be able to use the API's to store the volunteer and event data quickly. Authorized parties would be able to have a admin login that they can ask the API's for specific information that they need. The researchers would be able to go to the API and see all of the volunteer opportunities and do an analysis to determine future grant investments. The benefits of using microservice is the flexability of tech stack. It is also easy to reduce the clutter by having flexible data storage. A disadvantage of microservices are that having multipe databases could be hard the manage. Microservices also have huge security challenges becasue of the inter-service communication over networks. Changes are needed because there would be to many users that would be trying to submitting forms and registering for events. That would usually cause a crash but by using the microservice you are able to have API's do it really fast. 

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.