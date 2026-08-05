---
layout: single
classes: wide
author_profile: true
title: "Mohammed Mahdi Jahangiri"
header:
  overlay_color: "#0B1F33"
  overlay_filter: "0.7"
  overlay_image: "/portfolio/assets/images/hero-bg.jpg"
  actions:
    - label: "View Projects"
      url: "#projects"
    - label: "Contact"
      url: "#contact"
excerpt: "Games Programmer & AI Engineer. I build gameplay systems, AI-driven NPC interaction, and VR experiences with Unity, Unreal Engine, C#, C++, and Python."
---

## Featured Work {#projects}

Projects that demonstrate gameplay engineering, AI systems, VR publishing, and academic research.

---

### 360° Dome Projection UI Warping — Awkward Studios / Media Cymru

**Unity, C#, TextMesh Pro, URP, GitHub PR workflow**

Fixed severe text distortion on a 360° dome-projection game-show installation for CULTVR Lab.

- Developed an editor-safe **Unity C#** component that directly manipulated **TextMesh Pro** vertex buffers using trigonometry and **Quaternion** rotations to warp text around a virtual cylinder.
- Engineered a projection-boundary clipping system using **InverseLerp** and **SmoothStep** to eliminate text artifacting at half-sphere dome limits.
- Authored **URP shaders**, material setups and particle effects for large-scale immersive projection.
- Programmed modular mini-game state transitions using **C# delegates** and **coroutines**, decoupling sequence logic from UI flow.

**Result:** Legible text at extreme projection angles across a half-sphere dome, shipped for a live installation.

```csharp
// Maps flat TextMesh Pro vertices onto a virtual cylinder
// preserving text legibility at extreme projection angles
for (int i = 0; i < vertices.Length; i++)
{
    Vector3 localPos = transform.InverseTransformPoint(vertices[i].position);
    float angle = Mathf.Atan2(localPos.z, localPos.x);
    float radius = domeRadius + localPos.y * heightScale;

    vertices[i].position = new Vector3(
        radius * Mathf.Cos(angle),
        localPos.y,
        radius * Mathf.Sin(angle)
    );
}
```

---

### AI-Driven NPC Interaction Prototype

**Unreal Engine 5, C++, Python, FastAPI, Whisper, Wit.ai, Hugging Face**

A real-time, voice-driven NPC interaction system in Unreal Engine 5.

- Built a local **Python FastAPI** server bridging real-time microphone input to a **C++** application via a custom REST API.
- Integrated **Whisper** (speech-to-text), **Wit.ai** (intent classification) and local **Hugging Face** models for real-time text and voice emotion detection.
- Trained the voice-emotion model and configured **Wit.ai** intents using custom voice recordings.
- Wired microphone capture in **C++**, returning predicted intent/emotion signals to drive real-time **behaviour-tree** decision logic.

**Result:** A working end-to-end pipeline from player voice input to NPC-relevant intent and emotion signals.

```python
@app.post("/predict")
async def predict(audio: UploadFile):
    text = whisper_model.transcribe(audio.file)
    intent = wit_client.message(text)
    emotion = emotion_pipeline(text)
    return {"text": text, "intent": intent, "emotion": emotion}
```

**System Architecture:**

```
[Player Microphone]
        ↓
[Unreal C++ Mic Capture]
        ↓ (HTTP POST)
[Python FastAPI Server]
    ├── [Whisper] → Speech-to-Text
    ├── [Wit.ai] → Intent Classification
    └── [Hugging Face] → Emotion Detection
        ↓ (JSON Response)
[Unreal Behaviour Tree] → NPC Action
```

---

### Apoceus: Winter Wars — Landell Games

**Unity, C#, Unity DevOps, Plastic SCM, Steam**

A 3–6 person Unity team project, shipped weekly to a private Steam branch.

