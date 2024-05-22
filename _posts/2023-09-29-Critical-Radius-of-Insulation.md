---
layout: post
title: Critical Radius of Insulation
tags: [Heat Transfer]
---

Consider a pipe with a fluid that you are trying to insulate, so that you can minimize the heat loss of the fluid flowing through the pipe.

Depending on your requirement for heat loss, you might simply increase the thickness of the insulation around the pipe. However, this does not always yield the results you might be looking for.

In fact, increasing the thickness of insulation around the pipe may actually work against your goal, cooling down the fluid more efficiently. This is because the rate of heat transfer $\dot{Q}$ of the pipe actually has two competing properties when changing the thickness of the insulation. Assume we are increasing the thickness of insulation, then:

-   The thicker insulation creates a larger thermal resistance, $\dot{Q}\downarrow$
-   The thicker insulation creates a larger surface area for convection to occur $\dot{Q}\uparrow$

It is important that we know how to setup our insulation such that we can maximize the property we desire.

# Definition of the Critical Radius

These two competing properties do not vary linearly, and there exists a point where they balance each other out, which we call the critical radius.

Let us consider the fluid flow example from earlier with its insulation at the critical radius, illustrated as follows:

![](/images/CriticalRadius/PipeDiagram1.svg)

<!--
Code used to generate diagram in Asymptote http://asymptote.ualberta.ca

unitsize(1.5cm);

pen p = rgb(255,255,255);

filldraw(circle((0,0), 3), mediumgray);
filldraw(circle((0,0), 2), white);

draw((0,0) -- (1.5,2.598076211), arrow=Arrow(TeXHead));
label("$r_{cr}$", (1.625,2.814582562), p);
draw((0,0) -- (2,0), arrow=Arrow(TeXHead));
label("$r_1$", (1, 0.2));

label("$T_{\infty}$", (3.5, 0), p);
label("$h$", (3.5, -0.3), p);
-->

We can use this to construct a thermal circuit:

![](/images/CriticalRadius/ThermalCircuit.svg)

<!--
Code used to generate diagram in Asymptote http://asymptote.ualberta.ca
unitsize(1.5cm);

draw((0,0) -- (1,0));
draw(box((1,-0.25),(2,0.25)));
draw((2,0) -- (3,0));
draw(box((3,-0.25),(4,0.25)));
draw((4,0) -- (5,0));

fill(circle((0,0), 0.05));
label("$T_1$", (0,0.25));

fill(circle((2.5,0), 0.05));
label("$T_2$", (2.5,0.25));

fill(circle((5,0), 0.05));
label("$T_{\infty}$", (5,0.25));

label("$R_{insul}$", (1.5,-0.5));
label("$R_{conv}$", (3.5,-0.5));
-->

In case you haven't dealt with thermal circuits before, we can calculate the heat transfer rate across a section of the circuit as:

$$
\dot{Q} = \frac{T_1 - T_2}{R_{eq}}
$$

Which if we apply to the whole circuit becomes:

$$
\dot{Q} = \frac{T_1 - T_{\infty}}{R_{total}}
$$

$$
R_{total} = \frac{\ln{\left( \frac{r_{cr}}{r_1} \right)}}{2\pi kL} + \frac{1}{hAL} = \frac{\ln{\left( \frac{r_{cr}}{r_1} \right)}}{2\pi kL} + \frac{1}{h2\pi r_{cr} L}
$$

In order to find the critical radius, we need to find the maximum point of $\dot{Q}$. Consider that $r_1$ is known because that is simply the radius of the pipe that we are insulating, so we just have to evaluate:

$$
\frac{d R_{total}}{d r_{cr}} = 0
$$

$$
\frac{d R_{total}}{d r_{cr}} = \frac{1}{2\pi kL} \frac{r_1}{r_{cr}} \frac{1}{r_1} - \frac{1}{2\pi Lh} \left( \frac{1}{r_{cr}} \right)^2 = 0
$$

Solving this equation for $r_{cr}$ yields:

$$
r_{cr} = \frac{k}{h}
$$

Nice! It evaluates into a small and easy to compute equation! However, we need to understand what specific conditions occur at this value and how we can make use of them.

When the outer edge of the insulation around the pipe is at the critical radius:

-   $\dot{Q}$ is maximum
-   Thermal resistance $R$ is minimum

## Applying the critical radius concept

The example used in this article discusses how you would like to minimize the rate of heat loss of the fluid in the pipe, in which case you want to have a radius of insulation larger than the critical radius.

However, note that having a radius of insulation less than or equal to the critical radius is also desirable in other scenarios, such as a wire. Electrical wires carrying large currents get hot, and so it helps to setup wire insulation such that you can maximize the heat loss of the wire.

It is helpful to graph out these functions to understand how they vary:

<iframe src="https://www.desmos.com/calculator/xht72m2lla?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

The red line represents the change in thermal resistance as the radius of insulation increases, while the purple line represents the change in heat transfer as the radius of insulation increases.

We notice that at the critical radius, the heat loss for the system is at its maximum, and the thermal resistance is at its minimum.

Therefore, the most efficient cooling of the system is achieved at the critical radius.
