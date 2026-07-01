# Future Work

This document serves as the prioritized implementation backlog for the project. Since the core architecture and all abstract interfaces are fully complete, focus shifts entirely to concrete computer vision implementations.

## Remaining Modules (Strict Priority Order)
1. **DINOv2 Feature Extractor**: Wrap DINOv2 to output dense features from both RGB and Thermal modalities (Highest Priority).
2. **Global Similarity Matching**: Implement semantic comparison logic.
3. **Coarse Heatmap Localizer**: Convert global features into bounding box candidates.
4. **ALIKED Keypoint Detector**: Implement the fine feature extractor.
5. **LightGlue Integration**: Implement the FineMatcher.
6. **RANSAC Geometric Verification**: Implement OpenCV based homography/fundamental matrix estimation to refine the bounding box.
7. **Metrics Integration**: Implement IoU, Precision, Recall calculations.
8. **RGB + Thermal Validation**: Benchmark unified pipeline performance.
9. **Jetson Optimization**: Apply TensorRT/INT8 quantization for deployment.

## Research Tasks
- Investigate the impact of various thermal preprocessing techniques (e.g., histogram equalization, pseudocolor) on DINOv2 zero-shot performance within the unified pipeline.
- Evaluate LoFTR vs. LightGlue in the FineMatcher stage on thermal sequences.

## Optimization Tasks
- Profile the `CoarseToFineEngine` latency once concrete models are active.
- Export DINOv2 and LightGlue to ONNX.

## Deployment Tasks
- Develop a TCP/UDP client for live video stream ingestion.
- Implement JSON serializers for bounding box telemetry output to ground stations.
- Containerize the application for Jetson (Docker + NVIDIA Runtime).

## Documentation Tasks
- Document the internal tensors shapes (e.g., `(B, C, H, W)`) throughout the pipeline.
- Produce video/GIF demonstrations of the pipeline working on validation sets.

## Long-term Improvements
- Support multi-object tracking (MOT) across frames using temporal heuristics.
- Investigate end-to-end differentiable matching architectures.
