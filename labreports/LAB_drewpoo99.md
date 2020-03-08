# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Spring 2020
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Drew Weaver
GitHub: [@drewpoo99](https://github.com/drewpoo99)
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
| Title | Volunteer Keeps Track of His Hours |
| Description / Steps | |
| 1.| The volunteer navigates to his profile |
| 2.| The profile page displays total hours volunteered and a break down of how they volunteered (org type)|
| Primary Actor | User -> Volunteer |
| Preconditions | |
| 1.| The user has an account |
| 2.| The user has volunteered at least one time for a duration of at least 1 hour | 
| Postconditions | |
| 1.| A report is generated on the profile page|

| Use Case #2 | |
|---|---|
| Title | Organization Adds New Event |
| Description / Steps | |
| 1. An organization wants to use this app to add a new event to the system |
| Primary Actor | Use -> Organization |
| Preconditions | |
| 1.| The organization is registered and logged into the system |
| 2.| The event does not already exist
| Postconditions | |
| 1.| The event is added to the map. |
| 2.| The event shows up for volunteer searches |
| 3.| Volunteers can register for the event |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Volunteer History | Profile Page | Load the user's volunteering history from the DB|
| Organization Event Listing | Dashboard | Load the organizations event listings from the DB|
| Event Information | Event Listing | Load the details of the listing from the DB|
| Map Events In Area | Mapbox View | Load and populate the map with event listings from the DB|

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

![MVC Diagram](https://github.com/drewpoo99/cis411_lab1/blob/master/assets/MVC%20Diagram.jpg)


# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.
    1. Microservice
        - Benefits:
            - Easy to scale and add more base features
            - Easy to create API services for embedding in external websites
        - Issues:
            - Can be overly complex for small applications
            - Communication between services becomes complex
    2. Broker
        - Benefits:
            - Allows for scalability
            - Allows for transparency to clients, offering easy API access
        - Issues:
            - May be too complex for a small application

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

![Microservice Diagram](https://github.com/drewpoo99/cis411_lab1/blob/master/assets/Microservices.jpg)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

* I would implement a microservices architecture for this change. I would create microservices to handle current features of the app, allowing them to be used across different platforms (web, native mobile). Microservices will be available to create API’s to allow for embedding in third party applications and for creating API’s to allow authorized apps to issue queries to access data for different uses such as research (3 and 4). We will be able to handle mass influxes of data by separating data ingestion into a separate microservice so it can run without the overhead of the rest of the app (1), and connecting them to data storage microservices for high-speed read and write queries (2). All of these microservices will allow for a highly scalable app that can accommodate large influxes of users and data creation. Keeping each microservice separate from each other but allowing for interconnectivity will allow for high performance during peak use periods as users will only need to utilize the services that are required for completing their current task, freeing resources for other users working on other tasks. The consequences of creating a microservice architecture is increased complexity. With the migration of MVC services to microservices and creation of new microservices, the application ecosystem will get considerably complex, however I believe the benefits will outweigh this consequence. 

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.