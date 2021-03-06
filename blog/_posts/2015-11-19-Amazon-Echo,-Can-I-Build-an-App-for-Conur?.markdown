---
layout: post
title:  Amazon Echo, Can I Build an App for Concur?
date:   2015-11-19
tags:
  - Business-Travel
author: Chris Trudeau
---

Want to use Amazon Echo to ask about upcoming business trips? It’s easy. The [Alexa Skill Kit][alexa-skill-kit] enables you to build Echo apps that can call APIs, including Concur APIs. Here’s a quick overview of how to integrate Alexa Skill Kit with the Concur JS SDK to enable travelers request details on their next trip. Sample code referenced is also available on [Github][github].

### What Kind of Functionality Can I Create?

You can have Alexa provide information on upcoming trips in Concur—and then add functionality to ask Alexa about travel destinations, flight arrival and departure times, car service details or any other data related to trips in Concur.
For example:

User: “Alexa, ask Concur: when is my next trip?”
Alexa: “Your upcoming Concur trip is <TripName>”

### Development Process

Development is fairly straight-forward if you’re using NodeJS. Be sure to look at invocations and intents for an overview of how the voice interface works. For Alexa services, a user calls “intents” (or requests) with their voice, while “invocations” are the name of the functions requested.

By creating an IntentSchema for the skill (in this case, “when is my next trip”) and SampleUtterances, and then using the Concur SDK, you can retrieve a list of trips for a specific user as you see below. Then you can create new intents to add more functionality, such as details on hotel, transportation and flight plans or any other information available via the [Concur Itinerary API][concur-itinerary-api]. One issue to note with this integration is that it does not support Oauth, which means it only works for a single user token.


{% highlight ruby %}

//This will contain a list of Itineraries
  var options = {
oauthToken:oauthToken


{% endhighlight %}

{% highlight ruby %}

concur.itinerary.get(options)
.then(function(data) {
  // Data will contain the Itinerary
})
.fail(function(error) {
  // Error will contain the error returned.
});

{% endhighlight %}

I’ve enjoyed working with the Amazon Echo and use it at home to control my lights and thermostat and even as a radio. Now I can use it to organize my trips.

Find out what else you can create with Alexa and Concur. Here’s links for more information:


[Alexa Skill Kit][alexa-skill-kit]
[Concur Itinerary API][concur-itinerary-api]
[Concur Developer][concur-developer]


[alexa-skill-kit]: https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/getting-started-guide
[github]: https://github.com/concurlabs/amazon-echo-concur
[concur-itinerary-api]: https://developer.concur.com/api-reference/travel/itinerary/itinerary.html
[concur-developer]: https://developer.concur.com
