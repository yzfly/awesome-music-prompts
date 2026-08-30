<p align="center"><h1>Awesome Music Prompts 🚀</h1></p>

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![Code License](https://img.shields.io/badge/License-MIT-green.svg)](https://github.com/yzfly/awesome-music-prompts/blob/main/LICENSE)

> English version: [README.md](README.md)

欢迎来到 **Awesome Music Prompts** 仓库！这里收集了用于 AI 音乐生成工具和模型的提示词（Prompt）范例与写作技巧——既包括「关键词堆叠」式的纯器乐生成器，也包括能直接生成完整歌曲（含人声和歌词）的端到端模型。

这个领域发展很快：2023 年第一波（MusicLM、Stable Audio）之后，又出现了 Suno、Udio 这样的端到端歌曲生成器，输入提示词加歌词即可得到一首成品歌曲。本仓库同时覆盖这两种范式。

欢迎你[提交自己的提示词](https://github.com/yzfly/awesome-music-prompts/edit/main/README.md)！

## 目录

- [工具与模型](#工具与模型)
- [两种提示词范式](#两种提示词范式)
- [Suno / Udio 提示词写法（歌词 + 结构标签 + 风格标签）](#suno--udio-提示词写法歌词--结构标签--风格标签)
- [Stable Audio 提示词生成器](#stable-audio-提示词生成器)
- [关键词堆叠式提示词（Stable Audio / MusicFX / MusicGen）](#关键词堆叠式提示词stable-audio--musicfx--musicgen)
- [许可协议](#许可协议)
- [作者](#作者)

## 工具与模型

| 工具 / 模型 | 链接 | 一句话简介 |
|--------------|------|----------------------|
| **Suno v5.5** | [suno.com](https://suno.com) | Suno 当前模型（2026 年 3 月）：新增 *Voices*（用你自己的声音唱）、按个人曲库训练的 *Custom Models* 与个性化引擎 *My Taste*，下文的标签 + 歌词写法依然适用。 |
| **ACE-Step 1.5** | [github.com/ace-step/ACE-Step](https://github.com/ace-step/ACE-Step) | 开放权重的音乐基础模型（Apache-2.0），目前最接近「本地 Suno」；配合 [ace-step-ui](https://github.com/fspecii/ace-step-ui) 可获得类 Suno 的工作台。 |
| **HeartMuLa** | [github.com/HeartMuLa/heartlib](https://github.com/HeartMuLa/heartlib) | 2026 年开源音乐生成模型，支持参考音频风格迁移；有 [HeartMuLa-Studio](https://github.com/fspecii/HeartMuLa-Studio) 与 ComfyUI 节点。 |
| **audio.cpp** | [github.com/0xShug0/audio.cpp](https://github.com/0xShug0/audio.cpp) | 纯 C++（ggml）的音频模型推理引擎，一个本地二进制跑 TTS / STT / 变声 / 音乐生成。 |
| **Suno** | [suno.com](https://suno.com) | 端到端歌曲生成器，可生成含人声的完整歌曲，支持 `[Verse]` / `[Chorus]` 等结构标签。 |
| **Udio** | [www.udio.com](https://www.udio.com) | 端到端歌曲与人声生成器，通过风格标签加自定义歌词驱动。 |
| **Stable Audio 2.0** | [stableaudio.com](https://stableaudio.com) | Stability AI 的商业文本转音频工具，可生成器乐、分轨与音效。 |
| **Stable Audio Open** | [huggingface.co/stabilityai/stable-audio-open-1.0](https://huggingface.co/stabilityai/stable-audio-open-1.0) | 开源权重版本，可在本地生成短样本、循环与音效。 |
| **Google MusicFX** | [labs.google/fx/tools/music-fx](https://labs.google/fx/tools/music-fx) | Google 的文本转音乐工具，是 MusicLM 面向公众的继任者。 |
| **Meta MusicGen / AudioCraft** | [github.com/facebookresearch/audiocraft](https://github.com/facebookresearch/audiocraft) | Meta 的开源可控音乐与音频生成库（MusicGen、AudioGen）。 |
| **Riffusion** | [www.riffusion.com](https://www.riffusion.com) | 从文本生成音乐，支持基于歌词构建歌曲。 |
| **MusicLM**（研究） | [示例](https://google-research.github.io/seanet/musiclm/examples/) | Google 最初的研究模型，其公开体验版现已变为 [MusicFX](https://labs.google/fx/tools/music-fx)。 |

## 两种提示词范式

AI 音乐工具的提示词写法有两种本质不同的范式，二者技巧并不通用：

1. **关键词堆叠**（Stable Audio、MusicFX、MusicGen、Riffusion 文本模式）：用逗号分隔的列表描述一段器乐，包含曲风、情绪、乐器和 BPM，通常没有歌词和人声。详见[关键词堆叠章节](#关键词堆叠式提示词stable-audio--musicfx--musicgen)。
2. **歌词 + 结构标签**（Suno、Udio）：提供真实的歌词，并用 `[Verse]`、`[Chorus]` 等结构标签组织，再加一段简短的风格描述，模型会演唱你的歌词。详见 [Suno / Udio 章节](#suno--udio-提示词写法歌词--结构标签--风格标签)。

## Suno / Udio 提示词写法（歌词 + 结构标签 + 风格标签）

与关键词堆叠类工具不同，**Suno** 和 **Udio** 生成的是含人声的完整歌曲。一个好的提示词由三部分组成：

### 1. 风格描述（「Style of Music」框）

一段简短的、逗号分隔的描述，包含曲风、情绪、嗓音和速度。要聚焦——风格太多、互相冲突会让结果变浑浊。

```
melodic dark pop, female vocals, emotional, atmospheric, 90 BPM
```

```
upbeat synthwave, retro 80s, male vocals, driving bassline, energetic
```

### 2. 带结构标签的歌词

结构标签单独成行，用方括号包裹。模型据此安排编曲（能量、强弱、重复）。常用标签：

- `[Intro]` `[Verse]` `[Pre-Chorus]` `[Chorus]` `[Bridge]` `[Outro]`
- `[Instrumental]` `[Solo]` `[Hook]` `[Drop]`
- 演唱提示：`[Spoken]`（口白）、`[Whispered]`（低语）、`[Build]`（铺垫）、`[Fade Out]`（淡出）

歌词示例：

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

### 3. 技巧

- 结构标签要用**方括号而不是圆括号**——圆括号会被理解为和声/即兴衬词，例如 `(ooh ooh)`。
- **风格框要短**（几个标签即可），过长会稀释效果。
- 完全相同的 `[Chorus]` 倾向于返回相同的旋律——适合打造记忆点副歌。
- 想要纯器乐，可留空歌词、只用风格框（或使用 `[Instrumental]`）。
- 在风格框里加上速度和调性提示（如 `120 BPM`、`key of A minor`）有助于多次生成保持一致。

## Stable Audio 提示词生成器

打开 ChatGPT 助手来生成 Stable Audio 提示词：
[Stable Audio Prompt Generation Helper](https://chat.openai.com/share/05539213-ed59-4eed-8aa9-4b49bd263ab4)

完整的提示词角色定义见英文版 [README.md](README.md#stable-audio-prompt-generation)，核心要点：

- **加细节**：曲风、描述性短语、乐器、情绪都很有用。
- **定情绪**：把音乐性词汇（groovy、rhythmic）和情感性词汇（sad、beautiful）结合使用。
- **选乐器**：给乐器名加形容词，例如 Reverberated Guitar、Powerful Choir、Swelling Strings。
- **设 BPM**：明确速度，且选用符合该曲风的 BPM（如 Drum and Bass 可写 170 BPM）。

可生成三类音频：完整器乐、单独分轨（stems）、音效（sound effects）。

## 关键词堆叠式提示词（Stable Audio / MusicFX / MusicGen）

以下逗号分隔、以器乐为主的提示词适用于 Stable Audio、MusicFX、MusicGen 以及 Riffusion 的文本模式。

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
Trance, Ibiza, Beach, Sun, 4 AM, Progressive, Synthesizer, 909, Dramatic Chords, Choir, Euphoric, Nostalgic, Dynamic, Flowing
```

```
Disco, Driving Drum Machine, Synthesizer, Bass, Piano, Guitars, Instrumental, Clubby, Euphoric, Chicago, New York, 115 BPM
```

```
Ambient Techno, meditation, Scandinavian Forest, 808 drum machine, 808 kick, claps, shaker, synthesizer, synth bass, Synth Drones, beautiful, peaceful, Ethereal, Natural, 122 BPM, Instrumental
```

```
Electric guitar top line solo instrumental, no drums, Classic Rock, 105 BPM, Grade: Featured, Instruments: Guitar
```

> 更多范例见英文版 [README.md](README.md#keyword-stacking-prompts-stable-audio--musicfx--musicgen)。

## 许可协议

本项目基于 [MIT 协议](LICENSE) 开源。

## 作者

作者：云中江树，微信公众号: 云中江树

由 [yzfly](https://github.com/yzfly) 维护。
