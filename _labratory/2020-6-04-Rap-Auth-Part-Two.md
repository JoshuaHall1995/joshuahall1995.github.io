---
layout: post
title: Rap Authentication - Part One - Spittin Bars
permaLink: /2020-6-04-Rap-Auth-Part-Two/
---
Before I can even consider authentication I need to make sure my voice can be heard and acknowledged. A simple speech to text service is required, something the Microsoft Speech Api can easily cover...

And that Macs hate if you are trying to do it for a console app. Atleast in my short experience.

EXPLOSION ONE!
The Speech Recognition API has some easy to follow setup examples. Within 10 minutes I was good to go.

<h6>Details here: https://github.com/Azure-Samples/cognitive-services-speech-sdk/tree/master/quickstart/csharp/dotnetcore/from-microphone</h6>

And then “NOMATCH: Speech could not be recognized.” arrived and my day got less fun. The smart thing about the RecognizeOnceAsync method is that it is designed to pick up audio automatically. No hassle all positive vibes. 

With a Mac the microphone setup/ permissions is more complicated. They have solutions like “AVCaptureDevice” as Xamarin supported packages to be able to create virtual wav files which can then be passed onto the Speech Recognition API. 

But who likes Xamarin. Straight away my rap buddy got more complicated.

If I was worried about looking like a know it all I would mention the solution to the problem. But like all good programmers, I adapted and overcame. In other words, like the jar of olives at the back of the fridge creating life, I pushed the issue to the back of my brain and worried about something else.

Specifically, if I was going to authenticate via raps I needed a way of creating and identifying them. 

A quick google and I discovered the RhymeBrain api, and this told me that apparently rhyming has different values for strength of the rhyme with 300 or above a perfect rhyme. Naturally all of my rhymes are 300 quality.

<h6>(Details here: https://rhymebrain.com/api.html)</h6>

I created a nice iRhymeRepository as I was not sure if I would use a third part or my own in the long term and because I recall a senior friend of mine hating interfaces and it has since always reminded me of their existence. 

Console Application rolled up, the test delayed and I was in a world of wonder and excitement passing down my “hello” to rhyme with my hardcoded string.

<i style="text-align:center">“And to you all I say hello,
Money on tap, the crowd get low” </i>

Was my expectation. Hell I would have accepted:

<i style="text-align:center">“And to you all I say hello,
Money on tap, the crowd get buffalo” </i>

Instead I got a poetic,

[<img src="{{ site.baseurl }}/images/roadBed.png" alt="Roadbed" 
    style="width: 400px; 
    display: block;
    margin-left: auto;
    margin-right: auto;"/>]({{ site.baseurl }}/)

Free third party API giveth, three third party API taketh away.

Thankfully because I had decoupled what I was doing because I have inherent trust issues and believe every person, place and code base will let me down.

I switched it out for the equally well named RhymeZone, which even had its score returned as an integer. Basically an upgrade.

<h6>(Details here: https://www.datamuse.com/api/)</h6>

For rap, since the high level skills can’t all be generated from my own brain directly, I needed a way of creating test bars. 

[<img src="{{ site.baseurl }}/images/exampleBars.png" alt="Txt file of bars" 
    style="width: 400px; 
    display: block;
    margin-left: auto;
    margin-right: auto;"/>]({{ site.baseurl }}/)

I added a few test lines in a text file as part of a implementation of a IWordRepository. One day these files of pre stored rap templates and adjectives, verbs etc could be stored somewhere nicer. For now they live in a dirty text file in my solution.

Now I had the template it was fill me up time. With a quick google and some adorable points of reference I rediscovered what a verb, noun and adjective were and set up an easily identifiable string placeholder to replace later.

For now efficiency is less important than pure fire. People wait years for a rap album, they can wait a second for my autogenerated bars.

[<img src="{{ site.baseurl }}/images/WordRepo.png" alt="WordRepo" 
    style="width: 400px; 
    display: block;
    margin-left: auto;
    margin-right: auto;"/>]({{ site.baseurl }}/)

I reused the TextWordRepository, passing in the type of word I was using, as a way of avoiding making half a dozen classes I would only temporarily implement as I messed around. Imagine all the test cases, disgusting. 

From there my templates could be called and filled and the console became my playground. 

[<img src="{{ site.baseurl }}/images/isItRhyme.png" alt="IsItRhyme" 
    style="width: 400px; 
    display: block;
    margin-left: auto;
    margin-right: auto;"/>]({{ site.baseurl }}/)

For the final part of step one I decided my happy little rap generator needed some substance. So I added a IsItARhyme method. So upon populating three fire bars I could prompt a user for a final which will one day be speech inputted. If the final word is not atleast a 250 it is not a Josh worthy bar and access denied. 

[<img src="{{ site.baseurl }}/images/unauthShot.png" alt="Unauth" 
    style="width: 400px; 
    display: block;
    margin-left: auto;
    margin-right: auto;"/>]({{ site.baseurl }}/)

[<img src="{{ site.baseurl }}/images/authShot.png" alt="Unauth" 
    style="width: 400px; 
    display: block;
    margin-left: auto;
    margin-right: auto;"/>]({{ site.baseurl }}/)

With that I had it. The base portion of a phrase based authentication method which included a butchered line from “New York State of Mind”. It didn’t know who provided the fire but it knew it was hot enough to access what it wanted. For now it did the job.

Now to really populate it with templates and to take my sweet sweet vocals and put them onto the console. But that is for another post. 