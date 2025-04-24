# MS20_Multimode_Resonant_Filter_Eurorack
Multimode resonant filter module based on MS20 MKII for Eurorack Synthesizers.

# Intro
Filters are one of the most interesting components of a synthesizer. They assolve a fundamental role in defining the "character" of a musical device and very likely are the most important weapon a sound engineer has in its hands to shape the "perfect" sound.

One of my favourite filter is the one Korg developed for its MS20 synthesizer. In particular, I must admit that I have a soft spot for the so called "Mark II" filter because less aggressive then more suited to my musical tastes than the Korg35 custom chip (shame on meeee).

Here is my new attempt at recreating that iconic filter :)

# Circuit design
There are various projects developed around the MKII filter out there. Just to cite a few, take a look at [René Schmitz](https://www.schmitzbits.de/ms20.html) or [Kassutronics](https://kassu2000.blogspot.com/2019/07/ks-20-filter.html) work. Kassutronics one is particularly interesting because of the implementation of a blending function between the two filter modes.

Original MKII filter's active components are LM13600 Dual Operational Transconductance Amplifiers (OTA), some generic amplifiers in buffer configuration at the LM13600 outputs and a JRC4558 dual op-amp in the feedback circuit. A dual PNP transistor in single package (A798F) is at the core of the circuit takeing care of CV tracking.

These components are mostly obsolete, but there are very good replacements available.

The LM13700 OTA is a direct replacement for 13600. No need to look further :)

High performane amps for audio applications are nowadays common (e.g. the NE5532), but you can bet even "cheaper" op-amps (like the TL072) are likely better suited for the task than those available in the '80's (yes, you want to use legit integrated circuits for such a delicate task and, yeees, these are great years for being a tinkerer!!).

The A798F dual transistor in the exponential converter circuit is commonly replaced by two BC557. Matching these is a good practice for better tracking, but not mandatory (it's not a VCO, in the end).

This project's circuit design doesn't add too much to those cited.

I used TL072 for audio and feedback paths. I made some testing by using TL072 in place of NE5532 (being regarded as more preferrable op-amp for audio) and, honestly, could not hear any difference.

The input level to the first OTAs channel is commonly kept relatively high (remember the "keep signal low or distortion will trigger" thing?) being in the 400 mA ballpark with an input level of 10Vpp. This is generally adopted online, and I could argue it's because some distorsion at this stage of the filter contributes to it's character.

My 2 cents here is the introduction of a trimmer to attenuate the signal hitting the first OTA. The trimmer is accessible from the front panel and is dimensioned so that you can load the OTAs input well above it's confort zone when fully counter clockwise and gradually attenuate it turning clockwise.

In the SMD version of the main board, I have used a dual PNP transistor in a SMD package (BC857BS) for the CV circuit. Being in the same device makes the two transistors work the same at any temperature and operating condition. This makes them "almost matched" and should allow for better voltage tracking.

Perfect tracking is not that important in a filter with respect to a voltage controlled oscillator, where a reliable pitch tracking is mandatory, but, hey: we are tring to do our best here :)

# Module Design
The module is designed for compatibility with standard Eurorack synthesizer formats, ensuring ease of assembly and integration.

I spent due efforts to keep the module width as small as possible, ending at 6 HP.

The module features two CV inputs, one direct and the other with control over CV level. CV level is a simple potentiometer in voltage divider configuration, so nothing fancy.

This design operates either as low-pass or high-pass filter. Changing operation mode is as simple as flipping a switch from one position to another.

This configuration flexibility allows for diverse sound-shaping possibilities within a modular synthesizer setup. You can use a single filter and have a two poles filtering, or increase the number of filters in series thus increasing the number of poles. If you want to reproduce the MS20 filter configuration, place two of these in series, the first one in HP configuration, the second one in LP config and there you are :) .

The module is made of three boards intended to be stacked one over the other. The first one is the front panel. This has no traces and is intended for mechanical installation on your eurorack case. It is preferred to be realized in alluminum alloy.

The other two PCBs are the front board and the main board. Front board hosts jacks, mode switch and control potentiometers. The main board hosts most of the filter circuitry.

The module is intended to work on +/-12V, but should work on +/-15V without problems.

As already said, I have layed down not one but two versions of the main board for this filter. The first one is made of THT components only. It's easyer to build, but you could have some trouble finding legit components for it. In the moment I am writing, four-out-of-four main sellers don't have the LM13700 in DIP16 package in stock (as far as I know Texas Instruments has discontinued the production of the DIP version some year ago, while the SOIC is still in production).

This is why I also layed down a version with some SMDs. This version could be more complex to assemble by yourself, but at least you can find legit SOIC16 LM13700!

# Acknowledgments
Many thanks to [JLCPCB](https://jlcpcb.com/?from=IAT) for sponsoring the manufacturing of PCBs and the assembly of main board's SMDs for this module.

Without their contribution this project would have never reached it's actual level of developent.

JLCPCB is a high-tech manufacturer specialized in the production of high-reliable and cost-effective PCBs. They offer a flexible PCB assembly service with a huge library of more than 600.000 components in stock.

3D printing is part of their portfolio of services so one could create a full finished product, all in one place!

By registering at JLCPCB site via [THIS LINK](https://jlcpcb.com/?from=IAT) (affiliated link) you will receive a series of coupons for your orders. Registering costs nothing, so it could be the right opportunity to give their service a due try ;)

