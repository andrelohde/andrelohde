+++
date = '2026-08-09T21:07:53+02:00'
draft = false
title = 'About aligning polarization-maintaining fibers'
summary = 'Here, I share how I use peltier elements to correctly align the polarization of light for incoupling into a polarization-maintaining fiber, which I often experience as quite finicky.'
+++

I recently returned from holiday to a Johannes (my colleague) who wasn't very happy with one of our lasers. It was acting up and lasers are *my job*, so naturally I had to deal with it. This is the 493 nm laser, our cooling laser (quite important for our ions) which was misbehaving, badly. As Johannes described it, the 493 nm laser power reaching our ion trap was fluctuating immensely. 

Now, I haven't been in the lab for a few weeks, but before my leave this hasn't been an issue for a while. Perhaps the temperature in the lab was fluctuating more than usual, after all we had a few quite hot days here in Amsterdam. Anyhow, when setting up the laser in the first place, coupling and the alignment of the polarisation-maintaining fiber incoupling was a pain in the ass. Nonetheless, the alignment has to be good and the setup involves a lot of fibers - because we need a total of 5 different wavelengths to manipulate the ions alone, not including the photo-ionization laser. So when I started the project, one of my first things to do was finding a way of accommodating all the necessary optics. We went with fiber-coupled optical drawers in a rack.

The reason why we chose to design our system like this is that it is _very_ convenient. At least, once it is set up and working, any misalignment will only cause trouble in one part of the setup. So, if for any reason the coupling from the laser head to the first fiber gets messed up, I don't have to realign all 30 or so mirrors downstream. Here's a picture: 

<img src="/img/blog/pm-fiber-hack/rack_drawers.jpg" alt="Optical breadboard in a rack. The drawer can be closed with a lid." width="40%"/>

Pretty neat, right?

## About polarization-maintaining fibers

Anyways, atomic transitions are sensitive to polarisation, so we have to make sure to always deliver the same polarisation. And normal fibers are not good at that, because "Optical fibers always exhibit some degree of birefringence, even if they have a circularly symmetric design because in practice there is always some amount of mechanical stress or other effect which breaks the symmetry. As a consequence, the polarization of light propagating in the fiber gradually changes in an uncontrolled (and wavelength-dependent) way, which also depends on any bending of the fiber and on its temperature." (RP Photonics encyclopedia [<a href="#references">1</a>])

This is why there are special polarization-maintaining (PM) fibers. And they work great, the only problem with them is that the polarization of the incoupled light needs to be linearly polarized and _exactly_ aligned along the correct direction. Below is an illustration (credit once more to RP Photonics [<a href="#references">1</a>]) of two different types of PM fiber. What they have in common is that the circular symmetry is broken by so-called stress rods. 

<img src="/img/blog/pm-fiber-hack/pm_fibers.webp" alt="Two types of PM fiber: PANDA (left) and bow-tie (right)" width="30%"/>

The stress rods create two birefrengent axes, and you want the polarization of your light to be aligned with one of them. Since the refractive index is different for light polarized along either of these two axes, the polarization states corresponding to an electric field aligned with the axes have different group velocities, which is why sometimes you might see the terms "slow axis" and "fast axis" to refer to the two different axes of birefringence. In general, one of these axes seems to preserve polarization slightly better, but I don't know why or which one. 

Coupling light into a single-mode fiber can already be tricky by itself. But I tell you, getting the polarization right can be even more annoying. Especially, if there is no specialized equipment around. So here's how I do it, perhaps this might help someone in the future: 

## PM fiber alignment procedure

Prerequisite for the alignment of a PM fiber is a linear polarization state of the light to be incoupled. The reason is that polarization components along the slow and the fast axis experience different phase retardation as they propagate through the fiber. But not only that, the refractive indices will vary with stress on the fiber or with temperature changes, which will effectively scramble the polarization around. This is why we want to produce a linear polarization perfectly aligned with the correct fiber axis. Here's the optical setup that I typically use to ensure correct alignment:

<img src="/img/blog/pm-fiber-hack/setup.png" alt="Optical setup I use for polarization alignment of a PM fiber." width="40%"/>

I use a half wave plate (HWP) in front of the PM fiber to be able to rotate the polarization. That's not strictly necessary, there are also ways of rotating the fiber coupler, but then again any tilt might lead to misalignment of the fiber. On the other side of the fiber I use another half wave plate to rotate the polarization state, a polarizing beam splitter (PBS) and a power meter. 

Now, we can make use of the (in my experience biggest) issue with PM fibers: imperfect polarization will fluctuate with temperature. Just heat that thing up! Normally, I used to do this with a heat gun (seriously), but I decided that is not repeatable enough and I was always a little bit scared of melting the jacket (the outer plastic around the actual fiber). From others I heard they are just bending the fiber slightly, but I would be worried of breaking it and, again, this is also not perfectly repeatable every time. So I improvised a more heating mechanism using some spare peltier elements lying around:

<img src="/img/blog/pm-fiber-hack/photo_peltier_heater.jpg" alt="The peltier heater. Sorry for the photographer's thumb. It's cramped in there." width="50%"/>

With about 2 A of current through my improvised heater I had a quick way of heating the fiber. With this current I didn't risk destroying the elements. As you can see, I just taped the fiber on top of the heater and the entire construction onto the optical table, which acts as a good thermal reservoir. 

How does it work? Heating up the fiber will generally rotate the polarization, which means that the amount of power transmitted through the PBS behind fiber and HWP fluctuates. I want to minimize the amplitude of fluctuations. So here's a simple protocol I like to follow:

0. Measure the full power transmitted through the fiber without a PBS. Then place the PBS in front of the power meter.
1. Set the angle of the input HWP to $0°$.
2. Adjust the output HWP to minimize transmission through the PBS.
3. Turn on the heater.
4. Observe the transmitted power increase until it reaches a maximum and drops again. Note down the maximum value.
5. Repeat steps 1-4 for input HWP angles from $0°$ to $45°$ in $5°$ steps. You will find that a specific angle $\alpha$ gives a minimal amount of fluctuation.
6. Find the optimum angle close to $\alpha$ and try to see if $\alpha + 45°$ offers even better performance. For my purposes a few percent of amplitude fluctuation is typically good enough.

Et voilà, this is how you can very easily align a PM fiber to $1-2°$ precision without any bigger troubles.

### References

<div id="references">
<b>[1]</b> The RP photonics encyclopedia is a fantastic resource, here's the article about Polarization-maintaining fibers: <a href="https://www.rp-photonics.com/polarization_maintaining_fibers.html">https://www.rp-photonics.com/polarization_maintaining_fibers.html</a>

</div>
