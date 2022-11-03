---
layout: project 
title: Paroli 
bannerImg: /assets/img/paroli_banner.webp
summary: Paroli is a web-based platform, designed to support organisations in running group activities with offline participants through standard phone calls.
heroColour: "#5526e4" 
featureImg: /assets/img/paroli_featuredImg.webp
---

I lead the design, development and research for *Paroli*: a digitally-augmented
telecoms platform designed to support remote group engagements where participants 
have little access to Internet infrastructure. One of Aciton Lab's core projects, 
Paroli is currently deployed in Australia, Bangladesh, and Nepal with our 
international NGO partners.

## What is Paroli?

Through the use of Interactive Voice Response (IVR) technology over standard phone 
calls, Paroli makes it possible for organisations to host remote, structured group 
engagements---without requiring participants be able to read, write, have Internet
access or own a smart device. A single host user organises and manages the call 
through a web interface, allowing them to invite, drop, mute, and unmute participants
during the call. Through button presses on their phone's keypad, participants are 
able to mute themselves and put their hand up to request to be unmuted. 

To support recordkeeping, creation of content such as podcasts, and detailed 
post-analysis of partipants' engagement during the call, the system keeps detailed 
logs regarding participant actitivity (e.g. speech utterances, button presses), and
each participant's audio is recorded into separate files alongside the primary 
conference recording.

The digitially-augmented nature of Paroli also means we can support interactions that 
would ordinarily be impractical or impossible on a standard phone call. For example, 
the call host is able to create polls, where the participants use their dialpads to 
vote on different options. The call's topology can also be manipulated to support 
different interaction archetypes: for example, Zoom-style breakout rooms can be manually 
used to support remote workshops with group activities, or could be programmatically
manipulated to support round-robin pairings of participants in speed-dating interactions.


## Paroli's infrastructure
![Paroli's system overview](/assets/img/paroli_system.webp)

Paroli is a cloud-based platform which utilises an variety of technologies and archetectures.
The open source codebase [is available here](https://gitlab.com/action-lab-aus/phoneconferencing).

### Firebase Realtime Database (RTDB), Functions, Authentication and Storage

Paroli makes extensive use of Google Firebase. Firebase RTDB is used to store all user and 
call-based data, including user accounts, contacts, and interaction logs. Serverless Firebase 
Functions are used when the website should alter elements in the RTDB: for example, creating 
new conference calls, muting a user, or dialling a new participant. Call recordings and audio
prompts are stored in and retrieved from Firebase Storage, and are converted to appropriate 
file formats via automated Functions.

### Web Interface

Call hosts interact with the platform through a Vue.JS website. The web interface subscribes 
to the RTDB, meaning that any changes are displayed to the host in realtime. The website's 
interactions with the RTDB are kept read-only, and any changes are requested via the Firebase
Functions API. As hosts are likely to use the system from a variety of contexts, Paroli's
website has been designed to be fully usable across desktop, tablet, and smartphone screen sizes.
If the host's internet is stable, they can also opt to join the call through the website via 
WebRTC, rather than use their own phone.

### FreeSWITCH and the Node.JS Server App

A separate server (typically deployed on an AWS EC2 instance) contains the core phone logic.
The open source platform *FreeSWITCH* is a programmable software PBX, and is used to initiate, 
receive and manage calls through SIP via both WebRTC and the PSTN (via an external SIP trunk).
A separate Node.JS application is used to subscribe to changes to the RTDB. When a new instruction
has been received from the database, the application commands FreeSWITCH to perform actions via 
its CLI. The application also listens to FreeSWITCH's output for new data (e.g. user interactions)
 to write to the RTDB.

As the installation and configuration of FreeSWITCH can be a long and sordid affair, 
I prepared [an Ansible script](https://gitlab.com/action-lab-aus/phoneconferencing/freeswitch-deployment) 
to make deployment easier.