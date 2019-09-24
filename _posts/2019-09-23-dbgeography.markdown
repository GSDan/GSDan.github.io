---
layout: post
title:  "An Intro to DbGeography: the Importance of Looking Before You Leap"
date:   2019-09-23 13:54:45 +0100
image: location.png
categories: development c# ourplace
---

One of the main features of [the OurPlace app](/ourplace) is that created
Activities can be designated as being related to a given location. For this to
be of any real use, [the OurPlace API](https://github.com/GSDan/OurPlace) needs
to be able to query these locations and return which ones are closest to a
given latitude/longitude point. This is something I hadn't had to do before.

"_Ok_", I thought. "_Let's look up how we go about measuring the distance
between two lat/long points. I bet it's more complicated than you would think,
because they're on the surface of a globe, not on a 2D plane._"

Low and behold, [the answer](https://stackoverflow.com/a/27943) is miserable:

{% highlight c# %}
public static double GetDistanceBetween(double lat1, double lon1, double lat2, double lon2, char unit)
{
    double theta = lon1 - lon2;
    double dist = Math.Sin(deg2rad(lat1)) * Math.Sin(deg2rad(lat2)) +
                  Math.Cos(deg2rad(lat1)) * Math.Cos(deg2rad(lat2)) *
                  Math.Cos(deg2rad(theta));
    dist = Math.Acos(dist);
    dist = rad2deg(dist);
    dist = dist * 60 * 1.1515;
    if (unit == 'K')
    {
        dist = dist * 1.609344;
    }
    return (dist);
}
private static double deg2rad(double deg)
{
    return (deg * Math.PI / 180.0);
}
{% endhighlight %}

"_Jesus, that looks expensive_", I mutter. "_I sure as hell don't want that to
run against every row in my dataset. I need to divide and conquer._"

And so I did. Knowing that the [Google Places
API](https://developers.google.com/places/supported_types) could return
localities which pertain to wider areas, I decided that I would keep a separate
database table of those to apply the above operation on. Then, places within
that locality could be searched against. This would avoid having to run the
operation on every row in the `Places` table, but introduced a separate
(otherwise unused) `PlaceLocalities` table and utilised some pretty
horrible, maths-ridden code which--to be frank--I don't fully understand.

But... it worked. Was it performant? Probably not. But I could feed my API the
user's location, and it would return any Activities that had been made within
3km--without querying the entirety of the `Places` table with some disgusting
maths operations. And so I left it.

Two years later, through some absent-minded Google searching, I stumbled upon the [SQL
Spatial
Types](https://docs.microsoft.com/en-us/sql/t-sql/spatial-geography/spatial-types-geography?view=sql-server-2017).

_Bugger._

It turns out that there's a data type made _for the exact thing I wanted to do_,
and it could even be used with Linq. All I needed to do was add a new column of
the DbGeography type into my database, and instantiate it by feeding the lat &
long into the constructor. You can then use a built-in `Distance` function to
get the distance between it and another point:

{% highlight c# %}
DbGeography pointA = DbGeography.FromText(string.Format("POINT({1} {0})", latitude1, longitude1));  
DbGeography pointB = DbGeography.FromText(string.Format("POINT({1} {0})", latitude2, longitude2));

double? distanceInMeters = pointA.Distance(pointB);  
{% endhighlight %}

Using this, you can search, filter and order results according to their distance
from a target:

{% highlight c# %}
IEnumerable<Place> places = db.Places.Where(pl => pl.Location.Distance(thisLoc) <= 3000).OrderBy(pl => pl.Location.Distance(thisLoc));
{% endhighlight %}

Implementing this in OurPlace (including updating the existing places which had
been posted over the last two years to use this new column) took all of 30
minutes.  I don't remember how much time I spent on the other method, but it was
a lot longer than that.

The lesson learned? Check that the wheel hasn't already been invented and
included in a standard library before getting your chisel out.