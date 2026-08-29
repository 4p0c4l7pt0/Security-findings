---
layout: page
title: "Hardware: Critical Flight"
permalink: /ctf/hardware/critical-flight/
---

# Hardware: Critical Flight

| Field | Details |
|---|---|
| **Platform** | Hack The Box |
| **Category** | Hardware |
| **Difficulty** | Easy |
| **Technique** | Gerber file and PCB-layer inspection |

> **Scope note:** This write-up covers an intentionally designed CTF challenge. All analysis was performed using the files provided for the challenge.

## Introduction

To practice another area of security and CTF problem solving, I chose the hardware challenge **Critical Flight**.

After downloading and extracting the provided archive, I noticed several files using the `.gbr` extension.

![Initial inspection of the extracted Gerber files]({{ '/assets/images/ctf/hardware-critical-flight/01-gerber-files-initial-inspection.png' | relative_url }})

*Figure 1 — Initial inspection of the files supplied with the challenge.*

---

## Understanding the file format

Files with the `.gbr` extension commonly contain **Gerber** data.

Gerber is a standard format used in PCB manufacturing workflows to describe individual layers of a printed circuit board. Depending on the layer, Gerber files can represent copper traces, pads, solder masks, silkscreen, board outlines, and other manufacturing information.

I first checked whether the complete flag might simply be available as readable text in one of the files.

![Continued inspection of the extracted Gerber data]({{ '/assets/images/ctf/hardware-critical-flight/02-gerber-files-continued-inspection.png' | relative_url }})

*Figure 2 — Continued inspection of the challenge files before moving to a visual PCB representation.*

A basic text-based inspection did not reveal the complete flag. This suggested that the useful information might instead be encoded visually in one or more PCB layers.

---

## Rendering the PCB

To inspect the Gerber data visually, I loaded the supplied files into a Gerber/PCB viewer.

The rendered result showed the PCB as a complete design, making it possible to inspect individual manufacturing layers.

![Rendered overview of the PCB design]({{ '/assets/images/ctf/hardware-critical-flight/03-rendered-pcb-overview.png' | relative_url }})

*Figure 3 — Combined visual rendering of the PCB generated from the supplied Gerber files.*

At first glance, the complete flag was not immediately obvious.

Because the challenge was categorized as easy, I considered the possibility that the answer was intentionally visible in the PCB artwork. I therefore began inspecting the layers individually rather than relying only on the combined board view.

---

## Inspecting the bottom copper layer

While examining the board layers, I found a visible piece of text on the **bottom copper layer**.

![Bottom copper layer revealing part of the hidden text]({{ '/assets/images/ctf/hardware-critical-flight/04-bottom-copper-layer-clue.jpeg' | relative_url }})

*Figure 4 — Bottom copper layer containing the first visible portion of the challenge answer.*

Submitting that portion by itself did not solve the challenge, indicating that the visible text was only one part of the final answer.

---

## Finding the remaining clue

I continued inspecting the other available layers and found another piece of text that had not been obvious during the initial inspection.

![Additional PCB layer revealing the remaining clue]({{ '/assets/images/ctf/hardware-critical-flight/05-additional-layer-clue.jpeg' | relative_url }})

*Figure 5 — Additional layer inspection revealing the remaining portion needed to reconstruct the complete flag.*

Combining the text fragments from the relevant layers produced the complete flag.

---

## Flag

```text
HTB{533_7h3_1nn32_w02k1n95_0f_313c720n1c5#$@}
```

---

## Key Takeaways

- `.gbr` files commonly contain **Gerber PCB manufacturing data**.
- PCB designs are composed of multiple layers, each of which can contain unique visual information.
- A combined board rendering can hide clues that become visible when layers are inspected separately.
- In hardware and PCB-oriented CTFs, visual analysis can be as important as text-based file inspection.
- When a discovered answer fragment does not validate, inspecting the remaining layers may reveal additional required information.

---

## Skills Demonstrated

`Gerber Analysis` · `PCB Inspection` · `Hardware CTF` · `Visual Analysis` · `File Format Analysis`
