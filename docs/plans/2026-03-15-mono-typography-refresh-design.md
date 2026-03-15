# Mono Typography Refresh Design

**Date:** 2026-03-15

## Goal

Improve the page typography while keeping a strict one-font rule across the entire experience.

## Context

The current page uses a single monospaced font, but it applies that font nearly uniformly across the hero, metadata, table headers, and body cells. That flattens the hierarchy and makes the page feel more like a default developer view than a deliberate market-radar interface.

## Chosen Direction

Use a more refined mono family and create hierarchy through:

- weight contrast
- tighter spacing and rhythm
- more deliberate letterspacing
- clearer numeric emphasis
- responsive scale tuning

The visual target is institutional terminal: data-dense, premium, and controlled.

## Scope

- Keep the current layout, colors, and interaction model.
- Keep the one-font constraint across all selectors.
- Refresh the hero, subtitle, chip, table header, and numeric styling.
- Preserve mobile readability in the card layout.

## Non-Goals

- No structural layout rewrite
- No new JavaScript behavior
- No additional font families

## Verification

Add a small regression script that checks:

- exactly one Google Fonts family is imported
- the page defines one mono font token
- all explicit `font-family` declarations resolve to that mono token
- key selectors retain the intended hierarchy rules
