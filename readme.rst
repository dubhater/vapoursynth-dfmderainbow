Description
===========

DFMDerainbow is a derainbow function for VapourSynth. DFMDerainbowMC
performs motion compensation before calling DFMDerainbow.

DFMDerainbowMC only works with progressive video.

This is a port of the Avisynth function of the same name from 20140223.


Usage
=====
::

    DFMDerainbow(clip[, maskthresh=10, mask=False, interlaced=False, radius=1])


Parameters:
    *clip*
        A clip to process.

    *maskthresh*
        
        Default: 10.

    *mask*

        Default: False.

    *interlaced*
    
        Default: False.

    *radius*
        Temporal radius. Must be 1 or 2.

        Default: 1.


::

    DFMDerainbowMC(clip[, maskthresh=12, radius=1])


Parameters:
    *maskthresh*
        Passed to DFMDerainbow.

        Default: 12.

    *radius*
        Temporal radius for the motion compensation and for
        DFMDerainbow.

        Default: 1.


Requirements
============

DFMDerainbow function requirements:
   * `TemporalMedian                        <https://github.com/dubhater/vapoursynth-temporalmedian/releases>`_
   * `TemporalSoften2 v1 or newer           <https://github.com/dubhater/vapoursynth-temporalsoften2/releases>`_
   * `FluxSmooth                            <https://github.com/dubhater/vapoursynth-fluxsmooth/releases>`_
   * `MSmoosh                               <https://github.com/dubhater/vapoursynth-msmoosh/releases>`_
   * `MiniDeen                              <https://github.com/dubhater/vapoursynth-minideen/releases>`_

DFMDerainbowMC function requirements:
   * DFMDerainbow function
   * `MVTools                    <https://github.com/dubhater/vapoursynth-mvtools/releases>`_
   * `FFT3DFilter                <https://github.com/myrsloik/VapourSynth-FFT3DFilter/releases>`_


License
=======

???
