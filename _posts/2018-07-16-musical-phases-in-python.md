---
layout: post
title: Musical Phases in Python
---

Hello, all!

For a couple days I've been making a simple script that will loop between
portions of a track, with a transition phase that goes between them. I've
always been interested in the workings of boss battle music, and how they
embody the dramatic character you're fighting against, or portray a
lyrical representation of the conflict between the player's character and
their enemy.

Boss music can be fantastic, take [MG RAY](https://youtu.be/f3bHENs9-2A)
from <em>Metal Gear Rising: Revengeance</em>,
[Jeanne](https://youtu.be/zSsXXrlkYEI) from <em>Bayonetta</em>,
the [Abyss Watchers](https://youtu.be/vv_qryPwmig) in <em>Dark Souls 3</em>,
[The Chain](https://youtu.be/pl4g_r6ryxU) from <em>Furi</em>,
and the classic [Vergil](https://youtu.be/09IpDe7V8ZE) from <em>Devil
May Cry 3</em> all accompany a proper challenge with a phenomenal soundtrack.

In all honesty I don't recommend looking at these videos if you have <em>any</em>
interest in playing those games, as these boss fights are incredible to go
through without any knowledge, beforehand. Nevertheless, It's always exciting
to hear these tracks over and over again even while you're getting
mauled, and sometimes humiliated by the aforementioned DMC3 when you die
enough times:

![placeholder](https://i.imgur.com/LliVm.jpg "DMC3 Kicks Your Ass...")

Now, onto the project. If you notice from the videos (or if you remember the
tracks), some of these songs go through multiple set piece phases that get
more climactic as you progress. It's another reward/incentive for the player
as the game tests your skills against a gatekeeping boss. I wanted to emulate
that for what will probably be applied to a future project (not sure yet...),
so I whipped something up in Python to get the job done.

Since I'm mostly working with video game OSTs, I used the pygame module for
its [mixer](https://www.pygame.org/docs/ref/mixer.html) capabilities. PyGame's
<code>pygame.mixer</code> module has a wealth of channels available for sound
playback, as well as a special channel for streaming music. Knowing that, I
could give portions of a song I want (in .ogg) looped to the music channel, while I send
transition sounds and portions to a channel in order to keep those entities separate.

Unfortunately, I don't have the abilities to automatically find loop points in
a song, but that doesn't mean I'm not trying to learn how at some point! Since I
am finding these points manually, I just popped the song I wanted open in Audacity
in order to cut up the track into the parts that I want, and record these into
a .csv file.

![placeholder](https://i.gyazo.com/fd90bae1dca1d3dabe9098897d1e4a20.png "Look at those tracks")
![placeholder](https://i.gyazo.com/030a006de2b0409944e18a5147eef0bd.png "A file that will be loaded in")

Each track aside from the top one is a part I wanted to either loop (1), or make a
transition into the next loop (0). Now that I have the timings, I needed to find a way
for the channels to play the proper portion of the song I was loading. Thankfully,
there's a wonderful interface called [PyDub](https://github.com/jiaaro/pydub) that
allows you to easily manipulate audio that will suit your needs. The song will be
loaded in through PyDub, and cut based on the timings placed in the file mentioned
above. These portions will then be queued in the order the user wrote down, and are
now loaded into the proper channel when they are needed!

![placeholder](https://i.gyazo.com/3f00ceb79e70638423782ccbd77d234d.png)

It's super simple to cut a song based on the milliseconds you have loaded in,
as shown in the fourth line of the image. When all the music is queued up, a
transition phase will (hopefully) seamlessly cut into the next loop, and whenever
the user desires they can fade into the next transition track.

Before I close, I'd like to talk about limitations and future plans. As of writing
this, you can only start and end a queue with a transition phase. You also can't
transition a looped phase with another looped phase, and likewise with
transition phases. I hope to change this soon to give the user more flexibility with
how they want to order the parts of the song they want. I hope to accept more
audio formats (although the output will still probably be .ogg files).

As said before, I think something that's a ways away is to automatically find
loop points in a song based on what the user wants to be the starting point. Once
I become more experienced I'll be sure to tackle this problem and see the
opportunities it brings.

This was a fun, small project to get started on, and I'm happy with its first
major version. Thank you for reading!

<strong>NOTE: I am cleaning up the code a little bit to make it more readable.
I'm planning on uploading it to GitHub very soon!</strong>

<em>Also if you have any cool songs to share or any thoughts at all, feel free to
share them below.</em>
