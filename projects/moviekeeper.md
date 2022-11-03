---
layout: project 
title: MovieKeeper 
bannerImg: /assets/img/moviekeeper_banner.webp
summary: MovieKeeper is a mobile app which makes it easy to keep track of your physical movie library
heroColour: "#f24e56" 
featureImg: /assets/img/moviekeeper_featuredImg.webp
---

In an effort to teach myself React Native (and because I kept nearly buying multiple 
copies of the same movie), I developed MovieKeeper: a smartphone app designed to make 
it easy to document, rate, and sort your physical movie library.

## What does MovieKeeper do?

The app lets you create and manage a library of movies and TV shows.  It's been developed
with both smartphones and tablets in mind---if you have a tablet, MovieKeeper takes advantage
of the extra screen real estate to show high quality posters of your collected movies. 

An item can be added to your library either by scanning its barcode, or by searching for its title. 
If it's something that a user hasn't previously added, the system attempts to find it through
a combination of the eBay API and IMDB, returning a set of potential matches for the user to
choose from.

Once an item has been added, you can track what formats you own it on (DVD, Blu-ray, or UHD),
give it a rating, and, if it's a TV show, select what seasons you own.

The system pulls in a variety of information from IMDB and OMDB, allowing the app to offer 
multiple sorting and filtering options. You can sort by items' titles, user ratings, Rotten
Tomatoes percent score, IMDB user score, running time, or release year. You can filter items by
disc format, genre, or their age rating. The profile page offers some fun statistics about your
library, such as: the total combined running time of all your movies, the average IMDB score,
and a breakdown of your library by genre.

## MovieKeeper's archetecture

The open source codebase for the whole MovieKeeper platform [is available on GitHub](https://github.com/GSDan/MovieKeeper).

The MovieKeeper mobile application was produced in React Native, using the [Expo framework](https://expo.dev/).
While Expo supports building cross-platform, native applications for both Android and iOS, due to
a lack of Apple build tools it's currently only available for Android, 
[on the Play Store](https://play.google.com/store/apps/details?id=me.danrichardson.moviekeeper).

The platform's backend is created through Firebase, which handles user authentication, the 
platform's API service (Firebase Functions), and the database (Cloud Firestore). To respond to 
user queries, the API can interact with several external services, including eBay, IMDB, and OMDB.

## The process for looking up a disc's barcode

Unfortunately there isn't an affordable, easily accessible and well-populated repository or API 
available for querying movie barcodes. 

![Paroli's system overview](/assets/img/moviekeeper_flow.webp)

To overcome this, when a user scans a barcode not previously recorded in the system, MovieKeeper 
searches the eBay API for listings corresponding with products eBay has associate with that barcode.
The MovieKeeper API then processes the resulting listings, removing common phrases (e.g. 'Brand New', 
'Sealed', 'free P&P') in an attempt to determine the movie's title. To make this more reliable, the 
first three listings are also compared to find any common words between them. The titles are also 
searched for any clues which can be used to guess the disc's format (e.g. 'ultra HD', 'HDR'). Once a
potential title has been found, IMDB is searched, and the user is presented with the potential matches.