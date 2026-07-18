---
name: Kirimdev B2B Dashboard
description: Clean, flat, minimalist CRM dashboard focused on technical productivity and clarity.
colors:
  primary: "#10B981"
  background: "#FFFFFF"
  surface: "#FFFFFF"
  surface-hover: "#F9FAFB"
  text-primary: "#111827"
  text-secondary: "#6B7280"
  border: "#E5E7EB"
  success: "#10B981"
typography:
  h1:
    fontFamily: "Inter, sans-serif"
    fontSize: "1.5rem"
    fontWeight: 700
    lineHeight: 1.2
    letterSpacing: "-0.02em"
  h2:
    fontFamily: "Inter, sans-serif"
    fontSize: "1rem"
    fontWeight: 600
    lineHeight: 1.5
  body-md:
    fontFamily: "Inter, sans-serif"
    fontSize: "0.875rem"
    fontWeight: 400
    lineHeight: 1.5
  label-sm:
    fontFamily: "Inter, sans-serif"
    fontSize: "0.75rem"
    fontWeight: 500
rounded:
  sm: "4px"
  md: "6px"
  lg: "8px"
  xl: "12px"
  full: "9999px"
spacing:
  xs: "4px"
  sm: "8px"
  md: "16px"
  lg: "24px"
  xl: "32px"
components:
  button-outline:
    backgroundColor: "transparent"
    textColor: "{colors.text-primary}"
    border: "1px solid {colors.border}"
    rounded: "{rounded.md}"
    padding: "6px 12px"
  button-outline-hover:
    backgroundColor: "{colors.surface-hover}"
  card:
    backgroundColor: "{colors.surface}"
    border: "1px solid {colors.border}"
    rounded: "{rounded.xl}"
    padding: "0" # Inner sections handle padding
---

## Overview
This design system is tailored for a professional, technical B2B tool. It prioritizes information density, readability, and a calm working environment. The aesthetic relies heavily on structure and typography rather than decorative elements.

## Colors
The palette is monochromatic (blacks, whites, grays) with a single emerald green accent used extremely sparingly. The green is reserved only for active indicators, status success, or specific promotional tags ("BETA").

## Typography
Geometric sans-serif (Inter) is used globally. Hierarchy is established purely through font weight (bold for headers, regular for body) and color contrast (near-black vs cool gray), rather than drastic size differences.

## Spacing & Layout
Follows a strict 8px grid. Layouts use a max-width approach on the main canvas to prevent lines of text from becoming too long on ultrawide monitors.

## Shapes
Corners use subtle rounding (6px-8px) to soften the interface slightly, preventing it from feeling completely brutalist, while maintaining a sharp, precise software feel.

## Elevation & Depth
**Strictly Flat.** No drop shadows are used in the primary interface. Depth and separation are achieved entirely by using a universal `1px solid #E5E7EB` border. 

## Motion & Interaction
- **Hover States:** Subtle background shifts to `#F9FAFB` on interactive rows.
- **Collapsible Elements:** The sidebar shrinks smoothly. Tooltips appear on hover when the sidebar is in its collapsed state to retain context without sacrificing screen real estate.

## Rules to Never Break
- Never use drop shadows or heavy blur effects.
- Never use primary colors (green) for large background areas or main layout elements.
- Always use the standard hairline border (`border-gray-200`) to separate distinct logical groups.