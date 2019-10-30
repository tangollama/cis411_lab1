# Lab Report Template for CIS411_Lab1
Course: Messiah College CIS 411, Fall 2019
Instructors: [Joel Worrall](https://github.com/tangollama) & [Trevor Bunch](https://github.com/trevordbunch)
Name: Reagan Lyle
GitHub: [reaganl1998](https://github.com/reaganl1998)

Collaborators: [Drew Feldman and Stephen Maloney]


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
| Title: Churches Eager to Serve | |
| Description / Steps: A church can use this website to find projects to better serve the community for His kingdom. | |
| Primary Actor: Second Non-Denominational Church of Mechanicsburg | |
| Preconditions: My church is struggling to find projects to better serve our community | |
| Postconditions: My church is now signed up to serve in projects in our community | |

| Use Case #2 | |
|---|---|
| Title: Christians Looking to Spread His Kingdom | |
| Description / Steps: Christians looking to grow His kingdom through serving in community projects through spiritual gifts | |
| Primary Actor: Corey Colgate | |
| Preconditions:  I am looking for projects to better serve my community | |
| Postconditions: I was able to find projects that I can use my gifts to serve with | |


2) Highlight a [table](https://www.tablesgenerator.com/markdown_tables) of at least **four models, views, and controllers** needed to produce this project.

| Model | View | Controller |
|---|---|---|
| Project repository | A simple screen that lists community projects that users can get involved in | SQL Queries, Web APIs |
| Login | A simple screen for a user to login with an email and password | SQL Queries, Web APIs |
| User gifts | Simple tags on user's profile that indicate their spiritual gifts. | SQL Queries, Web APIs |
| Project calendar | A simple calendar that keeps track of user's projects, sends email reminders and keeps hours worked. | SQL Queries, Web and Email APIs |

3) Generate and [embed]( [https://www.draw.io/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=Untitled%20Diagram.drawio#R7VtZd5s4FP41fkwOIPDymK2dpTmnc5JOmkcZZKNWIFeI2O6vH22schLaOJWdzkuCLgik7159d5E8AhfZ5j2Dq%2FSaJoiMAi%2FZjMDlKAh8LwjFPynZakkUAi1YMpyYhxrBDf6Oqp5GWuIEFZ0HOaWE41VXGNM8RzHvyCBjdN19bEFJ96sruESW4CaGxJbe4YSnWjoNJo38D4SXafVlfzzTdzJYPWxmUqQwoeuWCFyNwAWjlOurbHOBiASvwkX3e%2FfI3XpgDOV8SIdycQ%2BvL9555PLD7dd09vdfV8HnE%2FOWB0hKM%2BFPBWISuyQppNpQgRlK5IcY%2FSIBlvhLvAVCeQKZmRvfVoAxWuYJkt%2F0RuB8nWKOblYwlnfXwkSELOUZES1fXJqvI8bR5tFp%2BTVYwsoQzRBnW%2FGI6QAqS9lWGjDtdaMuv9JB2lLV2MigsZBl%2FeoGRHFhcPwBTEPPAgUlwqhMkzKe0iXNIblqpOdd2JpnPlC6MmB9QZxvzQqBpdDCDijlh54GUoyLlixGT0wg2A04QwRy%2FNB9%2Fy70TNePFOe8pahJT1GTngI4ZEvETa%2BeDuphvEAt%2FltQi1h%2BCqan1vQjC2aw%2Fl5k%2FYHFKJeQwzkskOwpOeVbiRhWnLLGYoUKdB6QMhTx3uBCzhBnSF%2BtKBe3MJRfTQU%2Bsrvgpwekn3RMPaEPuhY9c009YHbkNg6G2rhLEweWiYu4R9mosu8EFysCt7ssnNBYjI%2FmfTuHedKycIa%2BldLrno6CMcyk3ebzYlUD7dDiA6%2FH4c4tPrJ08a7MY42xVkfMEORKGSpwQRnE8q2ljnOUjKEMKw3wFGXiH13oa8M2OEaVDk%2Bdq6BPOiB0rYJw7IJ0BFxs%2B7nduJcvO42q5uXGvFy3tqa1R7IaDySriUuyCidH7hKGojx1ifLYjnrqzKlHITUvwTxGRD7hOoMKuqQeBq4ZZWKh%2BZ4h7VBpKQHMXuBvH3G2ztUQ9BLZyHOthnDqlNhbXH7fofJXJ%2Fbp0Cj0pZnyi9QztTnn0UxLhTkZfUB1YFMtEXUH5lRIVTwE5wSpKXCIc5wv27Rl5Wd6KT2VpbmOlqKfXFSzV1tUdsR65A7ar%2Bqyzy2XyOVqqUbZwv0OzStLZeoiVzVPVRKuypwEa9vPYJziHLk36F74X7O%2FOy8xe3MGPbjS5tai7VJbK%2FftJrYm28U64pGO4PC4eey8cu%2BHFqK3aMMtpLgUduBgItr%2FrlynRm8lq9hqeNH5KLoUEmmxhTZe2QESvMzFNUEL%2BSoJJI4hOTNiLq3%2BvBDwCxd8q5bASbgf2CNv3HWJYGrBHu5APXg11G2PeJTM3Ddn57Ux385K%2FVPRvv5Xxm5nLJaYxLxkNni2hRec0a%2FoghLKhCSnuWTtBSakJ6oMOxawCeXZpp3hJFGUv0slXaXtQSu93HaHTn6trdupbSBVcpWnMI91uN1VzDMV4LeqqIlrTVWr%2BberavqDs9%2BZy%2BgncrKdewDFicH6aZ0ycRGd2uWJTznWGzF3UI5jDWWIZNy5dPGjqqDAUIywqlU0p04SyKFzHw9Al6Wmzmt0vp19NZVnjZlVJe2B%2BAxssFjpg1ULvJFQ74Xsxz0cpzaO0x0wTl%2BN7e1cygW97JEmKit8nibcHhfxLOD%2FqauWbfvFMkpZMaQZZC5HSChU15DIrRRW04cucIrQ6VspD9edz1HBm1Y7sdAbMSkV7FMRkYjDEtKUSeX2gOp%2BYNnFdGh28WqFzMhOlo99yQwtZAbA6ZKxK5k3lUFr6%2B3W%2Fg%2FCc%2Fbt1%2Fecu87APsdz9vHPUVNuMPSjaIGnmCV6xlxOqxCAHQCofg%2FUHX70F5%2FHiVyQwGNp0%2BQX5k3VSffn2cPpSYXI7Wkd7zQMg7aSTrxTD%2FjPqEm1PgpCExjIWoU73TnNeQPb5V7jHBd6DJ18qlS7wCboH3X3aJsDKSa9kr3UpgFdy79rND8IegPVXml9tN95STXYvem%2BI8kSAeuoPqjiGMgg6AEZuPcTdiHUBS%2Ftk0NmAzkEuI0e7YLB%2FwnXrthq%2FLNr5vUyLpt8jnzNgKHn%2FUHocs0AO1M4goxr3N3n9UPnGRew45cfzbi0W11QVp%2FTlx1WpFzKGwcHufOAJfwdjjSE0ayDOxiHFux72jwUzeYnu%2Fqnic0Pn8HVfw%3D%3D](https://www.draw.io/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=Untitled Diagram.drawio#R7VtZd5s4FP41fkwOIPDymK2dpTmnc5JOmkcZZKNWIFeI2O6vH22schLaOJWdzkuCLgik7159d5E8AhfZ5j2Dq%2FSaJoiMAi%2FZjMDlKAh8LwjFPynZakkUAi1YMpyYhxrBDf6Oqp5GWuIEFZ0HOaWE41VXGNM8RzHvyCBjdN19bEFJ96sruESW4CaGxJbe4YSnWjoNJo38D4SXafVlfzzTdzJYPWxmUqQwoeuWCFyNwAWjlOurbHOBiASvwkX3e%2FfI3XpgDOV8SIdycQ%2BvL9555PLD7dd09vdfV8HnE%2FOWB0hKM%2BFPBWISuyQppNpQgRlK5IcY%2FSIBlvhLvAVCeQKZmRvfVoAxWuYJkt%2F0RuB8nWKOblYwlnfXwkSELOUZES1fXJqvI8bR5tFp%2BTVYwsoQzRBnW%2FGI6QAqS9lWGjDtdaMuv9JB2lLV2MigsZBl%2FeoGRHFhcPwBTEPPAgUlwqhMkzKe0iXNIblqpOdd2JpnPlC6MmB9QZxvzQqBpdDCDijlh54GUoyLlixGT0wg2A04QwRy%2FNB9%2Fy70TNePFOe8pahJT1GTngI4ZEvETa%2BeDuphvEAt%2FltQi1h%2BCqan1vQjC2aw%2Fl5k%2FYHFKJeQwzkskOwpOeVbiRhWnLLGYoUKdB6QMhTx3uBCzhBnSF%2BtKBe3MJRfTQU%2Bsrvgpwekn3RMPaEPuhY9c009YHbkNg6G2rhLEweWiYu4R9mosu8EFysCt7ssnNBYjI%2FmfTuHedKycIa%2BldLrno6CMcyk3ebzYlUD7dDiA6%2FH4c4tPrJ08a7MY42xVkfMEORKGSpwQRnE8q2ljnOUjKEMKw3wFGXiH13oa8M2OEaVDk%2Bdq6BPOiB0rYJw7IJ0BFxs%2B7nduJcvO42q5uXGvFy3tqa1R7IaDySriUuyCidH7hKGojx1ifLYjnrqzKlHITUvwTxGRD7hOoMKuqQeBq4ZZWKh%2BZ4h7VBpKQHMXuBvH3G2ztUQ9BLZyHOthnDqlNhbXH7fofJXJ%2Fbp0Cj0pZnyi9QztTnn0UxLhTkZfUB1YFMtEXUH5lRIVTwE5wSpKXCIc5wv27Rl5Wd6KT2VpbmOlqKfXFSzV1tUdsR65A7ar%2Bqyzy2XyOVqqUbZwv0OzStLZeoiVzVPVRKuypwEa9vPYJziHLk36F74X7O%2FOy8xe3MGPbjS5tai7VJbK%2FftJrYm28U64pGO4PC4eey8cu%2BHFqK3aMMtpLgUduBgItr%2FrlynRm8lq9hqeNH5KLoUEmmxhTZe2QESvMzFNUEL%2BSoJJI4hOTNiLq3%2BvBDwCxd8q5bASbgf2CNv3HWJYGrBHu5APXg11G2PeJTM3Ddn57Ux385K%2FVPRvv5Xxm5nLJaYxLxkNni2hRec0a%2FoghLKhCSnuWTtBSakJ6oMOxawCeXZpp3hJFGUv0slXaXtQSu93HaHTn6trdupbSBVcpWnMI91uN1VzDMV4LeqqIlrTVWr%2BberavqDs9%2BZy%2BgncrKdewDFicH6aZ0ycRGd2uWJTznWGzF3UI5jDWWIZNy5dPGjqqDAUIywqlU0p04SyKFzHw9Al6Wmzmt0vp19NZVnjZlVJe2B%2BAxssFjpg1ULvJFQ74Xsxz0cpzaO0x0wTl%2BN7e1cygW97JEmKit8nibcHhfxLOD%2FqauWbfvFMkpZMaQZZC5HSChU15DIrRRW04cucIrQ6VspD9edz1HBm1Y7sdAbMSkV7FMRkYjDEtKUSeX2gOp%2BYNnFdGh28WqFzMhOlo99yQwtZAbA6ZKxK5k3lUFr6%2B3W%2Fg%2FCc%2Fbt1%2Fecu87APsdz9vHPUVNuMPSjaIGnmCV6xlxOqxCAHQCofg%2FUHX70F5%2FHiVyQwGNp0%2BQX5k3VSffn2cPpSYXI7Wkd7zQMg7aSTrxTD%2FjPqEm1PgpCExjIWoU73TnNeQPb5V7jHBd6DJ18qlS7wCboH3X3aJsDKSa9kr3UpgFdy79rND8IegPVXml9tN95STXYvem%2BI8kSAeuoPqjiGMgg6AEZuPcTdiHUBS%2Ftk0NmAzkEuI0e7YLB%2FwnXrthq%2FLNr5vUyLpt8jnzNgKHn%2FUHocs0AO1M4goxr3N3n9UPnGRew45cfzbi0W11QVp%2FTlx1WpFzKGwcHufOAJfwdjjSE0ayDOxiHFux72jwUzeYnu%2Fqnic0Pn8HVfw%3D%3D) ) at least one diagram of the interaction between an Actor from the Use Cases, and one set of Model(s), View(s), and Controller(s) from the proposed architecture, including all the related / necessary services (ex: data storage and retrieval, web servers, container tech, etc.)

_Note: You are free to use any diagraming tool and framework that you want as long as it clearly communicates the concept. I typically use a UML System Use Case or [UML Sequence Diagram](https://www.uml-diagrams.org/index-examples.html).  If you do not have a preferred diagramming tool: [draw.io](http://draw.io) or [lucidchart](http://lucidchart.com) are good cloud-based options._

# Step 2: Enhancing an Architecture
After an initial release and a few months of operation, Serve Central encounters a tremendous growth opportunity to extend their service and provide a volunteer recuitment and management interface to __four__ of the primary volunteer entities in the United States. As such, a reevaluation of the architecture is required, one that allows:

1. Thirdparty services to both input and retrieve data from the Serve Central model/datastore. (For instance, receiving volunteer opportunities from United Way chapters across the country.)
2. Building organization-specific interfaces on top of the Serve Central business and data logic. (For instance, allowing the registration services of Serve Central to be embedded in the website of local churches, [ah-la Stripe embedding](https://stripe.com/payments/elements).)

To support these objectives:
1. What architectural patterns (either of those presented in class on based on your own research) are appropriate? Justify your response, highlighting your presumed benefits / capabilties of your chosen architecture(s) **as well as as least one potential issue / adverse consequence** of your choice.

    1. **Broker**: 

       Since this service has seen tremendous growth, the broker architecture allows for services to have load balancing and to scale on demand. Load distribution allows for third party interaction to have a stable platform to Serve Central. This allows for there to be less worry on whether or not the third party requests data efficiently and further reduce the threat of Serve Central being brought down by too many requests.

       A potential issue could be waste of resources during down time.

2. Using your preferred diagramming tool, generate a diagram of the new Serve Central architecture that supports these two new requirements.

# Step 3: Scaling an Architecture
18 months into the future, Serve Central is experiencing profound growth in the use of the service with more than 100k daily, active users and nearly 1M event registrations per month. As a result, the [Gates Foundation](https://www.gatesfoundation.org/) has funded a project to build and launch a mobile application aimed at encouraging peer-to-peer volunteer opportunity promotion and organization. 

In addition to building a new mobile application interface, the grant requires that the project prepare for the following future needs:

1. Consuming bursts of 10k+ new volunteer opportunities per hour with a latency of less than 15 seconds between submitting an opportunity and it's availability in the registration service.

   **Master-Slave: **

   Having load balancing is critical to being able to adapt to massive spikes of service requests that occur at random and being able to have as little interruption in service as possible. 

2. Supporting a volunteer and event data store that will quickly exceed 50TB of data

   **Blackboard:**

   Allows for data retention to scale and work independently of each other to increase reliability. It allows for data to be analyzed and see how to more efficiently use storage space even with data usage increasing dramatically. 

3. Allowing authorized parties to issue queries that traverse the TB's of data stored in your datastore(s).

   **Client-server:**

   Using HospitalRun development, allows for authorized third parties to securely access critical and sensitive data stored by Serve Central severs with physical versatility of using mobile platforms. 

4. Enabling researchers to examine patterns of volunteer opportunities as a way of determining future grant investments.

   **Blackboard:**

   Allows for data to be broken down into multiple surface spaces to be efficiently analyzed. Can scale for big data.

   

What archictural pattern(s) will you employee to support each of these needs? What will the benefits and consequences be? Why are changes needed at all? Justify your answers.

# Extra Credit
1. Create and embed a comprehensive diagram of your final architecture (i.e. one that meets all the requirements of this lab, including Step 3).
2. Augment/improve the assignment. Suggest meaningful changes in the assignment and highlight those changes in the extra credit portion of your lab report.