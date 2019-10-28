# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Michael Williams
GitHub: [Michael Williams](https://github.com/mw1421)
(if appropriate) Collaborators: [Names of colleagues you worked with on this assignment]


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
| Title | ServeCentral Organization Use Case |
| Description / Steps | Organizations have a hard time finding volunteers for their various projects. This new platform gives a chance to help organizations keep all of their information in one place and be able to track and find volunteer help. 
| 1 | The organization sets up an organization account. |
| 2 | The organization first sets up an event. |
| 3 | The organization then waits for people to sign up for the event, promote the event on ServeCentral or other social media platforms, or invite specific people to the event. |
| 4 | The event happens with the volunteers that signed up for the event. |
| Primary Actor | Organization |
| Preconditions | There is a need for volunteer help. |
| Postconditions | The event is complete. |

| Use Case #2 | |
|---|---|
| Title | ServeCentral Volunteer Use Case |
| Description / Steps | Volunteers find it hard to volunteer at different events, since it is all very unorganized. This platform will help both parties find the right people for the right events. |
| 1 | Volunteers set up a volunteer account. |
| 2 | Volunteers sign up for events. |
| 3 | Volunteers complete events. |
| Primary Actor | Volunteers |
| Preconditions | |
| 1 | There is a want to volunteer. |
| 2 | There is a means of transportation to event. |
| Postconditions | The event is complete. |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| MongoDB | React Native | Express |
| MongoDB | Swift | Amazon S3 |
| Google Firebase | React Native | Github |
| PounchDB | React Native | Express |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

[Volunteer interaction with MVC](https://drive.google.com/file/d/1EivcE_Z6Ys4kXk2HEvbp6M3Ko_jvzecw/view?usp=sharing)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

I would choose the layered architecture. 
First of all, it fits perfectly with the MVC framework because the MVC framework is a layered architecture. The model is the database which is the very core of the architecture. That then communicates to the next layer of the controller where the logic resides, and finally goes to the view where it is reflected back to the user to see. The architecture is clear and easy to maintain, test, separate, and update. 
There could be a separate account for third-party services (with proper authentication) to allow them to input and retrieve data seom the Service Central database. Just a small change within the controller of the architecture. 
With this architecture, the model and controller can remain the same, with the same database and the same logic. The front-end has the ability to change, so then there can be an embed into another company's website / application. 
There are some caveats to the architecture though. Since it is very open, it can get very unorganized quickly if there is no one maintaining the code and making sure that it is organized. 

[Layered Architecture for Serve Central](https://drive.google.com/file/d/1Oqr21kb68dbzXrTU_xcuocZZqLNknDRP/view?usp=sharing)

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