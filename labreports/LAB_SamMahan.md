# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2018
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Samuel Mahan
GitHub: [SamMahan](https://github.com/SamMahan)
Collaborators: [Ben Underwood, Kira Fernandez]


# Step 0: Reviewing Architectural Patterns
See the [lecture / discussion](https://docs.google.com/presentation/d/1nUcy63FWPFYO3OJmERJpMjEtdaFtaIBbuUkpmNRVRas/edit#slide=id.g45345bd5ea_0_136) from CIS 411. You'll need to be familiar with the content from this lecture to complete this assignment.

Note: you are free to work with classmates on this assignment. _Good architecture is born out of collaboration - not reclusive mad-scientist behavior._ However, if you work with colleagues:

1. You must specifically note your collaborators by name at the top of your report.
2. You may not completely copy each others work (diagrams and descriptions, even if your solutions are identical).

# Step 1: MVC Architecture
Review the proposals for the Serve Central project. Let's imagine that the project has been granted (relatively) unlimited resources if they can deliver a version 1 release in 120 days. As a result, the team decides to implement an MVC architecture for its version 1 release, delivering functionality through a [responsive web application](https://en.wikipedia.org/wiki/Responsive_web_design). 

Based on the [this](https://docs.google.com/presentation/d/1UnU0xU0wF1l8pAB8trtLpdM0yuskx66jTFJzd64nsjU/edit#slide=id.g439b9c6866_2_53) and [this](https://docs.google.com/presentation/d/1-VZfAFoBVr6ijNepKAtRA7JoAQsV2Jlbf2l1WPDMhI0/edit) presentation:

1) Document two use cases of your choosing

<table>
  <tr>
    <th>Use Case #1</th>
    <th></th>
  </tr>
  <tr>
    <td>Title</td>
    <td>Joining a charitable activity</td>
  </tr>
  <tr>
    <td>Description</td>
    <td>The user wants to find a charitable event in the local area</td>
  </tr>
  <tr>
    <td>Primary actor</td>
    <td>non-organization user</td>
  </tr>
  <tr>
    <td> Normal Course </td>
    <td>
      <ol>
        <liThe system serves a page showing the event's time, place, and host organization of the event. a "signup" button is shown as well</li>
        <li>Upon signup, the system serves a "terms and agreements" page and the option to accept or reject terms and conditions. It                  stores the response locally.</li>
        <li>upon acceptance of the terms and conditions, the system serves a page that collects the time the user would like to work. It             stores the response locally.</li>
        <li>upon entry of desired time, the system stores the response locally and serves a review page, where the user's commitment is             summarized.</li>
        <li>upon acceptance of the commitment page, the system sends the entered data to the server along with the user's id and the                  event's id. The serverside system inserts the user's relationship to the event into the database.</li>
      </ol>
    </td>
  </tr>
  <tr>
    <td>Preconditions</td>
    <td>
      <ol>
        <li>The user must be a "standard user" (as opposed to an "organization tool")</li>
        <li>The user must have the application installed</li>
        <li>The user must have a valid account and be logged in to that account</li>
        <li> The user must have already selected that event from the search functionality. </li>
      </ol>
     </td>
  </tr>
  <tr>
    <td>Postconditions</td>
    <td>
      <ol>
    <li>Organization users can see the new user on their dashboard</li>
    <li>If the threshold of helpers for that event has been reached, that event is marked "full" when searched</li>
    <li>A notification is pushed to the user's phone via the app on the day of the event. </li>      
      </ol>
    </td>
  </tr>
</table>
    


<!-- case number 2-->
<table>
  <tr>
    <th>User case #2</th>
    <th> </th>
  </tr>
  <tr>
    <td>Title</td>
    <td>User Registration</td>
  </tr>
  <tr>
    <td>Description</td>
    <td>A new user wants to register (non-organization account)</td>
  </tr>
  <tr>
    <td>Primary actor</td>
    <td>non-organization user</td>
  </tr>
  <tr>
    <td> Normal Course </td>
    <td>
      <ol>
        <li>The system detects that a user has no session upon application startup and serves a login page with a button giving the                  option to "create a new account". User clicks the "create a new account" button. </li>
        <li> The system serves a page with fields for first name, last name, residence, and email. The user fills out these fields and      `         presses "submit"</li>
        <li> Upon submission, the system stores the new user in the database. </li>
        <li> The system initializes a session on the user's phone </li>
        <li> The system redirects the user to the user account page </li>
        
      </ol>
    </td>
  </tr>
  <tr>
    <td>Preconditions</td>
    <td>
      <ol>
        <li>The user must be trying to log in as a "standard user" (as opposed to an "organization tool")</li>
        <li>The user must have the application installed on a supported phone</li>
        <li>The application must not be storing a user session</li>
      </ol>
     </td>
  </tr>
  <tr>
    <td>Postconditions</td>
    <td>
      <ol>
      <li> the user is sent a confirmation email to to be set as a "confirmed" user</li>
      </ol>
    </td>
  </tr>
</table>

2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Components   |         |       |              |          |
|--------------|---------|-------|--------------|----------|
| Views        | Login   | User  | Event        | Register |
| Controllers  | GetUser | Login | Register     | GetEvent |
| Model Tables | User    | Event | Organization | Location |

3) Generate and [embed](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)


[Architecture Diagram For Login](https://github.com/SamMahan/cis411_lab1/blob/master/Architecture-diagram.jpg)


_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:


1. Third party services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

**Answer**
  I would recommend the use of a layered architecture with three layers: presentation, business, and database. Since queries would be     made from within the Node.js business logic codebase, there would be no need for a persistence layer.
  
  The reason why this architecture is ideal is because the site can now handle a more diverse set of requests for its data. On top of     being required to serve content to be used by view pages, it also must accept requests from outside organizations looking to             contribute to their own internal dashboards and datasets. To serve this data properly, it must ensure that its api's are only loosely   coupled to views, since they no longer serve only views.
  
  A setback of this is that the dependencies between all of the components of the website will have to be tracked, since the               functionality will no longer be considered single-use. This could cause confusion during updates, as changes could lead to failures in   services outside the organization that rely on the APIs.
  
  
2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

**Answer**
[Serv Central Model](https://github.com/SamMahan/cis411_lab1/blob/master/Serv-central-architecture.jpg)

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.
2. Supporting a volunteer and event data store that will quickly exceed 50TB of data
3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).
4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

**Answer**
<ol>
  <li> I would implement a (bypassable) service layer above my business layer. Most likely, this would take the form of GraphQL. This would allow my organization and outsiders to quickly and efficiently grab large volumes of data from a diverse set of API's for analysis, while still preserving those API's themselves for use by lighter queries from the presentation layer if necessary.</li>
  <li> I would deploy my server side application using Kubernetes to balance the increased traffic. This would allow me to scale up my hardware easily to meet demand</li>
  <li> I would not do anything to the database itself. Since it is a firebase database, it is managed by google and I do not have direct access to it's hardware, the way queries are executed in it, or the number of instances it runs on. All the data we harvest will be data from our systems, so we do not need the capability to read unstructured or semi-structured data. I imagine that google can deal with my increased traffic without trouble.</li>
  
</ol>
**Consequences**
<ol>
  <li> as a consequence of implementing all of these features, the website will grow more complicated and require more documentation to maintain. Also, it will not be as changeable, since its design encourages outside services to rely on it.</li>
  </ol>
  

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.

**Augumentation/Improvement**
<ol>
  <li>Diagrams. I liked that we had to make diagrams, but I was left feeling like I had made them incorrectly. I suppose I do not know the level of detail that I need since there seems to be a range from very general to very specific</li>
</ol>
