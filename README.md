<p align="center"><h1>Awesome Music Prompts 🚀</h1></p>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re) 
[![Code License](https://img.shields.io/badge/License-MIT-green.svg)](https://github.com/yzfly/awesome-music-prompts/blob/main/LICENSE)

Welcome to the "Awesome Music Prompts" repository! This is a collection of prompt examples to be used with the [MusicLM](https://aitestkitchen.withgoogle.com/experiments/music-lm) model and [StableAudio](https://stableaudio.com/).

[MusicLM](https://google-research.github.io/seanet/musiclm/examples/) and [StableAudio](https://stableaudio.com/) are AI technology that allows you to generate your own synthetic music for inspiration. 

In this repository, you will find a variety of prompts that can be used with MusicLM and StableAudio. We hope you find these prompts useful! And we encourage you to [add your own prompts](https://github.com/yzfly/awesome-music-prompts/edit/main/README.md) to the list.


## Stable Audio Prompt Generation

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

## Prompts

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