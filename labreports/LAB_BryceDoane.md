# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Bryce Doane
GitHub: [BryceDoane](https://github.com/BryceDoane)
(if appropriate) Collaborators: Will Newcomb and Matt Laven


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
| Title | As a user I want to find and register for nearby volunteer events |
| Description / Steps | This scenario describes a verified user is looking for nearby volunteer opportunities. 1. User logs in. 2. User enters their location. 3. User registers for event. 4. User tracks updated volunteer hours after event. | 
| Primary Actor | Registered User |
| Preconditions | The event is created. |
| Postconditions | The user is registered for the event. The event roster is updated. |

| Use Case #2 |  |
|---|---|
| Title | As an event coordinator, I want to be able to create an event and have users register|
| Description / Steps | This scenario describes an event coordinator creating an event and making it available for users to sign up. 1. The coordinator logs in. 2. The coordinator creates a new event. 3. The coordinator enters the details of the event. 4. The coordinator publishes the event.|
| Primary Actor | A registered event coordinator|
| Preconditions | An event is scheduled to take place|
| Postconditions | The event is successfully created. Users can sign up for the event.|


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Event| Event Description Page |  Get Event Details|
| Login| Login Page | Security Gateway |
| User| User Information Page | Get Profile Information |
| Roster| List of Attending Events | Get Users Registered for Specific Event |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)
![MVC Diagram](MVCDiagram.jpg)
_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.<br><br>
**The architectural patterns that are appropriate to support these objectives are broker and rails architecture.  Broker architecture is very easy to expand and grow with while keeping easy maintanence.  One issue with this pattern is the need for special software while also relying heavily on the broker.  If the broker goes out, the whole system would be down.  For rails, it is cost-effective and enables easier and faster development.  The consequences of rails is that it is often seen as slow.**<br><br>

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

![New Serve Central Model](NewModel.jpg)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.
<br><br>
**A solution similar to Docker (which uses client-server) would be best for this immense project. Docker uses containers to scale up and down which would be ideal to handle these future needs with the ease and speed necessary. The system needs to be changed because a broker architecture would not be able to handle the size with the speed necessary of the system.  It is simply too much data to process and distribute in too little time.  Some potential consequences of the new system are high cost and also the centralization aspect if a server goes down**
# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
<br><br>
![Extra Credit Diagram](ExtraCredit.jpg)
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.
<br><br>
**My only real suggestion to make to this lab would be to hint at what answers may be more correct than others.  In class we very briefly went over each of the many architectural types and did not go in-depth with all of them so at times, I had to look up many of them which brought more confusion from some internet sources.**