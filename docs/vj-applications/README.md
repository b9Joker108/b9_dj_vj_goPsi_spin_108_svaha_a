# VJ Applications - State-of-the-Art FOSS Tools

## Overview

VJ (Video Jockey) applications are essential tools for real-time visual performance, live video mixing, and interactive visual displays. This section covers the most sophisticated FOSS VJ applications available on GNU/Linux.

## 🎬 Core VJ Applications

### 1. **Xjadeo** (Advanced Video Monitoring)
- **Description**: Video player that displays a video-clip in sync with an external time source (MTC, LTC, JACK-transport)
- **Use Cases**: Professional video monitoring, sync with audio DAWs
- **Key Features**:
  - Frame-accurate video playback
  - Multiple timecode sources support
  - JACK audio integration
  - Low-latency performance
- **Website**: https://xjadeo.sourceforge.net/
- **Installation**: Available in most distro repositories

### 2. **FreeJ** (Real-time Video Mixer)
- **Description**: Vision mixer for live performances, streaming, and VJing
- **Use Cases**: Live performances, streaming, video art installations
- **Key Features**:
  - Multiple video layers
  - Text generator
  - Live camera input
  - Various video effects and filters
  - Scriptable with JavaScript
  - Audio reactive capabilities
- **Website**: https://freej.dyne.org/
- **Installation**: `sudo apt install freej` (Debian/Ubuntu)

### 3. **Flowblade** (Multitrack NLE with VJ Mode)
- **Description**: Non-linear video editor with advanced capabilities suitable for VJ work
- **Use Cases**: Video editing, live performance preparation, quick edits
- **Key Features**:
  - Fast rendering
  - Proxy editing
  - Multiple video tracks
  - Comprehensive effects library
  - Batch processing
- **Website**: https://jliljebl.github.io/flowblade/
- **GitHub**: https://github.com/jliljebl/flowblade

### 4. **Veejay** (Real-time Video Sequencer and Effects)
- **Description**: Real-time video performance application with powerful effects processing
- **Use Cases**: Live VJ performances, video sampling, real-time effects
- **Key Features**:
  - Sample and stream-based editing
  - 160+ built-in effects
  - VIMS (Video Instrument Message System)
  - Multi-track timeline
  - MIDI control support
  - OSC (Open Sound Control) support
  - Very low latency
- **Website**: http://veejayhq.net/
- **GitHub**: https://github.com/c0ntrol/veejay

### 5. **GLMixer** (OpenGL Video Mixer)
- **Description**: Real-time graphics and video mixing application
- **Use Cases**: Video installations, live performances, VJing
- **Key Features**:
  - GPU-accelerated rendering
  - Multiple source types (video, images, cameras, render buffers)
  - Advanced blending modes
  - Real-time effects
  - Recording capabilities
  - Session management
- **Website**: https://sourceforge.net/projects/glmixer/
- **Status**: Legacy project but still functional

### 6. **Gephex** (Modular Video Synthesis)
- **Description**: Modular environment for creating real-time video effects
- **Use Cases**: Generative art, visual synthesis, VJ performances
- **Key Features**:
  - Modular architecture
  - Node-based interface
  - Custom effects creation
  - Real-time performance
- **Website**: http://www.gephex.org/
- **GitHub**: https://github.com/lucasw/gephex

## 🎨 Visual Synthesis & Generative Tools

### 7. **Processing** (Creative Coding Platform)
- **Description**: Flexible software sketchbook and language for visual arts
- **Use Cases**: Generative art, data visualization, interactive installations
- **Key Features**:
  - Easy to learn programming environment
  - Extensive library ecosystem
  - Video library for video manipulation
  - OpenGL support
  - Export to various formats
- **Website**: https://processing.org/
- **Installation**: Download from website or via package manager

### 8. **Pure Data (Pd) + GEM** (Visual Programming)
- **Description**: Visual programming environment with Graphics Environment for Multimedia
- **Use Cases**: Interactive installations, algorithmic art, VJ performances
- **Key Features**:
  - Real-time audio and video processing
  - Extensive visual effects library
  - MIDI and OSC control
  - Modular patching environment
  - Shader support
