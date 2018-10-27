# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018<br/>
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)<br/>
Name: Andrew Douglass<br/>
GitHub: [douglassjohnandrew](https://github.com/douglassjohnandrew)<br/>
Collaborators: None


# Step 0: Reviewing Architectural Patterns
See the [lecture / discussion](https://docs.google.com/presentation/d/1nUcy63FWPFYO3OJmERJpMjEtdaFtaIBbuUkpmNRVRas/edit#slide=id.g45345bd5ea_0_136) from CIS 411. You'll need to be familiar with the content from this lecture to complete this assignment.

Note: you are free to work with classmates on this assignment. _Good architecture is born out of collaboration - not reclusive mad-scientist behavior._ However, if you work with colleagues:

1. You must specifically note your collaborators by name at the top of your report.
2. You may not completely copy each others work (diagrams and descriptions, even if your solutions are identical).

# Step 1: MVC Architecture
Review the proposals for the Serve Central project. Let's imagine that the project has been granted (relatively) unlimited resources if they can deliver a version 1 release in 120 days. As a result, the team decides to implement an MVC architecture for its version 1 release, delivering functionality through a [responsive web application](https://en.wikipedia.org/wiki/Responsive_web_design). 

Based on [this](https://docs.google.com/presentation/d/1UnU0xU0wF1l8pAB8trtLpdM0yuskx66jTFJzd64nsjU/edit#slide=id.g439b9c6866_2_53) and [this](https://docs.google.com/presentation/d/1-VZfAFoBVr6ijNepKAtRA7JoAQsV2Jlbf2l1WPDMhI0/edit) presentation:

1) Document two use cases of your choosing:<br/>
2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project:<br/><br/>

Both the 2 use cases and the table are in this [spreadsheet](https://docs.google.com/spreadsheets/d/1wJGX0KvONKKr31ELXoccJqDb_Ce_XQcLfyW1UQiJGx4/edit?usp=sharing)<br/><br/>

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

The diagram can be found [here](https://docs.google.com/drawings/d/1Nv9ZRuDwvTA9LeLYFbo0K0rlJPx-HFwy50KNTDmHeB0/edit?usp=sharing)

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

One possible architecture is the client-server architecture. This architecture seems to match ServeCentral's situation quite well because ServeCentral would function as the server and the four volunteer entities would be the clients. The 4 main volunteer organizations in the U.S. do not tend to collaborate with one another, so they can use ServeCentral's volunteering services independently of one another. Particularly, each of the 4 entities can input / retrieve data and build organization-specific interfaces at their own discretion.<br/>
The major potential issue ServeCentral would face is that if ServeCentral fails temporarily, every entity connected to ServeCentral would have to wait for ServeCentral to get back up and running. It is possible that ServeCentral could have a back-up server to prevent this from happening, but backup servers come at an extra cost, and the constant data flow from entities to ServeCentral would get costly rather quickly.

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

The diagram can be found [here](https://docs.google.com/drawings/d/17dGeHN6OFnmD4pSWDZXkSco1dfAzhgnS2ZAtO6GfCw8/edit?usp=sharing)


# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers:

1. 10K opportunities and < 15 sec latency: Using an [event-driven architecture](https://docs.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven) would work well for this need. If an event is defined as adding a listing, then an Event Creation would be an organization creating a new listing, an Event Manager would be the set of internal processes the data goes through for the listing data to be delivered, and the Event Consumers (who receive events) could be the database to store the data, or the website to be updated and show the new listing. According to Microsoft (the link I gave), event-driven architecture is a low-latency / high volume & velocity oriented architecture.
2. 50TB of data: A [big data architecture](https://docs.microsoft.com/en-us/azure/architecture/guide/architecture-styles/big-data) is required to properly work with data sets as large as 50TB. While costly, it is necessary for ServeCentral to employ this architecture to satisfy this future need (and #3). Managing big data effectively can benefit ServeCentral many ways, including the ability for researchers to analyze the data (#4)
3. Queries to traverse TB's: Combining the big data architecture from #2 with a client-server component can allow authorized parties to find the information they need, similar to Step 2. Giving each client (e.g. the 4 entities in Step 2) access to a centralized data lake allows them to query effectively. However, the difficulty would come with differentiating the data between clients (e.g. United Way shouldn't be able to access Red Cross information, and vice versa).
4. Researchers to examine patterns: A broker architecture would work well for this scenario, because when the client sends a request, the broker can determine the best way to address the problem. Accessing the necessary algorithms, data stores, and the servers that the big data architecture has, the broker can return the solution the client needs.<br/><br/>

Organizations need to consider different architectures as organizations grow and change because new needs arise, such as the 4 needs given, and organizations need to be able to handle these needs effectively. Different needs have different requirements, and there is no perfect solution to any architectural problem, so considering these architectural changes is necessary for any tech company to grow.

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.

