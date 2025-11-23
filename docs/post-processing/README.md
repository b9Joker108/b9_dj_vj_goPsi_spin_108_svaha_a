# Post-Processing - Advanced Techniques and Tools

## Overview

This section covers sophisticated post-processing techniques, tools, and methodologies for video stylistics, effects, compositing, masking, and mystical magico-intentional transformations on GNU/Linux.

## 🎨 Color Grading and Color Science

### 1. **Color Grading Tools**

#### **DaVinci Resolve Color Page**
- **Primary Corrections**: Lift, Gamma, Gain wheels
- **Secondary Corrections**: Qualifiers and power windows
- **Curves**: RGB, Hue vs Sat, Hue vs Hue, Luma vs Sat
- **Color Match**: AI-powered color matching
- **HDR Tools**: HDR grading and tone mapping
- **LUT Support**: 1D and 3D LUTs
- **Scopes**: Waveform, Vectorscope, Histogram, Parade

#### **Kdenlive Color Tools**
- **RGB Parade**: Analyze color balance
- **Waveform Monitor**: Luminance analysis
- **Vectorscope**: Saturation and hue analysis
- **Color Correction Effects**:
  - Lift/Gamma/Gain
  - Color Balance
  - Curves
  - Levels
  - HSV Adjust
  - SOP/Sat (Slope, Offset, Power)

#### **Blender Compositor**
- **Color Management**: OCIO-based color pipeline
- **Color Nodes**: RGB Curves, Color Balance, Hue/Saturation
- **Film Look**: Color Grading via compositor nodes
- **LUT Application**: Custom LUTs via ColorManagement

### 2. **Color Theory for Video**

#### **Color Palettes**
- **Complementary**: Orange/Teal (popular in modern cinema)
- **Analogous**: Harmonious color schemes
- **Triadic**: Balanced three-color schemes
- **Monochromatic**: Single hue variations

#### **Emotional Color Mapping**
- **Warm tones**: Energy, passion, warmth
- **Cool tones**: Calm, sad, professional
- **High contrast**: Drama, tension
- **Low contrast**: Dream-like, ethereal

#### **LUT Resources**
- **Free LUTs**: 
  - RocketStock Free LUTs
  - Bounce Color Free LUTs
  - Film Emulation LUTs
- **Creation**: Create custom LUTs in DaVinci Resolve

## 🌟 Visual Effects and Compositing

### 3. **Natron - Node-Based Compositing**

#### **Core Techniques**
- **Keying**: Remove green/blue screen
  - Keyer node
  - IBK (Image Based Keyer)
  - DespillMatte
- **Rotoscoping**: Frame-by-frame masking
  - Roto node
  - Bezier curves
  - Feathering
- **Tracking**: Motion tracking
  - Tracker node
  - Planar tracking
  - Match moving
- **Compositing**: Layering and blending
  - Merge nodes
  - Blend modes
  - Layer management

#### **Advanced Techniques**
- **CG Integration**: Blending 3D renders
- **Atmospheric Effects**: Fog, haze, god rays
- **Lens Effects**: Lens flares, optical effects
- **Color Correction**: Per-element grading

### 4. **Blender - VFX Pipeline**

#### **Motion Tracking**
- **Camera Tracking**: Reconstruct 3D camera
- **Object Tracking**: Track objects in scene
- **Solve**: Calculate camera movement
- **Ground Plane**: Set up 3D space
- **Integration**: Composite 3D elements

#### **Compositor Nodes**
- **Transform**: Scale, rotate, translate
- **Blur**: Gaussian, bokeh, directional
- **Color**: RGB curves, hue/sat, color correction
- **Filter**: Sharpen, soften, despeckle
- **Keying**: Chroma keying
- **Tracking**: Stabilization, match move

#### **Grease Pencil**
- **2D Animation in 3D Space**
- **Hand-drawn elements**: Integrate with 3D
- **Rotoscoping**: Draw over footage
- **Effects**: Modifiers and materials

### 5. **G'MIC (GREYC's Magic for Image Computing)**

