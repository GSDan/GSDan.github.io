---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: project
title: OurPlace
bannerImg: /assets/img/ourplace_banner.JPG
featureImg: /assets/img/ourplace_featureImg.png
summary: OurPlace is the main project of my PhD. It's a mobile learning platform, designed to support communities in creating and sharing interactive learning activities about the places they care most about.
heroColour: "#8BC04C"
github: https://github.com/GSDan/OurPlace
google: https://play.google.com/store/apps/details?id=com.park.learn
apple: https://itunes.apple.com/us/app/ourplace/id1378985779?ls=1&mt=8
---

### **_How can mobile learning technologies better surface and utilise the civic value of places and empower the communities which give them meaning?_**

## About the App

OurPlace is a mobile platform which supports the creation, sharing and
completion of highly customisable mobile learning activities. These activities
are built by combining together bite-size modular tasks, which can each ask the
user to perform a particular action. Tasks can ask the learner to take photos or
video, record an audio clip, listen to a given audio clip, match an existing
image (by comparing to an image overlay), draw a picture, draw on top of an
existing image, mark locations on a map, navigate to a given location, answer a
multiple choice question or simply read a piece of text.

This functionality is further expanded by supporting ‘follow-up’ tasks, which
become available to the learner once another task has been completed. For
example, an activity might ask the learner to walk to a particular location
where, upon arrival, follow-up tasks ask them to document their thoughts through
photos and an audio recording. Once created, activities can be shared in
numerous ways. The [accompanying website](https://ourplace.app) supplies QR
codes which can be printed and launch the activity when scanned. Users can also
enter given share codes, or launch activities when nearby the location
activities have been optionally tagged with.

The 'native' applications were developed in Xamarin Android and Xamarin iOS,
with the REST server running Web API 2.0 and an ASP.Net website. Because the
whole project is written in C#, each component can share common code and be
opened from the same Visual Studio solution. The OurPlace project is
open-source, and [can be downloaded from my
GitHub](https://github.com/GSDan/OurPlace).

## OurPlace in HCI Research

OurPlace--and its precursor, ParkLearn--was developed using a participatory and
iterative design process with multiple stakeholders, including local community
experts and enthusiasts, school teachers and students. The research aims to
explore how approachable mobile learning technologies can support stakeholders
in creating their own bespoke, interactive resources to share their values and
knowledge with others. Over the course of the project we ran small design
workshops with park rangers and teachers, mixes of short and longitudinal
studies with local schools and ethnographic studies with local heritage groups.
I've organised open invitation workshops and events for community heritage
enthusiasts, with the largest OurPlace workshop attracting nearly 50 attendees
from around the North of England. 

The app has been used by community members and schools in contexts ranging from
local parks to lighthouses, and from zoos to castles. Much of the research to
date is covered in detail in the publications listed below. We are currently
exploring how technologies like OurPlace can help facilitate cultural exchanges,
with children in different communities sharing and comparing their ways of life,
beliefs and values. We hope that this work will be published at CHI 2020.

![Schoolchildren design OurPlace activities using a jigsaw
activity](/assets/img/ourplace_jigsaw.JPG) *Schoolchildren use a custom jigsaw
to prepare paper prototypes while designing their OurPlace activities*


## Resulting Publications

<ul class="paper_list">
        <li>
            <p class="paper_title">Exploring Public Places As Infrastructures for Civic M-Learning</p>
            <p class="paper_detail">Dan Richardson, Clara Crivellaro, Ahmed Kharrufa, Kyle Montague, Patrick Olivier</p>
            <p class="paper_detail">2017 | International Conference on Communities and Technologies | <a
                    href="https://doi.org/10.1145/3083671.3083678" target="_blank">DOI</a> | <a
                    href="/assets/pdf/ExploringPublicPlacesAsInfrastructuresForCivicMLearning.pdf"
                    target="_blank">PDF</a></p>
        </li>

        <li>
            <p class="paper_title">Parklearn: Creating, Sharing and Engaging with Place-Based Activities for Seamless
                Mobile Learning</p>
            <p class="paper_detail">Dan Richardson, Pradthana Jarusriboonchai, Kyle Montague, Ahmed Kharrufa</p>
            <p class="paper_detail">2018 | International Conference on Human-Computer Interaction with Mobile Devices
                and Services | <a href="https://doi.org/10.1145/3229434.3229462" target="_blank">DOI</a> | <a
                    href="/assets/pdf/ParkLearnCreatingSharingEngagingwithPlace.pdf" target="_blank">PDF</a></p>
        </li>
    </ul>