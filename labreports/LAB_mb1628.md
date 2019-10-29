# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018</br>
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)</br>
Name: Matthew Bromley</br>
GitHub: [mb1628](https://github.com/mb1628)</br>
Following: [MUEsic](https://github.com/SamMahan/MUSEsic)</br>

Collaborators:</br>
Kerlin</br>
Collette</br>
Houck</br>
Coldsmith</br>

# Step 1: MVC Architecture

| Use Case #1 | |
|---|---|
| Title | Signing Up for an Event as a Volunteer|
| Description / Steps | 1) A volunteer must browes the app and choose a registered event.</br> 2) After an event is chosen the volunteer must register for said event through the apps registration process.|
| Primary Actor | Volunteer |
| Preconditions | A user wishing to volunteer must have an account before registering for an event. |
| Postconditions | The user will have an updated list of events they are registerd for. Each item in the list will contain specific information on the event. |

| Use Case #2 | |
|---|---|
| Title | Creating an Event as an Organiation|
| Description / Steps | 1) Event creator must brows to the event registration portion of the app.</br> 2) Event creator must then enter all required information about the event into the provided feilds. (Location, time, etc...)</br> 3) The event creator will then submit the completed form to create the event.|
| Primary Actor | Organization wishing to host an event|
| Preconditions | Organization must be registerd and approved by ServeCentral.|
| Postconditions | The organization will now have a live even that is accessible to volunteers for registration.|



| Model         | Controller                            | View                            |
|---------------|---------------------------------------|---------------------------------|
| Volunteers    | Register for Event                    | Event Screen                    |
| Organizations | Register an Event                     | Create Event Screen             |
| Events        | Browse Events                        | Map with Pins/Event List Screen |
| Users         | Register as Volunteer or Organization | Profile Creation Screen         |


![MVC Diagram](mvcDiagram.PNG "MVC Diagram for volunteer")


# Step 2: Enhancing an Architecture

The primary structure I chose for this growth was the layer structure. Other companies could build their systems off the information in serveCentral's database. Through a server connection each company will be able to grab this information and integrate it with their systems.

The biggest problem I can see with this is server connection. ServeCentral databse or server goes down, all other company's applications that rely on serveCentral will no longer function.

![MVC Diagram](serveCentralGrowth.PNG "MVC Diagram for volunteer")

# Step 3: Scaling an Architecture

The current solution I have decided on is a Master-Slave relationship. If millions of people are downloading the app and using the website we need a way to gather that information quickly. Instead completing all transactions through a master server, we send out slaves to complete the user transaction and report that data back to the master server. This way the master server will not be overwhelmed by all the requests.

The biggest concern with master slave is  the latency issue. Even with the slaves doing the majority of the processing the server may still have trouble processing all data comming in. This could lead to delay for users. 