#### **Description**
- Full-featured framework for image processing
- 500+ filters and effects
- Command-line and GUI versions
- Integration with GIMP and Krita

#### **Key Features**
- **Artistic Effects**: Oil paint, watercolor, sketch
- **Deformations**: Distortions, morphing
- **Degradations**: Artistic noise, grain
- **Color Manipulation**: Advanced color transforms
- **Sequences**: Batch process image sequences

#### **Installation**
```bash
# Debian/Ubuntu
sudo apt install gmic gmic-qt

# Command line usage
gmic input.jpg -fx_bokeh 3,8,0,8,4,0.4,1,0,0,0 -output output.jpg
```

#### **Video Processing**
```bash
# Extract frames
ffmpeg -i input.mp4 frames/frame_%04d.png

# Process with G'MIC
gmic frames/*.png -fx_stylize 0.5,10,0.1 -output processed/frame_%04d.png

# Reassemble
ffmpeg -i processed/frame_%04d.png -c:v libx264 output.mp4
```

## 🎭 Masking and Rotoscoping

### 6. **Masking Techniques**

#### **Natron Roto Tools**
- **Bezier Masks**: Vector-based precision
- **Feathering**: Soft edges
- **Motion Blur**: Realistic mask motion
- **Keyframe Animation**: Animated masks
- **Clone Stamp**: Remove unwanted elements

#### **Blender VSE Masks**
- **Strip Modifiers**: Mask strips
- **Adjustment Layers**: Apply effects selectively
- **Alpha Over**: Compositing with transparency

#### **Advanced Masking**
- **Gradient Masks**: Smooth transitions
- **Luminance Masks**: Based on brightness
- **Difference Matting**: Isolate changes
- **Core Matte**: Professional keying technique

## ✨ Stylistic Effects

### 7. **Film Emulation**

#### **Grain and Texture**
- **Film Grain**: Authentic analog look
- **Digital Grain**: Synthetic texture
- **Tools**: 
  - Kdenlive: Add Grain effect
  - Blender: Compositor grain node
  - FFmpeg: grain filter

#### **Gate Weave and Flicker**
- **Simulating film artifacts**
- **Random variation in position**
- **Luminance flicker**

#### **Color Shifts**
- **Bleach Bypass**: High contrast, desaturated
- **Cross Processing**: Unusual color palettes
- **Vintage Look**: Faded colors, vignetting

### 8. **Glitch Art**

#### **Digital Artifacts**
- **Datamoshing**: Compression artifacts
- **Pixel Sorting**: Algorithmic sorting
- **Bit Crushing**: Reduced bit depth
- **Scan Line Effects**: Analog distortion

#### **Tools and Techniques**
```bash
# FFmpeg glitch effects
ffmpeg -i input.mp4 -vf "noise=alls=20:allf=t+u" glitch.mp4
ffmpeg -i input.mp4 -vf "hue=s=0:h=90" colorshift.mp4
```

#### **Glitch Tools**
- **FFglitch**: Advanced FFmpeg glitching
- **Datamosh**: Python scripts for datamoshing
- **Processing**: Custom glitch sketches
- **Pure Data**: Real-time glitch generation

### 9. **Artistic Stylization**

#### **Painterly Effects**
- **Oil Paint**: Thick brush strokes
- **Watercolor**: Fluid, transparent
- **Sketch/Pencil**: Line art conversion
- **Cartoon**: Cel-shaded look

#### **G'MIC Filters**
```bash
# Artistic styles
gmic input.mp4 -fx_stylize 0.5,10,0.1
gmic input.mp4 -fx_brushify 0.5,8,0.1
gmic input.mp4 -fx_bokeh 3,8,0,8,4,0.4
```

#### **Blender Freestyle**
- **Edge Detection**: Line art rendering
- **Stylized Edges**: Controllable line rendering
- **Integration**: Combine with other elements

## 🌈 Advanced Color Techniques

### 10. **Split Toning**
- **Highlights Color**: Warm or cool tones in highlights
- **Shadows Color**: Contrasting shadow colors
- **Balance**: Control the blend point
- **Usage**: Create mood and atmosphere

