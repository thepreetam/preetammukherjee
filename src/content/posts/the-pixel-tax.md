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

For many years, video technology has been tailored to match what the human eye perceives.

Every video format, like H.264, HEVC, and AVI, relies on standards such as SSIM or VMAF to determine how appealing a video appears to us. However, machines have now quietly become the main consumers of these videos. When a camera in a factory or on an offshore platform feeds data into a PyTorch model, its goal isn't to entertain viewers. Instead, it aims to spot defects, monitor objects, or detect anomalies.

Yet despite this change in audience focus, we continue to pay for encoding and transmitting raw video data that neural networks promptly discard. This is what we're now calling the "pixel tax."

The tax gets collected at three separate points: uplink, cloud decode, and storage layer. Sure, bandwidth costs are dropping, but it's misleading to mix up the consumer's cheaper download with the more expensive industrial upload. Thanks to Starlink and 5G, downloading from the cloud is almost effortless, but uploading from distant devices isn't easy. Remote sensors still deal with limited or slow cellular and satellite connections. Adding more cameras just moves the issue from wireless backhaul to the cloud intake cluster, where costs pop up again: every frame needs full reconstruction or entropy decoding. The model applies motion compensation and loop filtering, only to shrink it into a small feature grid later.

Right now, the usual industry response is to shift inference tasks to the edge devices. However, managing many remote hardware devices is quite challenging. A 15W edge ASIC can't compete with a large cloud-based system. Moreover, if the edge model fails, you lose visual context needed for later analysis. All you're left with is a mysterious device and no way to trace what happened.

It's not about choosing between raw pixels or edge inference; instead, it's about where the representation layer should be located. We need to move beyond sending pixels and focus on delivering something more meaningful.

Neural networks now work with compressed latent representations. Attempts have been made before, like with VACE and DARPA's Mind's Eye, but those were ahead of their time. They relied on hand-crafted feature descriptors such as SIFT or HOG, which proved too fragile and ran on hardware incapable of real-time processing.

However, things have changed now. With the advancement of transfer learning, multi-task feature pyramids, neural entropy coding, and efficient edge accelerators, it's finally possible to run a learned encoder in practical scenarios. Cameras today can encode data into a compact bitstream that's native to the model. This bitstream is sent over an uplink and unpacked by a cloud system. The service supports multiple downstream models at the same time. If someone needs to view the footage, a neural reconstruction head can generate the RGB on demand. Standards organizations are beginning to take notice. ISO/IEC's MPEG-FCM implies that the old methods are obsolete, even if their early drafts seem to squeeze machine features into outdated YUV frameworks.

Major players like Apple and InterDigital are acquiring neural-codec startups, which indicates a shift in core technology. In the long run, owning the bitstream format won't hold much value — it will become as common as JPEG.

The true advantage will lie in mastering the adaptation pipeline. Maintaining this edge is crucial. The real challenge is in aligning edge encoders with the ever-changing cloud infrastructure. They must keep an eye on shifts in features due to dynamic physical surroundings and constantly adjust for hardware limitations.

For new setups, particularly those using limited and costly connections, this shift is not theoretical but an urgent need. As priorities move from mere visuals to data-driven intelligence, the financial dynamics of the whole infrastructure can transform rapidly.