- **Website**: https://puredata.info/
- **GEM**: https://gem.iem.at/

### 9. **Vuo** (Real-time Interactive Media)
- **Description**: Visual programming tool for real-time interactive media
- **Use Cases**: VJ performances, installations, interactive art
- **Key Features**:
  - Node-based visual programming
  - Live coding capabilities
  - Extensive protocol support (OSC, MIDI, DMX, Syphon)
  - GPU-accelerated rendering
  - Export to standalone apps
- **Website**: https://vuo.org/
- **Note**: Free version available, pro features require license

### 10. **Cables.gl** (Visual Programming in Browser)
- **Description**: Web-based visual programming environment for interactive 3D and 2D
- **Use Cases**: Web-based VJ tools, generative art, interactive experiences
- **Key Features**:
  - Browser-based (WebGL)
  - Node-based interface
  - Real-time collaboration
  - Shader editor
  - Export capabilities
- **Website**: https://cables.gl/

## 🌊 Shader-Based Tools

### 11. **KodeLife** (Real-time GPU Shader Editor)
- **Description**: Real-time shader coding environment
- **Use Cases**: Live coding performances, shader art, VJ visuals
- **Key Features**:
  - Multi-buffer support
  - Built-in post-processing
  - Camera and audio input
  - OSC and MIDI support
  - ISF (Interactive Shader Format) support
- **Website**: https://hexler.net/kodelife

### 12. **Bonzomatic** (Live Shader Coding Tool)
- **Description**: Tool for live coding graphics using GLSL shaders
- **Use Cases**: Live coding performances, shader art sessions
- **Key Features**:
  - Multiple rendering backends
  - MIDI input support
  - Shader recording
  - Lightweight and fast
- **GitHub**: https://github.com/Gargaj/Bonzomatic

### 13. **The Force** (Web-based Live Shader Coding)
- **Description**: WebGL live coding editor for creating visuals
- **Use Cases**: Live coding, shader performances, quick prototyping
- **Key Features**:
  - Browser-based
  - Audio reactive
  - Multiple examples and presets
  - Easy to learn syntax
- **Website**: https://shawnlawson.github.io/The_Force/

## 🎭 Projection Mapping

### 14. **MapMap** (Projection Mapping Software)
- **Description**: Free, open-source video projection mapping software
- **Use Cases**: Projection mapping installations, architectural mapping
- **Key Features**:
  - Mesh warping
  - Multiple input sources
  - Layer-based workflow
  - Real-time preview
  - Timeline-based animation
- **Website**: https://mapmapteam.github.io/
- **GitHub**: https://github.com/mapmapteam/mapmap

### 15. **Lpmt** (Little Projection Mapping Tool)
- **Description**: Simple projection mapping tool
- **Use Cases**: Quick projection mapping setups, installations
- **Key Features**:
  - Quad warping
  - Multiple surfaces
  - Video playback
  - Camera input support
- **GitHub**: https://github.com/Chpetrou/lpmt

## 🎹 MIDI/OSC Control Systems

### 16. **OSCulator** (Alternative: oscpack, liblo)
- **Description**: OSC (Open Sound Control) routing and conversion tools
- **Use Cases**: Connecting controllers to VJ software, protocol bridging
- **Key Features**:
  - OSC to MIDI conversion
  - Custom routing
  - Multiple protocol support
- **Libraries**: 
  - oscpack: http://www.rossbencina.com/code/oscpack
  - liblo: http://liblo.sourceforge.net/

### 17. **QLC+** (Q Light Controller Plus)
- **Description**: DMX and lighting control software
- **Use Cases**: Controlling lights in sync with video, integrated AV shows
- **Key Features**:
  - DMX control
  - Art-Net support
  - Fixture library
  - Timeline sequencer
  - Audio triggers
- **Website**: https://www.qlcplus.org/

## 📹 Video Capture & Streaming

### 18. **OBS Studio** (Open Broadcaster Software)
- **Description**: Professional live streaming and recording software
- **Use Cases**: Live streaming, screen recording, video mixing
- **Key Features**:
  - Multiple scenes and sources
  - Real-time video/audio mixing
  - Plugin ecosystem
  - Streaming to multiple platforms
  - Advanced audio mixing
  - Chroma keying
