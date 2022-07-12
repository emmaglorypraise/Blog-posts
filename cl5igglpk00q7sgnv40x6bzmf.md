## Everything I learnt in my first dApp Competition

June 2022 was a particularly memorable month for me. Aside from my frequent travels (I visited a different state every week), I spent most of my time working on this dApp competition.

This article provides a step-by-step summary of how I entered my first Blockchain dApp Developer Grant competition, advanced to the final round, and was selected as one of the winners. I built a dApp  that used OAK's JS-SDK to manage assets and automate tasks, giving users of OAK's networks a pleasurable and transparent experience.

OAK Network organized this contest. On the Polkadot and Kusama ecosystems, OAK Network is an automation infrastructure layer for Web3.0 networks. By utilizing the capabilities of substrate and the Polkadot ecosystem, the OAK team is developing an automation platform that could be used to address automation issues. OAK and Turing networks on the Polkadot and Kusama ecosystems are the outcome of their work. OAK will go operational in Q4 of 2022, and Turing is already live on the Kusama network.

![](https://paper-attachments.dropbox.com/s_B4B3AB1864CADDECA341203A7E036094AA7B92F9F1B61A6B4F14FA0B77CFC1ED_1657580133510_dapp-competition.jpeg)



## How it all started

So when a friend sent me the link to the competition, I instantly looked into the organization and the contest. After carefully reading the competition's guidelines, I submitted my application. I chose to work on Automaty (Automaty from Automation - you get it😂), which I named after the most interesting of the three choices I saw, and I submitted my application after making sure it complied with their requirements.

Soon after, I received a message informing me that my application had been accepted and gone on to the next level, which is an onboarding meeting with a member of their team to discuss my proposed project. 

I soon received an email stating that my application had been approved, that I had moved on to the next stage, which involved meeting with a member of their team to discuss my proposed project, and that meeting had gone well. I then received another email stating that I could now participate by starting to build my project.


## Team work

Since I didn't want to work alone now that I was sure I had been accepted, I contacted [Adeola](https://twitter.com/FafemiAdeola) and [Ifeoma](https://twitter.com/Sandie_iphy). We worked as a team at the web3ladies in-house hackathon and were one of the winners, taking home a cash prize. They were enthusiastic when I told them about the project. We needed a UI/UX designer, so we contacted [Favour](https://twitter.com/molimiii), another web3ladies alumnus, and we got ready to work on the project.


## Remote collaboration

In our first meeting, we talked about the project, defined the task's scope, and distributed the work in accordance with our individual strengths.

While the rest of us began studying the documentation for the JavaScript SDK that we would be using, Favour, the designer among us, began working on the design.

Although none of us had prior experience working on the Polkadot blockchain and the project's deadline was roughly one month (June 1–July 4), we were willing to give it a try and pick up some knowledge along the way.

My team's ability to work together despite the fact that the four of us are spread out across different cities is one unique aspect. Who said women can't work together again? We have done it twice 😂 


## Working on the project

The rest of us continued when the design was finished (following multiple meetings when we discussed how it should look and the features of the dApp). We made the decision to use JavaScript to communicate with the JS SDK and React to build the dashboard and other displays. However, we ran into a number of problems and roadblocks along the way.

To begin with, I created the initial dashboard page and integrated Polkadot.js wallet into it so that the dApp could obtain the user's wallet address and utilize it to automate transfers and task scheduling. Once I was finished, I sent it to Ifeoma so she could access the data from the wallet.

Due to issues we encountered with the SDK's interaction, we were unable to obtain all the data we required from it. As a result, we had to construct a backend, saving it on the database to make implementation open for extension like being able to make modification to a task, delete tasks, get all tasks by the address provided or by a particular task id etc. Generally to store the data so that we could utilize it to generate transactions. 

Since we were now working with APIs, we changed the project's stack, using Nextjs and Tailwind CSS for the frontend and eventually switching to Typescript, NestJs, Typescript and MongoDB for the backend.

Adeola headed the team working for more than a week to debug and integrate the various components.

Following completion of all tasks, we tested the dApp by initiating transfers and generating tasks, and it functioned as intended.

We finished, submitted, and posted the last modifications to GitHub.

Now, the major reason we ran out of time before finishing the last feature on the dApp was that we wanted to make sure the others were functioning properly first.

### The tools and technologies we used for this project include:
- Figma
- Nextjs
- Tailwind CSS
- Javascript
- Typescript
- NestJs 
- MongoDB
- Postman
- React toastify
- Vercel for hosting frontend 
- Heroku for hosting API
- and more

Personally, this project taught me a lot about React and Nextjs, managing forms, integrating a wallet, making the dashboard responsive, working with the SDK, and other technical skills. Even seeing my peers code was a kind of coding tutorial for me because I discovered new approaches to fixing issues. I ran across a lot of errors along the way, but I was able to fix them with the help of Google search, stack overflow, and, of course, my teammates. One important  tech skill is knowing how to find solutions.

I must inform you that my team emerged one of the winners of the competition in order for this article to be complete.

We won 3rd place!

![](https://paper-attachments.dropbox.com/s_B4B3AB1864CADDECA341203A7E036094AA7B92F9F1B61A6B4F14FA0B77CFC1ED_1657580045340_announcements.png)


A big shout out to my team members, you ladies rock! 

Another big shoutout to the Oak team for organizing.

View live project [here](https://oak-d-app-automaty-project.vercel.app/).
View code [here](https://github.com/emmaglorypraise/Oak-dApp-Automaty-Project).

Note: You have to have polkadot.js extension installed to use dApp.

That’s all for now, thank you for reading

Until we meet again, 

Adios!
