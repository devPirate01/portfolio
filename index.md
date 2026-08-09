---
layout: splash
author_profile: false
classes: wide
title: "Mohammed Mahdi Jahangiri"
header:
  overlay_color: "#0b1f33"
  overlay_filter: "0.55"
  overlay_image: /assets/images/hero.jpg
  actions:
    - label: "View projects"
      url: "#projects"
    - label: "Contact"
      url: "#contact"
excerpt: "Games Programmer: Gameplay & AI Systems. Specialising in C#/C++ across Unity and Unreal Engine 5, NPC dialogue pipelines, and real-time gameplay mechanics."
---

## Featured work {#projects}

Projects demonstrating gameplay engineering, AI systems, and academic research.

<div class="project-card">
  <div class="project-card__media">
    <div class="project-media-viewer" id="viewer-skyrim">
      <div class="viewer-nav">
        <button class="active" onclick="showMedia('viewer-skyrim', 0)">Media</button>
        <button onclick="showMedia('viewer-skyrim', 1)">Architecture</button>
        <button onclick="showMedia('viewer-skyrim', 2)">Code</button>
      </div>
      <div class="viewer-slides">
        <div class="slide active">
          <img src="{{ '/assets/images/skyrim-hero.jpg' | relative_url }}" alt="Skyrim LLM companion prototype" loading="lazy" />
        </div>
        <div class="slide">
<pre class="diagram">
[Creation Kit Mod: CompanionLLMV01.esp]
        ↓
[Papyrus In-Game Hook: MMJ_TavernWitnessChatLauncher]
        ↓ (Writes request.json via JContainers)
        ↓
[Python Orchestrator: bridge.py]
    ├── [data_director.py]         → IO, Session Memory, & Logging 
    ├── [llm_payload_builder.py]   → Profile & Quest State Prompt Injection
    ├── [KoboldCpp / OpenWebUI]    → Gemma-4-E4B SLM Execution
    └── [llm_reply_processor.py]   → JSON Sanitisation & Quest Policy Validation
        ↓
        ↓ (Writes response.json via JContainers)
[Skyrim Quest Engine: MMJ_PoisonedMeadQuestScript]
</pre>
        </div>
        <div class="slide">
{% highlight python %}
#This is send with the main prompt to give a template for the llm's reply
def build_output_contract() -> dict:
    return {
        "schema_version": OUTPUT_SCHEMA_VERSION,
        "dialogue": "Short player-facing NPC dialogue",
        "player_intent": "One allowed intent",
        "topic": "One allowed topic",
        "policy_id": "One policy available to this NPC",
        "response_type": "One allowed response type",
        "clue_claims": ["Zero or more clue IDs"],
        "action_request": None,
    }
{% endhighlight %}
        </div>
      </div>
    </div>
  </div>
  <div class="project-card__content">
    <h3>Dissertation: LLM Integration — Skyrim LLM Companion (MOD)</h3>
    <p class="project-card__meta"><strong>Skyrim, Creation Kit, SKSE</strong></p>
    <p>MSc dissertation prototype integrating a local LLM as an in-game companion for Skyrim.</p>
    <ul>
      <li>Built a custom Skyrim companion mod using <strong>Creation Kit</strong>, <strong>Papyrus</strong>/<strong>PapyrusUtil</strong> JSON request/response files and a <strong>Python LLM bridge</strong>.</li>
      <li>Prototyped LLM-driven companion dialogue with bounded context, safety constraints, and session/error logging as design priorities.</li>
      <li>Evaluating companion AI against branching-dialogue baselines, measuring player interaction quality, latency, safety, and reliability.</li>
    </ul>
  </div>
</div>

<div class="project-card">
  <div class="project-card__media">
    <div class="project-media-viewer" id="viewer-apoceus">
      <div class="viewer-nav">
        <button class="active" onclick="showMedia('viewer-apoceus', 0)">Media</button>
        <button onclick="showMedia('viewer-apoceus', 1)">Code</button>
      </div>
      <div class="viewer-slides">
        <div class="slide active">
          <img src="{{ '/assets/images/apoceus-hero.jpg' | relative_url }}" alt="Apoceus Winter Wars gameplay and team workflow" loading="lazy" />
        </div>
        <div class="slide">
{% highlight csharp %}
// ScriptableObject data configuration for unit stats
/ Calculate the perimeter of the search circle for unoccupied positions
// then determine the expected number of free positions based on the unit radius
int maxNumberOfSurroundingCircles = 50;
int[] expectedPositionCounts = new int[maxNumberOfSurroundingCircles];

