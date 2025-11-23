# Practical Workflows - Real-World Production Pipelines

## Overview

This section provides practical, tested workflows for various video production scenarios using FOSS tools on GNU/Linux. Each workflow includes step-by-step instructions, tool recommendations, and tips for optimization.

## 🎬 Workflow 1: YouTube Content Creation

### Complete YouTube Video Production Pipeline

#### **Phase 1: Pre-Production**
1. **Planning**
   - Script/outline creation
   - Shot list preparation
   - Asset gathering
   
2. **Recording**
   - Screen recording: SimpleScreenRecorder or OBS Studio
   - Camera recording: Use camera or webcam
   - Audio: Audacity or Ardour
   
3. **Organization**
   ```bash
   project/
   ├── raw_footage/
   ├── audio/
   ├── assets/
   │   ├── images/
   │   ├── music/
   │   └── sound_effects/
   ├── exports/
   └── project_files/
   ```

#### **Phase 2: Editing** (Kdenlive)
1. **Import and Organize**
   - Create bins for different media types
   - Generate proxies for 4K footage
   - Label and tag clips

2. **Rough Cut**
   - Assemble main narrative
   - Remove dead space
   - Establish pacing

3. **Fine Cut**
   - Add B-roll footage
   - Insert graphics/text
   - Trim to perfection
   - Add transitions (sparingly)

4. **Audio Mixing**
   - Balance voice/music/SFX
   - Apply noise reduction if needed
   - Use compression for consistent levels
   - Add fade ins/outs

5. **Color Grading**
   - Apply basic color correction
   - Create consistent look
   - Use adjustment clips for global changes

#### **Phase 3: Effects and Polish**
1. **Graphics**
   - Title/intro sequence
   - Lower thirds
   - End screen
   - Subscribe animation

2. **Effects**
   - Zoom/pan on still images
   - Speed ramping on action
   - Picture-in-picture for reactions
   - Screen glitch transitions (if appropriate)

#### **Phase 4: Export and Upload**
1. **Export Settings** (Kdenlive)
   ```
   Format: MP4
   Video Codec: H.264
   Bitrate: 8-12 Mbps (1080p), 15-20 Mbps (4K)
   Audio Codec: AAC
   Audio Bitrate: 192-320 kbps
   Resolution: 1920x1080 or 3840x2160
   Frame Rate: Match source (23.976, 24, 25, or 30)
   ```

2. **Quality Check**
   - Watch full export
   - Check audio sync
   - Verify thumbnail clarity
   - Test on mobile device

3. **Upload Prep**
   - Create thumbnail (GIMP/Krita)
   - Write description
   - Add tags and timestamps
   - Schedule or publish

#### **Tools Used**
- **Editor**: Kdenlive
- **Screen Capture**: OBS Studio
- **Audio**: Audacity
- **Graphics**: GIMP, Inkscape
- **Encoding**: HandBrake (optional secondary encode)

---

## 🎨 Workflow 2: Music Video Production

### Artistic Music Video with Effects

#### **Phase 1: Conceptualization**
1. **Listen and Visualize**
   - Analyze music structure
   - Note tempo and key changes
   - Sketch visual ideas

2. **Shot Planning**
   - Storyboard key moments
   - Plan performance shots
   - Design abstract sequences

#### **Phase 2: Footage Acquisition**
1. **Primary Footage**
   - Shoot performance (multiple angles)
   - Capture B-roll
   - Record abstract textures

2. **Generated Content**
   - Create generative visuals (Processing)
   - Render 3D elements (Blender)
   - Generate fractals/patterns

#### **Phase 3: Editing** (Flowblade or Kdenlive)
1. **Musical Foundation**
   - Import audio track
   - Add markers at key moments
   - Mark bars and beats

2. **Cut to Beat**
   - Place clips on beat
   - Vary shot duration
   - Build energy through editing

3. **Layering**
   - Multiple video tracks
   - Blend modes for textures
   - Opacity adjustments

#### **Phase 4: Effects Processing**
1. **Stylistic Effects**
   ```bash
   # G'MIC artistic effects on frames
   mkdir frames processed
   ffmpeg -i shot001.mp4 frames/frame_%04d.png
   gmic frames/*.png -fx_stylize 0.5,10,0.1 -output processed/frame_%04d.png
   ffmpeg -i processed/frame_%04d.png -c:v libx264 shot001_styled.mp4
   ```

