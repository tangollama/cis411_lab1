# Lab Report for CIS411_Lab1  
Course: Messiah College CIS 411, Fall 2018    
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)    
Name: Kai Yuen Leong  
GitHub: kaiyuenleong(https://github.com/kaiyuenleong)

# Step 1: MVC Architecture
Review the proposals for the Serve Central project. Let's imagine that the project has been granted (relatively) unlimited resources if they can deliver a version 1 release in 120 days. As a result, the team decides to implement an MVC architecture for its version 1 release, delivering functionality through a [responsive web application](https://en.wikipedia.org/wiki/Responsive_web_design). 

Based on the [this](https://docs.google.com/presentation/d/1UnU0xU0wF1l8pAB8trtLpdM0yuskx66jTFJzd64nsjU/edit#slide=id.g439b9c6866_2_53) and [this](https://docs.google.com/presentation/d/1-VZfAFoBVr6ijNepKAtRA7JoAQsV2Jlbf2l1WPDMhI0/edit) presentation:

1) Document two use cases of your choosing

| Use Case #1 | |
|---|---|
| Title | Sign up for a service opportunity/event |
| Description / Steps | 1. The volunteer selects either the "map view" or "list view" of events <br/> 2. In "map view", the system highlights the closest events to the volunteer on a map <br/> 3. In "list view", the system shows a list of nearby service events, sorted by distance from the volunteer's location <br/> 4. The volunteer selects a pin (in map view) or a listed event (in list view) <br/> 5. The system shows details of the selected event <br/> 6. If the volunteer selects the "register for event" option, the system notifies the event organizer of the signup and sends basic volunteer information to the event organizer; if the volunteer exits from the currently shown event, return to step 3 <br/> 7. The system notifies the volunteer of a successful signup|
| Primary Actor | Volunteer |
| Preconditions | Volunteer is logged in; list of events and respective details are up-to-date |
| Postconditions | Volunteer is signed up for an event; event organizer is notified of volunteer signup |

| Use Case #2 | |
|---|---|
| Title | Sign up for a ServeCentral account |
| Description / Steps | 1. The system prompts the user to enter an email address and a password <br/> 2. The system checks the database of registered users to ensure that the user-entered email is not already in the system; prompts the user to log in instead if email already exists <br/> 3. The system adds the user's email and password to the registered users database <br/> 4. The system notifies the user of successful signup |
| Primary Actor | Unregistered User |
| Preconditions | Database of registered users are up-to-date |
| Postconditions | Volunteer is registered in the ServeCentral platform |

2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Private User Data | User Profile Settings | System pulls a user's data from a database and displays it on his/her profile settings |
| Nearby Events | Events Map | System pulls nearby events based on a user's location and displays the events in the form of pins on the map |
| Created/Organized Events | Map on Web Application | System pulls an organization's created events and displays the events on a map |
| User's Public Volunteer History | User Dashboard | System pulls an aggregate of a user's volunteer history and displays it on the user's dashboard |

3)
 
![Step 1 Part 3 Diagram](https://github.com/kaiyuenleong/cis411_lab1/blob/master/labreports/step1_part3_diagram)

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

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.