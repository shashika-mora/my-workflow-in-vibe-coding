# The Aesthetic Vibe Guide

This document instructs agents on how to generate aesthetic and consistent UI outputs.

## Adaptive Design Philosophy
- **Project Specific:** Always use a UI style and design system that best fits the specific project, application, and user requirements. Do not apply a rigid aesthetic (like glassmorphism) unless explicitly requested.
- **Context Awareness:** Before generating new UI components, analyze existing components in the `/src` directory to match their vibe.

## General Best Practices
- **Clean Structure:** Prioritize clear visual hierarchy and generous padding (`rem`-based spacing) over crammed layouts.
- **Micro-Animations:** Enhance UX with smooth, subtle interactions (e.g., slight scale transform or shadow on hover). Avoid jittery or hyper-fast animations; everything should feel deliberate.
- **Color & Typography:** Use harmonious, curated color palettes rather than generic primary colors. Use modern, highly readable web fonts depending on the project's brand guidelines.
