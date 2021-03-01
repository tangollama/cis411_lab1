# Lab Report: Continuous Integration
___
**Course:** CIS 411, Spring 2021  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Bryan Chang  
**GitHub Handle:** Triggum  
**Repository:** cis411_lab2_arch  
**Collaborators:** Jmtonnies
___

# Step 1: Confirm Lab Setup
- [done] I have forked the repository and created my lab report
- [done] I have reviewed the [lecture / discsussion](../assets/04p1_SolutionArchitectures.pdf) on architecture patterns.
- [done] If I'm collaborating on this project, I have included their handles on the report and confirm that my report is informed, but not copied from my collaborators.

# Step 2: Analyze the Proposal
Serve Central allows for a volunteer to find volunteering opportunities and apply for them. The user can see the event, service agency information and apply conveniently in one app.

## Step 2.1 Representative Use Cases  

| Use Case #1 |ID:UC-1|
|---|---|
| Title | Applying to volunteer|

| Description| The volunteer fills out the necessary information to apply and submits it. The system processess the request by forwarding it to the respective service agencies for approval

Steps:  
1. Applying to volunteer for an event
    1. The volunteer looks for an event they are interested in and applies for it.
    2. The system notifies the service agency of the application.
    3. The system stores the application in the pending application datastore|
   
| Primary Actor |
The volunteer |

| Preconditions | 
  1. The Volunteer has their identity authenticated.
  2. The event is open for application.
  3. The pending application datastore is up-to-date and on-line|
| Postconditions |
  1. The request is approved or refused by the service agency
  2. The volunteer is notified of the approval decision.
    2.1. If approved, event details are given. |

| Use Case #2 |ID: UC-2 |
|---|---|
| Title |
Creating an event|

| Description / Steps |
Description: The service agencies creates an event to recruit volunteers by stating information about the event like the event title, which area of service its serving and location of the event

Steps: 
  1. Service agency creates an event
    1. The service agency specifies the event details and the reason for the event
    2. The system stores the event in the organization datastore.
    3. The system notifies users in the area that a new event is open.
    4. The system opens up the event for applicants.|

| Primary Actor |Service Agencies|

| Preconditions |
  1. The service agency's identity is authenticated.
  2. The service agency has a valid event being held.
  3. The organization datastore is up-to-date and on-line.|
   
| Postconditions |
  1. The system notifies the service agency about the confirmation of the event.
  2. The event is stored in the organization datastore.
  3. The volunteers are notified of a new event |

## Step 2.2 Define the MVC Components

|   Model   |           View          |  Controller |
|:---------:|:-----------------------:|:-----------:|
|  MongoDB  | Firebase + React Native |  Express.js |
|  RavenDB  |        Bootstrap        |   ember.js  |
| RethinkDB |          Ionic          | Backbone.js |
|  OrientDB |      Apache Cordova     | Knockout.js |

## Step 2.3 Diagram a Use Case in Architectural Terms
* The process of a Volunteer applying for an event.
![Use Case Diagram](\assets\use_case.PNG) 


# Step 3: Enhancing an Architecture

## Step 3.1 Architecture Change Proposal
The architectural pattern that would be appropriate is the peer-to-peer architectural pattern. This pattern meets the two new requirements as it allows for thirdparty services to input  and retrieve data from the Serve Central model/datastore because it allows for equal access to all its nodes. Besides that, it allows for Serve Central to provide its services onto different partner organzations. The benefits for using this structure is that it allows for limited redundancy when dealing with multiple organizations, quick access to necessary information, and integration with software like Stripe Elements which is an open-source checkout ui. The drawbacks from using this architectural pattern is that it requires attention to who uses it, confidentiality might be difficult if there are many peers in the network. Other than that, if a virus gets uploaded by accident, it would effect the other nodes as well which is a huge danger.

## Step 3.2 Revised Architecture Diagram
![Architecture](\assets\Architecture diagram.PNG)

# Step 4: Scaling an Architecture
The architectural change proposal would be to change to a broker architectural pattern. This allows for availability of service for a larger amount of people than the previous peer-to-peer service. Along with that, the broker would be able to handle data exceeding 50TBs and allow for authorized parties to query the data stored. This is significant because the previous architectural pattern would not be able to handle a load of more than 50TB and would end up crashing the network. The queries issued by authorized parties can also help researchers examine patterns. The benefits for using this architectural pattern is that it can be used to query data from datastores and allow for continued service as the broker has services it can provide along with being a bridge to the Serve Central servers. Disadvantages of a brokered architectural pattern is that it is relient on the broker to be stable and able to provide services reliably.
# Extra Credit
If you opt to do extra credit, then include it here.