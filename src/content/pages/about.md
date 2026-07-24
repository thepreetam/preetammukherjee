---
title: "About"
description: "About Preetam Mukherjee"
---

I build systems that let machines see without needing a firehose of data.

Most AI systems assume more bandwidth than is available in the field. Raw video is heavy, slow, and expensive to move over links like drone, subsea, and remote sensor connections. At Mahamaia Systems, I'm building OUTPOST, a neural feature compression codec that extracts meaning from sensor data before transmission, reducing what has to travel over the connection.

## Background

I started in robotics, doing cleanroom automation at Asyst Technologies, testing SMIF I/O systems used to move silicon wafers through fabrication lines.

I then worked at Cisco on Enterprise Voice and Video over IP, dealing with latency, jitter, and packet loss in real-time communication systems.

At UC Berkeley's Garage Cinema Research group, I worked on Active Capture and Adaptive Media, research that contributed to the formation of Yahoo! Research Berkeley. The work focused on automating media production — using computer vision and interaction design to automatically direct, capture, and edit footage into finished media.

## Marcellus

In 2009, I co-founded Marcellus. We bootstrapped the company, grew the engineering team from two people to thirty, and built an on-demand video transcoding platform used by media companies across Asia, the Middle East, and Africa, including Jagran, Star TV, Nation Media, and Reliance Entertainment. I worked as a forward-deployed engineer, running workflow assessments with enterprise customers and building integration patterns adapted to each customer's existing systems.

As Managing Partner of The Marcellus Agency, I served as primary technical advisor to brands including VANS and New Balance, leading delivery on systems tied to multi-million-dollar revenue programs. This involved translating business requirements into technical architecture and coordinating stakeholders from discovery through deployment.

## OUTPOST

After roughly fifteen years working on video transmission, I shifted focus from moving video faster to reducing how much data needs to move at all. The constraint in edge deployments — drones, subsea vehicles, remote sensors — is typically uplink bandwidth, power budget, and latency, often measured in milliseconds rather than compute capacity.

This led to OUTPOST: instead of transmitting full frames, the system extracts and transmits semantic features — the minimum signal required for a downstream model to perform detection or classification.

## Current work

I own product vision end-to-end. I've built and shipped a complete encoder-decoder pipeline in Python, built a downstream-aware evaluation framework using Faster R-CNN to measure detection accuracy retention under bandwidth and frame-drop constraints, and filed patents on constrained quantum optimization and tensor-train networks for parameter-efficient medical imaging.

I work across PyTorch, LangGraph, Docker, and Kubernetes on AWS and GCP, building evaluation frameworks that connect model performance to business outcomes, and translating customer requirements into production architecture.

## Location and focus

I'm based in San Francisco, working at the intersection of AI, video infrastructure, and edge deployment constraints — bandwidth, power, and latency.

If you're working on similar constraints — defense, robotics, industrial AI, or another edge-deployment problem — I'd like to hear from you.