float[] angleIncValues = new float[maxNumberOfSurroundingCircles];
float[] currentAngles = new float[maxNumberOfSurroundingCircles];
float[] offsets = new float[maxNumberOfSurroundingCircles];

//Track the total positions to avoid inefficient .Sum() calls inside the loop
int currentTotalPositions = 0;

// Loop outward in concentric circles until the required amount of positions is met
//or the maximum number of circles is reached (to avoid index out of bounds)
for (int i = 0; currentTotalPositions < amount && i < maxNumberOfSurroundingCircles; i++) 
{
    offsets[i] = offset * (i + 1);
    expectedPositionCounts[i] = Mathf.FloorToInt(2.0f * Mathf.PI * offsets[i] / ((refUnit.Radius + spacing) * 2.0f));
    
    // Prevent division by zero. Ensures the centre position or any 
    // mathematically small circumference defaults to testing at least 1 position
    if (expectedPositionCounts[i] == 0)
    {
        expectedPositionCounts[i] = 1;
    }
        
    //Calculate the angular increment value for the current circle
    angleIncValues[i] = 360f / expectedPositionCounts[i]; 
    currentAngles[i] = 0.0f;
    
    currentTotalPositions += expectedPositionCounts[i];
}
{% endhighlight %}
        </div>
      </div>
    </div>
  </div>
  <div class="project-card__content">
    <h3>Apoceus: Winter Wars — Landell Games</h3>
    <p class="project-card__meta"><strong>Unity, C#, Unity DevOps, Plastic SCM, Steam</strong></p>
    <p>A Unity PC project shipping to Steam, developed by a remote cross-disciplinary team.</p>
    <ul>
      <li>Coordinated a <strong>3–6 person programming team</strong>, translating production priorities into sprint tasks and raising sprint success from <strong>40% to 90%</strong>.</li>
      <li>Profiled and optimised rendering bottlenecks with the <strong>Unity Profiler</strong>, improving frame time by <strong>10–30 FPS</strong> on target hardware.</li>
      <li>Implemented <strong>ScriptableObject</strong>-based unit/data configuration and gameplay <strong>state-machine</strong> logic, supporting designer-led balance tweaks.</li>
      <li>Owned weekly <strong>Unity DevOps</strong> branch merges and uploaded builds to a private <strong>Steam</strong> branch.</li>
    </ul>
    <div class="project-links">
      <a href="https://store.steampowered.com/app/1841690/Apoceus_Winter_Wars/" class="btn btn--primary" target="_blank" rel="noopener noreferrer">View on Steam →</a>
      <a href="https://www.youtube.com/watch?v=rFADxjYHDF0" class="btn btn--inverse" target="_blank" rel="noopener noreferrer">Watch video →</a>
    </div>
  </div>
</div>

<div class="project-card">
  <div class="project-card__media">
    <div class="project-media-viewer" id="viewer-dome">
      <div class="viewer-nav">
        <button class="active" onclick="showMedia('viewer-dome', 0)">Media</button>
        <button onclick="showMedia('viewer-dome', 1)">Code</button>
      </div>
      <div class="viewer-slides">
        <div class="slide active">
          <img src="{{ '/assets/images/dome-hero.jpg' | relative_url }}" alt="360° dome projection interface" loading="lazy" />
        </div>
        <div class="slide">
{% highlight csharp %}
// Called during the LaunchSequence coroutine to animate letters along an arc
private void ApplyLetterTransforms(float t)
{
    foreach (OrbitLetter orbitLetter in letters)
    {
        Transform letterTransform = orbitLetter.letter.transform;

        // Interpolate the linear base position from start to end
        Vector3 basePosition = Vector3.Lerp(
            orbitLetter.startPoint.position,
            orbitLetter.endPoint.position,
            t
        );

        // Calculate a vertical arc offset using a sine wave to simulate projectile-like motion
        float arcOffset = Mathf.Sin(t * Mathf.PI) * arcHeight;

        letterTransform.position = basePosition + (Vector3.up * arcOffset);

        // Apply spherical interpolation for smooth rotation alignment
        letterTransform.rotation = Quaternion.Slerp(
            orbitLetter.startPoint.rotation,
            orbitLetter.endPoint.rotation,
            t
        );
    }
}

