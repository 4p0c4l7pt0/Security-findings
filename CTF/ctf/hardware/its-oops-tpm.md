---
layout: page
title: "Hardware: It's Oops TPM"
permalink: /ctf/hardware/its-oops-tpm/
---

# Hardware: It's Oops TPM

| Field | Details |
|---|---|
| **Platform** | Hack The Box |
| **Category** | Hardware |
| **Difficulty** | Easy |
| **Technique** | VHDL source-code and logic analysis |

> **Scope note:** This write-up covers an intentionally vulnerable CTF challenge. All interaction described here was performed against the challenge files and service provided by the platform.

## Introduction

I selected **It's Oops TPM** as a hardware-focused CTF challenge and started by downloading and inspecting the provided files.

Most of the relevant design files were written in **VHDL**. VHDL (VHSIC Hardware Description Language) is a hardware description language used to describe and model digital systems. It is text-based, which makes source-code review an important part of analyzing a challenge like this one.

![Initial inspection of the supplied challenge files]({{ '/assets/images/ctf/hardware-its-oops-tpm/01-challenge-files-terminal.png' | relative_url }})

*Figure 1 — Initial inspection of the challenge files, including the VHDL design files.*

The challenge also included a schematic image. Reviewing that diagram first helped establish the intended logic and data flow.

---

## Understanding the schematic

The schematic presents a simplified security-related data path involving cryptographic logic, validation logic, and a **multiplexer (MUX)**.

A multiplexer is a digital circuit that selects one of several possible inputs and forwards the selected input to its output. In this design, the MUX is therefore best understood as a **selection component** within the data path.

![Simplified schematic showing the data flow and selection logic]({{ '/assets/images/ctf/hardware-its-oops-tpm/02-schematic-data-flow.png' | relative_url }})

*Figure 2 — Simplified challenge schematic showing the input, cryptographic processing, validation logic, and multiplexer.*

The important observation was the presence of an alternate path associated with a validation condition. This suggested that a particular input or key-related condition could cause data to follow a different route through the design.

That observation became the starting point for reviewing the VHDL implementation.

---

## Analyzing the VHDL design

I also used **GHDL** while examining the supplied design.

GHDL is an open-source VHDL analyzer, compiler, and simulator. It can be useful for checking design structure and behavior, although in this challenge the most important information was visible directly in the source files.

![GHDL analysis of the supplied VHDL design]({{ '/assets/images/ctf/hardware-its-oops-tpm/03-ghdl-analysis-output.png' | relative_url }})

*Figure 3 — GHDL output used while inspecting the relationships and structure of the supplied VHDL design.*

After the initial analysis, I focused on the individual source files.

---

## Reviewing `encryption.vhdl`

The `encryption` entity exposes two input ports, `D` and `K`, and one output port, `E`.

The source performs bitwise logic involving the input data and key, including XOR operations. The implementation also contains conditional behavior that affects specific values or positions.

![Relevant section of the encryption VHDL source]({{ '/assets/images/ctf/hardware-its-oops-tpm/04-encryption-vhdl-source.png' | relative_url }})

*Figure 4 — The relevant `encryption.vhdl` logic showing the bitwise processing used by the challenge.*

A terminology point is worth noting here: values connected through an entity interface are more accurately described as **ports and signals** than as function arguments.

Although this file explained the normal processing path, it did not provide the most direct solution.

---

## Reviewing `backdoor.vhdl`

The key behavior appeared in `backdoor.vhdl`.

This entity has one input, `D`, and one output, `B`. The source defines a fixed constant named `Pattern`:

```text
1111111111101001
```

![Relevant section of the backdoor VHDL source]({{ '/assets/images/ctf/hardware-its-oops-tpm/05-backdoor-vhdl-source.png' | relative_url }})

*Figure 5 — The `backdoor.vhdl` source containing the fixed comparison pattern.*

The value is a 16-bit binary number. In hexadecimal notation, it is:

```text
0xFFE9
```

The comparison logic checks whether the supplied input matches this exact pattern. When the comparison succeeds, the output is asserted; otherwise, it remains deasserted.

Within the context of this intentionally vulnerable CTF design, the hard-coded comparison acts as a trigger condition for the alternate behavior suggested by the schematic.

---

## Solution

After identifying the required trigger value, I connected to the challenge service using the IP address and port supplied by the platform and submitted:

```text
1111111111101001
```

The challenge accepted the value and returned the flag.

![Challenge service response after submitting the trigger value]({{ '/assets/images/ctf/hardware-its-oops-tpm/06-trigger-submission-result.png' | relative_url }})

*Figure 6 — Challenge response after the identified trigger pattern was submitted.*

## Flag

```text
HTB{4_7yp1c41_53cu23_TPM_ch1p}
```

---

## Key Takeaways

- **VHDL** is a hardware description language used to model digital logic.
- A **MUX** selects between inputs and forwards the selected signal to its output.
- **GHDL** can analyze, compile, elaborate, and simulate VHDL designs.
- In VHDL, interface values are generally described as **ports and signals**, rather than function arguments.
- Hard-coded comparison values can reveal hidden trigger conditions in intentionally vulnerable challenge logic.
- Binary-to-hexadecimal conversion can make fixed bit patterns easier to recognize and analyze.

---

## Skills Demonstrated

`VHDL Analysis` · `Hardware CTF` · `Source Code Review` · `Digital Logic` · `Binary Analysis`