### 11. **Color Isolation**
- **Selective Color**: Keep one color, desaturate rest
- **Techniques**:
  - HSV Adjust with masks
  - Chroma keying inverted
  - Natron color selection nodes

### 12. **Look Development**
- **Consistent Style**: Develop signature look
- **LUT Creation**: Save and reuse grades
- **Reference Images**: Match specific aesthetics
- **Shot Matching**: Consistent look across project

## 🎬 Temporal Effects

### 13. **Time Manipulation**

#### **Speed Ramping**
- **Slow Motion**: Emphasize moments
- **Fast Forward**: Compress time
- **Freeze Frame**: Hold on important frames
- **Reverse**: Time reversal effects

#### **Tools**
- **Kdenlive**: Speed effect with curves
- **Blender VSE**: Time modifier
- **FFmpeg**: setpts filter for speed

### 14. **Optical Flow**
- **Frame Interpolation**: Create smoother slow motion
- **Tools**:
  - **SVP (SmoothVideo Project)**: Real-time interpolation
  - **Butterflow**: Frame interpolation utility
  - **FFmpeg**: minterpolate filter

### 15. **Trails and Echoes**
- **Echo Effect**: Ghosting from previous frames
- **Motion Trails**: Emphasize movement
- **Blender**: Accumulation pass
- **Natron**: Frame blending nodes

## 🔮 Mystical and Psychedelic Effects

### 16. **Kaleidoscope and Mirrors**
```bash
# FFmpeg kaleidoscope
ffmpeg -i input.mp4 -vf "zoompan=z='min(zoom+0.0015,1.5)':d=1,crop=iw/4:ih/4:(iw-ow)/2:(ih-oh)/2,tile=2x2" kaleidoscope.mp4
```

### 17. **Fractals and Patterns**
- **Processing**: Generate fractal animations
- **Blender**: Procedural textures and animations
- **Pure Data + GEM**: Real-time fractal generation

### 18. **Warping and Distortion**
- **Lens Distortion**: Fisheye, barrel, pincushion
- **Displacement Maps**: Texture-based warping
- **Swirl and Pinch**: Circular distortions
- **Wave Effects**: Ripple and wave patterns

#### **FFmpeg Examples**
```bash
# Wave effect
ffmpeg -i input.mp4 -vf "wave=x=16:y=16" wave.mp4

# Perspective transform
ffmpeg -i input.mp4 -vf "perspective=..." perspective.mp4
```

### 19. **Chromatic Aberration**
- **Simulate lens aberrations**
- **RGB channel separation**
- **Color fringing effects**
```bash
# Chromatic aberration
ffmpeg -i input.mp4 -vf "chromashift=rbshift=10:gbshift=-10" aberration.mp4
```

### 20. **Slit-Scan Effects**
- **Time-based displacement**
- **2001: A Space Odyssey style**
- **Tools**: Processing, Pure Data, custom scripts

## 🎨 Input Masks and Alpha Channels

### 21. **Alpha Channel Techniques**

#### **Creating Alpha Channels**
- **Rotoscoping**: Hand-drawn masks
- **Chroma Keying**: Green/blue screen
- **Luminance Keying**: Based on brightness
- **Difference Keying**: Motion-based extraction

#### **Alpha Operations**
- **Premultiply**: Prepare for compositing
- **Unpremultiply**: Remove premultiplication
- **Alpha Over**: Standard compositing
- **Alpha Add**: Additive blending

### 22. **Matte Techniques**

#### **Core Matte**
- **Hold-out Mattes**: Define clear separation
- **Garbage Mattes**: Rough isolation
- **Edge Mattes**: Refine edges

#### **Advanced Matting**
- **IBK (Image Based Keyer)**: Professional keying
- **Light Wrap**: Edge integration
- **Spill Suppression**: Remove color spill
- **Edge Blur**: Smooth transitions

## 🌟 Advanced FFmpeg Filters

### 23. **Complex Filter Graphs**

