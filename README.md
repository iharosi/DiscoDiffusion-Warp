# Disco Diffusion v5.2 - WarpFusion

[![Disco Diffusion v5.2 - Warp](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/iharosi/DiscoDiffusion-Warp/blob/main/Disco_Diffusion_v5_2_Warp.ipynb)

# About
This version improves video init. You can now generate optical flow maps from input videos, and use those to:
- warp init frames for consistent style 
- warp processed frames for less noise in final video

## Init warping
The feature works like this: we take the 1st frame, diffuse it as usual as an image input with fixed skip steps. Then we warp in with its flow map into the 2nd frame and blend it with the original raw video 2nd frame. This way we get the style from heavily stylized 1st frame (warped accordingly) and content from 2nd frame (to reduce warping artifacts and prevent overexposure)

#

## Optical flow input warping

### Settings: 
(Located in animation settings tab)

Video Optical Flow Settings:
- flow_warp - check to warp
- flow_blend: 0 - you get raw input, 1 - you get warped diffused previous frame 
- check_consistency: check forward-backward flow consistency (uncheck unless getting too many warping artifacts)

## Output warping
This feature is plain simple - we just take any frame, warp in to the next frame, blend with real next frame, get smooth noise-free result.

### Settings: 
(located in create video tab)
blend_mode: 
- none: just mash frames together in a video
- optical flow: take frame, warp, blend with the next frame
- check_consistency: use consistency maps (may prevent warping artfacts)
- blend: 0 - you get raw 2nd frame, 1 - you get warped 1st frame

#

This is a variation of the awesome [DiscoDiffusion colab](https://colab.research.google.com/github/alembics/disco-diffusion/blob/main/Disco_Diffusion.ipynb#scrollTo=Changelog)
