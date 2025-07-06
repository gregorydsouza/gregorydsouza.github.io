---
name: Revolutionizing Adaptive Kayaking
tools: [Biomechanics, Control Systems, 3D Printing]
image: /images/KayakProject/PXL_20250322_143215020.jpg
description: An adaptive kayaking device with PID-controlled active assistance, designed to support rehabilitation for paraplegics and quadriplegics through a user-tested, accessible design.
---

# Revolutionizing Accessibility: An Adaptive Kayaking Mechanism For All

![](/images/KayakProject/PresentationBanner.jpg)

#### **Gregory Dsouza, Brooke Mueller, Levi Blumer, Lucia Westgate**

**Mechanical Engineering Department, Embry-Riddle Aeronautical University, Daytona Beach, FL 32114**

As the team lead for this capstone project, I guided a multidisciplinary engineering team in developing an adaptive kayaking system for individuals with mobility impairments, particularly paraplegics and quadriplegics. Our project, in partnership with the Oceans of Hope Foundation, aimed to address the significant barriers to watersport participation faced by people with disabilities.

Our system builds on foundational work from previous teams, who developed a 4-bar linkage mechanism designed to replicate the natural motion of an able-bodied paddle stroke. While that mechanical system was well-studied, our work focused on critical new areas:

-   Designing a non-invasive, modular mounting system
-   Implementing an encoder-based assistive control system
-   Developing a business and deployment plan for wider adoption

## 4-bar Linkage System

The 4-bar linkage was originally developed using VICON motion tracking to analyze the biomechanical path of a paddle stroke. This mechanical solution translates rotational input into a natural stroke arc that mimics the ergonomic motion used by able-bodied kayakers.

We refined this system and validated its performance through motion tracking data and stroke angle analysis.

{% include elements/figure.html image="/images/KayakProject/StrokeProfileWithLinkage.png" caption="Figure 1. Paddle Motion Comparison" %}

<center>
    <video align="center" width="640" height="480" style="pointer-events: none;" autoplay loop muted>
        <source src="/videos/KayakProject/ManimLinkageAnimated.mp4" type="video/mp4">
    </video>
</center>

The linkage system served as the base for our control logic: by tracking the crank angle ($\theta$), we used encoder feedback to determine stroke position and apply assistive torque via motor control.

## Mounting System Overview

To make the 4-bar system viable for real-world use, we engineered a snap-on mounting bracket made from 3D-printed TPU, which securely attaches to the kayak’s rim without permanent modification. This not only improves comfort but also ensures compatibility with borrowed or rental kayaks.

Key features:

-   Snap-fit TPU clamps for easy mounting
-   Spring-loaded ratchet & pawl adjustment for modular positioning
-   Accelerometer-based emergency release system for user safety
-   Waterproof housing for all electronics, printed using PETG

{% include elements/figure.html image="/images/KayakProject/NonInvasive1.jpg" caption="Figure 2. Non-Invasive Design" %}

{% include elements/figure.html image="/images/KayakProject/MountingMechanismFullAssembly.png" caption="Figure 3. Full Mounting System Assembly" %}

## Active Assistance

To enhance paddling performance and reduce fatigue, we implemented a PID-controlled motor system. The system uses encoder data to apply targeted assistance throughout the paddle stroke cycle. Our control loop is optimized for smoothness and realism, simulating the resistance and motion of traditional paddling.

## Design Challenges and Growth

Our team encountered and overcame several challenges, including:

-   Learning new tools like SolidWorks, Cura, and PrusaSlicer from scratch
-   Navigating hurricane-related delays and lab access limitations
-   Staying under budget while maintaining prototype quality (total cost: ~$450)
-   Each obstacle pushed us to grow in technical skill, team communication, and creative problem-solving.

Data collected from various users provided validation for the shaft length, providing optimal comfort and stability. This information is presented below:

## Conclusion

Our adaptive kayak system improves upon previous designs by offering a safer, more comfortable, and more practical solution. The mounting system is lightweight, modular, and secure. The control system makes kayaking more accessible to individuals with upper-body mobility impairments. Together, these features bring us closer to enabling truly independent, inclusive watersports experiences.

## Acknowledgements

Special thanks to the Oceans of Hope Foundation, Dr. Victor Huayamave, Dr. Christine Walck, Dr. Marc Compere, Sheridan Perry, and Mario Gomez for advising, supporting, and helping with this project.
