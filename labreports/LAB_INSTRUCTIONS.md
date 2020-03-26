# CIS 411 Lab 1: Architectural Review
The purpose of this lab is to engage students in the considering the purpose, value, and unique differentiation of system architectural patterns.

## Submitting work
Lab reports will be submitted by generating a markdown file in the labreports directory under the naming convention: **LAB_[GITHUB HANDLE].md**, and submitting a Pull Request to this repository that include your lab report as well as any accompanying images/files (there are diagrams required in the lab content). The link to that Pull Request must be submitted to Canvas as a

* Throughout these instructions, you'll find that **items marked in bold text** reference content you are to submit in your lab report.
* For the purposes of clear communication, you may base your lab report off of the template found in [LAB.md](LAB.md), but you're also free, welcome, and encouraged to get more creative.
* If you are unfamiliar with markdown, I recommend checking [1000 places on the Interwebs](http://lmgtfy.com/?q=learn+markdown) that will help you close that gap.

# Step 0: Create a GitHub account++
1. If you don't have a GitHub account already, [create one](https://github.com/join). If you do, **record the name of your handle in your lab report** and **record a link to one repository you either follow or star**.
2. If you don't already have _git_ installed on your development machine, [do so](https://git-scm.com/downloads).
3. Install a text editor or some sort of application for local development. Lately, I'm partial to [Visual Studio Code](https://code.visualstudio.com/) and my instructions assume it's use, but you're welcome to diviate. _Each one should choose their own sword, etc. etc._
4. To run the project in Step 2, you'll need to have [node.js](https://nodejs.org/en/download/) and [npm](https://docs.npmjs.com/cli/install) installed.

# Step 1: Fork this repository and create your lab report file
1. After logging in, navigate to the [root](https://github.com/tangollama/cis411_lab1) of this repository.
2. Fork this repository to your personal GitHub account (hint: read the page).
3. Navigate to your forked repository in your GitHub account and copy the reference to your repository in from the <button class="btn btn-sm btn-primary">Clone or Download</button> button.
4. Open the terminal or command line interface on your development machine, navigate to your chosen working directory, and execute the following command: ```git clone [YOUR COPIED GITHUB CLONE REFERENCE]```.
5. Navigate to that directory ```cd cis411_lab1```.
6. Create a lab report mardown file (ex. ```cp labreports/LAB.md labreports/LAB_[GITHUB USERNAME].md``` ).
7. Add your lab report ```git add *```
8. Add the file to your branch ```git commit -a -m "your commit message"```.
9. Push the change to GitHub ```git push -u origin master```.
10. As you make additional changes to the lab report, commit and push your changes.

# Step 2: Submitting a Pull Request
Once you've completed your report markdown, and have committed all your changes to your (primary) master branch, initiate a Pull Request in GitHub to submit your Lab Report.
1. Navigate to the root of your forked repository (ex. https://github.com/YOURHANDLE/cis411_lab1).
2. Click the _New pull request_ button.
3. Choose the base fork _tangollama/cis411_lab0_ is the target and that your fully updated _master_ branch is the source.
4. Enter a title and description for the Pull Request (PR), **referencing at least one other student in the content via their GitHub handle**, and submit the PR.
5. Submit that URL to canvas as your lab report work.