2. **Color Grading**
   - Establish color palette
   - Match shots for continuity
   - Create dramatic looks
   - Export/apply LUT

3. **Visual Effects** (Natron/Blender)
   - Compositing layers
   - Particle effects
   - Light leaks
   - Glitch effects

#### **Phase 5: Final Assembly**
1. **Conforming**
   - Replace shots with processed versions
   - Final timing adjustments
   - Add final effects

2. **Audio Finishing**
   - Master audio level
   - Add subtle risers/impacts
   - Final mix

#### **Export**
```
Format: MP4 or ProRes (for further distribution)
High quality settings for festival/screening
Compressed version for online
```

#### **Tools Used**
- **Editor**: Flowblade or Kdenlive
- **3D/VFX**: Blender
- **Compositing**: Natron
- **Effects**: G'MIC, Processing
- **Color**: DaVinci Resolve (optional)

---

## 🎭 Workflow 3: Live VJ Performance Setup

### Complete VJ Rig Configuration

#### **Phase 1: Content Preparation**
1. **Build Visual Library**
   ```
   vj_library/
   ├── loops/
   │   ├── abstract/
   │   ├── geometric/
   │   └── nature/
   ├── one_shots/
   ├── text/
   └── effects/
   ```

2. **Optimization**
   ```bash
   # Convert to efficient codec for playback
   for file in raw/*.mp4; do
     ffmpeg -i "$file" -c:v mjpeg -q:v 3 optimized/$(basename "$file")
   done
   ```

3. **Organization by Theme**
   - Color-coded folders
   - BPM-labeled files
   - Mood categories

#### **Phase 2: Software Configuration**

**Setup 1: Veejay**
1. **Installation and Setup**
   ```bash
   sudo apt install veejay-server veejay-client
   # Start server
   veejay -d
   # Start client (Reloaded)
   reloaded
   ```

2. **Configure**
   - Load clips into sample bank
   - Set up effects chains
   - Configure MIDI mapping
   - Test transitions

3. **MIDI Controller Setup**
   ```bash
   # Connect MIDI device
   aconnect -l  # List MIDI devices
   # Map controls in Veejay
   ```

**Setup 2: OBS + Processing**
1. **OBS Scenes**
   - Scene per visual type
   - Configure sources
   - Set up transitions
   - Add filters

2. **Processing Sketches**
   - Real-time generative visuals
   - Audio-reactive sketches
   - Output via Syphon/Spout alternative

3. **Integration**
   - Use v4l2loopback for routing
   ```bash
   sudo modprobe v4l2loopback devices=1
   ```

#### **Phase 3: Audio Integration**
1. **JACK Setup**
   ```bash
   # Start JACK server
   jackd -R -d alsa -r 48000
   
   # Or use QJackCtl GUI
   qjackctl
   ```

2. **Audio Routing**
   - Connect DJ software to VJ software
   - Set up audio-reactive parameters
   - Test latency

#### **Phase 4: Performance Practice**
1. **Rehearsal**
   - Practice transitions
   - Build muscle memory
   - Create cue sheets
   - Test backup plans

2. **Technical Check**
   - Test all connections
   - Verify MIDI responses
   - Check output resolution
   - Prepare backup content

#### **Phase 5: Live Performance**
1. **Setup** (2 hours before)
   - Boot system
   - Start all software
   - Connect hardware
   - Test projection

2. **Soundcheck** (30 min before)
   - Test audio input
   - Verify sync
   - Adjust levels

3. **Performance**
   - Stay present
   - Read the room
   - Flow with music
   - Enjoy the moment

4. **Breakdown**
   - Save session
   - Backup settings
   - Notes for next time

#### **Tools Used**
- **VJ Software**: Veejay or FreeJ
- **Backup**: OBS Studio
- **Generative**: Processing or Pure Data
- **Audio**: JACK
- **Control**: MIDI controller + QLC+

---

## 🎥 Workflow 4: Documentary Production

### Documentary Editing Workflow

#### **Phase 1: Ingestion and Organization**
1. **Import Footage**
   ```bash
   # Create project structure
   mkdir -p project/{footage,interviews,broll,audio,graphics,exports}
   
   # Copy and verify footage
   rsync -av --progress /media/card/ project/footage/
   ```

2. **Transcoding for Editing**
   ```bash
   # Generate proxies (if needed)
   for file in footage/*.mp4; do
     ffmpeg -i "$file" -c:v prores -profile:v 0 -c:a pcm_s16le proxies/$(basename "$file" .mp4).mov
   done
   ```