[ContextMenu("Restart Orbit Launch")]
public void RestartSequence()
{
    // Validates references and logs errors before attempting execution
    if (!ValidateLetters()) 
        return;

    StopAllCoroutines();
    StartCoroutine(LaunchSequence());
}

{% endhighlight %}
        </div>
      </div>
    </div>
  </div>
  <div class="project-card__content">
    <h3>360° Dome Projection UI — Awkward Studios / Media Cymru</h3>
    <p class="project-card__meta"><strong>Unity, C#, TextMesh Pro, URP, GitHub PR workflow</strong></p>
    <p>R&D for CULTVR Lab: a 360° dome-projection game-show installation.</p>
    <ul>
      <li>Solved 360° dome-projection UI distortion by developing an editor-safe <strong>Unity C#</strong> component that directly manipulated <strong>TextMesh Pro</strong> vertex buffers using trigonometry and <strong>Quaternion</strong> rotations.</li>
      <li>Engineered a projection-boundary clipping system to reduce text artifacting where UI elements crossed half-sphere dome limits.</li>
      <li>Programmed modular mini-game state transitions using <strong>C# delegates</strong> and <strong>coroutines</strong>, decoupling sequence logic from UI flow.</li>
    </ul>
  </div>
</div>

<div class="project-card">
  <div class="project-card__media">
    <div class="project-media-viewer" id="viewer-ai">
        <div class="viewer-slides">
        <div class="slide active">
<pre class="diagram">
[Player Microphone]
        ↓
[Unreal C++ Mic Capture]
        ↓ (HTTP POST)
[Python FastAPI Server]
    ├── [Whisper] → Speech-to-Text
    ├── [Wit.ai] → Intent Classify
    └── [Hugging Face] → Emotion
        ↓ (JSON Response)
[Unreal Behaviour Tree] → NPC Action
</pre>
        </div>
      </div>
    </div>
  </div>
  <div class="project-card__content">
    <h3>AI-Driven NPC Interaction Prototype</h3>
    <p class="project-card__meta"><strong>Unreal Engine 5, C++, Python, FastAPI, Whisper, Wit.ai, Hugging Face</strong></p>
    <p>A real-time, voice-driven NPC interaction system built for Unreal Engine 5.</p>
    <ul>
      <li>Built a local <strong>Python FastAPI</strong> server bridging player microphone input to <strong>Unreal Engine 5</strong> via a custom API.</li>
      <li>Integrated <strong>Whisper</strong> (speech-to-text), <strong>Wit.ai</strong> (intent classification), and local <strong>Hugging Face</strong> models for real-time text and voice emotion detection.</li>
      <li>Trained the voice-emotion model and configured <strong>Wit.ai</strong> intents using custom voice recordings.</li>
      <li>Wired microphone access in <strong>Unreal C++</strong> and Blueprint, returning predicted intent/emotion signals for real-time NPC behaviour-tree logic.</li>
    </ul>
  </div>
</div>

<div class="project-card">
  <div class="project-card__media">
    <img src="{{ '/assets/images/vr-quest-hero.jpg' | relative_url }}" alt="VR Playground project hero image" loading="lazy" />
  </div>
  <div class="project-card__content">
    <h3>VR Playground — Meta Quest Store</h3>
    <p class="project-card__meta"><strong>Unity, C#, Meta Quest SDK</strong></p>
    <p>A standalone VR game, shipped to the Meta Quest Store.</p>
    <ul>
      <li>Built and tuned the <strong>core gameplay loop</strong> with physics-based standalone headset-only interaction.</li>
      <li>Handled the full <strong>Meta Quest Store</strong> submission, compliance, and publishing pipeline.</li>
      <li>Iterated post-launch on player feedback, tuning interaction and performance constraints.</li>
    </ul>
    <div class="project-links">
      <a href="https://www.oculus.com/experiences/quest/5789612427788431/" class="btn btn--primary" target="_blank" rel="noopener noreferrer">View on Meta Quest →</a>
      <a href="https://www.youtube.com/watch?v=H5RhL2Hi9-w" class="btn btn--inverse" target="_blank" rel="noopener noreferrer">Watch Trailer →</a>
    </div>
  </div>
