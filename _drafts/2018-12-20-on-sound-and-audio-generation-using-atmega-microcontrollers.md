---
layout: post
title: On sound and audio generation using Atmega microcontrollers
tags:
- electronics
- coding
feature-img: assets/img/oie_baNTtLXGH28C.jpg
thumbnail: ''
date: '2018-12-20T05:28:25.000+00:00'
excerpt_separator: "<!--more-->"
enableNepali: false

---
I recently made a circuit to demonstrate audio generation using an atmega32a microcontroller and even though mostly knew the concepts involved, I ended up learning loads.

For one, I learnt that matrix boards are very annoying when dealing with microcontroller pins. I ended up really messing up the circuit's backside because I hadn't planned beforehand (Did I mention that this is my first time using a matrix board?).

<!--more-->

Next, I learnt that CR2032 batteries don't last long. I really don't know how it happened, but I had two nearly fresh CR2032 batteries which both ran out in the span of two hours. I mean, Atmega32a consumes around 8mA at 8MHz. The R-2R DAC had an equivalent resistance of 2k ohms if I remember correctly. The total current in the system can't have been more than 15 to 20 mA of current in the system at any given time. Granted, that's out of the specs of the battery, but it should have gone at least 4 hours.

I also found this nifty code to reverse bit order in a byte:

{% highlight c linenos %}
unsigned char reverse( unsigned char x )
{
x = ((x >> 1) & 0x55) | ((x << 1) & 0xaa);
x = ((x >> 2) & 0x33) | ((x << 2) & 0xcc);
x = ((x >> 4) & 0x0f) | ((x << 4) & 0xf0);
return x;
}
{% endhighlight %}

This is better than looping 8 times or something and also looks beautiful. Win-win. (I have no idea how this function works, though)

That is about all. The demo went nicely too. I think I will write a detailed post on all the things I had to do to get this to work, because I had to learn a lot of things before I got this kind of system working the first time (most of the troubles had to do with converting audio into samples).