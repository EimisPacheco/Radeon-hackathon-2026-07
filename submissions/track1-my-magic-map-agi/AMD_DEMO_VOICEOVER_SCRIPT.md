# My Magic Map AGI — AMD Track 1 Demo Voiceover

Target length: 4:00–4:40. Spoken language: English.

## Recording gate

Do not record the final take until the Radeon bridge is online and the app's
AMD status reports `reachable: true`. Hide or blur bearer tokens, API keys,
email addresses, SSH host details, and other credentials. Keep the actual AMD
inference portions at normal speed so judges can evaluate execution time and
stability.

## Shot plan and narration

### 0:00–0:25 — Problem, user, and value

**On screen:** Title, then the live My Magic Map AGI interface with Street View
and the webcam movement panel.

**Voiceover:**

“This is My Magic Map AGI, a multimodal, body-controlled world exploration and
content-creation tool. It is designed for travelers, families, students,
creators, and people who benefit from hands-free interaction. Instead of
navigating only with a mouse, a user can walk in place, steer with body motion,
point at the world, ask questions, and transform real places into visual
memories.”

### 0:25–1:00 — Prove the AMD Radeon/ROCm runtime

**On screen:** Radeon Cloud workspace and a terminal. Show `rocminfo`, then a
short PyTorch check that displays the HIP version and confirms GPU availability.
Show the authenticated bridge health response without exposing the token.

Suggested terminal evidence:

```bash
rocminfo | grep -m1 "Marketing Name"
python -c "import torch; print(torch.__version__, torch.version.hip, torch.cuda.is_available(), torch.cuda.get_device_name(0))"
curl -H "Authorization: Bearer [HIDDEN]" https://[RADEON-BRIDGE]/health
```

**Voiceover:**

“The creative and semantic-vision workloads run on an AMD Radeon GPU in the
ROCm 7.2 environment. PyTorch reports HIP 7.2 and an available Radeon device.
Inside this workspace, ComfyUI runs locally with the SDXL base model, while
Qwen2.5-VL runs in BF16 for visual understanding. ComfyUI is bound to loopback;
only our bearer-token-protected FastAPI bridge is exposed to the application.”

### 1:00–1:25 — Show the complete startup path

**On screen:** Start ComfyUI, the FastAPI bridge, and the Radeon tunnel; then
start the React/Express project with `npm run dev`. Show `/amd/status` returning
the AMD provider as reachable. Keep secrets hidden.

**Voiceover:**

“This is the actual execution path. We start the ROCm image service, the
authenticated multimodal bridge, and the application server. The app checks the
bridge before generation and reports AMD Radeon ROCm as the active provider.
The same secure server boundary carries image generation and object-vision
requests, while credentials never enter the browser.”

### 1:25–2:15 — Actual operation: Paint a Place

**On screen:** Use body motion to move through Street View. Open Paint a Place,
select an art style, generate, and keep the before/after images and AMD timing
metadata visible. Do not cut or accelerate the inference wait.

**Voiceover:**

“I walk through Street View using live pose detection, choose the place I am
actually viewing, and open Paint a Place. The Express API sends this selected
scene—not the webcam feed—to the Radeon bridge. ComfyUI encodes the source
image, applies the prompt and palette through SDXL image-to-image generation,
and returns a transformed result that still reflects the original location.
The interface displays the AMD provider, GPU generation time, and total
round-trip time. In our measured warm runs, SDXL averaged 11.981 seconds.”

### 2:15–2:50 — Diversity and practical creative output

**On screen:** Generate or reveal a second, clearly different style as a
postcard or virtual memory. Show download/save behavior and two outputs side by
side.

**Voiceover:**

“The same Radeon pipeline supports ordinary postcards and virtual memories.
Here I use a different visual direction to demonstrate output diversity, then
save the result as a usable memory artifact. This is practical content
creation: a traveler can reinterpret a destination, a family can preserve a
shared place, and a student can turn geographic exploration into a visual
story.”

### 2:50–3:30 — Actual operation: pointed-object vision

**On screen:** Return to Street View, point with a hand, nose, or companion paw,
ask ‘What is this?’, and show the identified object, confidence, description,
and result card. Show AMD/Qwen timing metadata.

**Voiceover:**

“AMD acceleration also powers semantic vision. I point at an object and ask
what it is. The app derives the target locally, captures the complete Street
View scene plus a focused crop, and sends both to Qwen2.5-VL on Radeon. The
model returns structured identity, category, description, confidence, and a
safe search query. Warm vision inference averaged 7.089 seconds in our live
tests. This closes the complete multimodal loop: gesture, map imagery, vision,
language, and an actionable result.”

### 3:30–4:10 — Architecture, innovation, and functional completeness

**On screen:** Show the current architecture diagram. Highlight browser-local
tracking, React, Express, the AMD Radeon ROCm block, and the two AMD models.

**Voiceover:**

“The innovation is not only generating an image. My Magic Map combines
embodied interaction with geospatial media and uses one Radeon service for two
complementary modalities: SDXL creates content, while Qwen understands what the
user selected. Latency-critical pose, face, and hand tracking stays on-device
for privacy and responsiveness. Expensive creative and semantic inference runs
on Radeon, where GPU throughput adds the most value. OpenAI provides the live
voice experience and an availability fallback, but AMD is the primary provider
for Paint a Place, standard postcards, virtual memories, and pointed-object
vision.”

### 4:10–4:35 — Criteria summary and close

**On screen:** Three labels—Functional completeness, Practical value,
Innovation—followed by the result gallery and repository URL.

**Voiceover:**

“This demonstrates functional completeness through an end-to-end workflow from
body input and a real map scene to Radeon inference and a saved final result.
It demonstrates practical value through accessible exploration, education,
travel memories, and creator-ready outputs. It demonstrates innovation by
connecting physical gestures, real-world geography, local privacy-preserving
tracking, Radeon-accelerated generation, and Radeon-accelerated vision in one
coherent product. This is My Magic Map AGI, built for AMD AI DevMaster Track
One.”

## Final recording checklist

- Show the Radeon terminal and ROCm/PyTorch GPU evidence.
- Show the bridge health check and app AMD-online indicator.
- Keep at least one complete inference wait uncut and at normal speed.
- Show one Paint a Place result and one different postcard or virtual-memory
  result to demonstrate diversity.
- Show one successful Qwen pointed-object result.
- Show provider and timing metadata after every Radeon operation.
- Show a saved or downloaded final artifact, not only a preview.
- Include the architecture diagram and explain the deliberate browser/AMD split.
- Do not claim that voice or identity-preserving two-reference generation runs
  on AMD; those are OpenAI services/fallbacks in the current architecture.
- End with the repository URL and the exact submission pull-request title:
  `Track 1, Eimis Pacheco, My Magic Map AGI`.