3. **Transcription**
   - Use Subtitle Editor
   - Or manual notes
   - Mark key quotes

#### **Phase 2: Assembly** (Kdenlive or Cinelerra)
1. **String-Out**
   - Place all good takes on timeline
   - Remove obvious bad takes
   - Don't worry about order yet

2. **Rough Structure**
   - Organize by theme/chronology
   - Create narrative arc
   - Identify gaps

3. **Paper Edit**
   - Review and refine structure
   - Mark emotional beats
   - Plan B-roll placement

#### **Phase 3: Fine Editing**
1. **Interviews**
   - Tighten responses
   - Remove ums, pauses
   - Maintain authenticity
   - Add cutaways

2. **B-Roll Integration**
   - Illustrate points
   - Cover edits
   - Build atmosphere
   - Vary shot types

3. **Pacing**
   - Vary clip duration
   - Build and release tension
   - Allow breathing room
   - Create rhythm

#### **Phase 4: Polish**
1. **Graphics**
   - Title cards (Inkscape/GIMP)
   - Lower thirds
   - Maps/diagrams
   - Credits

2. **Color Correction**
   - Match shots
   - Fix exposure
   - Create consistent look
   - Final grade in DaVinci Resolve

3. **Audio Mix**
   - Balance interviews
   - Mix music
   - Add ambient sound
   - Master output

#### **Phase 5: Export and Delivery**
1. **Master Export**
   ```
   Format: ProRes 422 HQ or DNxHD
   Resolution: 1920x1080 or 4K
   Audio: 48kHz, 24-bit
   ```

2. **Distribution Versions**
   ```bash
   # YouTube/Vimeo
   ffmpeg -i master.mov -c:v libx264 -preset slow -crf 18 -c:a aac -b:a 192k youtube.mp4
   
   # Screening DCP (advanced)
   # Use OpenDCP or similar tools
   ```

#### **Tools Used**
- **Editor**: Kdenlive or Cinelerra-GG
- **Transcription**: Subtitle Editor
- **Color**: DaVinci Resolve
- **Audio**: Ardour
- **Graphics**: Inkscape, GIMP

---

## 🌈 Workflow 5: Experimental/Glitch Art Video

### Creative Glitch and Experimental Workflow

#### **Phase 1: Source Material**
1. **Gather Footage**
   - Found footage
   - Personal recordings
   - Abstract textures
   - Static/noise

2. **Intentional Corruption**
   ```bash
   # Create glitch versions
   ffmpeg -i input.mp4 -c:v libx264 -crf 40 compressed.mp4
   
   # Extract and corrupt
   ffmpeg -i input.mp4 -f rawvideo raw.yuv
   # Manually corrupt yuv file with hex editor or:
   dd if=/dev/urandom of=raw.yuv bs=1 count=100 seek=10000 conv=notrunc
   ffmpeg -f rawvideo -s 1920x1080 -r 30 -i raw.yuv -c:v libx264 glitched.mp4
   ```

#### **Phase 2: Processing** (Multiple Tools)
1. **FFmpeg Experiments**
   ```bash
   # Datamosh effect
   ffmpeg -i input.mp4 -c:v libx264 -g 999 -bf 2 -flags +mv4 datamosh.mp4
   
   # Color displacement
   ffmpeg -i input.mp4 -vf "chromashift=rbshift=10:gbshift=-10" chromashift.mp4
   
   # Pixel sorting
   ffmpeg -i input.mp4 -vf "noise=alls=50:allf=t" pixelate.mp4
   ```

2. **Processing Sketches**
   ```processing
   // Pixel sorting
   PImage img;
   void setup() {
     img = loadImage("frame.jpg");
     // Sort pixels
     // Save result
   }
   ```

3. **G'MIC Glitches**
   ```bash
   gmic input.mp4 -fx_distort_lens 0.5,0.5,0,0.5,1
   ```

#### **Phase 3: Composition** (Natron or Blender)
1. **Layer Glitched Elements**
   - Stack multiple processed versions
   - Use blend modes
   - Add displacement maps
   - Create feedback loops

2. **Temporal Effects**
   - Echo effects
   - Frame delays
   - Reverse sections
   - Speed variations

#### **Phase 4: Aesthetic Refinement**
1. **Color Treatment**
   - Extreme color grading
   - Posterization
   - Solarization
   - Split toning