- **Website**: https://obsproject.com/
- **GitHub**: https://github.com/obsproject/obs-studio

### 19. **V4L2Loopback** (Virtual Video Device)
- **Description**: Kernel module creating virtual video devices
- **Use Cases**: Routing video between applications, virtual cameras
- **Key Features**:
  - Multiple virtual cameras
  - Integration with various tools
  - Low latency
- **GitHub**: https://github.com/umlaeute/v4l2loopback

### 20. **FFmpeg** (Multimedia Framework)
- **Description**: Complete solution to record, convert and stream audio and video
- **Use Cases**: Video conversion, streaming, basic effects
- **Key Features**:
  - Extensive codec support
  - Powerful filtering system
  - Command-line interface
  - Streaming capabilities
  - Format conversion
- **Website**: https://ffmpeg.org/

## 🎪 Additional Performance Tools

### 21. **Krita** (Digital Painting with Animation)
- **Description**: Professional digital painting application with animation features
- **Use Cases**: Frame-by-frame animation, rotoscoping, digital art
- **Key Features**:
  - Animation timeline
  - Onion skinning
  - Brush engine
  - Layer management
  - PSD support
- **Website**: https://krita.org/

### 22. **Synfig Studio** (2D Vector Animation)
- **Description**: Vector-based 2D animation software
- **Use Cases**: Motion graphics, animated content creation
- **Key Features**:
  - Vector tweening
  - Bone system
  - Advanced layer types
  - Real-time preview
- **Website**: https://www.synfig.org/

### 23. **Pencil2D** (Traditional Animation)
- **Description**: Hand-drawn animation tool
- **Use Cases**: Traditional frame-by-frame animation
- **Key Features**:
  - Simple interface
  - Bitmap and vector support
  - Onion skinning
  - Export to video
- **Website**: https://www.pencil2d.org/

## 🔧 Utility Tools

### 24. **Jack Audio Connection Kit** (JACK)
- **Description**: Professional audio server for low-latency audio connections
- **Use Cases**: Audio routing, syncing audio/video applications
- **Key Features**:
  - Low latency
  - Flexible routing
  - Session management
  - Multiple application support
- **Website**: https://jackaudio.org/

### 25. **PipeWire** (Multimedia Processing)
- **Description**: Modern multimedia processing server
- **Use Cases**: Audio/video routing, session management
- **Key Features**:
  - Unified audio/video handling
  - JACK compatibility
  - Low latency
  - Modern architecture
- **Website**: https://pipewire.org/

## 🎯 Recommended Combinations

### Setup 1: Live Performance
- **VJ Software**: Veejay or FreeJ
- **Control**: MIDI controller + QLC+
- **Audio**: JACK or PipeWire
- **Capture**: OBS Studio
- **Effects**: Pure Data with GEM

### Setup 2: Shader-Based Performance
- **Live Coding**: KodeLife or Bonzomatic
- **Control**: OSC via TouchOSC or similar
- **Capture**: OBS Studio with virtual camera
- **Processing**: Processing for additional layers

### Setup 3: Projection Mapping Installation
- **Mapping**: MapMap
- **Content**: Veejay for playback
- **Control**: QLC+ for lighting sync
- **Backup**: FFmpeg for content preparation

## 📚 Learning Resources

- **VJ Handbook**: Community resources on VJ techniques
- **Cables.gl Academy**: Tutorials for node-based programming
- **Processing Tutorials**: https://processing.org/tutorials
- **Veejay Manual**: http://veejayhq.net/documentation/
- **Pure Data Documentation**: https://puredata.info/docs

## 🚀 Next Steps

1. Explore individual tool documentation in subdirectories
2. Check [Installation Guides](../installation-guides/) for setup instructions
3. Review [Practical Workflows](../practical-workflows/) for usage examples
4. Study [Learning Resources](../learning-resources/) for tutorials

---

*For detailed installation instructions and configuration guides, see the [Installation Guides](../installation-guides/) section.*
