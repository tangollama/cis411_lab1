# Lab Instructions

# Step 0: Create a GitHub account
1. If you don't have a GitHub account already, [create one](https://github.com/join). If you do, **record the name of your handle in your lab report** and **record a link to one repository you either follow or star**.
2. If you don't already have _git_ installed on your development machine, [do so](https://git-scm.com/downloads).
3. Install a text editor or some sort of application for local development. Lately, I'm partial to [Visual Studio Code](https://code.visualstudio.com/) and my instructions assume it's use, but you're welcome to diviate. _Each one should choose their own sword, etc. etc._

# Step 1: Fork this repository and create your lab report file
1. After logging in, navigate to the [root](https://github.com/trevordbunch/cis411_lab2_arch) of this repository.
2. Fork this repository to your personal GitHub account (hint: read the page).
3. Navigate to your forked repository in your GitHub account and copy the reference to your repository in from the <button class="btn btn-sm btn-primary">Clone or Download</button> button.
4. Open the terminal or command line interface on your development machine, navigate to your chosen working directory, and execute the following command: ```git clone [YOUR COPIED GITHUB CLONE REFERENCE]```.
5. Navigate to that directory ```cd cis411_lab2_arch```.
6. Create a lab report mardown file (ex. ```cp labreports/LAB_Template.md labreports/LAB_[GITHUB USERNAME].md``` ).
7. Add your lab report ```git add *```
8. Add the file to your branch ```git commit -a -m "your commit message"```.
9. Push the change to GitHub ```git push -u origin main```.
10. As you make additional changes to the lab report, commit and push your changes.

**Note:** you are free to work with classmates on this assignment. _Good architecture is born out of collaboration - not reclusive mad-scientist behavior._ However, if you work with colleagues:

1. You must specifically note your collaborators by name at the top of your report.
2. You may not completely copy each others work (diagrams and descriptions, even if your solutions are identical).

# Step 2: Analyze the Proposal  
Review the proposal for the [Serve Central](assets/ServeCentral.pdf) project. Let's imagine that the project has been granted (relatively) unlimited resources if they can deliver a version 1 release in 120 days. As a result, the team decides to implement an MVC architecture for its version 1 release, delivering functionality through a [responsive web application](https://en.wikipedia.org/wiki/Responsive_web_design). 

Summarize Serve Central in 1-2 sentences for those who have not been able to review the slide deck.

## Step 2.1 Document Use Cases
Consider the target audiences for Serve Central (volunteers and service agencies), define one use case for each of those audiences.

Dennis, Wixom and Roth (2014) have a full chapter (4) on writing use cases.  You are welcome to use an alternative format (there are plenty of alternative templates out there), but please ensure that you include the following elements: Title, Description / Steps, Primary Actor, Preconditions, & Postconditions.  A sample is included in the [assets folder](assets/UseCase_Sample.md).   

## Step 2.2 Define the MVC Components  
Build a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project based on the business requirements you do not need to research any technology solutions for this steps.  Here's a hint:  
- Models typically reflect your data entities
- Views typically mirror your pages or screens
- Controllers govern system performed actions

## Step 2.3 Diagram a Use Case in Architectural Terms
Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 3: Architecture Enhancement
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recruitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

# Step 4: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employ to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

# Step 5: Submitting a Pull Request
Once you've completed your report markdown, reviewed your markdown formatting, and have committed all your changes to your (primary) main branch, initiate a Pull Request in GitHub to submit your Lab Report.
1. Navigate to the root of your forked repository (ex. https://github.com/YOURHANDLE/cis411_lab2_arch).
2. Click the _New pull request_ button.
3. Choose the base fork _tangollama/cis411_lab0_ is the target and that your fully updated _main_ branch is the source.
4. Enter a title and description for the Pull Request (PR), **referencing at least one other student in the content via their GitHub handle**, and submit the PR.
5. Submit that URL to canvas as your lab report work.

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 4).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.