# Lab Report: Continuous Integration
___
**Course:** CIS 411, Spring 2021  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Elijah Murray  
**GitHub Handle:** eliguy5474  
**Repository:** https://github.com/eliguy5474?tab=repositories
**Collaborators:** NONE
___

# Step 1: Confirm Lab Setup
- [Y] I have forked the repository and created my lab report
- [Y] I have reviewed the [lecture / discsussion](../assets/04p1_SolutionArchitectures.pdf) on architecture patterns.
- [Y] If I'm collaborating on this project, I have included their handles on the report and confirm that my report is informed, but not copied from my collaborators.

# Step 2: Analyze the Proposal
ServeCentral is an app for information about events in your area. It is also an app for volunteers to sign up to help out at the events that agencies have posted.

## Step 2.1 Representative Use Cases  

| Use Case #1 | |
|---|---|
| Title | Finding a volunteer position - Volunteer |
| Description / Steps | As a new ServeCentral user, a volunteer is looking for a volunteer oppertunity in their area.<br>1. The user navigates on the ServeCentral webpage, and searches around on the map page.<br>2. The user then finds an oppertunity that pleases them.<br>3. The user then clicks on the event to sign up for it inputting their information.<br>4. The user is then directed to a thank you page with more details about the event.|
| Primary Actor | Volunteer |
| Preconditions | None |
| Postconditions | 1. The user found a volunteer oppertunity and signed up for it.<br>2. The user also receives more information about the event after signing up. |

| Use Case #2 | |
|---|---|
| Title | Creating an event on ServeCentral - service agencies |
| Description / Steps | An agency is trying to uplaod an event on ServeCentral and is looking for more voulenteers.<br>1. The service agency would click the events tab on the app, located on the bottom right.<br>2. The agency will then be able to create and post an event for volunteers can sign up for. |
| Primary Actor | Service agency |
| Preconditions | None |
| Postconditions |1. The event is now published for volunteers to sign up for. |

## Step 2.2 Define the MVC Components

| Model | View | Controller |
|----------|---|---|
| Profile  |Profile page  |showProfileController  |
| Event Locator Map | Events locator | showLocatorController |
| Event Information | Event information  | showEventInfoController |
| Create Event | Create event | showCreateController |

## Step 2.3 Diagram a Use Case in Architectural Terms
![UseCase](3.2%20Lab2.png)

# Step 3: Enhancing an Architecture

## Step 3.1 Architecture Change Proposal
The most fitting architectural pattern that helps meet these two new requirements is the load balancing architecture model. It supports the new requirements in providing way to deal with the traffic that the third-party services will bring. It will also deal with the load of data that is being brought in as well. The second requirement can be supported with the load balancing architecture for the web interface can be embedded in aother website and still ab able to send the user input and information to the ServeCenter servers'. A potiental issue / adverse consequence could be maintaining the load balancing which can be expensive to keep the databases and web servers snyced.



## Step 3.2 Revised Architecture Diagram
![RevisedArchitecture](Revised_Architecture%20(1).png)

# Step 4: Scaling an Architecture
The Load Balancing architecture will be a good way to go to support the needs of the company as it will help support the traffic of the users. There will be a good amount of databases that will be needed for the queries from the users. On top of that, we there will be the backend servers to help with the traffic with the users and the servers. The architecture will be good for the mobile app as well. The one drawback I see is the price of the infrastructure as it'll cost a lot for fast communication for the systems.

# Extra Credit
If you opt to do extra credit, then include it here.