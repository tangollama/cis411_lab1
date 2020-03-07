# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: YOUR NAME
GitHub: [JostonChan](https://github.com/JostonChan)
(if appropriate) Collaborators: [Tanner Stern](https://github.com/tannerstern)


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
| Title |  Display events' location in the location view |
| Description / Steps | User is able to locate events to find volunteer work in the area.  |
| Primary Actor | User |
| Preconditions | 1.Information of the events are already created and stored in the database. |
|               | 2.The view and controller for the location are already created. |
| Postconditions| The user is able to view the events in the area. |

| Use Case #2 | |
|---|---|
| Title | View description of the event |
| Description / Steps | 1. When a user clicks on a event, the web application displays the description of the event. |
| Primary Actor | User|
| Preconditions | The web application must have the description of the event in the database. |
| Postconditions | The web application display the description of the event. |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Login model - retrieve the information from the controller and updates the login model  | Login view - User can view the login page, input his/her username and password, and click the login button to login.  | LoginController.php - retrieves, verifies and sends the login information to a model.  |
| User model - stores the user's information to a database.| Profile view - user can view their information.| UserController.php - retrieves, verifies and sends the user's information from view to a model. |
| Location model - stores the event's location to a database.| Location view - user can view their location and its surrounding area. | LocationController.php - retrieves, verifies and sends the location of a event to a model.|
| Event model - stores the event's information to a database.| Event view - displays the information of the events. | EventController.php - retrieves, verifies and sends the information of a event to a model. |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

![MVC_Model Diagram](images/MVC_Model.png)

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Third party services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

**Answer:**
For this redesign, I would suggest the **Layer architecture pattern** because it breaks down the web application into several layers, each of which has a certain level of abstraction and is independent from the other layers. Therefore, a layer has little to no knowledge of the inner workings of other layers in the architecture. Thus, they will have no impact to the other layers and pinpoints the location of errors. It will also ease the testability of the web application due to the layered nature. 

The main issue with the redesign is **the complexity of the achitecture pattern**. Layered architecture pattern is complex because of the importance of each layer not being impacted by other layers. Not only that, the performance is low. The web application must go through multiple layers of the architecture to fulfill a request. 

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.
![Layered Architecture Diagram](images/Layered_Architecture.png)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

**Answer:**
Changes are needed because of the slow processing speed of the current MVC model due to large volume of data. To combat this, I would suggest implementing the **microservice architecture pattern**. With this, the structure of the web application will be broken down even more into distinct service components, causing development and deployment of services to be easier as we do not need to modify the whole application. The benefits of implementing the microservice pattern is due to its scalability. We will able scale up or down for certain services and pinpoint and maintain services that have network traffic. Thus, we are able to work with the large volume of data. Not only that, if one of the service components fails, we can use another service component and the application will continue to run. The drawback with this architecture pattern is **the communication between services is complex** because of the broken-down nature. Additionally, we need to create and maintain multiple databases for the many services. 

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.