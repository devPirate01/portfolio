---
layout: single
classes: wide
author_profile: false
title: "Portfolio"
header:
  overlay_color: "#0B1F33"
  overlay_filter: "0.7"
  overlay_image: /assets/images/hero-bg.jpg
  actions:
    - label: "View Projects"
      url: "#projects"
    - label: "Contact"
      url: "#contact"
  caption: ""
excerpt: "Games Programmer & AI Engineer. I build gameplay systems, AI-driven NPC interaction, and VR experiences with Unity, Unreal Engine, C#, C++, and Python."
---

## Featured Work

Projects that demonstrate gameplay engineering, AI systems, VR publishing, and academic research.

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
- Owned weekly **Unity DevOps** branch merges and uploaded builds to a private **Steam** branch.
- Implemented **ScriptableObject**-based unit/data configuration, Unity asset/**LOD** setup and gameplay **state-machine** logic, supporting designer-led balance tweaks.

**Result:** Consistent weekly playable builds across the team's Steam branch.

---

### VR Playground — Meta Quest Store

**Unity, C#, Meta Quest SDK**

A standalone VR game, shipped to the Meta Quest Store.

- Built and tuned the **core gameplay loop** with physics-based standalone headset-only interaction.
- Handled the full **Meta Quest Store** submission, compliance and publishing pipeline.
- Optimised draw calls and texture memory for mobile VR constraints, maintaining stable frame rates on Quest 2 hardware.
- Iterated post-launch on player feedback, tuning interaction and performance.

**Result:** Live, published title on the Meta Quest Store.

---

### Hand-Tracked VR Interaction Prototype

**Unity, hand-tracking SDKs, mobile VR**

A hand-tracked VR interaction prototype, built after evaluating Unreal's mobile VR pipeline against Unity.

- Compared Unreal and Unity for mobile VR and hand-tracking support, choosing Unity based on API and documentation maturity.
- Integrated third-party hand-tracking APIs with limited documentation.
- Delivered a working prototype under real technical uncertainty, planning sprints around unknown variables.

**Result:** A working hand-tracked prototype, and a clear technical comparison that shaped the engine choice for the project.

---

### Publication — ICHORA 2024

**Research, LLMs, pursuit learning automata, NLP, local AI systems**

Published and presented a conference paper on resource-efficient NPC dialogue using local LLMs.

***Balancing Game Satisfaction and Resource Efficiency: LLM and Pursuit Learning Automata for NPC Dialogues***

- Proposed a resource-efficient local LLM pipeline for dynamic NPC dialogue, applying **pursuit learning automata** to balance player satisfaction against computational cost.
- Explored local AI methods that reduce reliance on cloud APIs for real-time applications.
- Presented research findings at ICHORA 2024.

**Result:** A published paper linking academic research to game AI engineering. This research underpins my current MSc dissertation on safe, efficient AI companions.

[View on Google Scholar →](https://scholar.google.com/scholar?q=Balancing+Game+Satisfaction+and+Resource+Efficiency+LLM+Pursuit+Learning+Automata+NPC+Dialogues)

---

## About

MSc Artificial Intelligence candidate at **Cardiff University**. Published research on LLM-driven NPC dialogue (**ICHORA 2024**). Shipped a VR title to the **Meta Quest Store**. Led a programming team on a Steam-bound Unity project. I work at the intersection of gameplay, AI, and real-time systems — delivering playable game features, AI prototypes, and production pipelines for small teams and immersive titles.

---

## Contact

Get in touch for gameplay engineering, AI systems, or portfolio reviews.

- **Email:** [mapjiv@live.com](mailto:mapjiv@live.com)
- **LinkedIn:** [linkedin.com/in/m-jahangiri](https://linkedin.com/in/m-jahangiri)
- **GitHub:** [github.com/devPirate01](https://github.com/devPirate01)

<a href="assets/Mahdi_Jahangiri_CV_Games.pdf" class="btn btn--primary" download>Download CV</a>
