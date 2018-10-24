# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Garrett Reichert
GitHub: g-reichert(https://github.com/g-reichert)
(if appropriate) Collaborators: 

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
| Title | Volunteer can sign up and create an account |
| Description / Steps | Volunteer can click on "create an account" and enter an email and password to create an account that they can use. |
| Primary Actor | Volunteer |
| Preconditions | Volunteer does not have an account and has downloaded the app |
| Postconditions | Volunteer has an accesable account, and is now on the map view |

| Use Case #2 | |
|---|---|
| Title | Volunteer can sign up for an event |
| Description / Steps | While the volunteer is on the more info screen, there is a button for signing up. This button leads to a form that can be filled out, with a submit button |
| Primary Actor | Volunteer |
| Preconditions | The volunteer is on the more information screen. |
| Postconditions | The volunteer's filled out information will be uploaded into the database and the organization will be notified of a new volunteer.  |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Volunteer Class | Profile Page | Volunteer Profile Controller |
| Organization Class | Organization Informtional Page | Organization Controller |
| Event Class | Event information Page | Event Controller |
| Event's location and information | Map View | Map Controller |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

![alt text](https://github.com/g-reichert/cis411_lab1/blob/master/labreports/usecase.jpg "Step 1")

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

I would head towards a layered architectural pattern. This would probably allow for us to navigate to the layer we need depending on where we our gathering our information. Local churches could have a different presentation layer, while still accessing the same services layer. This would allow us to provide our services in multiple different locations and in different ways. It would allow third party services to access the database layer to retrieve information that they needed without jumping through unnesscary hoops.

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

![alt text](https://github.com/g-reichert/cis411_lab1/blob/master/labreports/Architetecute2.jpg "Picture 2")

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

I would move towards a Master-Slave architecture, and maybe try to use some of the influences of broker architecture to handle the amount of responses we would need to send out each second. The Master-Slave architecture should allow us to hand both number 2 and 3 efficiently. We should be able to have a database (or multiple) to hold the 50TB data, and then we can use the slaves to efficiently pass back that information to people who are navigating our datastores. If we can implement some sort of broker architecture as well, we should be able to take in all of the opportunities and passed the information back quickly, which should benefit 1 and 3. I am unsure how exactly this will be helpful in addressing number 4, but hopefully having a slave database that they can have access to and query when need be will help researches be able find patterns of volunteers. 
The primary concern that I would want to research before comitting to this is that the Master-Slave architecture can hold the information and pass it out with out creating to much latency and making the time requirement in step 1 impossible. 


# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.