</div>

<div class="project-card">
  <div class="project-card__media">
    <div class="project-media-viewer" id="viewer-ichora">
      <div class="viewer-nav">
        <button class="active" onclick="showMedia('viewer-ichora', 0)">Presentation</button>
        <button onclick="showMedia('viewer-ichora', 1)">In-Game</button>
      </div>
      <div class="viewer-slides">
        <div class="slide active">
          <img src="{{ '/assets/images/ichora-photo.jpg' | relative_url }}" alt="Research poster and presentation for ICHORA conference" loading="lazy" />
        </div>
        <div class="slide">
          <img src="{{ '/assets/images/ichora-ingame.jpg' | relative_url }}" alt="In-game NPC dialogue interaction" loading="lazy" />
        </div>
      </div>
    </div>
  </div>
  <div class="project-card__content">
    <h3>Publication — ICHORA 2024</h3>
    <p class="project-card__meta"><strong>Research, LLMs, pursuit learning automata, NLP, local AI systems</strong></p>
    <p><strong>Balancing Game Satisfaction and Resource Efficiency: LLM and Pursuit Learning Automata for NPC Dialogues</strong></p>
    <ul>
      <li>Published and presented a paper proposing a resource-efficient local <strong>LLM pipeline</strong> for dynamic NPC dialogue.</li>
      <li>Applied <strong>pursuit learning automata</strong> to balance player satisfaction against computational cost.</li>
      <li>Expanded this research via an MSc dissertation focusing on <strong>safe AI companions for games</strong> using Skyrim, Creation Kit, and a Python LLM bridge.</li>
    </ul>
    <div class="project-links">
      <a href="https://scholar.google.com/scholar?q=Balancing+Game+Satisfaction+and+Resource+Efficiency+LLM+Pursuit+Learning+Automata+NPC+Dialogues" class="btn btn--primary" target="_blank" rel="noopener noreferrer">View on Google Scholar →</a>
    </div>
  </div>
</div>

## About {#about}

**Games Programmer: Gameplay & AI Systems**

Gameplay and AI programmer with 2+ years of C#/C++ experience across Unity and Unreal Engine 5. Core programming team lead at **Landell Games**, shipping a commercial Unity title to Steam, alongside a standalone VR release on the Meta Quest Store. 

MSc Artificial Intelligence graduate (**Cardiff University**), specialising in bridging complex local AI pipelines with real-time game engines for advanced NPC interactions.

<div class="project-links">
  <a href="{{ '/about/' | relative_url }}" class="btn btn--inverse">Read Full Profile</a>
</div>

## CV {#cv}

<div class="project-links">
  <a href="{{ '/cv/' | relative_url }}" class="btn btn--primary">View CV Document</a>
  <a href="{{ '/assets/Mahdi_Jahangiri_CV_Games.pdf' | relative_url }}" class="btn btn--inverse" download>Download PDF</a>
</div>

## Contact {#contact}

Available for gameplay engineering and AI systems roles.

- **Email:** <a href="mailto:mapjiv@live.com">mapjiv@live.com</a>
- **LinkedIn:** <a href="https://www.linkedin.com/in/m-mahdi-jahangiri/" target="_blank" rel="noopener noreferrer">linkedin.com/in/m-mahdi-jahangiri</a>
- **GitHub:** <a href="https://github.com/devPirate01" target="_blank" rel="noopener noreferrer">github.com/devPirate01</a>

<script>
// Lightweight script to handle media tabs in project cards
function showMedia(viewerId, index) {
  const viewer = document.getElementById(viewerId);
  if (!viewer) return;
  const buttons = viewer.querySelectorAll('.viewer-nav button');
  const slides = viewer.querySelectorAll('.slide');
  
  buttons.forEach((btn, i) => {
    if (i === index) btn.classList.add('active');
    else btn.classList.remove('active');
  });
  
  slides.forEach((slide, i) => {
    if (i === index) slide.classList.add('active');
    else slide.classList.remove('active');
  });
}
</script>