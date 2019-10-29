
# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2019
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Nathan Chan
GitHub: [nathanczh](https://github.com/nathanczh)


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
| Title | Volunteer signing up for event |
| Description / Steps | 1. Volunteer clicks / taps "sign up" button <br> 2. Event organizer is notified of volunteer registration |
| Primary Actor | Volunteer |
| Preconditions | 1. Volunteer has account in Serve Central <br> 2. Event is open for volunteer signup |
| Postconditions | Registration is recorded in system for both volunteer and organizer to see |

| Use Case #2 |  |
|---|---|
| Title | Organizer creating an event |
| Description / Steps | 1. Organizer navigates to event creation page <br> 2. Organizer fills in required information for event <br> 3. Organizer clicks the "Publish" button to persist data and publish to event lists|
| Primary Actor | Organizer |
| Preconditions | 1. Organizer has a verified account |
| Postconditions | 1. Event data persisted to database 2. Event data displayed on event listings |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| EventModel | EventListView | EventCreateController |
| VolunteerAccountModel | EventCreateView | EventRegistrationController |
| OrganizerAccountModel | EventRegistrationView | OrganizerNotificationController |
| EventRegistrationModel | VolunteerAccountCreationView | AccountCreationController |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

![enter image description here](https://docs.google.com/drawings/d/e/2PACX-1vR06_1E1pyH7ozLKyTls7pm45FKEQ2O6Pkk6QFHyMndbg-ST3YQYXcCivADk4tkgTga7HhVoR4rg8Sj/pub?w=1320&h=454)

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:

3. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilities of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

We would want a client-server based system with a load balancer giving it some of the characteristics of a broker architecture. This will allow API calls to be responded to quickly, by caching and performing all business logic on a cluster of load-balanced servers, and only persisting / reading from a database server cluster when necessary.

The client application itself should be written as a client side layer-based MVC application. By having an additional caching layer on the client application, we can ensure that calls to the server are only made when necessary, increasing the speed of the application and decreasing the load on the servers.

The multiple layers of caching might, however, cause some delays in data persistence and retrieval, potentially causing data inconsistency. These could be mitigated by validation at multiple points, but handling things when it goes wrong might get complicated.

4. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

![enter image description here](https://docs.google.com/drawings/d/e/2PACX-1vRsxV6DnJGwKKnCarS7Khvz0Gvu6Z-hAKsg6U6jDr320ytb6npO7leYQwVnFTPbPT2gK-vNJn605mZI/pub?w=585&h=591)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What architectural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

Beyond potentially increase the cluster sizes, there should be no changes necessary in order to support such an interface. This scalable architecture means that little startup cost is necessary.

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.
