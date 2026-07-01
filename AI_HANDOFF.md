# AI Handoff

This file is the permanent shared memory between ChatGPT, Claude, Gemini, and future AI assistants to continue development seamlessly.

## Current Stage

Architecture is 100% complete. Implementation of concrete computer vision algorithms is starting.

## Current Architecture Status

The core architecture (Strategy Pattern + Dependency Injection) is fully finalized. The `CoarseToFineEngine` orchestrates abstract components: `FeatureExtractor`, `CoarseLocalizer`, `FineMatcher`, and `GeometricVerifier`. Data models use frozen dataclasses to ensure immutability.

## Completed Components

- BenchmarkRunner
- MatchingEngine abstraction
- Prediction models
- Metrics placeholder
- CoarseToFineEngine orchestration
- FeatureExtractor abstraction
- CoarseLocalizer abstraction
- FineMatcher abstraction
- GeometricVerifier abstraction
- Dummy benchmark pipeline
- Complete coarse-to-fine interface hierarchy

## Remaining Components

- DINOv2 Feature Extractor
- Global Similarity matching
- Heatmap Generation
- Candidate Localization
- ALIKED Keypoint Detection
- LightGlue Feature Matching
- OpenCV RANSAC Geometric Verification
- Metrics implementation
- RGB + Thermal Validation
- Jetson Optimization

## Current Implementation Status

Dummy engines work. No real neural networks are hooked up yet. The next phase will implement real models targeting the abstract interfaces.

## Next Immediate Task

Implement `DINOv2FeatureExtractor`.

## Known Architectural Decisions

- **Single Unified Pipeline**: The benchmark supports BOTH RGB and Thermal images using ONE unified pipeline. Separate RGB and Thermal models will NOT exist. The same engine must process both modalities. Future datasets will contain RGB references and Thermal references using the same directory structure.
- **Framework Independence**: Core abstractions do not depend on ML frameworks.
- **Orchestrator-Only Engine**: `BenchmarkRunner` only orchestrates; it does not match or evaluate.

## Current Pipeline Status

- Interfaces: Implemented and complete.
- Concrete Implementations: Future/Pending.

## Repository Health

- Architecture is clean, modular, and highly documented.
- No duplicated documentation.
- Validation dataset and XML parsing are functional.

## Recent Milestones

- Finished the entire architectural layout, including `GeometricVerifier` abstraction, finalizing the `CoarseToFineEngine` pipeline design.

## Future Milestones

- Integrate DINOv2
- Implement Global Similarity & Heatmap Candidate Localization
- Integrate ALIKED & LightGlue
- Implement RANSAC
- Calculate Metrics
- Jetson Deployment