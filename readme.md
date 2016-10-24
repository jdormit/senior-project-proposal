# Senior Project Proposal: Spark
## by Jeremy Dormitzer

### Abstract
`Spark` is a collaborative web-based code editor in the style of Google Docs. It aims to facilitate remote pair-programming and streamline the collaborative development process. Existing tools attempt to solve this issue, but they are proprietary, buggy, and usually locked behind a paywall. `Spark` will be open-source, making it easy-to-host and hackable. I intend `Spark` to be a complete collaborative development solution that allows multiple developers to code together in real-time. The project has two deliverables: the `Spark` server and a `Spark` web application. The server will be implemented using [`Node.js`](https://nodejs.org/en/), and the client will be implemented using the [`React`](https://facebook.github.io/react/) framework.

### Introduction
Collaboration is a key part of the software business. Everyone, from undergraduates starting CMPT 201 to Senior Engineers building the next Facebook, utilizes pair programming and collaborative processes to maximize their productivity and gain insight into the software they write.

Pair programming works great when developers can sit next to each other and code on the same machine. However, remote work is a rapidly growing trend in the industry. Big companies are hiring employees who live in other states or halfway across the world. Universities and coding boot camps offer online programs to a global audience. It is much more difficult for pair programming to be effective in these remote environments.

Existing tooling for remote pairing lacks functionality, depends on external tools, or locks key features behind a paywall. Furthermore, these proprietary solutions don’t give developers access to the source code, limiting the extensibility and flexibility of the platform.

I want to build an open source, extensible, web-based code editor that allows multiple developers to collaborate on a single source file - working title, `Spark`. My hope is that by open-sourcing the application, I can build a community of developers to bring this idea to its full potential.

This is a big, ambitious project, and I won’t be able to deliver a feature-complete version by the end of next semester. For that reason, my senior project will focus on building the minimum viable product (MVP) version, and I will lay out “stretch goals” that I will pursue once the MVP is complete.

### MVP Features
- Real-time collaborative editing
- Basic security
  - HTTP Basic Authentication
  - Encrypted web socket traffic
- Autosave
- Syntax highlighting (using an existing solution)
- File tree
- Text chat
- Tabs and multiple open files
- Configurable via the UI or a config file

### Stretch Features
- Plugin system (for things like third-party integrations or debugging support)
- Moveable, resizable panes
- IDE Features
  - Autocompletion
  - Refactoring
- Video/voice chat
- Multiple key binding schemes
- Color themes
- Git/Github integration
- Support for more languages
- Progressive web app for easy mobile/tablet use
- Desktop client built with Electron

### Background
What follows is a brief history of real-time collaborative text editors, an analysis of `Spark`'s place in the market, and a technical overview of the project.

#### History
The idea of collaborative document editing has been around for nearly as long as the idea of the personal computer. The earliest documented implementation of a collaborative real-time editor was demonstrated by Douglas Engelbart in 1968, as a part of the aptly-name [Mother of All Demos](https://en.wikipedia.org/wiki/The_Mother_of_All_Demos). Engelbart aimed to demonstrate the as-yet untapped potential of the personal computer as a platform for communication and data storage in addition to mere number-crunching. However, despite the demo's widespread influence, collaborative real-time editing did not take off for nearly 40 years. The first mainstream real-time collaborative editor was Writely, a web-based text editor launched in 2006. It was quickly [bought by Google](http://www.informationweek.com/google-acquires-writely-online-word-processing-service/d/d-id/1041208?), and is now known as Google Docs. It remains the most popular real-time collaborative editor in the world. However, it is not an effective tool for writing code, due to its lack of syntax highlighting, IDE features such as refactoring and autocompletion, and file tree management. In recent years, several products have sought to fill this gap. These include editor plugins such as [Floobits](https://floobits.com/) and web-based editors such as [Codeanywhere](https://codeanywhere.com/), [Cloud9](https://c9.io/), and [Kobra](https://kobra.io/#/), among others. 

The web-based solutions have several things in common:

- Their software is proprietary
- They host their own servers internally, and require developers to connect to those servers to use the product
- They hide some or all functionality behind a paywall

This is where `Spark` fits in. As an open-source project, anyone can host their own server. Additionally, anyone can access and modify the source code to suit their needs. This alone should be enough to make `Spark` stand out in a crowded market. However, the real power of open-source is the community that can form around an open-source project. I hope to build an extended community of contributors and users that can help move the project forward and spread the word.

#### Technical Details
At a high level, the editor will be made up of a server and one or more clients. I plan on using [`Node.js`](https://nodejs.org/en/) to write the server, and the [`React`](https://facebook.github.io/react/) JavaScript framework to write the client. The server will not only serve the web app, but also allow access to one or more project directories living on the host machine. I will most likely implement this as a `workspace` directory that holds one or more `project` folders, each of which hold the source code for a different project.

Specifically, the server will use [`Express.js`](https://expressjs.com) and [`Socket.io`](http://socket.io) to handle real-time web traffic. As this is supposed to be an open source project, I will not worry about hosting the server for now (ideally, those who want to use the editor will download the source code and host it themselves).

From a security standpoint, the sysadmin will need the ability to limit access to individual projects. This will most likely be done via a config file or command-line options passed to the `vapor` executable (the server). Options will include setting up access checks via RSA key authentication or basic HTTP authentication (username-password), opening up the project to anyone who gets an invite, or making the project totally open to the public. I anticipate that invite-only will be the most useful choice for students; as this will be my initial target demographic I will focus on that first.

As previously mentioned, the client view layer will be handled by [`React`](https://facebook.github.io/react/). To manage the data layer I will use [`Redux`](http://redux.js.org/). I will manage dependencies and load external libraries using [`Webpack`](http://webpack.github.io/).

### Proposed Work
This is a large software project. Even with the stated goal of implementing only MVP features, it will require careful planning. Furthermore, as an Honors student I need to complete some sort of research paper that goes along with the project. I will leave the details of that paper out of this proposal; however, my schedule needs to take the additional work into account. I plan on loosely following the [Agile](http://www.agilemodeling.com/essays/introductionToAM.htm) methodology - specifically, I will divide the work to be done into one- or two-week [sprints](http://agilemodeling.com/essays/prioritizedRequirements.htm) during which I will complete one or more [user stories](http://www.agilemodeling.com/artifacts/userStory.htm). I am using [Trello](https://trello.com/b/pREfdFQ7) to keep track of user stories and sprints.

#### Tasks
Here is the full list of tasks (details follow):	

- User stories and mock-ups
- Brainstorm paper topics
- Plan architecture and implementation details
- Build proof of concept
- Research and outline paper
- Implement MVP features
- Begin community building
- Write paper
- Implement stretch features (if time)

#### Rationale
I see a real need in the developer ecosystem for robust and open remote work tooling. An open source project can be used by anyone, improved by anyone, and runs on a student's laptop just as well as it runs on a corporate network. The web is a natural home for this sort of innately online software. In addition, building a web client allows me to leverage the millions of existing open-source JavaScript libraries, and lowers the barriers to entry for contributors by building on the most popular development platform in the world.

#### Plan of Work

##### User Stories and Mock-ups:
A user story is an Agile development technique for defining the functionality of the finished product. They are typically written in the form, *"As a [type of user], I want [goal] so that [reason]"*. They are intended to express on at a high level a specific function of the application. They do not contain implementation details. I have already written the user stories for `Spark`. You can see them on the [Trello board](https://trello.com/b/pREfdFQ7).

The mock-ups will be simple wireframe drawings of the application. I will need one at a minimum, showing the main editor view, and probably a few others showing other possible application states. I will figure out what mock-ups I need based on the user stories.

**Deliverable:** The Trello board of user stories and one or more annotated wireframe images.

##### Brainstorm Paper Topics:
This is pretty self explanatory. As a starting point, I want to draw connections between the open-source/free software movement and the globalization of the development community.

**Deliverable:** A one or two sentence description of the topic.

##### Plan Architecture and Implementation Details:
I don't want to spend a ton of time on this, as it will likely change during development. However, I would like to have a basic idea of the architecture of the software - the server- and client-side data structures, especially regarding text buffers and user input; the synchronization between clients, which will involve serializing user inputs and sending them over the network; and some idea of how the server handles incoming changes, both in terms of writing those changes to disk and handling conflicts.

**Deliverable:** A two-page technical document - one page for the server architecture and one page for the client architecture.

##### Build Proof of Concept:
I want to code something as early as possible. This is to validate the idea, and also because I'm excited about the project and want to hack something out as soon as I can (also, it's in the project requirements). The proof of concept should be as small as possible. It will consist of a single server that needs to be able to:

- Display a text buffer of a file and handle user input
- Write those changes to disk
- Allow multiple clients to connect and edit the same text buffer
- Update the buffer for every client in real-time, showing changes from other clients and the cursor positions of other clients

I will not worry about any of the other features for the proof of concept.

**Deliverable:** A JavaScript project with the above functionality.

##### Research and Outline Paper:
I will engage in preliminary research for the Honors paper and generate a fairly detailed outline.

**Deliverable:** An outline document.

##### Implement MVP Features:
This is the meat of the project. Although I list it as one task, it will actually be divided into as many sprints as is necessary to complete it. Each sprint, I will choose one or more user stories and implement them. The details of this will obviously depend on the story; however, the general process will go something like:

1. Write unit tests to determine the API and give some measurable goal
2.  Code the feature(s) until all unit tests pass
3.  Write documentation

**Deliverables:** For each user story, a set of passing unit tests and a section in the documentation.

##### Begin Community Building:
This is extremely important to me. At this point, I should have a (mostly) working MVP application and I will be looking to build a community around `Spark`. This means people using `Spark` and people contributing the its development on Github. To do this, I will use social media and hopefully word-of-mouth to get people interested in the project. Specifically, I will write a blog post introducing the project and publish it to my website. I will also reach out to the Twitter community and online developer hubs like [Hacker News](news.ycombinator.com). I will also reach out to Westminster faculty and students, asking if anyone would like to get involved or start using `Spark`. Finally, and most importantly, I will write a robust `README` file for the Github repository, as well as a `LICENCE` file detailing the project's open-source license (probably the [MIT license](https://writing.kemitchell.com/2016/09/21/MIT-License-Line-by-Line.html) and a `CONTRIBUTING` file detailing contribution guidelines such as pull request formats and contact.

I understand that this is my senior project, and that it may seem to be inappropriate to ask for community contributions. However, I would argue that actually writing the code is not really the point of the project - my goal is to build and maintain a large, open-source software project, and involving the community will give me real-world leadership, marketing, and development experience.

**Deliverables:** The blog post, and the `README`, `LICENSE`, and `CONTRIBUTING` files.

##### Write Paper:
I will use the outline and research to write an eight to ten page paper about the topic I decided on previously. This will likely be divided into a couple sprints.

**Deliverable:** The paper.

##### Implement Stretch Features (If Time):
At this point the project goals will be complete and the paper written. If I get this far before the semester ends, I will use the remaining time to add new user stories reflecting the "stretch features", and implement them using the same process outlines above.

**Deliverable:** Passing unit tests and documentation for each user story.

#### Preliminary Work
As stated above, I have already written user stories for the MVP features. They can be found on the [`Spark` Trello board](https://trello.com/b/pREfdFQ7).

#### Timeline
The Agile methodology is all about flexibility. Sprints are usually not planned very far in advance, except in very general detail. This allows the developers (i.e., me) to pivot easily as requirements or contexts change. Therefore, the following timeline should be taken as merely a guideline, and I will determine the actual dates and deliverables for each sprint at the end of the previous sprint, based on the plan of work proposed above. As this is a major project, I will start working on it this semester rather than waiting until next semester.

- 10/17/16 to 10/30/16: User stories and mock-ups. These are already nearly complete.
- 10/31/16 to 11/06/16: Brainstorm paper topics and plan software architecture and implementation.
- 11/07/16 to 11/20/16: Build proof of concept. This will consist of several user stories, probably spread across two sprints. The stories for the proof of concept live on a [separate Trello board](https://trello.com/b/adA2wCQA).
- 11/27/16 to 12/04/16: Research and outline paper.
- 12/05/16 to 01/08/17: Implement MVP features. I am giving myself 5 weeks to do this, but I will take more if I need to. I will determine the exact timing of the sprints when the time comes.
- 01/09/17 to 01/15/17: Community building.
- 01/16/17 to 02/05/17: Write paper (first draft).
- 02/06/17 to 02/12/17: Revise paper.
- 02/13/17 to 02/26/17: Polish paper as needed. Deliver final draft on 02/26/17.
- 02/27/17 to 03/30/17: Implement stretch features and polish existing features. Prepare to present paper and project.

#### Evaluation
I should be evaluated on the status of the deliverables outlined above. More generally, the software I write should run without any major bugs. This can be evaluated by running unit tests and by manually testing the application. I should also be evaluated on my ability to manage and plan a large software project. This can be evaluated by examining my project management tools such as Trello, and by tracking how closely I stick to my plan. Although community development is a key aspect of the project for me, I don't think I should be evaluated on based on the community I manage to build, as that is a major undertaking that takes time to come to fruition and I may not see the results I anticipate by the end of next semester.
