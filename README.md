# doughbat

doughbat is a very minimal livecoding editor. Principles:

- Minimal API
- Bring your own abstractions
- Just a single HTML file

You can use it here: <https://felixroos.github.io/doughbat/>

doughbat is the spiritual successor to [doughbeat](https://raw.githubusercontent.com/felixroos/doughbeat>), using [AssemblyScript](https://www.assemblyscript.org/) instead of JavaAscript.

## Usage

The application is very simple, you just have to write a `dsp` function that uses its only argument `t` (time in seconds) to calculate a number between -1 and 1.
The returned number represents the speaker position for that moment in time: 0 is the resting position while -1 and 1 are maximum in / out.
The `dsp` function will be called 44100 times per second! Example:

Example:

```ts
export function dsp(t: f32): f32 {
  return ((110 * t * 1.0) % 1.0) - 0.5;
}
```

This is a simple sawtooth wave... The returned numbers will rise from -0.5 to 0.5 at a frequency of 110Hz.
This is just a very basic example.
You can actually write full music pieces with this abstraction.

## Read More

To understand more about making music with maths, read my blog post series:

- <https://loophole-letters.netlify.app/buffers/>
- <https://loophole-letters.netlify.app/dsp-lvl1/>
- <https://loophole-letters.netlify.app/dsp-lvl2/>
- <http://localhost:3501/assemblyscript-dsp//>

## Credits

- [htmlbytebeat](https://github.com/greggman/html5bytebeat)
- [wavepot](http://wavepot.com/) inspired the `dsp` function (before it was just a `t` expression)
- [javascriptmusic](https://github.com/petersalomonsen/javascriptmusic/) inspired the use of assemblyscript for live coding
