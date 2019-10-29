# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
<br>
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
<br>
Name: Josh Coldsmith
<br>
GitHub: jc1581(https://github.com/jc1581)
<br>
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

| Use Case #1 | |
|---|---|
| Title | Search for Service Opportunity |
| Description / Steps | This use case describes a volunteer who searches for a service opportunity: |
|   | Step 1: System displays an option to either log in or create an account (these are described in other use cases) |
|   | Step 2: System displays a home page with a search bar for opportunities |
|   | Step 3: Volunteer browses for opportunities based on type and location of opportunity |
|   | Step 4: System displays the search request of the volunteer and orders the results from closest to furthest away |
| Primary Actor | Volunteer |
| Preconditions | Web App is available and Opportunity Database is functioning |
| Postconditions | Volunteer has received service opportunities based on search results |

| Use Case #2 | |
|---|---|
| Title | Sign Up for a Service Opportunity |
| Description / Steps | This use case describes a volunteer who signs up for a service opportunity: |
|   | Step 1: System displays all information regarding the selected service opportunity |
|   | Step 2: Volunteer clicks agreement to sign up for service opportunity |
|   | Step 3: Volunteer verifies intention to sign up for service opportunity |
|   | Step 4: System displays volunteers profile with new service opportunity added |
| Primary Actor | Volunteer |
| Preconditions | Volunteer has found desired service opportunity |
| Postconditions | Volunteering agreement is recorded and saved to volunteer's account |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Volunteers | create account page | adding a new volunteer |
| Opportunities | create an opportunity page | adding a new opportunity |
| Organizations | create organization account page | adding a new organization |
| Administrators | create administrator account page | adding a new administrator |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

![alt text](cis411_lab1_Step1_Diagram.png "Step 1 Diagram")
![alt text](cis411_lab1_Step1_Diagram2.png "Step 1 Diagram 2")

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recruitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilities of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice. <br> <br>
    Client-Server Architecture: I believe that this architectural pattern would help Serve Central by allowing Thirdparty services to have access to the main central datastore. Due to the advantage of the client-server architecture allowing for access to it by multiple clients, I believe this would prove helpful. One struggle with this architecture would be the centralized server. A common issue with this architecture is that it is risky having all your eggs in one basket. If your centralized server goes down, it could result in your entire website going down. <br>
    Broker Architecture: This architecture pattern could also be useful going forward for Serve Central. This architecture would do well with offering organization-specific interfaces because of the broker deciding what the user should be directed to. Furthermore the broker could direct third-parties to be able to input and retrieve data. The one drawback of this is that it adds complexity to the project and this project may be too small to need this architecture. <br> <br>
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

![alt text](cis411_lab1_Step2_Diagram.png "Step 2 Diagram")

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.
