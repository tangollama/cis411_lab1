# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: NICHOLAS DESOLA
GitHub: [ND1227](https://github.com/ND1227)
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
| Title | Complete registration for the mobile application |
|Description / Steps | Sign-up will be completed by launching the application and clicking the sign-up button.  After this, the user inputs their information and completes the sign-up process by verifying their email.  To complete registration, the user logs into the application and inputs the rest of their information and clicks "update". |
| Primary Actor | New user |
| Preconditions | Application must be downloaded |
| Postconditions | User will be admitted into the system and the system will have the user's information within a database. |

| Use Case #2 | |
|---|---|
| Title | User applies for an event |
| Description / Steps | The selects the event that they would like to volunteer.  The user confirms their information and the event's information, and then the user clicks the sign-up button.  This initiates the backend to notify the event vendor of a new applicant and the user will receive a confirmation once they are successfully sign-up for the event.
| Primary Actor | Volunteer |
| Preconditions | User has an account.  Event is created. |
| Postconditions | User is signed-up for event.  Event is updated with the number of volunteers. Event is added to user's event list. |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model                               | View                                         | Controller                                                                                                |
|-------------------------------------|----------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| Adds volunteer to event             | "Sign up" button displayed at bottom of form | Receives volunteer information and notifies model to "add volunteer to event"                             |
| Update user information             | "Update" button that user clicks             | Receive update from view and notifies model to "update user"                                              |
| Display event on map                | Map with POI at location of events           | Active refresh to receive view information and notifies model to "update map view"                        |
| Update user's volunteer hours wheel | Volunteer hours wheel with matching legend   | Background refresh to receive completed events information and notifies model to "update volunteer wheel" |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._
 
![alt text](https://www.lucidchart.com/publicSegments/view/be629e92-e241-44a6-b28c-02465ff02acb/image.png "Event Registration")

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.
 
    Broker and Layer architectural patterns are appropriate because broker allows for dynamic CRUD operations that allows the system to grow on its own and make options on the fly.  Layer architectural pattern let's the system create multiple custom interfaces for each client, while lowering the need for management by the server. One issue for the broker architecture is that it will be very complex to initiate while the project is still small.  The Layer architecture will show adverse consequences because management will still have to oversee the project to confirm the layer work well together.

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.
 
    Blackboard and broker archiectural patterns will be able to support the requirements of this enhanced project.  Blackboard will allow the project to process massive amounts of data/information while allowing multiple components to be used with low latency.  Broker allows the larger project to be handled through dynamic CRUD operations and create transparent service distribution to the various clients. The change from layer is due to the fact that management oversight is required to run the achitecture.  Although many options can be made per service layer, the size of the project requires more physical oversight versus blackboard.

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.