2. **Additional Effects**
   - Scan lines
   - CRT simulation
   - VHS artifacts
   - Film grain

#### **Phase 5: Final Assembly** (Flowblade)
1. **Arrange Sequences**
   - Build narrative (if any)
   - Create rhythm
   - Consider audio sync

2. **Audio Processing**
   - Glitch audio similarly
   - Use granular synthesis
   - Create sonic texture

#### **Export**
```bash
# High quality for archival
ffmpeg -i final.mov -c:v libx264 -preset veryslow -crf 15 master.mp4

# Web version
ffmpeg -i final.mov -c:v libx264 -crf 23 web.mp4
```

#### **Tools Used**
- **Glitching**: FFmpeg, custom scripts
- **Processing**: Processing, Pure Data
- **Effects**: G'MIC, Natron
- **Assembly**: Flowblade or Kdenlive
- **Audio**: Audacity with plugins

---

## 🎬 Workflow 6: 3D Integration Pipeline

### Blender + Live Action Composite

#### **Phase 1: Filming with Tracking in Mind**
1. **Camera Setup**
   - Use tripod or consistent motion
   - Record tracking markers
   - Capture HDRI (for lighting)
   - Note camera settings

2. **Reference Material**
   - Measure real-world dimensions
   - Photograph set from multiple angles
   - Record lighting conditions

#### **Phase 2: Tracking** (Blender)
1. **Import Footage**
   ```python
   # In Blender
   # Switch to Movie Clip Editor
   # Import footage
   # Set frame range
   ```

2. **Track Camera**
   - Add tracking markers
   - Track forward/backward
   - Solve camera motion
   - Set scene scale

3. **Setup Ground Plane**
   - Define floor/reference
   - Orient correctly
   - Test with simple object

#### **Phase 3: 3D Content Creation**
1. **Model**
   - Create 3D elements
   - Match real-world scale
   - Proper topology

2. **Materials**
   - PBR materials
   - Match lighting
   - Test renders

3. **Animation**
   - Animate 3D elements
   - Match physics
   - Time to footage

#### **Phase 4: Rendering**
1. **Render Settings**
   ```
   Engine: Cycles or EEVEE
   Samples: High for quality
   Resolution: Match footage
   Format: OpenEXR with alpha
   Render Layers: Separate passes
   ```

2. **Render Passes**
   - Beauty pass
   - Shadow pass
   - Ambient occlusion
   - Reflection/refraction

#### **Phase 5: Compositing** (Blender Compositor or Natron)
1. **Combine Elements**
   - Import footage
   - Import render passes
   - Layer correctly
   - Adjust transparency

2. **Integration**
   - Match colors
   - Add shadows
   - Blur/defocus to match
   - Add grain/noise

3. **Final Touches**
   - Light wrap edges
   - Atmosphere effects
   - Camera artifacts
   - Final grade

#### **Export**
```bash
# Render sequence
# Blender outputs frames
# Compile with FFmpeg
ffmpeg -i frame_%04d.png -c:v prores_ks -profile:v 3 master.mov
```

#### **Tools Used**
- **3D/Tracking**: Blender
- **Compositing**: Blender Compositor or Natron
- **Finishing**: Kdenlive or DaVinci Resolve

---

## 📦 General Workflow Tips

### Performance Optimization
1. **Use Proxies**: Edit with lower resolution
2. **Render Cache**: Pre-render heavy effects
3. **Close Unnecessary Apps**: Free up RAM
4. **SSD Storage**: Faster media access
5. **Regular Cleanup**: Clear cache files

### Backup Strategy
```bash
# Automated backup script
#!/bin/bash
rsync -av --progress project/ /backup/project_$(date +%Y%m%d)/
```

### Project Management
- Use version control for project files
- Keep detailed notes
- Export project snapshots regularly
- Maintain organized folder structure

### Color Management
- Understand your monitor
- Use color scopes
- View on multiple devices
- Export test renders frequently

---

## 🔗 Related Resources

- [VJ Applications](../vj-applications/) - Tools for live performance
- [Video Editing](../video-editing/) - Software options
- [Post-Processing](../post-processing/) - Effects techniques
- [Installation Guides](../installation-guides/) - Setup instructions
- [Learning Resources](../learning-resources/) - Tutorials
- [Mystical Process Art](../mystical-process-art/) - Intentional practices

---

*These workflows are starting points. Adapt them to your needs, experiment with variations, and develop your own signature processes.*
