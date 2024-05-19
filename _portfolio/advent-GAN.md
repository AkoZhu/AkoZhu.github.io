---
title: "ADVENT: A DiVersE Neural Styles Transfer framework"
date: 2021-12-09
excerpt: "Built a DiVersE Neural styles Transfer framework in a team of three. <br/><img src='/images/portforlio/advent-style-transfer/diagram.png' width='70%'>"
location: "University of Pennsylvania"
collection: portfolio
---

_This is a course project for ESE546 Deep Learning(Fall 2021) at University of Pennsylvania._

Detail information shows in the [report](/files/advent-report.pdf).

# Introduction and Objective
Our team developed a framework, ADVENT(A DiVersE Neural styles Transfer framework) to address the limitations of traditional style transfer techniques. While existing methods like GANs are effective at transferring a single style to an entire image, they fall short when selective style transfer is required. Our goal is to create a versatile framework that allows multiple styles to be applied to different objects within a single image simultaneously. It could be achieved by integrating generative methods with object detection using pre-learned masks.

# Design Decision and Approach
The ADVENT framework processes images through the following pipeline:
1. **Resizing Images**: Images are resized to suit with the segment models.
2. **Object Segmentatin**: The resized images are passed through SegFormer and FCHarDNet to detect regions of interest and generate corresponding masks.
3. **Style Transfer**: Neural Style transfer modules apply different styles to the detected regions based on user selection.
4. **Blending**: The styled regions are blended with the original content image using binary masks to produce the final result.
We experimented with three publicly available dataset -- ADE20K, Cityspaces, and COCO-Stuff, to validate our framework's effectiveness. Each dataset provided diverse images and categories, allowing us to test the versatility and accuracy of our segmentation and style transfer models.

# Experimental Results and Conclusion
<p align="center">
  <img src="/images/portforlio/advent-style-transfer/example.png">
</p>
Our experiments demonstrated that ADVENT could achieve diverse neural style transfer with significant vidual impact. The framework successfully preserved the content of the original images while applying distinct styles to different objects, as evidenced by the clear visibility of details such as wrinkles in the styled images.

Despite the promising results, we identified areas for improvement, such as enhancing the boundary definition of segmented ojects and exploring additional filters to maintain content properties. 

Through developing the ADVENT, we have taken a significant step towards more intelligent and flexible neural style transfer, offering new possibility for creative expression and pratical applications in image process.
