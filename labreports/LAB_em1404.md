# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018  
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)  
Name: Eliezer Mwankenja, 
GitHub: [em1404](https://github.com/em1404)  
(if appropriate) 
Collaborators: [Names of colleagues you worked with on this assignment]


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
| Title |```Activity Sign up``` |
| Description / Steps | ```When a volunteer wants to sign up for an ctivity. They log into their app. Select the desiredd activity and sign up for it.``` |
| Primary Actor |```Volunteer``` |
| Preconditions |```Volunteer has a ServCentral account. Organizations using ServeCentral have posted volunteer opportunities. ```|
| Postconditions |```Activity will be added to the volunteer list of comming up activities. A volunteer reminder for the activity will be set. Organizations list of potential volunteers will be updated.``` |

| Use Case #2 | |
|---|---|
| Title |```Volunteer Activity Post``` |
| Description / Steps | ```When organizations are organizing an event for volunteer activities, they log into ServeCentral. Provide deatails for the event and publish it so that it can be seen by volunteers. ```|
| Primary Actor |```organization ```|
| Preconditions |```Organization has an account with ServCentral. Event has been set up and has an anticipated date along with other details like location and time.``` |
| Postconditions |```Update ServCentral list of posted events. Update other ServeCentral posted events info, like posted events locations. Update posting organization list of posted events.``` |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
|```volunteer``` |```volunteerDashboard ``` | ```volunteerController``` |
|```activitity ``` | ```activitySummary``` |```ActivityController```  |
| ```volunteerData ```| ```volunteerSummary``` | ```VolunteerDataController``` |
| ```organization``` |```organizationDashboard``` |```OrganizaitonController```  |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

---

![SOA architecture](user_interactions.jpg)

---

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice. 
---
--- 
### Architectural pattern of choice and benefits
>-  ``` The Service Oriented Architecture will be approprote because it allows for services to be used by multiple processes. SOA also, can simplify and accelerate provision of new business funtionality through organizing or orchestrating existing services to achieve the desired goal.```
---
###  Potential issue
>- ``` One of the main disadvantages associated with SOA is it requires a large upfront technology, development, and human resources investment.```
---     
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.
---

![SOA architecture](SOA.jpg)

---
---
# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers. 

---
---
### Architecture pattern and benefits
>- ```For 1 & 2 SOA  Integrated Service Environments like Oracle SOA are inherently scalable and allow for diverse types of scaling. To increase speed and efficience of the parten scalling could increase the parten capability and its capacity can be improved through configuration, tuning, management, and governance. Using the fund to buy new hardware or  cloud services can be used to support the new demand for data storage.``` 
>- ```The use of API like RESTful APIs could allow for authorized partis to traverse the TB's of dara stored in the data stores```
>- ```Because of SOA's flexibility and easy of integration, the parten could include integrationo of interfaces and analytics tools which can be used by reserchers.```    
### Consequences 
>- ``` the consequences for the changes required to support these needs will include increase cost of operation and mantaince because of the scale of the new system.``` 
### The need for changes
>- ``` Changes are needed because the increased number of consumers will increase the burden on the system and will require new resources. Also, the added services for researchers and authorised parties will require new capabilities and services from the system. ```  
---
---
# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.