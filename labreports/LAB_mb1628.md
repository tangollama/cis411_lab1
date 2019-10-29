# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018</br>
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)</br>
Name: Matthew Bromley</br>
GitHub: [mb1628](https://github.com/mb1628)</br>
Following: [MUEsic](https://github.com/SamMahan/MUSEsic)</br>

Collaborators:</br>
Kerlin</br>
Collette</br>
Houck</br>
Coldsmith</br>

# Step 1: MVC Architecture
Review the proposals for the Serve Central project. Let's imagine that the project has been granted (relatively) unlimited resources if they can deliver a version 1 release in 120 days. As a result, the team decides to implement an MVC architecture for its version 1 release, delivering functionality through a [responsive web application](https://en.wikipedia.org/wiki/Responsive_web_design). 

Based on the [this](https://docs.google.com/presentation/d/1UnU0xU0wF1l8pAB8trtLpdM0yuskx66jTFJzd64nsjU/edit#slide=id.g439b9c6866_2_53) and [this](https://docs.google.com/presentation/d/1-VZfAFoBVr6ijNepKAtRA7JoAQsV2Jlbf2l1WPDMhI0/edit) presentation:

1) Document two use cases of your choosing

| Use Case #1 | |
|---|---|
| Title | Signing Up for an Event as a Volunteer|
| Description / Steps | 1) A volunteer must browes the app and choose a registered event.</br> 2) After an event is chosen the volunteer must register for said event through the apps registration process.|
| Primary Actor | Volunteer |
| Preconditions | A user wishing to volunteer must have an account before registering for an event. |
| Postconditions | The user will have an updated list of events they are registerd for. Each item in the list will contain specific information on the event. |

| Use Case #2 | |
|---|---|
| Title | Creating an Event as an Organiation|
| Description / Steps | 1) Event creator must brows to the event registration portion of the app.</br> 2) Event creator must then enter all required information about the event into the provided feilds. (Location, time, etc...)</br> 3) The event creator will then submit the completed form to create the event.|
| Primary Actor | Organization wishing to host an event|
| Preconditions | Organization must be registerd and approved by ServeCentral.|
| Postconditions | The organization will now have a live even that is accessible to volunteers for registration.|



| Model         | Controller                            | View                            |
|---------------|---------------------------------------|---------------------------------|
| Volunteers    | Register for Event                    | Event Screen                    |
| Organizations | Register an Event                     | Create Event Screen             |
| Events        | Browse Events                        | Map with Pins/Event List Screen |
| Users         | Register as Volunteer or Organization | Profile Creation Screen         |


![MVC Diagram of a volunteer registering for an event](https://github.com/mb1628/cis411_lab1/Diagrams/MVC Diagram.png "MVC Diagram")
3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

# Feedback