#### **Filter Chaining**
```bash
# Multiple effects
ffmpeg -i input.mp4 -vf "eq=contrast=1.5:saturation=1.2,unsharp=5:5:1.0:5:5:0.0" output.mp4
```

#### **Split and Merge**
```bash
# Apply different effects to different parts
ffmpeg -i input.mp4 -filter_complex \
"[0:v]split=2[v1][v2]; \
[v1]crop=iw:ih/2:0:0[top]; \
[v2]crop=iw:ih/2:0:ih/2,hue=h=180[bottom]; \
[top][bottom]vstack" output.mp4
```

### 24. **Creative Filters**

#### **Video Effects**
```bash
# Vibrance
ffmpeg -i input.mp4 -vf "vibrance=intensity=1.0" output.mp4

# Edge detection
ffmpeg -i input.mp4 -vf "edgedetect=mode=colormix" output.mp4

# Posterize
ffmpeg -i input.mp4 -vf "posterize=levels=4" output.mp4

# Noise
ffmpeg -i input.mp4 -vf "noise=alls=20:allf=t+u" output.mp4

# Dilation/Erosion (morphology)
ffmpeg -i input.mp4 -vf "dilation=threshold0=65535" output.mp4
```

## 📦 Batch Processing Workflows

### 25. **Automated Processing**

#### **Shell Scripts**
```bash
#!/bin/bash
# Process all videos in directory
for file in *.mp4; do
    ffmpeg -i "$file" -vf "eq=contrast=1.3:saturation=1.1" "processed_$file"
done
```

#### **Python Automation**
```python
import subprocess
import glob

filters = "eq=contrast=1.5,unsharp=5:5:1.0"
for video in glob.glob("*.mp4"):
    output = f"processed_{video}"
    subprocess.run([
        "ffmpeg", "-i", video,
        "-vf", filters,
        output
    ])
```

## 🎯 Workflow Recommendations

### Workflow 1: Cinematic Look
1. **Color Grade**: DaVinci Resolve
2. **Add Grain**: Film grain effect
3. **Lens Effects**: Vignette, light leaks
4. **Final Touch**: Subtle color tint

### Workflow 2: Psychedelic/Mystical
1. **Effects**: Kaleidoscope, mirrors
2. **Color**: Vibrant, saturated, shifting
3. **Distortion**: Warps, displacement
4. **Compositing**: Layer multiple effects

### Workflow 3: Glitch Art
1. **Datamosh**: Compression artifacts
2. **Pixel Sort**: Algorithmic effects
3. **Color Shift**: RGB displacement
4. **Noise**: Digital artifacts

### Workflow 4: Documentary/Natural
1. **Color Correction**: Natural tones
2. **Stabilization**: Remove shake
3. **Noise Reduction**: Clean footage
4. **Sharpening**: Enhance detail

## 🔧 Performance Tips

### 26. **Optimization Strategies**

#### **Proxy Workflows**
- Generate lower resolution proxies
- Edit with proxies for speed
- Render with original high-res files

#### **RAM Disk for Temp Files**
```bash
# Create RAM disk for temporary rendering
sudo mkdir -p /mnt/ramdisk
sudo mount -t tmpfs -o size=4G tmpfs /mnt/ramdisk
```

#### **GPU Acceleration**
- Enable GPU rendering in NLEs
- Use CUDA/OpenCL when available
- Hardware encoding for faster renders

## 📚 Learning Resources

- **Color Grading**: "Color Correction Handbook" concepts
- **Compositing**: Natron tutorials on YouTube
- **Effects**: Blender Guru effect tutorials
- **FFmpeg**: Official documentation and filter guide

## 🔗 Related Sections

- [Video Editing](../video-editing/) - Primary editing tools
- [VJ Applications](../vj-applications/) - Real-time effects
- [Practical Workflows](../practical-workflows/) - Complete examples
- [Mystical Process Art](../mystical-process-art/) - Intentional methodologies

---

*For specific tool installations, see [Installation Guides](../installation-guides/)*
