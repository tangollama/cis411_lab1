# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: YOUR NAME
GitHub: [tran1996](https://github.com/tran1996)


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
| Title |Searching Events by Location|
| Description / Steps |The volunteer will use the app to search for service events based on the location chosen. 
                       -System displays homepage
                       -Volunteer select search  button
                       -System browse search events page
                       -Volunteer enters location
                       -System sends location to database
                       -System retrieves information
                       -System displays search results|
| Primary Actor |Volunteer, System, Database|
| Preconditions |The volunteer has an account, the volunteer is logged in |
| Postconditions |Events in the area will be displayed on a map using tags
                  -Evens in the area will be displayed in listing format|

| Use Case #2 | |
|---|---|
| Title |View Previous Attended Events|
| Description / Steps |The volunteer will use the app to view all events they volunteered for previously
                       -Volunteer goes to their profile page
                       -System retrieves their file from the database
                       -System displays profile page
                       -Volunteer clicks on the 'History' button in their profile page
                       -System goes to the database and pull their data of events they attended
                       -System will display the information of events they attended|
| Primary Actor |Volunteer |
| Preconditions |The volunteer has an accound, the volunteer is logged in |
| Postconditions |The volunteer will be able to see all their previous events|


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model                        	| View               	| Controller         	|
|------------------------------	|--------------------	|--------------------	|
| Login credentials            	| Login button       	| Login user         	|
| Service events details       	| Search engine      	| Update events map  	|
| Update view with new changes 	| View events w/map  	| Update events list 	|
| User profile data            	| View events w/list 	| Select event       	|

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)



# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. Microservice is one architecture I would recommend to allow these requirements. Microservices has many benefits for agile development as it is very modular. It starts off as building an application that allows for small services and once it has developed, these services can be deployed independently of one another and recombine on all layers of the architecture. It is easy to integrate with automatic deployment and, in this case, once the application has been built, thirdparty services can input and retrieve their data without affecting one another. Even if a thirdparty company were to make a mistake somewhere in the coding and the microservice fails, it would not affect the others. This architecture style would also allow for building organization-specific interfaces, such as embedding Serve Central to be embedded on the website of local churches. This architecture is easy to scale and integrate with third-party services. Software built with microservices can be broken down into multiple component services so that they can each be deployed, tweaked and redeployed independently without comprising the integrity of the application result. This architecture is easy to scale and integrate with third-party services. However, there are cons to this style as well as, with the increasing number of services, managing and integrating this application can become complicated. Not only that, developers have to make more of an effort in communicating between services. 
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.
Microservice architecture would be beneficial when dealing with these requirements, as it is useful for Agile development. As the number of people who work on and use the application grows, so does Microservices. This architecture is an evolutionary design and is ideal for growing systems where people cannot fully predict the device types that could eventually access this application. Microservice architecture will be able to support the first through third requirements as the data grows. Twitter, Amazon and Netflix are a few examples of companies that use microservices architecture, as they are accessed with different devices and growing members each day. However, as stated above, managing and integrating the application can become difficult as the number of services increases. This requires developers to put more effort into communicating between services along with dealing wtih the complexity of a distributed system. Nonetheless, these changes are needed to allow for the application to support the growing number of volunteers and services.
Blackboard architecture would be useful for the fourth requirement, as this style is useful for problems with no known solutions and storing raw data and calculated solutions. With Blackboard, several specialized subsystems assemble the knowledge to build a possibly partial or approximate solution. This would help with researchers in examining patterns of volunteer opportunities to determine future grants. While this architecture would benefit in searching for patterns, using this could lead to structural mutations in the pre-existing data which may introduce complex changes in management. 
# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.