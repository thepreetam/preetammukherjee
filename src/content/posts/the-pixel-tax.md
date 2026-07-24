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

Each AI vision system ends up paying for the entire process of dealing with billions of pixels—capturing, compressing, transmitting, decoding, and storing them. However, these neural networks often discard most of that data almost instantly. This hidden infrastructure cost is turning into a massive inefficiency in today's AI technologies. Welcome to what we call the "pixel tax." It's essentially the price paid for handling all that data which machine learning models don't actually use.

## Understanding Waste

To grasp this concept better, let's follow a single frame's journey:

```
Camera
   |
RGB Pixels (~8 MB)
   |
H.265 Encode
   |
Network
   |
Decode
   |
CNN / ViT Backbone
   |
Feature Tensor (~tens of KB)
```

It begins with a camera capturing RGB pixels (about 8 MB), then moves through H.265 encoding. From there, it travels over a network where it's decoded before reaching the CNN or [ViT](https://arxiv.org/abs/2010.11929) backbone to become a feature tensor (only tens of KB). Notice how everything above this stage involves copying and processing vast amounts of unnecessary data. The backbone exists because the transport layer requires pixels, not because the model relies on them. The detector doesn't analyze JPEG blocks or RGB pixels; it processes learned representations. Pixels act as a costly format to send information to the network's first layer.

H.265 dedicates bits to maintaining textures, colors, and visual quality because it focuses on human perception, not what neural networks need for decision-making. Consequently, we incur costs in bandwidth, storage, and decoding for about 7.93 MB of superfluous data per frame—this is what you might call a pixel tax.

This inefficiency isn't spread evenly; it impacts most where bandwidth is limited and cameras are plentiful: offshore platforms, factories, mines, farms, satellites, ships at sea, and remote utility sites. Imagine a facility with 100 cameras each streaming at 8 Mbps. That setup creates about 800 Mbps of constant upload traffic. If machine-native formats cut that by ten times, it's not just theory—it opens up new affordable network options.

## The Architecture We're Stuck With

Now let's talk about current camera systems. They still work like old-school TV broadcasts meant for lots of people to watch. Cameras capture images, encode them with H.265 or H.264, send them over expensive connections, decode them back into RGB in the cloud before feeding them into neural networks like CNNs or ViTs. This process finally shrinks the data down to small representations, often just tens of kilobytes. Detectors and trackers can work smoothly, but by the time the model gets what it needs, the system has already paid for processing pixels multiple times. Similar to how cloud computing replaced shipping physical servers with virtual machines, machine-native vision swaps transporting pixels for conveying meaning. The focus shifts from appearances to representations.

## The Future Architecture

Looking ahead, a solution is to move the representation layer closer to where data is captured. Cameras will be equipped with specialized encoders that compress information into a small bitstream—usually just tens or hundreds of kilobytes—before sending it over limited networks. This compressed data then goes to a cloud-based decoder capable of supporting several models at once. If a person needs to look at the scene, a neural reconstruction head can create RGB images on request. Now, RGB becomes a target for reconstruction instead of the main format for transport. The bitstream acts as an agreement between encoder and decoder rather than serving as something for humans to see.

## Why Now

So, why is this happening now? No single technology could make this possible on its own. Together, they break down the final barriers to building a machine-native vision infrastructure. Modern systems like [DINOv2](https://arxiv.org/abs/2304.07193) operate across various fields without needing manually crafted features such as SIFT or HOG. With [learned entropy coding](https://arxiv.org/abs/1802.01436), bit allocation within the latent space becomes adaptive. Over 200 TOPS of edge silicon is accessible within a power range of 15–50 W, enabling neural encoders to function directly within cameras. A single feature grid that handles detection, tracking, and segmentation all at once—as seen in models like [Segment Anything](https://arxiv.org/abs/2304.02643)—removes the need for separate processing pipelines for each task. Standards bodies are taking notice; [MPEG-FCM (Feature Compression for Machines)](https://www.iso.org/standard/85443.html) is highlighting that machine-focused visual representations are shifting from experimental to mainstream importance.

## The Competitive Edge

Video codecs like H.264 and H.265 became widely used because everyone followed the same standard, turning them into commodities. Machine-native codecs will follow this trend. The true advantage lies not in the bitstream itself but in continuously adapting these representations to align with new models, hardware, and environments. Companies that thrive won't be those stuck on pixels; they'll be those adept at managing how intelligence flows.

## Looking Forward

The past three decades have been about optimizing video for human eyes. The next three will focus on making it suitable for machines to understand. Pixels aren't going anywhere—but they're no longer the primary interface between the physical world and the intelligent systems that analyze it.
