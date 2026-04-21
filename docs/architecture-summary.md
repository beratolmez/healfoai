# Architecture Summary

## High-Level Components

### Mobile

- Flutter app
- handles onboarding, dashboard, history, profile, coach, and meal logging

### Backend

- FastAPI service
- handles auth, profile, targets, logs, stats, planner, and inference endpoints

### ML Workspace

- taxonomy
- dataset manifests
- training entrypoints
- benchmark tooling
- export metadata

## Food Analysis Flow

1. user captures or selects a meal image
2. mobile sends multipart image payload to `/infer`
3. backend inference returns ranked food predictions
4. predicted labels are mapped through a catalog layer
5. matched food records provide calorie and macro values
6. user saves one meal log with one or more food items

## Current Runtime Reality

- live runtime still uses the legacy ONNX classifier path
- exported classifier and detector pipeline are benchmark-stage surfaces
- runtime promotion is intentionally staged rather than immediate

## Why This Matters

This project is not just a mobile UI demo.

It includes:

- product UX
- API and database design
- nutrition planning logic
- CV/ML experimentation discipline
- rollout safety mechanisms
