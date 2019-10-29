# Lab Report Template for CIS411_Lab1

Course: Messiah College CIS 411, Fall 2018

Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)

Name: Ethan Wong

GitHub: [ethanwwm](https://github.com/ethanwwm)

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
| Title | Setting Up an Event On The App |
| Description / Steps | The organizer is able to add an event onto the organizations profile. Basic information such as a location, date of event, description, event title, cost of attending the event (if any), banner images and collaborating organizations should be provided when setting up this event. |
| Primary Actor | Service Event Organizer |
| Preconditions | The organizer has a chosen username and password which is used to then sign in to the app. The organizer also will be linked to an organization and has privileges to add/modify/delete an event. |
| Postconditions | At the end of the use case, the event and its details will be initialized onto the apps database. The event will be published onto the organizations page/site. |

  

| Use Case #2 | |
|---|---|
| Title | Signing Up For an Event |
| Description / Steps | The participant is able to view a list of all events in the area. Upon selecting an event, all details in relation to the event will be provided. The user will then be able to sign up instantly (in just a few clicks) for the event. |
| Primary Actor | Event Participant/App User |
| Preconditions | Participant has a chosen username and password which is used to then sign in to the app. Participant would also have provided all basic demographic information including their name, age, location, interests and payment information for quicker registration. |
| Postconditions | At the end of the use case, the event would be added onto the participants profile as an upcoming event. A confirmation email/receipt will be sent to the participants email. The link between the participant and this event will be initialized onto the apps database. |

  
  

2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

  

|  View | Controller | Model |
|---|---|---|
| User is on a login screen and enters login credentials, then clicks on the login button. **File(s): loginView.jsx** | Receives username and password and checks credentials. Controller sends login information (time, date, etc.) to the model for a log of all logins and if the login was successful or unsuccessful. **File(s): loginRequest.js** | Receives info from the controller and updates login log and updates the view based on whether the login was successful or unsuccessful. **File(s): loginLog.js**|
| Participant/user signs up for a new account on a "new user" form and fills all the required fields followed by clicking a "sign up" button. **File(s): signUp.jsx** | The controller receives information from the form and checks it against the current model for certain things. For example, if the username already exists, the controller will not modify the model yet and instead will directly modify the view to reflect that the username is already taken. If everything looks good, the controller sends all the information to the model. **File(s): createNewAccount.js** | Model stores data received from the controller to a database of users. **File(s): users.js**|
| Event organizer is on a "new event" form and fills all the required fields followed by clicking a "publish" button. **File(s): newEvent.jsx** | The controller receives information from the form and checks if all the required fields are filled in. If one or more required fields are not satisfied, the controller will directly modify the view to reflect the lack of completion. If everything looks good, the controller sends all the information to the model. **File(s): createNewEvent.js**| Model stores data received from the controller to a database of events linked to that specific organization. **File(s): events.js**|
| Participant/user registers to volunteer for a particular event on an event page. This event page shows information relating to the event. A "register" button is present. **File(s): eventPage.jsx** | When the "register" button is clicked, the controller directly manipulates the view and takes them through all the required steps to register for the event. Once all the steps are completed, the controller sends all the information to the model. **File(s): registerNewEvent.js**| Model receives data from the controller and updates two databases: The organizations database of registered volunteers and the participants database of registered events. **File(s): registeredEvents.js**|

  

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

![enter image description here](https://lh3.googleusercontent.com/WUK3BBq1I8nXGFT5GU1qZpCZD38LalJRnRmENpAlonYz0siPtiy9ivDeZ8HV6zRvPj4uDHdvdUX4uA "Interaction between participant &#40;actor&#41; and registering for an event")

  

# Step 2: Enhancing an Architecture

After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

  

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)

2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

  

To support these objectives:

1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.
- For this redesign, it would make more sense to adopt a **client-server architecture**. Ultimately, multiple clients will be using the same database. This will require a clarity of data authority and also a source of truth where a change in data is consistent across all clients using the same database. One disadvantage of this architecture would be **network congestion**. Unlike a peer-to-peer architecture that increases its bandwidth as the number of peers increase, a client-server architecture shares its bandwidth and can congest the network as more people start using this service. 

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

  ![](https://lh3.googleusercontent.com/helnE53GjEyGMilcaJI7JEkDtMKTp0BbXD69xcCK_JJCwvHLBEfcHDWC-jFjMotljtE_gmQ8luQcKw "Diagram of new ServeCentral architecture")

# Step 3: Scaling an Architecture

18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization.

  

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

  

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.

2. Supporting a volunteer and event data store that will quickly exceed 50TB of data

3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).

4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

  

What architectural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.
- In this case, these needs will require a more complex but flexible architecture. A microservices architecture would work much better as the structure is more broken down and more control/customization can be done. As demand for certain services go up and down, each individual service will also be able to scale up or down. This change is needed from the previous client-server architecture proposed as the sheer amount of traffic would cause the previous system to congest the network and severely slow it down. The caveat is that not all parts of this system will be easy to break down into smaller systems.

  

# Extra Credit

1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).

2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.