---
layout: post
title:  "Minivan Life and Youtube Content Creation"
date:   2023-03-13 12:18:39 -0400
categories: jekyll update
tags: youtube cars dara
---

<h2> The Minivan Life </h2>

Once again, it's been almost a full year since I wrote a post! So what's happened in the last year? For awhile, I was doing a great job of maintaining my physical health via the gym and weekly basketball. That kind of fell by the wayside when I started a new job Sep 2022 and my life got a lot busier, but that's probably just a poor excuse I give myself to be lazy... 

In other news, I bought a minivan:

![tnc1](/assets/cars/tnc1.jpg){:.center-size-image}

![tnc2](/assets/cars/tnc2.jpg){:.center-size-image}

![tnc3](/assets/cars/tnc3.jpg){:.center-size-image}

So why did I, an acknowledged gearhead, buy the most boring car imaginable? Well, I've come to conclusion that minivans have been unfairly cast as boring cars. They are actually purpose-built machines, it just so happens that the purpose is not to make driving engaging or enjoyable, but to ferry precious cargo (children) around. And to end, it excels, the side skirts on the sliding doors so the little ones can crawl in, the sliding doors so they don't slam other people's cars on opening, the accessibility of the interior space and maneuverability of the seats. In fact, I actually want to see car companies develop and market a luxury minivan. Imagine a Lexus minivan with the comfort and opulence of an LS in minivan form... how glorious would that be (before anyone bites my head off, I know Mercedes has a minivan but it is trash).

One of the main reasons I decided to buy the minivan is that Deckard is rapidly outgrowing his carseat. So our two kids, have 4 car seats between them... originally, Dara had two carseats, one for each car. Then when she outgrew them, we got her 2 more, one for each car. Now Deckard is outgrowing the car seats and I simply cannot justify buying more carseats. So what do we do? Move bulky car seats between cars as needed? No... we buy a minivan. And so, I have ascended to full dad-mode as I cruise in my minivan, outfitted with car seats, dedicated to the mission of shuttling children.

<h2> Youtube Content Creation </h2>

So why did it take me so long to write another post? Well, content creation is hard. I think we often take content creation for granted. We live in a time of plenty, where we no longer need to wait on a weekly basis for television shows to be released. Where we binge TV, sort new subreddits by `Top: all time`, slice through new youtube channels like butter, and generally just consume incredible amounts of content. But how much effort went into making that content? Based on my recent experiences uploading Dara and my videos to youtube, a lot.

![ac_odyssey](/assets/video-games/ac-odyssey.jpg)

Dara and I have been playing video games together since she was a wee little girl. She'd sit on my lap as I explored the beautiful worlds of [Assassin's Creed: Odyssey](ac-odyssey) and embarked on the "entirely-too-silly" adventure that is [Saint's Row 4](saints-row-4), or as Dara calls it, "Purple Game". I cherish these moments and in an effort to capture them, I decided to use a webcam and start recording some of our gaming sessions. Over the years, I've been accumulating this collection of unedited, unfiltered videos of Dara and I playing games together. And so, I finally decided it was time to upload them to [youtube](our-yt-channel)

![saints_row_4](/assets/video-games/saints_row_4.jpg)

And so that's what I did, but I quickly hit a snag, the 15-minute video time limit. Of course, I tried downloading some video editing tools to cut the videos but man, those tools are so full-featured and their UI so cluttered I couldn't figure out how to do my simple operation. So what'd I do???

```python
from moviepy.video.io.ffmpeg_tools import ffmpeg_extract_subclip
from moviepy.editor import VideoFileClip

from sys import argv

# Replace the filename below.
required_video_file = argv[1]
target_video_file = required_video_file.replace(".mp4", "_{}.mp4")

video = VideoFileClip(required_video_file)
video_duration = video.duration

stride = 720  # 600s = 10m
overlap = 5 # 5s video overlap
n_chunks = int(video_duration // stride + 1)

print(video_duration)
print(n_chunks)

starts = [(i * stride) - overlap for i in range(n_chunks)]
print(starts)

for i, start in enumerate(starts):
    ffmpeg_extract_subclip(required_video_file, start, start + stride, targetname=target_video_file.format(i))
```

And just like that, I had perfect control over what I wanted to do, and I was able to loop through all the videos to generate their cut components. It's also worth mentioning the the process of uploading and embellishing videos to youtube is very fun and their UI is quite intuitive, overall, I enjoyed the process but definitely see how managing an active youtube channel can be a full-time job. 

If you're looking for something to do, check out [our youtube channel][our-yt-channel] and don't forget to like and subscribe!


[ac-odyssey]: https://en.wikipedia.org/wiki/Assassin%27s_Creed_Odyssey
[our-yt-channel]: https://www.youtube.com/channel/UCQMfWHivvPp_raxqzejaJZg
[saints-row-4]: https://en.wikipedia.org/wiki/Saints_Row_IV


