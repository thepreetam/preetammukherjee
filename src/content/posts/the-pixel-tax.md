---
title: "The Pixel Tax"
description: "Why encoding and transmitting raw video for neural networks is a cost we can no longer afford."
pubDatetime: 2026-07-23
tags:
  - video
  - ai
  - edge-computing
  - neural-compression
  - infrastructure
---

These days, most videos aren't viewed by people. Instead, they are processed by neural networks. We've hit a turning point: machines, not human eyes, are the main audience for visual data. But our technology for handling this data hasn't caught up. Every video frame is still dealt with as if a person were watching it on the other side.

This outdated approach leads to what you could call the "pixel tax." It refers to all the costs of processing video data—encoding, sending, decoding, and storing—that machine learning systems end up ignoring anyway.

## Understanding Waste

To grasp this concept of waste, consider how things work. A high-resolution camera captures an 8 MB frame. It gets encoded using H.265, which is designed for human eyes, sent over a network, and decoded when it reaches the cloud's entry point. Only after these steps does it reach the model. However, the model doesn't require 8 MB of RGB textures. When data enters a ResNet or ViT backbone, the first convolutional layer immediately reduces its size, turning rich visual information into a smaller feature tensor, possibly around 64 KB.

This means we wasted resources on transferring and storing about 7.93 MB of unnecessary information. This inefficiency in handling pixels is what we call the "pixel tax."

Our current system architecture reflects outdated practices from when one server needed to communicate with many viewers at once. Today's cameras still operate under this old-fashioned model. Pixels are captured in their raw form and encoded using H.265 or H.264 standards, focusing on human-centric data processing. The network connection is costly when sending this information uplink, where it's decoded in the cloud into RGB format for further analysis using CNN or ViT backbones. The data is condensed into a latent representation of 64 KB, allowing detectors and trackers to operate efficiently. This integrated flow of capturing, transporting, and analyzing data means you can't tweak one part without affecting the others; optimizing transport impacts inference and vice versa.

The trend in technology demands a shift towards transport systems that natively handle representations rather than visual renderings. To achieve this, we should separate encoding processes from visual outputs. In this setup, edge devices take on the complex task of generating latent representations before any data reaches limited uplink channels.

In the future, cameras will incorporate learned latent encoders that compress data into a 64 KB bitstream before it traverses constrained networks. Uplink feeds into a system that decodes cloud features and tracks objects, possibly with neural RGB reconstruction. By sending data from the latent space, we drastically cut down on uplink requirements. The bitstream acts as an agreement between the encoder and decoder. If someone needs to examine a scene later, a neural reconstruction head can create RGB frames from stored data whenever needed.

Why is this happening now? Four major technologies are coming together, making this shift unavoidable. Modern backbones now work across different fields without needing manually created feature descriptors like SIFT or HOG. Also, we've reached the point where we can allocate bits adaptively within the latent space through learned entropy coding. Space holds a lot of information, even more than typical image codecs can manage. On the edge of technology, there's now over 200 TOPS edge silicon within a 15–50 W range. This advancement enables neural encoders to operate directly on cameras. A single feature grid can supply data for object detection, tracking, and segmentation all at once. This means frames don't need separate processing for each task anymore. Standards organizations are taking notice of this trend. MPEG-FCM (Feature Compression for Machines) is emerging as a sign that the industry is focusing more on machine-native visual representations rather than keeping them as a niche experiment.

## The Competitive Edge

When codec layers become widespread and standardized—as all bitstream formats eventually do—the real value will shift. Owning the format doesn't guarantee success. The real competitive advantage lies in the ability to adapt: keeping edge encoders aligned with evolving cloud infrastructures, checking for changes in dynamic environments, and adjusting latents to fit hardware limits. Companies that excel won't be those clinging to pixels; they'll be those mastering how intelligence flows.

## Looking Forward

Over the past thirty years, video has been refined for what humans see. In the coming three decades, it'll be shaped for how machines understand. Pixels aren't disappearing; they're just no longer at the forefront of interaction between the physical world and our smart systems.
