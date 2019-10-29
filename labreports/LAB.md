# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Drew Feldman
GitHub: [Drew Feldman](https://github.com/DrewRFeldman)
(if appropriate) Collaborators: [I worked with Reagan Lyle with the first few steps of this project, then I did the rest on my own.]


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
| Title: School assignment | |
| Description / Steps: Messiah College freshman Amelia Beckett is required to volunteer for 3 projects during her freshman year as part of a school project. She needs to find events, volunteer for them, and then report the results to her professor. | |
| Primary Actor: Amelia Beckett, Messiah Freshman | |
| Preconditions: Amelia needs to find and volunteer for 3 events. | |
| Postconditions: Through the Serve Central app, Amelia was able to find projects to volunteer for. She volunteered, put the time in, and reported back to her professor, completing her assignment. | |

| Use Case #2 | |
|---|---|
| Title: Work Release | |
| Description / Steps: Dynamite Dave got in a lot of trouble for blowing up the toilet in his jail cell. As a result, he is being required to volunteer for construction projects as a form of punishment in an effort to teach him that creation is a better way to use your time than destruction. He is required to do 100 hours of community service on volunteer construction projects. | |
| Primary Actor: Dynamite Dave | |
| Preconditions: Dynamite Dave needs to find volunteer construction tasks to meet his sentence for toilet desecration. This includes 100 hours of volunteer experience, specifically in construction. | |
| Postconditions: Dave was able to find events through the serve central app. This was easy because he filtered the events to show only volunteer opportunities that involved construction. He volunteered for a grand total of one hundred hours, and most importantly learned that it is better to build things than to break them. Good for Dave. | |

2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| The model here needs to store login credentials for users wishing to access the application. A single entry in this data table could include username, password, email, and full name. | Login/Signup screen: A simple screen that allows users to sign up or submit signin details in order to access the app. | The view calls the controller which checks information entered against information stored in the database. |
| This model gathers and displays general information about event types, such as the title of the event, the type of volunteer work (construction, feeding poor, landscaping), the dates and times that need filled, and the number of volunteers who have signed up. | Event Listing Page: This page is a sortable/filterable table of events that users can click through to find events that interest them. | The controller queries the database and returns a list of events that the event listing page view can display in an easily navigable table. |
| The model holds all the information specific to this event, such as location, project specifics, requirements to volunteer, point of contact, etc. Anything the user may need in order to get involved. | Specific Event Page: Once you find an event you are interested in, you can click it in the event listing page to navigate to the page for that specific event. This page will include more detailed information about the event and a call to action that allows you to sign up for that event. | The controller returns all the information stored about that specific event in a way that the view is able to render it for the user. |
| On this page, the model holds the data regarding past events the user has been involved in. Work categories, hours, locations, etc could all be stored in order to better provide the users with information regarding their volunteer history. | Volunteer History Page: This page gathers all the events that the user has volunteered for in the past and displays charts based on those events. This could include total volunteer time and time by volunteer category. | The controller returns a record of all events the user has previously volunteered for. |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

Here is my [embed](https://docs.google.com/document/d/1aKoTaFkicKXW-AZre2hjOuD5HYyxu9ov8vi-r58MsQM/edit?usp=sharing).

Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilities of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

   1. ​	I believe a good architecture for this specific business issue would be the layer architecture. At it's lowest level you would have the database layer that stores all the events and histories of the users. On top of that, you could have a series of business layers that are specific to the four main volunteer entities that Serve Central will be incorporating. These layers could each have an API that allows the volunteer entity to enter events into the database from their website. On top of these layers there would be a presentation layer which the users would access to view the events those entities were posting. 

      ​	The benefit of this software is the APIs for each entity could be tailored to that entity. They could request a standalone program, a web form, or even a mobile application that could integrate with the other layers of the architecture. Their interface could be exactly what helped them best. 

      ​	A downside to this is that the program would require a lot more management by the developers to get it running and to continue its proper function. You aren't just creating an application, you're also creating four separate APIs to cater to these large volunteer entities.

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

   Here is my [embed](https://docs.google.com/document/d/1aKoTaFkicKXW-AZre2hjOuD5HYyxu9ov8vi-r58MsQM/edit?usp=sharing).

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What architectural pattern(s) will you employ to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

Because of the scale that this application has ramped to, I believe the best architecture moving forward is a microservice implementing the previous layered architecture to allow quicker connectivity to the database and responsiveness across all aspects. On top of this, there will be a client-server system where the mobile application will be a client and the microservice architecture will control connectivity with the stored data. This new architecture will allow all of these needs to be met at lightning speeds, increasing responsiveness in the new App. 

Although this is a big change from the previous system, these changes are necessary because the previous layered architecture isn't enough to remain quickly responsive as the database grows and becomes more complicated. The microservice system will be scalable as the project grows to continue fast responsivity as size increases.

The consequence is that this project will be expensive to develop as it is significantly more involved than any architecture previously used for the system.  

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.