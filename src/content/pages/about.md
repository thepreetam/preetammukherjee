---
title: "About"
description: "About Preetam Mukherjee"
---

I build systems that let machines see without needing a firehose of data.

Most AI systems assume more bandwidth than is available in the field. Raw video is heavy, slow, and expensive to move over links like drone, subsea, and remote sensor connections. At [Mahamaia Systems](https://mahamaia.com), I'm building **OUTPOST**, a neural feature compression codec that extracts meaning from sensor data before transmission, reducing what has to travel over the connection.

## Background

I started in robotics at Asyst Technologies, testing SMIF I/O systems that moved silicon wafers through semiconductor fabrication lines.

Then [Cisco](https://www.cisco.com/c/en/us/tech/voice/ip-telephony-voice-over-ip-voip/index.html), where I worked on Enterprise Voice and Video over IP.

At [UC Berkeley](https://berkeley.edu)'s [Garage Cinema Research](https://www.ischool.berkeley.edu/events/2006/yahoo-research-berkeley-designing-future-social-media) group, I worked on Active Capture and Adaptive Media — research that contributed to the formation of Yahoo! Research Berkeley. The work focused on automating media production using computer vision and interaction design to direct, capture, and edit footage into finished media.

## Marcellus

In 2009, I co-founded Marcellus. We bootstrapped the company, grew the engineering team from two to thirty, and built an on-demand video transcoding platform used by major media companies across Asia, the Middle East, and Africa — including Jagran, Star TV, Nation Media, and Reliance Entertainment.

I operated as a forward-deployed engineer, running workflow assessments with enterprise customers and building integration patterns adapted to each customer's existing systems.

As Managing Partner of [The Marcellus Agency](https://agencym3.com), I served as primary technical advisor to brands including [VANS](https://www.mensjournal.com/travel/vans-launches-custom-boardshort-program) and New Balance, leading delivery on systems tied to multi-million-dollar revenue programs. This meant translating business requirements into technical architecture and coordinating stakeholders from discovery through deployment.

## OUTPOST

After roughly fifteen years working on video transmission, I shifted focus from moving video faster to reducing how much data needs to move at all. The constraint in edge deployments — drones, subsea vehicles, remote sensors — is typically uplink bandwidth, power budget, and latency, measured in milliseconds rather than compute capacity.

This led to OUTPOST: instead of transmitting full frames, the system extracts and transmits semantic features — the minimum signal required for a downstream model to perform detection or classification.

## Current work

I own product vision end-to-end. I've built and shipped a complete encoder-decoder pipeline in Python, designed a downstream-aware evaluation framework to measure detection accuracy retention under bandwidth and frame-drop constraints, and filed patents on [constrained quantum optimization](https://doi.org/10.64898/2026.01.27.699805) and tensor-train networks for parameter-efficient medical imaging. I built Prañāda, a retinal screening platform achieving 91.6% accuracy.

I work across PyTorch, LangGraph, Docker, and Kubernetes on AWS and GCP, building agentic AI systems and RAG pipelines, evaluation frameworks that connect model performance to business outcomes, and translating customer requirements into production architecture.

## Location and focus

I'm based in San Francisco, working at the intersection of AI, video infrastructure, and edge deployment constraints — bandwidth, power, and latency.

If you're working on similar constraints — defense, robotics, industrial AI, or another edge-deployment problem — I'd like to hear from you.
