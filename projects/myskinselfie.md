---
layout: project 
title: MySkinSelfie 
bannerImg: /assets/img/skinselfie_banner.webp
featureImg: /assets/img/skinselfie_featureImg.webp 
summary: MySkinSelfie makes it easier to keep track of how your skin conditions change over time. I developed the platform while I was a Research Associate in Open Lab, Newcastle University.
heroColour: "#00BCD5" 
github: https://github.com/GSDan/MySkinSelfie 
google: https://play.google.com/store/apps/details?id=skinselfie.droid 
apple: https://itunes.apple.com/vc/app/myskinselfie/id1096043432?mt=8
---

## About the App

I developed MySkinSelfie in collaboration with Consultant Dermatologist Dr
Philip Hampton. The app makes it easier for patients living with skin conditions
to keep track of how how they change over time, by assisting in taking
consistent photographs of their skin through an overlay system. 

Photos are organised by date, condition type and location on the body, making it
easier to track how they change over time through notes and a side-by-side
comparison tool. Taken images are stored in the cloud over a secure connection,
meaning patients can access them across multiple devices over periods of months
or years - perfect for long-term condition tracking.

All uploaded files are encrypted, meaning that patients can be safe in the
knowledge that no-one will get their hands on their sensitive images. Photos
deliberately kept out of your device's default image gallery in order to avoid
potential embarrassment, and users even have the option to lock the application
or individual photo albums behind a PIN.

The mobile applications were developed in Xamarin Forms, with the REST server
running Web API 2.0. Because the whole project is written in C#, each component
can share common code and be opened from the same Visual Studio solution.
MySkinSelfie is open-source, and [can be downloaded from my GitHub](https://github.com/GSDan/MySkinSelfie).

## MySkinSelfie as a HCI Research Project

The research goal of MySkinSelfie was to investigate if technology-assisted
patient-self monitoring---in combination with traditional healthcare
systems---could be used to ease the burden of unnecessary patient referrals upon
both the patients themselves and the UK's underfunded National Health Service.
The application was deployed within several NHS practices within the North of
England, with it being recommended to patients living with applicable skin
conditions. As well as an ongoing study within the NHS, several evaluations have
been undertaken and published. These evaluations showed that patients not only
found MySkinSelfie easy to use, but also genuinely useful for tracking the
progress of their skin conditions over time.

## Resulting Publications

<ul class="paper_list">
    <li>
        <p class="paper_title">Evaluation of MySkinSelfie: A New Mobile App for Patient Skin Self-Monitoring</p>
        <p class="paper_detail">Philip Hampton, Dan Richardson, Kyle Montague, Patrick Olivier</p>
        <p class="paper_detail">2017 | Journal of the American Academy of Dermatology | <a
                href="https://doi.org/10.1016/j.jaad.2017.04.504" target="_blank">DOI</a></p>
    </li>

    <li>
        <p class="paper_title">Usability Testing of MySkinSelfie: a Mobile Phone Application for Skin Self‐Monitoring</p>
        <p class="paper_detail">P Hampton, D Richardson, S Brown, C Goodhead, K Montague, P Olivier</p>
        <p class="paper_detail">2019 | Clinical and Experimental Dermatology | <a
                href="https://doi.org/10.1111/ced.13995" target="_blank">DOI</a></p>
    </li>
</ul>