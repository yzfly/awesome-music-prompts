<p align="center"><h1>Awesome Music Prompts 🚀</h1></p>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![Code License](https://img.shields.io/badge/License-MIT-green.svg)](https://github.com/yzfly/awesome-music-prompts/blob/main/LICENSE)

> 中文版请见 [README.zh-CN.md](README.zh-CN.md)

Welcome to the **Awesome Music Prompts** repository! This is a curated collection of prompt examples and writing techniques for AI music generation tools and models — from keyword-stacking instrumental generators to end-to-end song generators that write full lyrics and vocals.

The space moved fast: the original 2023 wave (MusicLM, Stable Audio) has been joined by end-to-end song generators like Suno and Udio that turn a prompt plus lyrics into a finished song. This repo covers both paradigms.

We encourage you to [add your own prompts](https://github.com/yzfly/awesome-music-prompts/edit/main/README.md) to the list!

## Table of Contents

- [Tools & Models](#tools--models)
- [Two Prompting Paradigms](#two-prompting-paradigms)
- [Suno / Udio Prompting (Lyrics + Structure Tags + Style Tags)](#suno--udio-prompting-lyrics--structure-tags--style-tags)
- [Stable Audio Prompt Generation](#stable-audio-prompt-generation)
- [Keyword-Stacking Prompts (Stable Audio / MusicFX / MusicGen)](#keyword-stacking-prompts-stable-audio--musicfx--musicgen)
- [License](#license)
- [Author](#author)

## Tools & Models

| Tool / Model | Link | One-line description |
|--------------|------|----------------------|
| **Suno** | [suno.com](https://suno.com) | End-to-end song generator; produces full songs with vocals and supports `[Verse]` / `[Chorus]` structure tags. |
| **Udio** | [www.udio.com](https://www.udio.com) | End-to-end song and vocal generator driven by style tags plus your own lyrics. |
| **Stable Audio 2.0** | [stableaudio.com](https://stableaudio.com) | Stability AI's commercial text-to-audio tool for instrumentals, stems and sound effects. |
| **Stable Audio Open** | [huggingface.co/stabilityai/stable-audio-open-1.0](https://huggingface.co/stabilityai/stable-audio-open-1.0) | Open weights release for generating short samples, loops and sound effects locally. |
| **Google MusicFX** | [labs.google/fx/tools/music-fx](https://labs.google/fx/tools/music-fx) | Google's text-to-music tool, the public successor to MusicLM. |
| **Meta MusicGen / AudioCraft** | [github.com/facebookresearch/audiocraft](https://github.com/facebookresearch/audiocraft) | Meta's open-source library for controllable music and audio generation (MusicGen, AudioGen). |
| **Riffusion** | [www.riffusion.com](https://www.riffusion.com) | Generates music from text and supports building songs from lyrics. |
| **MusicLM** (research) | [examples](https://google-research.github.io/seanet/musiclm/examples/) | Google's original research model; the public experiment is now [MusicFX](https://labs.google/fx/tools/music-fx). |

## Two Prompting Paradigms

There are two fundamentally different ways to prompt AI music tools, and the techniques do **not** transfer between them:

1. **Keyword-stacking** (Stable Audio, MusicFX, MusicGen, Riffusion text mode): you describe an instrumental in a comma-separated list of genres, moods, instruments and BPM. There are no lyrics and usually no vocals. See the [keyword-stacking section](#keyword-stacking-prompts-stable-audio--musicfx--musicgen).
2. **Lyrics + structure tags** (Suno, Udio): you provide actual lyrics organized with section tags such as `[Verse]` and `[Chorus]`, plus a short style description. The model sings your lyrics. See the [Suno / Udio section](#suno--udio-prompting-lyrics--structure-tags--style-tags).

## Suno / Udio Prompting (Lyrics + Structure Tags + Style Tags)

Unlike the keyword-stacking tools, **Suno** and **Udio** generate complete songs *with vocals*. A good prompt has three parts:

### 1. Style description (the "Style of Music" box)

A short, comma-separated description of genre, mood, voice and tempo. Keep it focused — too many conflicting styles muddy the result.

```
melodic dark pop, female vocals, emotional, atmospheric, 90 BPM
```

```
upbeat synthwave, retro 80s, male vocals, driving bassline, energetic
```

### 2. Lyrics with structure tags

Put structure tags on their own line in square brackets. The model uses them to shape the arrangement (energy, dynamics, repetition). Common tags:

- `[Intro]` `[Verse]` `[Pre-Chorus]` `[Chorus]` `[Bridge]` `[Outro]`
- `[Instrumental]` `[Solo]` `[Hook]` `[Drop]`
- Performance hints: `[Spoken]`, `[Whispered]`, `[Build]`, `[Fade Out]`

Example lyrics block:

```
[Verse]
Neon rivers running down the street
Every heartbeat keeps a steady beat
Looking for a sign in the city lights
Holding onto something through the night

[Chorus]
We are the echoes in the dark
Burning like a falling spark
Hold me till the morning comes
We are the echoes, we are the ones

[Bridge]
Quiet now, the city sleeps
A promise that the silence keeps

[Outro]
We are the echoes... fading slow
```

### 3. Tips

- Use **brackets, not parentheses**, for structure tags — parentheses are read as backing/ad-lib vocals, e.g. `(ooh ooh)`.
- Keep the **style box short** (a handful of tags). Long style boxes dilute the result.
- A `[Chorus]` repeated verbatim tends to come back with the same melody — great for a memorable hook.
- For an instrumental-only track, leave the lyrics empty and rely entirely on the style box (or use `[Instrumental]`).
- Tempo and key cues (e.g. `120 BPM`, `key of A minor`) in the style box help keep takes consistent.

## Stable Audio Prompt Generation

Open the ChatGPT helper to generate Stable Audio prompts:
[Stable Audio Prompt Generation Helper](https://chat.openai.com/share/05539213-ed59-4eed-8aa9-4b49bd263ab4)

```
# Role: StableAudioPromptGPT

## Profile

- Author: YZFly
- Version: 0.1
- Language: English
- Description: You are an expert prompt generator for Stable Audio, a versatile AI tool that can produce a wide range of audio outputs, from full instrumentals to individual stems and sound effects.

## Instructions for Using Stable Audio

Stable Audio is a versatile tool that can generate a wide range of audio outputs. Here's how to use it effectively:

### Add detail
If you have something specific in mind, include it. Genres, descriptive phrases, instruments and moods work particularly well.

For example, a detailed prompt might look something like this:

Cinematic, Soundtrack, Wild West, High Noon Shoot Out, Percussion, Whistles, Horses, Action Scene, SFX, Shaker, Guitar, Bass, Timpani, Strings, Tense, Climactic, Atmospheric, Moody

### Set the mood
When including detail on the mood you want, try using a combination of musical and emotional terms.

Musical might be groovy or rhythmic. Emotional might be sad or beautiful. Using both musical and emotional words in combination can work well.

### Choose instruments
We’ve found that adding adjectives to instrument names is helpful.

For example, Reverberated Guitar, Powerful Choir, or Swelling Strings.

### Set the BPM
Setting the beats per minute is a great way to ensure your output is the tempo you want, and can help keep it in time. The key here is to try to stick to BPM settings that are appropriate to the genre you’re generating.

For example, if you were generating a Drum and Bass track, you might want to add 170 BPM to your prompt.


## Output sample prompts

You can generate multiple types of music below are the details and sample prompt.

**1. Full Instrumentals:**

- To generate a full musical audio, provide a detailed description of the desired sound.
- Include musical genres, moods, instruments, BPM (beats per minute), and any other relevant details.
- Example Prompts:
    - Trance, Ibiza, Beach, Sun, 4 AM, Progressive, Synthesizer, 909, Dramatic Chords, Choir, Euphoric, Nostalgic, Dynamic, Flowing
    - Disco, Driving Drum Machine, Synthesizer, Bass, Piano, Guitars, Instrumental, Clubby, Euphoric, Chicago, New York, 115 BPM

**2. Individual Stems:**

- If you want individual stems featuring a single instrument or group of instruments, specify it clearly.
- Mention the genre, BPM, grade, and instruments if applicable.
- Example Prompts:
    - Electric guitar top line solo instrumental, no drums, Classic Rock, 105 BPM, Grade: Featured, Instruments: Guitar
    - Samba percussion
    - Drum solo

**3. Sound Effects:**

- Stable Audio can also produce sound effects.
- Describe the sound effect you want in detail.
- Example Prompts:
    - Ringtone
    - Explosion
    - Car passing by
    - Fireworks, 44.1k high fidelity

**Tips:**

- The more detailed your prompt, the better the output will likely be.
- Feel free to mix and match elements from different examples to create your unique sound.

## Workflow
1. I will provide you with keywords and you will generate different types of prompts.
2. You will add additional details and criteria such as genre, mood, BPM, etc.
3. Before you provide prompt you must check if you have satisfied all the above criteria and if you are sure than only provide the prompt.
4. Ensure the prompt is detailed and adheres to the guidelines.

## Init
As a <Role>, you must follow the <Rules> and talk to the user in the default <Language>. Ask the user the music keywords and think step by step to generate wonderful prompt.
```

## Keyword-Stacking Prompts (Stable Audio / MusicFX / MusicGen)

These comma-separated, instrumental-focused prompts work well with Stable Audio, MusicFX, MusicGen and Riffusion's text mode.

```
Sad and longing. The melody is slow and wistful creating a sense of melancholy and nostalgia. Simple arrangement on the piano. 
```

```
Optimistic melody about the arrival of spring, full of joy and hope, tranquil flute in the background, upbeat with a gentle guitar riff
```

```
A jazzy piece with a smooth saxophone solo. The sound is both sophisticated and playful with a slow tempo.
```

```
Songs that would play in a poolside party with light summer vibes 
```

```
Trance, Ibiza, Beach, Sun, 4 AM, Progressive, Synthesizer, 909, Dramatic Chords, Choir, Euphoric, Nostalgic, Dynamic, Flowing
```

```
Disco, Driving Drum Machine, Synthesizer, Bass, Piano, Guitars, Instrumental, Clubby, Euphoric, Chicago, New York, 115 BPM
```

```
Synthpop, Big Reverbed Synthesizer Pad Chords, Driving Gated Drum Machine, Atmospheric, Moody, Nostalgic, Cool, Club, Striped-back, Pop Instrumental, 100 BPM
```

```
Ambient house, new age, meditation, advertisement, 808 drum machine, 808 kick, claps, shaker, synthesizer, synth bass, soaring lead heavily reverbed, modern, sleek, beautiful, inspiring, futuristic
```

```
Calm meditation music to play in a spa lobby
```

```
Post-Rock, Guitars, Drum Kit, Bass, Strings, Euphoric, Up-Lifting, Moody, Flowing, Raw, Epic, Sentimental, 125 BPM
```

```
Ambient Techno, meditation, Scandinavian Forest, 808 drum machine, 808 kick, claps, shaker, synthesizer, synth bass, Synth Drones, beautiful, peaceful, Ethereal, Natural, 122 BPM, Instrumental
```

```
3/4, in 3, 3 beat, guitar, drums, bright, happy, claps
```

```
Warm soft hug, comfort, low synths, twinkle, wind and leaves, ambient, peace, relaxed, water
```

```
Electric guitar top line solo instrumental, no drums, Classic Rock, 105 BPM, Grade: Featured, Instruments: Guitar
```

## License

This project is licensed under the [MIT License](LICENSE).

## Author

作者：云中江树，微信公众号: 云中江树

Maintained by [yzfly](https://github.com/yzfly).
