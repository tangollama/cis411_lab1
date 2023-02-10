# Lab Report: Architechture
___
**Course:** CIS 411, Spring 2023  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Timothy Comerford
**GitHub Handle:** TComerford1972  
**Repository:** [Your Forked Repository](https://github.com/TComerford1972/cis411_lab2_arch.git)  
**Collaborators:** Sturty75 adn JG1579 (Zach Booher and John Gaston).
___

# Step 1: Confirm Lab Setup
- [X] I have forked the repository and created my lab report
- [X] I have reviewed the [lecture / discsussion](../assets/04p1_SolutionArchitectures.pdf) on architecture patterns.
- [X] If I'm collaborating on this project, I have included their handles on the report and confirm that my report is informed, but not copied from my collaborators.

# Step 2: Analyze the Proposal
Serve Central looks to make an app that streamlines the task of finding and signing up for volunteer opportunities.
Serve Central also helps organizations find the help they need as well as make the registration process smoother. 

## Step 2.1 Representative Use Cases  

| Use Case #1 | |
|---|---|
| Title |Organization sets up a volunteer event on Serve Central. |
| Description / Steps | 1. Organization volunteer coordinator clicks on "Add Event" button on Organization landing page. <br> 2. to enter the name, time, address, date, length and type of volunteer service.|
| Primary Actor |Volunteer Coordinator |
| Preconditions | 1. Serve Central app downloaded on mobile phone. <br> 2. Volunteer Coordinator has registered and set up company profile.|
| Postconditions |1. App generates new event in database. <br> 2. App sends out notifications to volunteers within a defined area. <br> 3. Opportunity is added to a list of local events tied to locality and organization. |

| Use Case #2 | |
|---|---|
| Title | Volunteer searches for an event. |
| Description / Steps | 1. User looks for events in his (user defined) area.|
| Primary Actor | Volunteer|
| Preconditions | 1. Serve Central app downloaded on mobile phone. <br> 2. Volunteer has registered and set up profile.|
| Postconditions |1. Event shows on volunteer's profile as upcoming with time and map to location. |

## Step 2.2 Define the MVC Components

| Model | View | Controller |
|---|---|---|
| Authentication Table | Splash page with user name and password fields. | Authenticator - Checks encrypted database for user name and hashed password. |
| Event Table | Events page defaults to a list of local events with map API component. | Using user location data, queries event table in the user-defined radius and returns a list. Uses API to place markers on a map for all events in list. Updates view.|
| Organization Table| Organization landing page shows organization name, address, contact info of volunteer coordinator, upcoming and previous events. | Queries organization table and event information and updates view. |
| User Table | User landing page shows user name, volunteer hours worked (broken down by type of volunteer work), user's upcoming events and a events attended history. | Querries user table for user specific information, queries event table for event info, updates view. |

## Step 2.3 Diagram a Use Case in Architectural Terms
![Setting up and registering for an event](https://github.com/TComerford1972/cis411_lab2_arch/blob/main/assets/Use_case.png?raw=true)

# Step 3: Enhancing an Architecture

## Step 3.1 Architecture Change Proposal
I propose that the company stick with the MVC model and install two APIs. One API that would allow the four entities access to the data and would update the Serve Central database, the other API would allow for websites to host registration code. MVC allows for the greatest amount of change on the fly and the most accessability across multiple platforms. The big drawback is the increased complexity of the code, also users can stress the views leading to less responsiveness and performance.

![New Architecture](https://github.com/TComerford1972/cis411_lab2_arch/blob/main/assets/New%20Design.png?raw=true)
# Step 4: Scaling the Architecture
In order to address the issues of scalability: <br> 1. Using Microsoft Azure (managed) along with a microservices architechture for the registration information. Contract would specify ability to process and transfer bursts of more than 10,000 new database records per hour with a latency of less than 15 seconds. <br> 2. This will also allow the company to utilize the IAAS as object and block storage for the 50 TB of data from events. <br> 3. A separate Data Lake (utilizing Hadoop) architecture for handling the large scale data queries. <br> 4. To find the patterns in data I recommend a tight-coupled architecture.