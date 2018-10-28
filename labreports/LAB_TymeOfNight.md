# Lab Report for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Justin Kim
GitHub: [TymeOfNight](https://github.com/TymeOfNight)
(if appropriate) Collaborators: [Names of colleagues you worked with on this assignment]

# Step 1: MVC Architecture
Review the proposals for the Serve Central project. Let's imagine that the project has been granted (relatively) unlimited resources if they can deliver a version 1 release in 120 days. As a result, the team decides to implement an MVC architecture for its version 1 release, delivering functionality through a [responsive web application](https://en.wikipedia.org/wiki/Responsive_web_design). 

Based on the [this](https://docs.google.com/presentation/d/1UnU0xU0wF1l8pAB8trtLpdM0yuskx66jTFJzd64nsjU/edit#slide=id.g439b9c6866_2_53) and [this](https://docs.google.com/presentation/d/1-VZfAFoBVr6ijNepKAtRA7JoAQsV2Jlbf2l1WPDMhI0/edit) presentation:

1) Document two use cases of your choosing

| Use Case #1 | User registers for an event |
|---|---|
| Title | Event Sign-up |
| Description / Steps | The user will select one of the listed events on the map screen they wish to attend.  The event description will notify them of any outstanding documentation they need to register in the app, or that they need to bring to the event site.  If all conditions are met, the user can complete their registration. |
| Primary Actor | User |
| Preconditions | User must have created an account. |
| Postconditions | The application must report the successful registration to the hosting organization, and inform the user that their registration has been submitted. |

| Use Case #2 | Organization Registers an Event |
|---|---|
| Title | Event Creation |
| Description / Steps | A client organization will create an event, specifying a location, description, maximum number of volunteers, and volunteer requirements. |
| Primary Actor | Organization |
| Preconditions | The organization must have subscribed to our service, and must have registered an Organization Account. |
| Postconditions | None. |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Map Model | Map View | Map Controller, Registration Controller |
| User Model / Organization Model | Account View | User Update Controller / Organization Update Controller |
| Calendar Model | Calendar View | Calendar Controller |
| Event Model | Event Details View | Event Update Controller |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.) 
![Event Registration Process][image1]

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Third-party services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either those presented in class or those based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as at least one potential issue / adverse consequence** of your choice.

    - The system could work really well designed as a so-called "GraphQL" application, or something similar.  The back end of the application would be accessible through a queryable API, which would serve front-end controllers and views, the mobile app, and any third-party services that wanted to read from/write to the back-end databases.  It would create a back-end that is easy to maintain and update, since all the back-end code would do the same things and serve the same data.
    Unfortunately, this also means that we might run into incompatibilities with existing organisations' processes.  The API would necessitate that users adapt to our system, and not all groups might have the resources to easily do that.

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

![GraphQL Flow Scheme][image2]

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

- We will need to scale the system, to ensure that these new needs can be met.  We will need multiple servers to host multiple API endpoints, and these servers will have to be behind a broker system. There needs to be a different system of brokered servers in each major region, and they should access a regional datastore (duplicated at two locations for redundency).  This will insure minimal latency for clients connecting to the service, and for events to be registered and visible to inhabitants of the system's assigned region.  

- There should be an internal service responsible for collating the data from these regions into a central datastore, which will be the data authority.  The service should independently query regions during observed low-activity time periods, so as to not interfere with a local system's primary functionality.  The system will use the data provided by the local system to update the master datastore.  Additionally, there should be a service to anonymize and collate data from the central database into various records and reports, for the use of grant investigators and other business members.  The system should be a limited-access system, available to grant investigators and others who have an established need to work with the data.

- This design will help to keep local systems small enough to be relatively small, making them easier to install and maintain.  At the same time, it prevents such a system from having hundreds of duplicates of the same gigantic amount of data.  If for some reason data is lost, the central data authority/regional backup can help to replenish it.  

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).

![Final Structure][image3]

[image1]: https://github.com/TymeOfNight/cis411_lab1/blob/master/images/image1.PNG
[image2]: https://github.com/TymeOfNight/cis411_lab1/blob/master/images/image2.PNG
[image3]: https://github.com/TymeOfNight/cis411_lab1/blob/master/images/image3.PNG