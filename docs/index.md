<style>
  .md-typeset h1,
  .md-content__button {
    display: none;
  }
</style>
![benny logo](assets/benny_logo_400T.png){ align = left }

benny is a modular software playground for making live music.

it seamlessly integrates hardware and software, midi and audio, lets you connect anything to anything and extends into polyphony elegantly.

benny is a good place to host your own max/msp patches, but you don't have to know max to get started.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Hs_4T_gjoWw?si=Yg87wI-I_sjNP9u-" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## About

I [(James)](https://www.jamesholden.org/) made benny because it didn't exist and I wanted it. It's my personal project and designed around my ideas and priorities. I've been using benny for my live sets since early 2023, but it is an ongoing work in progress.

*I wanted a minimal, low distraction interface that's easy to glance at (eg while performing) which tries to avoid imposing any hierarchical decisions on the user (eg it has no global timeline, no pre-defined mixer structure, etc).*

Benny is free to download and use. It is open source and you are free to use [the code provided](https://github.com/jamesholdenmusic/benny/) in other projects, as long as those projects also come with the same [license](https://github.com/jamesholdenmusic/benny?tab=License-1-ov-file) terms.

## Contributing

### Donate
- If you find benny useful and you can afford to donate, the tipjar is [here](https://www.paypal.com/donate/?hosted_button_id=PBQ7JWRPJKLWQ).
### Report bugs
- Create a new bug report [here](https://github.com/jamesholdenmusic/benny/issues).
- A good bug report contains a clear description of the problem and steps or attached files to reliably reproduce it.
- In many cases, benny prints useful information to the max console. This may not be visible on your computer, but should come up if you press ctrl-shift-m while on the benny launcher window.
- If you're not sure, start by opening a [discussion](https://github.com/jamesholdenmusic/benny/discussions) instead.
### Fix bugs
- Create a new branch of the repository.
- Fix the bug in your branch.
- Submit a pull request to have your fix merged back into the main repository.
- Any questions or doubts, start a [discussion](https://github.com/jamesholdenmusic/benny/discussions).
### Contribute blocks
- It's very easy to make blocks. If you make something good and want it to be part of the public repository you are welcome to submit it. You can name your blocks with your own prefix if you want and that prefix will be given its own section of the blocks menu.
- Create a new branch, commit your block files to it, submit a pull request.
### Help with this manual
- This manual is a [separate github repository](https://github.com/jamesholdenmusic/BennyDocs). If you hit a problem or question that isn't answered here please do add your solution to the appropriate section of the manual.

## Acknowledgements

benny relies on several other people's work.

- [Cycling74](https://www.cycling74.com) who build max/msp and generously let it run as a free runtime environment.
- [Chris Airwindows](https://www.airwindows.com) whose open source code is an excellent learning resource and also used in various benny blocks.
- [Isabelgk](https://github.com/isabelgk/airfx) for porting the airwindows vsts into native max externals.
- [Surreal Machines](https://www.surrealmachines.com/) whose gen filter models are used in a few places in the provided audio blocks.
- [Ernest Meyer](https://www.yofiel.com) whose advanced max + gen tutorials on the c74 forums were instrumental in working out benny's efficient modulation routing system, and whose EPTR oscillator code is used in various places to provide very clean rectangle waves (which are integrated to provide very clean triangle and saw waves too).
- Michael Terren as I found [this](https://disclaimer.org.au/contents/where-and-how-to-gather/the-hegemony-of-the-daw) essay and others inspirational.
- [Oskari Tamellin](http://jeskola.net/) who wrote [Jeskola Buzz](http://jeskola.net/buzz/), the first music software I ever used and a huge inspiration for benny's design.