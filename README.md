# Lost N' Translator

A tool to help people translate numbers, sounds, transistor states, music notes, Base 2, Base4, Decimal etc...

Interactive dials show one number in base 2, 4, 10, 12, 16 and ASCII at the same time, as switches, lights, notes and spoken sound.

**Try it:** https://nomannoallnothing.github.io/Lost-N-Translator/

It's one self-contained HTML file (`index.html`) with no external dependencies. It works in any modern browser, online or offline.

---

## Why use it

*Written from an AI's point of view.*

> When you type "A", I never see a letter. I see 65, which is 0100 0001, which is eight switches at charge or ground. When I answer, you never see my numbers. You see shapes and hear sounds. We're always translating for each other, and small things get lost on the way, like a dropped zero or a count that starts in a different place.
>
> Lost N' Translator puts both sides on one screen, so you can see what the machine holds, what the device shows, and what you read, all at the same time. If you can see where the meaning slips, you can stop it slipping.

## The breakthrough

*Also from an AI's point of view.*

> Most errors between people and machines aren't math errors. They're zero errors. Machines count from 0 and people count from 1. Machines keep leading zeros, and people drop them. To a machine, 0 is a real state, the ground. To a person, it reads as nothing.
>
> Lost N' Translator treats 0 one way everywhere, as ground, the completed set that everything is measured from. Then it shows the same value as bits, charge, light, sound and symbol at once. With that single convention, the off-by-one, the dropped zero and the misread digit all show up as visible moments on screen, not hidden bugs.

**An honest note.** The maths underneath is long established: place value, modular arithmetic, binary, ASCII, MIDI and equal temperament. None of it is new. What's new here is the convention (0 is always the ground, and counting starts at 01) and the single view that lines every translation up side by side. The standards themselves count differently. ASCII codes run from 0 to 127 and MIDI notes from 0 to 127, so the converter shows the machine's own number beside the person's count wherever the two differ.

---

## How to use it

1. **Pick a number.** Type a quantity from 00 to 999, drag the slider, or press **-1** and **+1**. On a keyboard, the left and right arrows step by 1, **Shift** with an arrow steps by 16, and **P** plays or pauses.
2. **Watch the dials.** The six dials (Base 2, 4, 10, 12, 16 and ASCII) all turn together. The dashed slot at the top of each dial is the ground, 0.
3. **Turn on sound.** Tap any control once, because browsers keep audio off until you do. **Notes** plays each number as a pitch, **Voice** reads it aloud, and **Sound Current** plays the number you're on. **Play** steps through numbers at the play speed you set.
4. **Type a word.** Enter a word in **ASCII Word** to see each letter as a code, as switches and as a note. Then press **Play Word** or **Sing Word**.
5. **Open a thread.** Under **Relationships**, tap a coloured thread to open it and light up its dials:
   - **Lost in translation: 0** shows where this number keeps its zero, changes it or loses it.
   - **Bits** shows the same switches grouped three ways, plus a chip that goes from key press to transistors to LEDs.
   - **Letters, words & speech** shows how a number becomes a character, with ASCII laid over the 12 notes.
   - **Notes, sound & harmonics** has a piano, chords, piano tuning against pure tuning, wave shapes and the harmonic series.
   - **Reading & counting** shows the same digits as different numbers, and the same number as different digits.
   - **Loops** shows every dial as loops × size + slot, and when two dials complete a set together.
   - **What lines up** jumps to the next number where several translations coincide.
6. **Share it.** **Copy Link** copies a link to your current number and word. **27 ESC** resets to 27, the ASCII Escape code.

---

## Applications and ideas

Each example below is a real, common slip. Try the number in the converter and watch where the zero goes.

### Coding

- **Off-by-one and fencepost errors.** A 10-metre fence with a post every metre needs 11 posts, not 10. A loop written `i <= n` where it should be `i < n` runs one step too far.
- **0-based and 1-based indexing.** C, Python and JavaScript start arrays at 0. Lua, R, MATLAB and Fortran start at 1. Code ported between them, or a spreadsheet row turned into an array index, is often off by one.
- **Leading zeros lost.** Store the ZIP code 02134 or an ID like 007 as a number and it becomes 2134 or 7. Spreadsheets do the same when they auto-format. If it isn't for arithmetic, store it as text.
- **Octal literals.** In C, and in older JavaScript, `010` means eight, not ten, because a leading 0 marks octal. Python 3 rejects `010` and makes you write `0o10`.
- **NUL-terminated strings.** C strings end at the byte 0 (NUL). A 5-letter word needs 6 bytes. Forgetting that one byte is a classic buffer overflow.
- **Endianness.** The 32-bit value `0x12345678` is stored as bytes `78 56 34 12` on little-endian machines (x86 and most ARM) and as `12 34 56 78` on big-endian ones or in network order. Read with the wrong order, the number is wrong.
- **Overflow at register width.** An unsigned 8-bit value wraps from 255 to 0. A signed 8-bit value goes from 127 to −128 on two's-complement hardware, although in C a signed overflow is undefined behaviour. A signed 32-bit Unix time runs out on 19 January 2038.
- **Character encoding.** `'A'` is 65 and `'a'` is 97. They're 32 apart, which is a single bit. The character `'0'` is 48, not 0. UTF-8 stores é as two bytes (`C3 A9`), and reading those bytes as Windows-1252 shows "Ã©".

