+++
date = '2026-08-09T21:07:53+02:00'
draft = true
title = 'PM Fiber Alignment Hack'
summary = ''
+++

Last week I returned from holiday to a Johannes who wasn't very happy with one of our lasers. It was acting up and lasers are *my job*, so naturally I had to deal with it. This is the 493 nm laser, our cooling laser - and laser cooling is quite important for ions - which was misbehaving, badly. As Johannes described it, the 493 nm laser power reaching our ion trap was fluctuating immensely. 

Now, I haven't been in the lab for a few weeks, but before my leave this hasn't been an issue for a while. Perhaps the temperature in the lab was fluctuating more than usual, after all we had a few quite hot days here in Amsterdam. Anyhow, when setting up the laser in the first place, coupling and the alignment of the polarisation-maintaining fiber incoupling was a pain in the ass. To explain to you why that might lead to power fluctuations I made a little illustration:

- Perhaps here I can enter an illustration of the setup - simple drawing with gwoptics 

As you can see, in my setup there are a lot of fibers involved. The reason why we chose to design our system like this is that it is _very_ convenient. At least, once it is set up and working, any misalignment will only cause trouble in one part of the setup. So, if for any reason the coupling from the laser head to the first fiber gets messed up, I don't have to realign all 30 or so mirrors downstream. Also, we can store our optics in drawers inside a 19" rack. 

- Image of drawer

Pretty neat, right?

Anyways, atomic transitions are sensitive to polarisation, so we have to make sure to always deliver the same polarisation. And normal fibers are not good at that, because "Optical fibers always exhibit some degree of birefringence, even if they have a circularly symmetric design because in practice there is always some amount of mechanical stress or other effect which breaks the symmetry. As a consequence, the polarization of light propagating in the fiber gradually changes in an uncontrolled (and wavelength-dependent) way, which also depends on any bending of the fiber and on its temperature." (RP photonics encyclopedia [^1])

<img src="/img/blog/pm-fiber-hack/photo_peltier_heater.jpg" alt="The peltier heater. Sorry for the photographer's thumb. It's cramped in there." width="50%"/>

[^1] The RP photonics encyclopedia is a fantastic resource, here's the article about Polarization-maintaining fibers: <a href="https://www.rp-photonics.com/polarization_maintaining_fibers.html">https://www.rp-photonics.com/polarization_maintaining_fibers.html</a>, accessed 09-08-2026. 
