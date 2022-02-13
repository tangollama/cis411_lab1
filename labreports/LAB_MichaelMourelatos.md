# Lab Report: Continuous Integration
___
**Course:** CIS 411, Spring 2022  
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
**Serve Central**: A user-friendly application that allows users to find volunteering opportunities nearby with ease. ServeCentral also allows all of the documents to be filled out in one spot, creating less of a headache for the user.

## Step 2.1 Representative Use Cases  

| Use Case #1 | |
|---|---|
| **Title** |**Volunteer Information**|
| **Description/Steps** | **Six Steps**:|
| *Step 1* | The volunteer will search through volunteering opportunities displayed on a map in their location |
| *Step 2* | The user will see the distance, location, time, number of attendees, and the type of event it is |
| *Step 3* | The user will select the event that they would like to be a part of |
| *Step 4* | The user must fill out any necessary information the events need from volunteers |
| *Step 5* | Once the user has filled out the required information, the organizers of the event will determine if the application should be accepted for the volunteer position |
| *Step 6* | The people organizing the volunteer event will notify any person who was accepted as a volunteer|
| **Primary Actor** | Person using the Application ServeCentral |
| **Preconditions** | **Three Steps**:|
| *Step 1* | The user must create an account using the email and password of their choosing |
| *Steps 2* | The user shall verify their account by having an email sent to them | 
| *Steps 3* | The user must be logged in before proceeding with the app |
| **Postconditions** | **Two Steps**: |
| *Step 1* | Users will be notified that their application for the volunteering event has been sent |
| *Step 2* | Users will be notified on whether their application has been accepted |

| Use Case #2 | |
|---|---|
| **Title** |**Event Information**|
| **Description/Steps** | **Six Steps**:|
| *Step 1* | An employee will make a post about an available volunteering opportunity with the address, expected number of attendees, name of the event, and the type of the event it is |
| *Step 2* | An employee will post the event |
| *Step 3* | The employee will receive applications sent from users interested in their event | 
| *Step 4* | Employee will notify users that the application has been received | 
| *Step 5* | Employee will notify if the users are qualified based on the requirements within the organization |
| *Step 6* | The Employee will notify users if any changes have been made to the events |
| **Primary Actor(s)** | Employees of ServeCentral and Organizers of Events Submitting Information |
| **Preconditions** | **Two Steps**: |
| *Step 1* | Have planners of events submit information to ServeCentral to post |
| *Step 2* | Have an employee post the necessary information to their application |
| **Postconditions** | **Two Steps**: |
| *Step 1* |  Notify users if they are selected for the volunteer spot |
| *Step 2*| Change or Update any information necessary for the volunteer events |

## Step 2.2 Define the MVC Components

| Model | View | Controller |
|---|---|---|
| Service Event Opportunities | Possible Events | EventPostingController |
| Volunteer Registration | Account Sign Up | RegistrationController |
| Type of Event | Event Registration Information | EventDataController |
| Organization Information | Organization Data Display | LoginController |

## Step 2.3 Diagram a Use Case in Architectural Terms
![Use Case Diagram](/assets/Use_Case_Diagram_2_13.jpg) 

**Description**: The user seeking out volunteering opportunities will go to the ServeCentral application to find an event they want to volunteer for. The user will make an account and log on to ServeCentral. Once completed, a message will be delivered to the controller. The database, through connection with the controller, provides the updates needed to the database. Finally, the controller allows the user to see the account is created, and the user can search through volunteering opportunities.

# Step 3: Enhancing an Architecture

## Step 3.1 Architecture Change Proposal
With ServeCentral expecting to receive tremendous growth and desire to extend their service and provide for primary volunteer entities in the United States, I believe it is wise for ServeCentral to use a Microservices architecture.

MVC architectures are sufficient with their maintenance, team integration, and building software. However, wanting to expand throughout the country requires more involvement from third-party services. Microservices utilizes multiple databases for their architecture which allows users to easily work with the framework and third-party services wanting to implement anything. Using multiple databases welcomes the possibility of adding or removing things from ServeCentral (or whatever app is in use).

To expand at an efficient rate with third-party contributions, this is where Microservices beats MVC. This is what satisfies the second requirement. Using multiple databases in the framework allows for "organization-specific" interfaces. MVC allows for easy team collaboration, but it is more difficult to add new interfaces. Having multiple databases in Microservices may bring a slower approach to implementing new interfaces, but it is easy to implement.

The downside to using Microservices would be the challenge of overcoming the transition from an MVC architecture to a Microservices architecture. Although this may be a hassle to take on, it will be beneficial in the long run.


## Step 3.2 Revised Architecture Diagram
![Microsystems Diagram](/assets/Microservices_Diagram_2_13.jpg)

**Description**: For this diagram, I switched to a Microsystems diagram instead of an MVC diagram. In this Microsystems diagram, there are three different categories: Users, Display, and Databases. The user will either be on the website of ServeCentral or the mobile option. They can access various displays of ServeCentral by going through the various databases. There are also third-party services and organization-specific services that can access certain databases. They are capable of implementing additional databases.

# Step 4: Scaling an Architecture
The architectural pattern to employ would continue to be the Microsystems architecture.

Microsystems find their identity in utilizing multiple databases for different areas of their framework. This welcomes efficiency due to the framework allowing various jobs to be split up for the database needed.

To combat bursts of over 10k+ new volunteer opportunities per hour, ServeCentral would need to implement more databases. Implementing more databases that target more specific information will allow the system to process quicker. By having various unique services run separately, latency is reduced.

To support a volunteer and event data store that will exceed 50TB of data is similar to the latency concern. Implementing more databases and having multiple databases allows jobs to be divided and data to be dispersed. However, utilizing multiple databases will not bring forth a storage concern.

When allowing authorized parties to issue queries, they will only have access to the necessary databases to move forward. These Third-Party Services or Organization Specific Interfaces don't need access to things such as "Login Information." However, they can be allowed access to the users that have signed up for which specific events.

Enabling researchers to examine patterns of volunteer opportunities can be done through giving researchers "Read-Only Access." This allows these researchers to view the data but not make any changes. This ensures the safety of the information.

Any drawbacks that occur within a Microsystems architecture would be the complexity of the multiple databases. Multiple databases are entered into Microsystems. Assembling this architecture poorly will lead to a challenging system to work with. However, this drawback only occurs when the databases are made with little care. Having a programmer that can construct good databases is a top priority in Microsystems. So, moving forward, there won't be any necessary changes with this type of architect.

# Extra Credit
![Extra Credit Microsystems Diagram](/assets/Extra_Credit_Diagram_2_13.jpg)

**Description**: In this diagram, "Authorized Parties" and "Research" were added. Authorized parties are essentially the back-end programmers. These authorized users need to have access to the databases to continue to implement any changes or add anything. The research addition was to prioritize adding any new information to the ServeCentral website/application. This addition only needs access to the "Organization Information" database since the researchers will be providing any information needed for the site/application.

**Meaningful Changes to the Assignment**: A change that I would implement would be more clarifying and in-depth instructions for the MVC framework. When going through making the MVC framework it was unclear whether or not we should suggest software to use or state how the MVC framework is implemented into the ServeCentral application. So, having more clear instructions would have allowed a more direct approach instead of researching various databases, views, and controllers to use.
