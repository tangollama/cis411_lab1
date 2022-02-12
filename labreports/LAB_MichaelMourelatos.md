# Lab Report: Continuous Integration
___
**Course:** CIS 411, Spring 2021  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Michael Mourelatos  
**GitHub Handle:** [MichaelMourelatos](https://github.com/MichaelMourelatos)  
**Repository:** [My Forked Repository](https://github.com/MichaelMourelatos/cis411_lab2_arch)  
**Collaborators:** [Andrew Coldsmith](https://github.com/andrewcoldsmith) and [Grace Schlauder](https://github.com/grace-schl)
___

# Step 1: Confirm Lab Setup
- [x] I have forked the repository and created my lab report
- [x] I have reviewed the [lecture / discsussion](/assets/04p1_SolutionArchitectures.pdf) on architecture patterns.
- [x] If I'm collaborating on this project, I have included their handles on the report and confirm that my report is informed, but not copied from my collaborators.

# Step 2: Analyze the Proposal
**Serve Central**: A user friendly application that allows users to find volunteering opportunities nearby with ease. Serve Central also allows for all of the documents to be filled out all in one spot, creating less of a headache for the user.

## Step 2.1 Representative Use Cases  

| Use Case #1 | |
|---|---|
| **Title** |**Volunteer Information**|
| **Description/Steps** | **Six Steps**:|
| *Step 1* | The volunteer will search through volunteering opportunities that are displayed on a map in their location |
| *Step 2* | The user will see the distance, location, time, number of attendees, and the type of event it is |
| *Step 3* | The user will the event that they would like to be a part of |
| *Step 4* | The user must fill out any necessary information the events need from volunteers |
| *Step 5* | Once the user has filled out the required information the organizers of the event will determine if the application should be accepted for the volunteer position |
| *Step 6* | The people organizing the volunteer event will notify any person who was accepted as a volunteer|
| **Primary Actor** |Person using the Application ServeCentral|
| **Preconditions** | **Three Steps**:|
| *Step 1* | The user must create an account using their email and password of their choosing |
| *Steps 2* | The user shall verify their account by having an email sent to them | 
| *Steps 3* | The user must be logged in before proceeding with the app |
| **Postconditions** | **Two Steps**: |
| *Step 1* | Users will be notified that their application for the volunteering event has been sent |
| *Step 2* |Users will be notified on whether their application has been accepted |

| Use Case #2 | |
|---|---|
| **Title** |**Event Information**|
| **Description/Steps** | **Six Steps**:|
| *Step 1* | An employee will make a post about an available volunteering opportunity with the address, expected number of attendees, name of the event, and the type of the event it is |
| *Step 2* | An employee will post the event |
| *Step 3* | The employee will receive applications sent from users interested in their event | 
| *Step 4* | Employee will notify users that the application has been received | 
| *Step 5* | Employee will notify if the users are qualified based of the requirements within the organization |
| *Step 6* | The Employee will notify users if any changes has been made to the events |
| **Primary Actor(s)** | Employees of ServeCentral and Organizers of Events Submitting Information |
| **Preconditions** | **Two Steps**: |
| *Step 1* | Have plannars of events submit information to ServeCentral to post |
| *Step 2* | Have an employee post the necessary information to their application |
| **Postconditions** | **Two Steps**: |
| *Step 1* |  Notify users if they are selected for the volunteer spot |
| *Step 2*| Change or Update any information necessary for the volunteer events |

## Step 2.2 Define the MVC Components

| Model | View | Controller |
|---|---|---|
| Service Events Opportunities | Possible Events | EventPostingController |
| Volunteer Registration | Sign Up | RegistrationController |
| Type of Event | Event Registration Information | EventDataController |
| Organization | Organization Information Display | LoginController |

## Step 2.3 Diagram a Use Case in Architectural Terms
INSERT IMAGE HERE with a Description.

# Step 3: Enhancing an Architecture

## Step 3.1 Architecture Change Proposal
INSERT Architectural change proposal here, and how it meets the two new requirements.  Explain both the benefits and draw backs of your proposal.

## Step 3.2 Revised Architecture Diagram
INSERT IMAGE HERE with a Description.

# Step 4: Scaling an Architecture
INSERT Architectural change proposal here, and how it meets the four new requirements.  Explain both the benefits and draw backs of your proposal.  If the changes are significant, then you need to explain why the changes are necessary versus a nice-to-have enhancement.

# Extra Credit
If you opt to do extra credit, then include it here.