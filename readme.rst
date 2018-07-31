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
        Larger values will derainbow more.
        
        Default: 10.

    *mask*
        If True, the function will return a mask showing the areas
        that won't be filtered. Use it to tune *maskthresh*.

        Default: False.

    *interlaced*
        Set to True if *clip* is interlaced.
    
        Default: False.

    *radius*
        Temporal radius. Must be 1 or 2.

        Default: 1.


::

    DFMDerainbowMC(clip[, maskthresh=12, radius=1, motion_vectors=None])


Parameters:
    *maskthresh*
        Passed to DFMDerainbow.

        Default: 12.

    *radius*
        Temporal radius for the motion compensation and for
        DFMDerainbow. Must be 1 or 2.

        Default: 1.

    *motion_vectors*
        A list of clips obtained by calling mv.Analyse or
        mv.Recalculate.

        With this parameter one can reuse the motion vectors from
        other motion-compensated filtering.

        The clips must be in this order:
            0. clip created with isb=False, delta=2. This clip should be omitted if *radius* is 1.
            1. clip created with isb=False, delta=1.
            2. clip created with isb=True, delta=1.
            3. clip created with isb=True, delta=2. This clip should be omitted if *radius* is 1.
        
        If this parameter is not used, the motion vectors will be
        created internally.

        Example of derainbowing and degraining using the same motion
        vectors for both::

            clip = your video here

            clip_super = core.mv.Super(clip=clip)

            forward2 = core.mv.Analyse(super=clip_super, isb=False, delta=2, chroma=False)
            forward1 = core.mv.Analyse(super=clip_super, isb=False, delta=1, chroma=False)
            backward1 = core.mv.Analyse(super=clip_super, isb=True, delta=1, chroma=False)
            backward2 = core.mv.Analyse(super=clip_super, isb=True, delta=2, chroma=False)

            clip = DFMDerainbowMC(clip=clip, motion_vectors=[forward2, forward1, backward1, backward2])

            clip = core.mv.Degrain2(clip=clip, super=clip_super, mvbw=backward1, mvfw=forward1, mvbw2=backward2, mvfw2=forward2)

        Default: None.


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