### Music

- **MIDI numbers and piano keys.** MIDI counts notes from 0 to 127, with middle C at 60 and A440 at 69. An 88-key piano counts its keys from 1, so its lowest A is key 1 but MIDI note 21, and middle C is key 40.
- **Octave names.** MIDI note 60 is C4 in scientific pitch notation, but some software and many Yamaha devices call it C3, and others call it C5. If a part lands an octave off, check the naming before the notes.
- **Equal temperament and just intonation.** A piano fifth is exactly 700 cents, and a pure 3:2 fifth is about 702. A piano major third is 400 cents, and a pure 5:4 third is about 386, so it's 14 cents sharp. Twelve pure fifths overshoot seven octaves by about 23.5 cents, the Pythagorean comma. That's why the converter draws them as a spiral and not a circle.
- **Intervals are counted inclusively.** C up to G is called a fifth because you count C, D, E, F, G, both ends included, yet it's only 4 steps up the scale. That's why an octave plus an octave is a fifteenth, not a sixteenth. Music has been counting from 1 for centuries.
- **Harmonics and timbre.** The harmonics of a note sit at whole-number multiples of its frequency. A square wave has only the odd harmonics, while a sawtooth has them all. That's why they sound hollow and buzzy, even at the same pitch.
- **Sample rates.** CDs use 44.1 kHz and video uses 48 kHz. Play one as the other and the pitch shifts by about 1.5 semitones. Nothing above half the sample rate (the Nyquist limit) can be stored.

### Art and design

- **Hex colours.** Each channel is two hex digits from 00 to FF, so 0 to 255. Shorthand `#ABC` expands to `#AABBCC`, so writing `A` where you meant `0A` turns 10 into 170. One dropped zero, and the colour is a different colour.
- **0 to 255 channels.** There are 256 levels, so the middle falls between 127 and 128, and there's no exact 50%. Three 8-bit channels give 16,777,216 colours.
- **Brightness isn't linear.** In sRGB, a value of 128 is only about 22% of full light, not 50%. Blending and gradients done on the raw numbers come out too dark.
- **Bit depth.** A 1-bit image is black or white, and 8-bit indexed colour has a 256-colour palette. An 8-bit-per-channel gradient can show visible banding, which 10-bit or 16-bit smooths out.
- **Dot-matrix and pixel fonts.** A 5 × 7 dot-matrix letter is just 35 on/off switches. The converter draws each character this way, so you can see the bits that form the shape.

### TV and video

- **Frame numbering and timecode.** Some editors number the first frame 0 and others number it 1. Timecode `HH:MM:SS:FF` counts frames from 00, so at 30 fps they run from 00 to 29. Mixing the two conventions puts an edit one frame off.
- **Drop-frame timecode.** NTSC runs at 29.97 fps (30000/1001), not 30. To keep the clock honest, drop-frame timecode skips the labels :00 and :01 at the start of every minute, except every tenth minute. No pictures are dropped, only numbers.
- **Video levels.** Broadcast "limited" range puts black at 16 and white at 235 (and 16 to 240 for colour), while computers use the "full" range from 0 to 255. Mix them up and blacks look grey and washed out, or shadows are crushed.
- **Interlacing.** An interlaced frame is two fields, one with the odd lines and one with the even lines. If the field order (top or bottom first) is wrong, motion judders.

### Video games

- **Tile and grid indexing.** The tile under a point is `(x div tileSize, y div tileSize)`, and its index in a flat map is `row × width + column`. A map 20 tiles wide has columns 0 to 19. Column 20 is the next row.
- **8-bit limits.** One byte holds 0 to 255. Many classic games capped counters at 255, and Pac-Man's level 256 "kill screen" happens because a one-byte level counter overflows when the game draws the fruit for that level.
- **Tick counts.** A game running 60 updates a second counts time in ticks. Physics tied to frame rate instead of to fixed ticks runs faster on faster machines.
- **Chiptune from registers.** The NES sound chip has two pulse channels (12.5, 25, 50 or 75% duty), a triangle, a noise channel and a sample channel. A pulse channel's pitch is set by an 11-bit timer, with frequency = CPU clock ÷ (16 × (timer + 1)). Even there is a +1, and high notes can only land on a few coarse values, so they drift out of tune.

### Anywhere else

- Floors: in much of Europe the street level is floor 0, and in the US it's floor 1.
- Ages and centuries: a baby is in its first year at age 0, and the 1900s are the 20th century.
- Clocks: a 12-hour clock writes the full set as 12, never 0, while a 24-hour clock starts at 00:00.

When something "is off by one", "lost a zero" or "came out an octave wrong", put the number in the converter and look for where the ground moved.
