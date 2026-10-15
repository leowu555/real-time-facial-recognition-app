# Real-Time Facial Recognition System in C++

A performance-oriented real-time facial recognition and computer vision system built in modern C++.

The project is designed to explore the intersection of computer vision, machine learning inference, concurrent systems, and computer networking. Rather than implementing facial recognition as a single sequential loop, the long-term goal is to build a modular real-time perception pipeline with concurrent video processing, embedding-based recognition, performance instrumentation, and networked recognition services.

> Status: Active development

---

## Overview

The system processes live webcam or video input and identifies known individuals using a multi-stage computer vision pipeline:

1. Capture video frames
2. Detect faces
3. Preprocess and align detected faces
4. Generate facial embeddings
5. Compare embeddings against enrolled identities
6. Produce recognition events and confidence scores

As the project develops, these stages will be separated into concurrent processing components and connected to a lightweight network service for remote recognition event delivery.

The project is intentionally designed as an incremental system: each development milestone produces a complete working application while introducing additional systems-level concepts.

---

## Goals

The main goals of this project are to explore:

- Modern C++ software architecture
- Real-time computer vision with OpenCV
- ML inference from C++
- Facial embedding and similarity search
- Multithreaded producer-consumer systems
- Thread synchronization and resource management
- TCP/IP networking
- Performance profiling and optimization
- Automated testing and reproducible builds

---

## Planned Architecture

```text
                ┌─────────────────────┐
                │ Camera / Video Input │
                └──────────┬──────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │   Frame Capture   │
                 └─────────┬─────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │ Bounded Frame Queue  │
                └──────────┬───────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │  Face Detection   │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Face Preprocessing│
                 │    / Alignment    │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Embedding Inference│
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Identity Matching │
                 └─────────┬─────────┘
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
      ┌────────────────┐        ┌─────────────────┐
      │ Local Display  │        │ Network Events  │
      └────────────────┘        └─────────────────┘
