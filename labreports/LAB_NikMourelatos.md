# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: YOUR NAME
GitHub: [NikMourelatos](https://github.com/NikMourelatos)
<br/>Collaborators: Eric Weischedel


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
| Title | As a an active member in my community I want to find out where service is needed, so that I may volunteer there.|
| Description / Steps | 1. The user would search for events. <br/>2. The UI will give a response of a map with all events that are nearby within their city/township.<br/>3. When the user finds an event that they are interested in they can click on that event and will proceed to a page where they are prompted for their information so that they can sign up as a volunteer.
| Primary Actor | The user looking for a place to volunteer. |
| Preconditions | The application has events loaded |
| Postconditions |The system sends a confirmation email within 10 seconds of the user signing up for an event to volunteer at. |

| Use Case #2 | |
|---|---|
| Title | A person has just moved into a new community and is looking for ways to get to know the people in his new place of living.|
| Description / Steps | 1. The user opens up the event finder application<br/> 2. The user enters a zipcode for where they would like to find events to go to.<br/>3. The user looks at the possible events near him <b4/> 4. The user clicks on an event they want to go to and signs  up for that event.|
| Primary Actor | The end user|
| Preconditions | Events are logged into the system |
| Postconditions | The user gets a confirmation email within 10 seconds of signing up for an event.|


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
|User info/registration model- Store users information|Sign up menu| Sign in controller- Sign in logic that makes sure all enetered fields are correct.|
|Verification Model- Makes sure that the users credentials are right. | Event Map  | Registration Controller- Upon clicking on an event they want to  sign up  for, the user is  taken to a signup menu |
|Event info Model- REST Get Request on event's home webpage  for the events information. |Event Registration | Search controller- Used to communicate with external API's to obtain information. |
|UI info model- This model obtains the information that the system has stored in the local database such as the map data and prepares it for the view.  |Log in screen | Update Controler- Used when the end user clicks the 'search' button and loads the information needed to populate the map. |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

### Diagram [here](https://drive.google.com/file/d/1DY4tQFHAAuo_n-y3FMc3TIynVROXGToD/view?usp=sharing).

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

## Answers:
1.  The best possible architeture to approach this is to stick with the MVC architecture, the reason for this is that one will not have to compeletely redesign their entire architecture, why reinvent the wheel. It is now necessary, however, that Source Central would need to create its own API in order to communicate their desired information with the local churches and let United Way sends them information. A pottential issue is that with the MVC approach the complete product is very bulky, this can become extremely difficult to maintain and if any other organizations wanted to interface with you for other reasons, such  as  being on a mobile application or special purpose services, and soon after you interface with a few more companies all these different files for controls, models and views grow very quickly.  

2. Diagram [here](https://drive.google.com/file/d/1s6dSP19VGmGecPsOes3neOms42Y1IO8y/view?usp=sharing).

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.
## Answers
1. The best architectural pattern for a system with this high of demand is a load balancer architecture.  The reason for this is because with all the new requests coming to your servers it is necessary that you dynamically allocate server space now so that no one server is overrun. Inside each server; however, I suggest we stick with the same MVC architectural as it has proven to work in precious examples. Lastly, we need another load balance for the multiple databases that we will have. The system as a whole will be on the cloud and provide swift quick access to all end users. However; if the load balancer were to fail the the servers would then be taken offline; to combat this I suggest having two load balancers incase one fails the other can pick up.
This new architecture is needed to keep the system runtime efficeint and responsive while still providing a service to the high amount of new users that the company has obtained.

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.

### Answers
1. Diagram [here](https://drive.google.com/file/d/1SiyLIBriVlETYm0wrN1jdjVcqF38raM6/view?usp=sharing).
2.  This project was very interesting as it required a lot of problem solving when it came to how to correctly depict everything in the MVC architecture. I like how open ended this project was, when looking at the last two questions. I do wish i had more knowledge of each architecture applications prior to going into those exercises with real world applications.  My suggestion for improving this project is (because i believe that these are important concepts) extend the project a little longer and give an example of three systems that use three different architectures and make us draw diagrams for those prior to making us have to decide which one is best for a system. I believe this  will real hit the nail and make us truly understand more architectures more and their  importance to a system as a whole.  I enjoyed the project altogether, as, to me, someone who does not need to take server side with my specific concentration, i found all this information very useful and informative