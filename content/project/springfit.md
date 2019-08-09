+++
# Date this page was created.
date = "2019-08-01"

# Project title.
title = "springFit: Joints and Mounts that Fabricate on Any Laser-Cutter"

# Project summary to display on homepage.
summary = "SpringFit converts models in the form of 2D cutting plans by replacing all contained mounts, notch joints, finger joints, and t-joints. <br><br> Full-Paper presented in UIST 2019, New Orleans, LA, US"

# Optional image to display on homepage (relative to `static/img/` folder).
image_preview = "springfit.png"

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["UIST"]

# Does the project detail page use math formatting?
math = false

# Wide header image file


+++

![Pantograph](/img/springfit.png) 

---

Joints are crucial to laser cutting as they allow making three-dimensional objects; mounts are crucial because they allow embedding technical components, such as motors. Unfortunately, mounts and joints tend to fail when trying to fabricate a model on a different laser cutter or from a different material. The reason for this lies in the way mounts and joints hold objects in place, which is by forcing them into slightly smaller openings. Such “press fit” mechanisms unfortunately are susceptible to the small changes in diameter that occur when switching to a machine that removes more or less material (“kerf”), as well as to changes in stiffness, as they occur when switching to a different material.

We present a software tool called springFit that resolves this problem by replacing the problematic press fit-based mounts and joints with what we call cantileverbased mounts and joints. A cantilever spring is simply a long thin piece of material that pushes against the object to be held. Unlike press fits, cantilever springs are robust against variations in kerf and material; they can even handle very high variations, simply by using longer springs. SpringFit converts models in the form of 2D cutting plans by replacing all contained mounts, notch joints, finger joints, and t-joints.

For more details visit [here](https://hpi.de/baudisch/projects/springfit.html).

---

### Publication

- Thijs Roumen, <u>__Jotaro Shigeyama__</u>, Julius Romeo Cosmo Rudolph, Felix Grzelka, and Patrick Baudisch: SpringFit: Joints and Mounts that Fabricate on Any Laser Cutter, In Proceedings of UIST'19, October, 2019, New Orleans, LA, US.