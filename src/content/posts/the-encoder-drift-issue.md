---
title: "The Encoder Drift Issue"
description: "Why learned encoders degrade over time and why versioning them is harder than it looks."
pubDatetime: 2026-07-25
tags:
  - video
  - edge-computing
  - neural-compression
  - ml-systems
  - infrastructure
---

In a recent post about pixel tax, the idea was put forward to handle compression at the edge. Instead of dealing with pixels, features would be encoded, then decoded once in the cloud. This approach allows for unlimited downstream models. However, an important aspect was overlooked: what occurs six months after deploying that encoder?

A learned encoder constantly adapts and changes. Likewise, the environment it was designed for evolves too. Outdoor cameras face different lighting conditions with seasonal shifts. Warehouses might rearrange shelving units or introduce new forklifts on the floor. Traditional codecs remain unaffected by such changes because they ignore frame content entirely. On the other hand, a learned encoder can encounter issues when things change like this.

The value of the encoder lies in its ability to understand the statistics of a scene, but when those statistics change, we face what is known as domain shift—a common issue in machine learning. What gets less attention is the impact on a fleet of edge encoders that you can't easily access. When an encoder's performance deteriorates without clear indicators, you won't see an error message. Instead, slightly inferior data starts flowing into all connected models simultaneously, without any obvious clue pointing back to the encoder as the source. As a result, the accuracy of detectors may decline. People might think the detector needs retraining, missing out on identifying the real issue: an outdated encoder providing poor input.

## The Versioning Problem

Once diagnosed, things get trickier with the versioning issue. Imagine you manage to spot it and send an updated encoder to all users. However, the decoder in the cloud still reads from the old encoder's output space. The new encoder reshapes and redistributes this data differently. So, either you must retrain the decoder to align with these changes, or make sure the encoder update is compatible with the existing decoder—limiting potential improvements.

This isn't a novel challenge in software. It's similar to updating a serialization schema across a distributed system or releasing a new API version without causing disruptions. For older clients, there's a noticeable difference. In typical software systems, changing a schema is an intentional event that involves versioning. However, in learned perception systems, the "schema" emerges from training and can change without any deliberate intervention.

## Approaches

Addressing this isn't cost-free. One option is to keep the encoder unchanged, which results in gradual performance decline, sacrificing accuracy for stability. Alternatively, the decoder can undergo retraining whenever the encoder updates; thus, each update at the edge requires a coordinated update in the cloud as well.

Another approach is designing both encoder and decoder with a versioned interface, similar to how Protobuf schemas function. Field additions can be handled without disrupting older readers by embedding sufficient metadata in the bitstream. This allows a decoder to identify the version of the encoder and make necessary adjustments.

Eventually, this approach is likely where things will settle, resembling the "adaptation pipeline" advantage discussed earlier. Anyone is capable of creating an encoder and decoder that meet standards. However, fewer individuals are able to manage the continuous tasks of monitoring changes, retraining periodically, and ensuring synchronization between encoder and decoder versions across a widely dispersed fleet that's hard to access physically.

Standardizing the codec is straightforward. The real challenge lies in maintaining its accuracy over time and at scale—this ongoing effort isn't highlighted in whitepapers but represents where substantial work truly resides.
