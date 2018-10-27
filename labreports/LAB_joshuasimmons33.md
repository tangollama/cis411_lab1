# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Joshua Simmons
GitHub: joshuasimmons33](https://github.com/joshuasimmons33)
(if appropriate) Collaborators: [Nik Sloop]


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
| Title | Select an Event |
| Description / Steps | 1. User selects a pin on the interactive map screen 2. The event information screen displays relevant information about the event, and also contains a sign up button. |
| Primary Actor | User |
| Preconditions | User has an account and is on the map page, and can see pins for volunteer events. |
| Postconditions | User sees an event information screen, with details about the event; user can see a sign-up button to volunteer for a specific event. |

| Use Case #2 | |
|---|---|
| Title | Make an Account |
| Description / Steps | 1. User locates the 'create account' button 2. Pressing the button prompts the user to enter an email address and a password. 3. The user clicks submit to enter their information |
| Primary Actor | User |
| Preconditions | User does not have an account |
| Postconditions | User has an account; account information stored in the database of user data; user has access to profile page; user can now see the map of nearby events; User also has access to the events page and can view upcoming events in a list format. |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Registered Volunteer class | Current Volunteers Page | Registered Volunteer Controller |
| Event class | Event Information Page | Event Controller |
| Organization class | Organization Page | Organization Controller |
| User class | Profile Page | Profile Controller |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

![alt text](https://github.com/joshuasimmons33/cis411_lab1/blob/master/labreports/UseCase.jpg "Use Case")
_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recruitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Third-party services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilities of your chosen architecture(s) **as well as at least one potential issue / adverse consequence** of your choice.

I think the layered model is the best option, since it allows other businesses to access certain layers of the ServeCentral data. For example, if a website only wanted to access the data that ServeCentral had on upcoming events, they could bypass the business and presentation layers and go right to the database layer through an API that is developed specifically for that purpose. Also, since it will be used by several different organizations, then the ability to use different technology choices is important. This however would prevent continuous deployment of updates, as things built with the outdated APIs would no longer function properly; you would need scheduled and announced updates to prevent this.

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.
![alt text](https://github.com/joshuasimmons33/cis411_lab1/blob/master/labreports/LayeredArch.jpg "New Architecture")

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization.

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What architectural pattern(s) will you employ to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

I think the best solution to these problems would be the blackboard architecture, primarily because of its ability to handle large amounts of multi-faceted data, which this problem calls for. Also, the broker functionality would allow for fast queries of the data, as opposed to a single layer that would slow down this process. For issue 4, the blackboard architecture is supportive of both raw and calculated data, meaning that analysis could be done on the data that is retrieved through the system. This would have to be changed from the layer architecture, since the large data needs would make the database layer more imbalanced, and the large increase in use and stress on the system might prove too much for it to handle; therefore, you'd need an architecture that is able to support a large amount of use.  

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.
