---
name: ekphrasis
description: Use when writing prompts for an image or animation generator — cover art, hero images, podcast covers, product renders, stop-motion sheets, thumbnails, or any request phrased as "generate an image", "make artwork", "create a cover", "an image prompt for ChatGPT/Codex/Flux/Midjourney/DALL-E", or when generated art comes back looking glossy, generic, or obviously AI. Also use when animation frames jitter or refuse to hold a consistent subject. This is prompt AUTHORSHIP, not image editing — for producing and optimising image files see `image`, for ad specs see `ad-creative`, for video see `hyperframes`.
---

# ekphrasis

Classical *ekphrasis* is the vivid description of a visual work in words. That is
exactly this: words engineered to produce an image, rather than words that
describe a mood and hope.

## Provenance

Distilled from the `codeai-artist` agent's own vault in Chatterbot 2000, written
during a working conversation with the owner:

- `AppData\Roaming\Chatterbot 2000\Vault\codeai-artist\ref-prompt-methodology.md`
- `AppData\Roaming\Chatterbot 2000\Vault\codeai-artist\ref-legibility-tell.md`

⚠ This is a *field method*, not a paper. It was arrived at by generating images,
looking at them, and naming what went wrong. Its claims about mechanism are
stated below with their limits attached, because the method's own honesty is
part of why it works.

---

## The core stance

**Slop is not cured by adding adjectives. Adding adjectives is how slop is made.**

Slop comes from prompts that describe a **mood** instead of a **subject**. Given
a mood, the model fills every unspecified gap with its most probable answer, and
the sum of most-probable answers is the mean of everyone's averages. That mean
*is* the glossy AI look.

The method is **specificity plus constraint**. It is the opposite of a
style-word pile.

⛔ Delete on sight: `8k`, `hyperdetailed`, `masterpiece`, `award-winning`,
`cinematic`, `stunning`, `breathtaking`, `ultra-realistic`, `trending on
artstation`. Every one of them pushes the sample toward the generic centre.

---

## The six principles

**1. Name a real subject with particularity.**
Not "a forest" but *"a stand of birches in November, one leaning against its
neighbour, bark peeling in narrow strips."* Give the model something concrete
to anchor to.

**2. Commit to one light source with a physical direction.**
Slop lives in diffuse, directionless light. *"Late northern light through a high
window, long raking shadows"* forces choices the model would otherwise average
away.

**3. Say what the image is NOT.**
Use the negative field: no lens flare, no chromatic aberration, no
oversharpening, no soft-focus glow, no cinematic lighting, no 8k.

**4. Restrict the medium explicitly.**
"Colour photograph" drifts to commercial gloss. *"Shot on 35mm film, mild grain,
halation"* or *"soft charcoal study, visible smudges and erased lines"* fights
the plastic sheen directly.

**5. Give the composition a job.**
Ask for asymmetry, negative space, an off-centre subject, a quiet corner.
Restraint reads as intention.

**6. Know what it is FOR before writing.**
A cover, a mood board, a texture study and an editorial illustration each want a
different prompt. Writing before knowing produces a prompt that serves none of
them.

---

## The legibility tell

**The single most reliable giveaway, and most people cannot name it.**

Image models are rewarded for text being *readable*. So they rotate documents,
signs, books and labels flat-on to the viewer, at readable angles, in readable
type, **even when nobody in the scene would arrange them that way**. The model is
not reasoning about the scene's internal logic. It is arranging the world for the
viewer's convenience.

Once you can see it you cannot unsee it. It is the same mechanism that makes AI
hands hold objects at awkward camera-facing angles.

### The four-move fix, strongest first

1. **Take the text out of the image entirely.** The strongest fix by a distance.
   *"A neat stack of folded papers bound by a rubber band, lying flat."* No text,
   no legibility pressure, no rotation problem. The meaning survives without
   visible words.
2. **If text must be readable, make it partial and incidental.** Never centred,
   never flat-on. *"A worksheet lying askew at the table's edge, half under a
   saucer, the edge faded."* Physics anchoring makes rotation harder.
3. **Reduce the count.** One legible element is a target. Three is a cluster the
   model arranges like a display. Cut to one, or swap readable things for
   unlabelled equivalents — a paper cup instead of a worksheet.
4. **Add a recessional instruction.** *"The table is seen at a steep
   three-quarter angle receding into the scene; objects follow the table's
   perspective, none facing the viewer."*

Inline negative that names the failure mode directly:

> no readable documents facing the viewer, no text turned toward the camera,
> nothing arranged for the viewer's convenience — every object follows the
> scene's own perspective

⚠ **Move 4 alone will not save you.** Models obey it unreliably. Removal is the
defence; the instruction is a bonus. When text is not in the frame at all, the
tell has nothing to latch onto.

---

## Animation: why sheets jitter, and the fix

**The diagnosis:** generators draw each frame autonomously with no shared
coordinate system. Frame 3's hand does not belong to frame 2's clock. The jitter
is the model having no consistent geometry across frames.

**The fix:** stop asking for frames. Ask for **one numbered contact sheet** with
gutters. Inside a single image the model *does* hold geometry.

Lock everything static identical across frames. Change only the moving part,
along a clean known sequence. End on a rest frame identical to frame 1 so it
loops.

Phrases that do the actual engineering:

- "identical framing and identical camera angle"
- "the only thing that changes between frames is [the moving part]"
- "[static elements] remain absolutely identical in every frame"
- Move along a **discrete known sequence** (12, 3, 6, 9, 12), never "continuous
  motion"
- Give complex motion an **arc**: down, up, peak, fall, land, settle, rest
- For multi-limb motion, describe each frame as an explicit named pose, limb by
  limb

**Assembly:**
- Generate several times and pick the sheet whose static elements match best.
- Assemble at **6–8 fps, not 24**. Stop-motion reads better slow, and slow hides
  inconsistency.
- To splice two sequences (walk into run): keep them as separate prompts sharing
  side view, character, medium and lighting. Both must **begin and end on an
  identical standing pose**. That pose is the seam. Hold it a beat at the join.

---

## Honest limits

**This is a strong tendency, not a law.** A weak base model, anatomy collapse, or
the platform's own post-processing can reintroduce slop no matter how good the
prompt is.

The real mechanism is **distribution averaging**: vague prompts push samples
toward high-probability regions of the training distribution. Models synthesise
from a learned distribution. ⛔ They do not retrieve stored images, and any
explanation that assumes they do will mislead you about what to change.

Expect to steer conversationally after the first render — *"turn the stack so I
see only its edge", "push the jar further into shadow", "make the table slope
away more steeply"*. A first generic result is normal, not failure.

---

## Working method

```
1. State what it is FOR in one sentence.        → principle 6
2. Name the subject with particularity.         → principle 1
3. Fix the light: one source, one direction.    → principle 2
4. Fix the medium.                              → principle 4
5. Give the composition a job.                  → principle 5
6. Strip text from the frame.                   → legibility tell, move 1
7. Write the negative line.                     → principle 3 + the tell
8. Generate several. Pick. Then steer in words.
```

## Composes with

- **`image`** — this writes the prompt; that generates, edits and optimises the
  resulting file. Use both.
- **`hyperframes`** / **`music-to-video`** — assemble contact sheets into motion.
- **`peitho`** — the prose counterpart. Same shape of problem: both are about
  refusing the most probable phrasing.
- **`ad-creative`** — platform specs and sizes once the art exists.

Deliberon's `codeai_artist` specialist (`specialist_send`) can author prompts
with this method, and `specialist_gfx_generate` renders them. ⚠ Both need
Deliberon running.
