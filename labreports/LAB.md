# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Luke Meads
GitHub: [lukemeads3](https://github.com/lukemeads3)
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
| Title |As a volunteer, I want to be aware of service activities near me that I can serve at|
| Description / Steps |
1| Login to user account
2| Search for nearby events 
3| sign up for events 
4| Log progress for hours served|
| Primary Actor |Volunteer|
| Preconditions |Events have to be logged into system, User must have an account to register for events|
| Postconditions |Confirmation email is sent to confirm of the date of the event and location|

| Use Case #2 | |
|---|---|
| Title |As an Organization, I want to be able to create an event where volunteers can sign up|
| Description / Steps |
1| Login to Organizational account
2| Create an event with a date and location|
| Primary Actor |Event Organizer |
| Preconditions |Organization must have an organization account, Event must already exsist outside of the app|
| Postconditions |Email alert when new volunteers sign up for the event|


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model(data/object) | View(a page) | Controller(action) |
|---|---|---|
| User | Profile Page | Edit Profile details |
| User | Registration page |Create new volunteer account|
| Organization event | Event Page | Edit event's location or time |
| User | Volunteer Map | sign up for an event|

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

[My Diagram](https://www.lucidchart.com/invitations/accept/49f88743-5d99-4650-97c5-696b89e2a9ff)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

The architectural pattern that would be appropriate for these changes is the [Client-Server](https://docs.google.com/presentation/d/1ffFm8bzBrIW2CtywJju77uehQolsN6H8ig90s_iBKfE/edit#slide=id.g45345bd5ea_0_128) architecture. This architecture is effective when the server interacts with the client in a rountinely manner. This will create a simple connection from the client trying to organize a volunteer-based events and the server processing the request. One potential issue with using this architecture is the reliability of the server to be able to process all the request that it is recieving. 

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

[My Diagram](https://www.lucidchart.com/invitations/accept/b87c5476-21a5-4409-9f7c-8c33dda47baa)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

To complete these four tasks, I will use a combination of two archictures, [Blackboard](https://docs.google.com/presentation/d/1ffFm8bzBrIW2CtywJju77uehQolsN6H8ig90s_iBKfE/edit#slide=id.g45345bd5ea_0_120) and [MVC](https://docs.google.com/presentation/d/1ffFm8bzBrIW2CtywJju77uehQolsN6H8ig90s_iBKfE/edit#slide=id.g45345bd5ea_0_0) architectures. The MVC model will help keep the project scaleable with its easy to adopt model and functional management advantages. The blackboard architecture will be used for having to sort through large data sets in a short time. We will use the blackboard architecture to allow authorized parties and researchers to query the database for future oppurtunities. These changes are needed to help combat all of the new users on the mobile application interface. We need to make the app fast and reliable for user so they keep returning to use the app.

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.