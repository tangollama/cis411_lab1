# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Caleb Weaver
GitHub: [cweaver136](https://github.com/cweaver136)
(if appropriate) Collaborators: [Names of colleagues you worked with on this assignment]


# Step 0: Reviewing Architectural Patterns
See the [lecture / discussion](https://docs.google.com/presentation/d/1nUcy63FWPFYO3OJmERJpMjEtdaFtaIBbuUkpmNRVRas/edit#slide=id.g45345bd5ea_0_136) from CIS 411. You'll need to be familiar with the content from this lecture to complete this assignment.

# Step 1: MVC Architecture

1) Document two use cases of your choosing

| Use Case #1 | |
|---|---|
| Title | ServeCentral SignUp |
| Description / Steps | A regsitered ServerCentral user can sign up for an event |
| Primary Actor | Individual Looking to Serve |
| Preconditions | User must have an account and an event must be created |
| Postconditions | User is signed up for an event |

| Use Case #2 | |
|---|---|
| Title | ServeCentral Sponser Created Events |
| Description / Steps | A ServerCentral sponser can create and list an event |
| Primary Actor | Individual looking to sponser an event |
| Preconditions | User must have a sponser level account |
| Postconditions | An event is listed for users to sign up for |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Database Update | Event Signup Page | Signup Button Pressed                  |
| Database Update | User Registration | Registration Button Pressed            |
| Database Query  | Find Events       | Search query entered and searched for  |
| Database Query  | User Profile Page | When user logs in, fire database query |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

[Diagram](https://drive.google.com/file/d/1sBFZCq0KhbL6-93iQy9kLfruDjqD2n8s/view?usp=sharing)

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

I belive that the microservice architecture would work well for this new architecture. This application can be broken up into multiple different pieces software that will be able to function indendently. One piece can be the main app, another piece can be the API implementation for 3rd party services to obtain data, whereas another could be the API implementation to allow for users to register online on other websites.

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

[Diagram](https://drive.google.com/file/d/1rhPn4FdTRV1NSHOki5EgVgwXzdXcbXB8/view?usp=sharing)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.



I believe that an MVC in combination with Microservice architecture will be sufficient for these needs. There need to be specific pieces to the architecture that are responsible for different things. The MVC architecture allows for the stuff that clients see to be completely different from the logic and functionality. Having these pieces seperate will allow for greater ability of analytics and tracking as well.

With a heavier amount of traffic hitting the database, there should be pieces set up to strictly handle those heavy amount of requests. The existing structure wouldn't be able to handle the immense amount of data well. The database itself would probably have to upgraded and scaled to match the demand of requests. 



# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.