# NeuroSymLand

Official repository for **NeuroSymLand: Neuro-Symbolic Landing-Site Assessment for Robust and Edge-Deployable UAV Autonomy**.

NeuroSymLand is a neuro-symbolic landing-site assessment framework for markerless UAV autonomy. The system combines lightweight visual perception with an explicit probabilistic semantic scene graph and deterministic symbolic reasoning, allowing candidate landing regions to be evaluated with interpretable safety constraints rather than an end-to-end black-box landing score.

## Code Release Status

Source code will be released once clearance is obtained from our drone company partner. We have already requested this clearance.

Until the release is approved, this repository serves as the public project page for the paper.

## Project Assets

- **Simulator visualization**: [Google Drive asset](https://drive.google.com/file/d/16Y5i1yXX0HGh6FK1l6ck3CDegux9-FHB/view?usp=drive_link)
- **Drone dataset and safety-rule construction collection**: [Google Drive asset](https://drive.google.com/file/d/1LwFUu4yvaTn38UN9Th2bbgJjNefIS3j0/view?usp=drive_link). This collection is used to construct and refine the safety rules.

## Overview

Safe landing-site assessment in unstructured environments requires reasoning about terrain, obstacles, people, spatial relations, and mission-specific constraints under perceptual uncertainty. NeuroSymLand addresses this by separating the system into three stages:

1. **Perception and geometric post-processing**: an INT8-quantized SegFormer-B0 backbone and lightweight geometric processing extract semantic regions and landing-relevant attributes from onboard monocular visual input.
2. **Probabilistic semantic scene graph construction**: semantic regions are lifted into a probabilistic semantic scene graph (PSSG) with object classes, geometric attributes, and spatial relations such as `near_to`, `adjacent_to`, and `contain`.
3. **Symbolic mission-level reasoning**: a validated Scallop rule set evaluates candidate landing regions using explicit constraints for hazards, obstacle clearance, terrain suitability, and mission context.

The deployed runtime does **not** query an LLM. LLMs are used only offline as rule-authoring assistants, where draft symbolic rules are inspected, tested, and refined through human-in-the-loop validation before deployment.


