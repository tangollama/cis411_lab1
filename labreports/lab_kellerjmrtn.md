# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Keller Martin
GitHub: [kellerjmrtn](https://github.com/kellerjmrtn)
Collaborators: none


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
| Title | Potential Volunteer |
| Description / Steps | Potential volunteer creates user account. They are presented with a list of possible volunteer opportunities. Opening one provides more information like time/location/instructions and contact info. User can sign up for volunteer event. |
| Primary Actor | Potential Volunteer |
| Preconditions | User must download app/visit website. Location services required. Volunteer opportunities must have already been input into the system. |
| Postconditions | Organization receiving volunteer must be notified. |

| Use Case #2 | |
|---|---|
| Title | Volunteer Organization |
| Description / Steps | Volunteer Organization creates organization account. They are allowed to add/edit/delete volunteer opportunities they offer. They may also view volunteers who have signed up for their events and contact them. |
| Primary Actor | Member of Volunteer Organization |
| Preconditions | Volunteer Organization must have an event they want people to come to. They must download the app/visit website. Location services are required. Ideally, there is already a set of users which they hope to see their posting. |
| Postconditions | Potential volunteers may be notified of new opportunities. Organizations are notified when a potential volunteer signs up. |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| User Model - stores user info & interactions | Profile View - Users and Organizations can view their profile and important data | Load/Reload Controller - upon loading the app or performing a manual reload, this controller calls upon the decision model to obtain the information required to display the list/map views. |
| Organization Model - stores organization info & interactions | List View - Users can view a list of possible volunteer opportunities | Link Controller - When a volunteer hits the 'sign up' button, this controller calls upon the communication model to perform the sign up logic. |
| Communication Model - governs the relationship between Users and Organizations. For example, the controller may request that a user signs up for a specific volunteer oportunity. The communication model governs how this is done.  | Map View - Volunteer opportunities overlayed on a map by location | History Controller - This controller ensures that whenever a transaction is input, its history is properly recorded by User and Organization Models. It can also work backwards, loading history for the history view. |
| Decision Model - This model can make decisions/recommendations based on user/organization history or other factors. For example, it may choose to rank closer opportunities higher in the list. | History View - Users and Organizations can see their history. | External Data Controller - This controller is used to communicate with external data sources and API's, like Google Maps for the map view. |

3) Generate and embed at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.). [Diagram Here](https://docs.google.com/presentation/d/15s_uJnM71f1ImCkJoGLDrAEajSFZGzJhAqt1X6x7HPQ/edit?usp=sharing) 

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

**Answers:**
1. Especially in the context that the app has already been developed with the MVC architecture and is already in production use, I think it would make sense to stick with an MVC architecture. This will keep costs low, as a complete redesign won't be necessary. However, for the integration of external data sources like connecting to United Way or embedding registration services in other sites, an API based model should be implemented (either GraphQL or REST). In my experience, this allows for the most flexible and controlled integration with other services. For example, if Serve Central wanted to embed a registration service into a church website, they could expose a registration API, that when given a volunteer's sign up information, automatically creates or logs in that user, and signs them up for that specific volunteer event. This has a few advantages. 1) Serve Central only needs to receive some simple json data about the user, and can then do all of the sign up logic in-house. This provides very little security threat and full control over the sign up process. 2) Defining an API creates a very clear interface that any church could implement. It is very 'plug and playable'. 3) Since the only data being exchanged between Serve Central and the church is some json text, the church can create any sort of form or input on their end. The church might be able to draw data automatically from their directory if they want, or they could style the registration form to best fit their website as they see fit. As long as the data ends up going to the API, *anything* is possible. One drawback to the MVC model is that the Models, Views, and Controllers are all so tightly interconnected. In the future, our Models may become outdated. However, it may not be possible to modernize our Models without having to rewrite the Controllers that interface with it. Or, adding another mode of access, like a separate iPad app or desktop website, might not be possible using the views currently implemented.

2. [Diagram Here.](https://docs.google.com/presentation/d/1AGlDLZ-Sh2qoi4Sba2-fqXH5M1lMbwEropfC3dB_PXM/edit?usp=sharinghttps://docs.google.com/presentation/d/1AGlDLZ-Sh2qoi4Sba2-fqXH5M1lMbwEropfC3dB_PXM/edit?usp=sharing) As I continued thinking about how this would work and updating my diagram accordingly, my model became almost a hybrid of MVC and Layered Architecture. I think I subconciously began to bring in concepts from a Layered Architecture to solve some of the issues with scaling/new functionality that I talked about earlier. Instead of the [mostly circular](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller#/media/File:MVC-Process.svg) approach of pure MVC, my diagram depicts a sort of layered approach. The GUI layer may register a button click, where the controller processes the request and causes the model to perform some logic. The Model then returns its data back up to the view. It may also return its data back to a controller if necessary; this could occur if the original request wants to combine data from the model with outside data. The controller could fetch data from the Model, but also get map data from a Google API before sending this information to the view. The view would then update the GUI layer. This model seems to follow a "Frontend --> Backend --> Database --> Backend --> Frontend" sort of flow.

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

**Answers:**
1. To deal with heavy server loads, we will use a Load Balancer Architecture. Ideally, we would something like AWS to host our application so that more resources may be dynamically allocated to our server programs during peak/burst times. A master/slave architecture could be considered, but the latency may become an issue. Would it really be possible/feasible to update each MySQL slave with current data every 15 seconds?

2. Using AWS, as mentioned above, would cover this. As far as the code on our side, the MVC approach would still work for incredibly large amounts of data, so long as our Models are well compartmentalized (quick searching for necessary data) and seldomly repetitive (keeps data size low).

3. Our API approach from Step 2 is already perfectly suited to perform this. Nice!

4. The API approach could also be used for this. Custom APIs could be developed for external users to query the Communication/User/Organization Models for relevant data

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.

**Answers:**
1. [Full Diagram.](https://docs.google.com/presentation/d/1USVDcMdsEFmd6vnbl1K9xLd9wir9P7csMWL_eD4ChKc/edit?usp=sharing) Note: API requests could be routed through the load balancer if that would be deemed necessary.

2. Though I liked how open ended it was nearer the end, the beginning was a bit too open. I didn't really know how to start the lab. I figured out the Use Cases pretty easily, but it took me a *while* to figure out what was supposed to go into the MVC chart on Step 2, and even then I'm not sure if I did it correctly. Step 2's instructions really just should've been a little more clear. Maybe a quick link to an example MVC Architecture for reference? Also, an easier way to submit Images/Graphics/Diagrams with the lab. I JUST DISCOVERED THAT DOING THIS WORKS:

> \[Link to Diagram1](./Diagram1.PNG) ---> [Link to Diagram1](./Diagram1.PNG)

Maybe make this the default format for submitting photos, not uploading them onto the internet somewhere