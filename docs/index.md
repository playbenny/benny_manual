<style>
  .md-typeset h1,
  .md-content__button {
    display: none;
  }
</style>
![benny logo](assets/benny_logo_400T.png){ align = left }

benny is a modular software playground for making live music.

it seamlessly integrates hardware and software, midi and audio, lets you connect anything to anything and extends flexibly into polyphony.

benny is a good place to host your own max/msp patches, but you don't need to know max to get started.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Hs_4T_gjoWw?si=Yg87wI-I_sjNP9u-" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## About

I [(James)](https://www.jamesholden.org/) made benny because it didn't exist and I wanted it. It's my personal project, designed around my ideas and priorities. I've been using benny for my live sets since early 2023, but it is an ongoing work in progress.

*I wanted a low distraction interface that is easy to glance at (while performing) and tries to avoid imposing any hierarchical decisions on the user (no global timeline, no pre-defined mixer structure etc).*

Benny is free to download and use. It is open source and you are free to use [the code provided](https://github.com/playbenny/benny/) in other projects, as long as those projects also come with the same [license](https://github.com/playbenny/benny?tab=License-1-ov-file) terms. 

If you want to get involved there are lots of ways users of all levels can [contribute](contributing.md). And if you find benny useful and you can afford it, the tip jar is [here](https://www.paypal.com/donate/?hosted_button_id=PBQ7JWRPJKLWQ).

## Acknowledgements

benny relies on several other people's work and ideas.

- [Cycling74](https://www.cycling74.com) who build max/msp and generously let it run as a free runtime environment.
- [Chris Airwindows](https://www.airwindows.com) whose open source code is an excellent learning resource and also used in various benny blocks.
- [Isabelgk](https://github.com/isabelgk/airfx) for porting the airwindows VSTs into native max externals.
- [Surreal Machines](https://www.surrealmachines.com/) whose gen filter models are used in a few places in the provided audio blocks.
- [Ernest Meyer](https://www.yofiel.com) whose advanced max + gen tutorials on the c74 forums were instrumental in working out benny's efficient modulation routing system, and whose EPTR oscillator code is used in various places to provide very clean rectangle waves (which are integrated to provide very clean triangle and saw waves too).
- [Luke Abbott](https://en.wikipedia.org/wiki/Luke_Abbott) for extensive input, inspiration and testing.
- Michael Terren as I found [this](https://disclaimer.org.au/contents/where-and-how-to-gather/the-hegemony-of-the-daw) essay and others inspirational.
- [Oskari Tamellin](http://jeskola.net/) who wrote [Jeskola Buzz](http://jeskola.net/buzz/), the first music software I ever used and a huge inspiration for benny's design.