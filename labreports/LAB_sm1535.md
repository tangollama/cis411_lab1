# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Stephen Maloney
GitHub: [sm1535](https://github.com/YOUR_HANDLE)
(if appropriate) Collaborators: [Reagan Lyle]


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
| Title | Fullfilling Requirements |
| Description / Steps | Social Work students at Messiah are required to volunteer once during every academic year and have it be approved by advisor.  |
| Primary Actor | Messiah College Social Work Students. |
| Preconditions | Social Work students must sign up for an event. |
| Postconditions | By using the Central Service app, Social Work students easily found places to volunteer and show those events to their advisors for approval. |

| Use Case #2 | |
|---|---|
| Title | Job Internship |
| Description / Steps | Hunter Zacerous, currently serves at an internship at Carlisle Presbyterian Church. As a part of the internship, his boss has asked him to find events that the he could serve at and encourage individuals to attend Carlisle Presbyterian Church. |
| Primary Actor | Hunter Zacerous |
| Preconditions | Hunter must find service events that he could attend to fulfill his bosses wishes and further spread the gospel. |
| Postconditions | By using the Central Service app, Hunter was able to find 4 different locations to serve at and encourage those that were present to attend Carlisle Prebyterian Church. Ultimately spreading the good news. |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| This model must hold or store secure user credentials such as username, password, name, and email. | Login Screen - This is most likely an opening screen that requires users to enter in their credentials to give them access to the full app. | When the user request access, the controller will check the credentials in the current database. |
| This model displays a list of current events available to sign up for. It will contain the event name, date, and location. | List of Events Screen - Users will be able to scroll through a list of available events and click on the one they desire to attend. | The database is queried and returns all the events avaiable on the List of Events Screen. |
| This model contains more in depth information about the event that was clicked on. It will hold the name of the event, the type of service needed to be done, the location, date, and the time. | More Event Information Page - this page will display all the information the user needs in an informative list as well as a way to sign up for the event.  | The controller will query the database and return the event information that is listed in events_information table. |
| This model will contain your general profile information as well as your past service projects you have attended. | Profile Page - this page will contain a profile picture, your full name and email address. It also will show a cohesive list underneath of all past service events completed. | The controller will query the database for the user's profile information including picture, email, and name. It will also return any events asscoiated as being completed by that user to be displayed on the profile page.|

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

[embed](https://docs.google.com/drawings/d/1PIGJqMrJxqGUBm0nILEDwz0kn_SXazYZFGY_4u22CH0/edit?usp=sharing)

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice. 

I believe that the layer architectural pattern would be the best to use for the solution. It allows for the implementation of many specific properties that the app will be incorporating. The top most layer would, (presentation layer), would be that in which users would view events the entities would post.  The lowest level would obviously be your database layer that contains all queried information.

The great thing about this pattern is it allows for more autonomous improvements because of insular compenents. So scaling is much simpler.

A disadvantage to this pattern you must have dependency management. 

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

[embed](https://docs.google.com/drawings/d/1tbEkJg02s3nrHatAMEZqAG1PKhfKGbQmuqdGeRF7FFo/edit?usp=sharing)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

The biggest issue that will needed to be combated immediately is the drastic increase in data. Which can be very unforgiving. With such a massive growth, I believe that the architecturel needed here is blackboard. After doing much needed research on this pattern it appears to be a fantastic solution. Blackboard can handle an enormous amount of data and the datastores can work independently of each other. Along with this, it allows for the ability to add and update new knowledge sources whcih is essential. Another great use of blackboard is its ability to make new discoveries about data that is being poured in.

The major problem with this, is was the problem is defined, blackboard really is unnecessary. Of course it can still be utilized, but the need for it becomes less and less. In my eyes it was designed as a cheat to use until you fully defined the problem.

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.