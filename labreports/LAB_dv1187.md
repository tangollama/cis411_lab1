# Donovan Varney Lab #1 Report
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name & GitHub: [Donovan Varney](https://github.com/dv1187)

# Step 1: MVC Architecture
Review the proposals for the Serve Central project. Let's imagine that the project has been granted (relatively) unlimited resources if they can deliver a version 1 release in 120 days. As a result, the team decides to implement an MVC architecture for its version 1 release, delivering functionality through a [responsive web application](https://en.wikipedia.org/wiki/Responsive_web_design). 

Based on the [this](https://docs.google.com/presentation/d/1UnU0xU0wF1l8pAB8trtLpdM0yuskx66jTFJzd64nsjU/edit#slide=id.g439b9c6866_2_53) and [this](https://docs.google.com/presentation/d/1-VZfAFoBVr6ijNepKAtRA7JoAQsV2Jlbf2l1WPDMhI0/edit) presentation:

1) Document two use cases of your choosing

| Use Case #1 | |
|---|---|
| Title: View Events in the Area | |
| Description / Steps: A user has decided that they want to volunteer in an event, so they will look for events being hosted in their area with an intent to volunteer at one of them. | |
| Primary Actor: Users | |
| Preconditions: The user has signed into a verified account, and there are searchable events in the database. | |
| Postconditions: The user can see a list of approved events that are available to have volunteers and can have the option to sign up for one or more of them. | |

| Use Case #2 | |
|---|---|
| Title: Add a new Event | |
| Description / Steps: A non-profit or business has decided that they need volunteers for an upcoming event, so they will add an event to ServeCentral with the intent of reaching out to potential volunteers. | |
| Primary Actor: Event Coordinators | |
| Preconditions: The event coordinator needs to have an account approved for creating volunteer events. | |
| Postconditions: An event is created and added to a database that users that are volunteers can see the event when they search for one. | |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| User login information (username, hashed password) | login page, login button | call login function, verify login |
| Event information (location, time, date) | event information page, signup button, contact button | signup function, contact event coordinator function |
| Change password (username, old password, new password, email address) | change password page, change password confirm button, cancel button | verify old password function, update database function |
| Create event information (location, company, time, date, number of volunteers needed) | add event form, confirm button, cancel button, edit button | create event function |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

![View Chart Here](https://github.com/dv1187/cis411_lab1/blob/master/Use%20Case%20with%20MVC.png)

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

`I think adjusting to a microservice architecture would be beneficial to the project at this point. This would allow for things like apis and additional services to be taken from the project for third party sites, and still use those apis for the main service. However, this split of service levels could cause problems when separated, and it might be hard to distinguish what the api would need separate from what it wouldn't.`

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

![Updated Chart](https://github.com/dv1187/cis411_lab1/blob/master/Second%20Diagram.png)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employ to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

`For this adjustment, it is incredibly important to have the ability to detect mobile use as well as quick load times. For these two reasons alone, I would like to use a broker architecture pattern. This will split the workloads amongst several servers which is necessary with the growth of user base as well as the needs to have everything done quickly. Breaking up the workload allows work to be diverted through servers with less of a load already on them and improve response time. The only problem would be trying to figure out which servers are experiencing more load than others, and designing a complex broker to manage all of the distribution for such a large project. The main reason changes were needed was because of the large influx in user base and the need to have processes done quickly and effectively. You could also combine some of the microservice features for ease of getting reports for how much each individual service is used and how long response times are.`
