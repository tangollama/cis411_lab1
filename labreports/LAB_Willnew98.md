
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)

Name: Will Newcomb

GitHub: Willnew98(https://github.com/Willnew98)

(if appropriate) Collaborators: Bryce Doane


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
| Title |As a user, I want to find volunteer work in my area|
| Description / Steps | This scenerio describes the user finding volunteer work in their area. The user logs in. The user puts in their location. The user The user finds work from the map. The user signs up for the event. The volunteer hours are recorded for the user.|
| Primary Actor |Registered User |
| Preconditions |The events are created and in the database.  |
| Postconditions | The user is signed up for the event. The attendee list is updated.|

| Use Case #2 | |
|---|---|
| Title | As an event coordinator, I want my event to show up on the app so people can sign up for it.|
| Description / Steps | This scenerio describes the event coordinator creating their event and having it added to the map for signup. The event coordinator is registered in the app. The event coordinator titles their event, adds a description, a maximum participant limit, time/date, and the location for the event.|
| Primary Actor | Event Coordinator|
| Preconditions | The event is scheduled|
| Postconditions | The event is added to the database and users can sign up for it.|


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
|Event  | Individual event page| Get event details |
|User | Volunteer profile page | Get profile information |
|Login |Login Page | Security Gateway |
|Roster | List of event attendees | Get attendees |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

![alt text](https://github.com/Willnew98/cis411_lab1/blob/master/labreports/Interaction%20Diagram.png)


# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.
- The best solution for these problems would seem to be a peer to peer architecture. Similar to GitHub, if thirdparty services want to imput and retrieve data, a peer to peer offers an architecture that distributes equal control to all nodes. All parties could pull and push their data for everyone else to recieve and make changes to if necessary. The downside to this, however, would be that there is no central point of data storage, so there is no one place to control the access of data.
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

![alt text](https://github.com/Willnew98/cis411_lab1/blob/master/labreports/Untitled%20Diagram.png)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

-The best architectural pattern for these needs would be a client server architecture. Knowing that storage will quickly exceed 50TB, we need a large computer, i.e. a server to manage that data. The benefits of a client server architecture is that all of the data is centralized, so it would be much easier for researchers to examine patterns in the data. The biggest consequence would be the occasional reliability issue, but I believe the benefits outweigh the cost. Changes are most definitely needed because a peer to peer architecture would not be able to sustain such large quantities of data, and it would make traversing through data so much harder since theres no central data storage. A client server architecture would also signifigantly improve any latency issues.

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.