- Coordinated a **3–6 person programming team**, translating production priorities into sprint tasks and raising sprint success from **40% to 90%**.
- Profiled and optimised rendering bottlenecks with the **Unity Profiler**, improving frame time by **10–30 FPS** on target hardware.
- Owned weekly **Unity DevOps** branch merges and uploaded builds to a a private **Steam** branch.
- Implemented **ScriptableObject**-based unit/data configuration, Unity asset/**LOD** setup and gameplay **state-machine** logic, supporting designer-led balance tweaks.

**Result:** Consistent weekly playable builds across the team's Steam branch.

<div class="project-links">
  <a href="https://store.steampowered.com/app/1841690/Apoceus_Winter_Wars/" class="btn btn--primary" target="_blank" rel="noopener noreferrer">View on Steam →</a>
  <a href="https://www.youtube-nocookie.com/channel/UCKcDQ1wqQHMPW7SKOFdixPQ" class="btn btn--inverse" target="_blank" rel="noopener noreferrer">YouTube Channel →</a>
</div>

---

### VR Playground — Meta Quest Store

**Unity, C#, Meta Quest SDK**

A standalone VR game, shipped to the Meta Quest Store.

- Built and tuned the **core gameplay loop** with physics-based standalone headset-only interaction.
- Handled the full **Meta Quest Store** submission, compliance and publishing pipeline.
- Optimised draw calls and texture memory for mobile VR constraints, maintaining stable frame rates on Quest 2 hardware.
- Iterated post-launch on player feedback, tuning interaction and performance.

**Result:** Live, published title on the Meta Quest Store.

<div class="project-links">
  <a href="https://www.oculus.com/experiences/quest/5789612427788431/" class="btn btn--primary" target="_blank" rel="noopener noreferrer">View on Meta Quest →</a>
  <a href="https://www.youtube.com/watch?v=H5RhL2Hi9-w" class="btn btn--inverse" target="_blank" rel="noopener noreferrer">Watch Trailer →</a>
</div>

---

### Hand-Tracked VR Interaction Prototype

**Unity, hand-tracking SDKs, mobile VR**

A hand-tracked VR interaction prototype, built after evaluating Unreal's mobile VR pipeline against Unity.

- Compared Unreal and Unity for mobile VR and hand-tracking support, choosing Unity based on API and documentation maturity.
- Integrated third-party hand-tracking APIs with limited documentation.
- Delivered a working prototype under real technical uncertainty, planning sprints around unknown variables.

**Result:** A working hand-tracked prototype, and a clear technical comparison that shaped the engine choice for the project.

<div class="project-links">
  <a href="https://www.youtube.com/watch?v=WXT4huBhOA0" class="btn btn--inverse" target="_blank" rel="noopener noreferrer">Watch Prototype Video →</a>
</div>

---

### Publication — ICHORA 2024

**Research, LLMs, pursuit learning automata, NLP, local AI systems**

Published and presented a conference paper on resource-efficient NPC dialogue using local LLMs.

***Balancing Game Satisfaction and Resource Efficiency: LLM and Pursuit Learning Automata for NPC Dialogues***

- Proposed a resource-efficient local LLM pipeline for dynamic NPC dialogue, applying **pursuit learning automata** to balance player satisfaction against computational cost.
- Explored local AI methods that reduce reliance on cloud APIs for real-time applications.
- Presented research findings at ICHORA 2024.

**Result:** A published paper linking academic research to game AI engineering. This research underpins my current MSc dissertation on safe, efficient AI companions.

<div class="project-links">
  <a href="https://scholar.google.com/scholar?q=Balancing+Game+Satisfaction+and+Resource+Efficiency+LLM+Pursuit+Learning+Automata+NPC+Dialogues" class="btn btn--primary" target="_blank" rel="noopener noreferrer">View on Google Scholar →</a>
</div>
```

---

## About {#about}

MSc Artificial Intelligence candidate at **Cardiff University**. Published research on LLM-driven NPC dialogue (**ICHORA 2024**). Shipped a VR title to the **Meta Quest Store**. Led a programming team on a Steam-bound Unity project. I work at the intersection of gameplay, AI, and real-time systems — delivering playable game features, AI prototypes, and production pipelines for small teams and immersive titles.

---

## Contact {#contact}

Get in touch for gameplay engineering, AI systems, or portfolio reviews.

- **Email:** <a href="mailto:mapjiv@live.com">mapjiv@live.com</a>
- **LinkedIn:** <a href="https://www.linkedin.com/in/m-mahdi-jahangiri/" target="_blank" rel="noopener noreferrer">linkedin.com/in/m-mahdi-jahangiri</a>
- **GitHub:** <a href="https://github.com/devPirate01" target="_blank" rel="noopener noreferrer">github.com/devPirate01</a>

<div class="project-links" style="margin-top: 1.5rem;">
  <a href="{{ '/assets/Mahdi_Jahangiri_CV_Games.pdf' | relative_url }}" class="btn btn--primary" target="_blank">View CV</a>
  <a href="{{ '/assets/Mahdi_Jahangiri_CV_Games.pdf' | relative_url }}" class="btn btn--inverse" download>Download CV</a>
</div>
```