# AEROMINE 3D Model Viewer

Professional 3D model visualization application built with React, Three.js, and Vite. This application provides an interactive platform for viewing and inspecting 3D models with real-time rendering and advanced controls.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Installation](#installation)
- [Development](#development)
- [Building for Production](#building-for-production)
- [Usage Guide](#usage-guide)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Model Integration](#model-integration)
- [Troubleshooting](#troubleshooting)
- [Support](#support)

## Overview

AEROMINE 3D Model Viewer is a web-based application designed to render and interact with 3D models in GLTF format. The application provides an intuitive interface with customizable viewing environments, real-time lighting, and comprehensive camera controls. It is optimized for professional use with focus on performance and visual quality.

## Features

- **Interactive 3D Model Rendering**: View GLTF/GLB models with hardware-accelerated WebGL rendering
- **Orbit Controls**: Intuitive mouse-based controls for rotation, panning, and zooming
- **Dynamic Backgrounds**: Seven preset background themes including gradient and solid options
- **Auto-Rotation**: Enable automatic model rotation for presentation mode
- **Grid Display**: Toggle grid overlay for spatial reference
- **Real-time Lighting**: Advanced lighting setup with ambient, directional, and point lights
- **Environmental Reflections**: Realistic material rendering with studio environment preset
- **Error Handling**: Comprehensive error boundary and loading indicators
- **High-Performance Rendering**: Optimized for crisp rendering on all screen densities
- **Loading Progress**: Real-time loading progress indicator for large models

## Technology Stack

- **React 18.3**: Modern UI framework for component-based development
- **Three.js 0.170**: 3D graphics library for WebGL rendering
- **React Three Fiber 8.17**: React renderer for Three.js
- **React Three Drei 9.117**: Utility library for common Three.js patterns
- **Vite 7.3**: Modern build tool and development server
- **JavaScript ES6+**: Modern JavaScript standards

## Installation

### Prerequisites

- Node.js 16.0 or higher
- npm 7.0 or higher (or yarn/pnpm)

### Setup Instructions

1. Clone the repository:
```bash
git clone https://github.com/aeromineRnD/AEROMINE_3D-Viewer-App-Cube.git
cd AEROMINE_3D-Viewer-App-Cube
```

2. Install dependencies:
```bash
npm install
```

3. Verify installation:
```bash
npm run dev
```

The application should automatically open in your default browser at `http://localhost:3000`.

## Development

### Starting the Development Server

```bash
npm run dev
```

The development server includes:
- Hot module replacement for instant code updates
- Fast refresh for React components
- Automatic browser opening
- Console error reporting

### Development Workflow

1. Make changes to source files in the `src/` directory
2. Changes are automatically reflected in the browser
3. Check the console for any errors or warnings
4. Commit changes when ready

## Building for Production

### Create Production Build

```bash
npm run build
```

This command:
- Optimizes and minifies the code
- Generates the production-ready assets in the `dist/` directory
- Creates source maps for debugging
- Optimizes bundle size

### Preview Production Build

```bash
npm run preview
```

This starts a local server to preview the production build before deployment.

### Deployment

The `dist/` folder contains all assets ready for deployment:
- Copy the contents to your web server
- Ensure proper CORS headers if serving models from different domain
- Configure your web server for SPA routing if needed

## Usage Guide

### User Interface

**Header Section:**
- Application title
- Control instructions for mouse interactions
- Auto-Rotate toggle button
- Grid display toggle button
- Background theme selector

**3D Viewer:**
- Central canvas area displaying the 3D model
- Loading progress indicator during model loading
- Error messages if model fails to load

**Footer:**
- Company branding (AEROMINE R&D)

### Controls

**Mouse Controls:**
- **Left Click + Drag**: Rotate model around all axes
- **Right Click + Drag**: Pan camera position
- **Mouse Wheel/Scroll**: Zoom in and out

**UI Controls:**
- **Auto Rotate**: Automatically rotates the model around vertical axis
- **Grid**: Toggles a reference grid in the scene
- **Background**: Change the background theme

### Background Themes

1. **Purple**: Purple to magenta gradient
2. **Midnight**: Dark blue gradient
3. **Sunrise**: Orange to yellow gradient
4. **Ocean**: Cyan to light blue gradient
5. **Forest**: Green forest gradient
6. **Slate**: Dark neutral gradient
7. **White**: Solid white background

## Project Structure

```
AEROMINE_3D-Viewer-App-Cube/
├── public/
│   └── models/
│       ├── Cube-Services1.gltf
│       ├── Cube-Services1.bin
│       └── textures/
│           └── Baked.png
├── src/
│   ├── components/
│   │   ├── Model.jsx          # Main model loading component
│   │   └── ModelViewer.jsx    # Canvas and rendering setup
│   ├── App.jsx                # Main application component
│   ├── App.css                # Application styles
│   ├── index.css              # Global styles
│   └── main.jsx               # Application entry point
├── index.html                 # HTML entry point
├── vite.config.js             # Vite configuration
├── package.json               # Project dependencies
└── README.md                  # This file
```

### Component Descriptions

**App.jsx**: Root component managing global state including:
- Model path selection
- Auto-rotate state
- Grid visibility
- Background theme selection

**ModelViewer.jsx**: Canvas container handling:
- Three.js scene setup
- Camera configuration
- Lighting setup
- Orbit controls
- Error boundary implementation
- Loading state management

**Model.jsx**: Model loading component responsible for:
- GLTF file loading and parsing
- Model positioning and scaling
- Animation handling (if present)

## Configuration

### Camera Settings

Modify camera properties in `ModelViewer.jsx`:
- **Position**: `[0, 0, 5]` - Starting camera distance
- **FOV**: `50` - Field of view angle
- **Near/Far clipping**: Adjust for model dimensions

### Lighting Configuration

Three light sources are configured:
- **Ambient Light**: General scene illumination (intensity: 0.5)
- **Directional Light**: Main casting light (position: [10, 10, 5], intensity: 1)
- **Point Light**: Secondary fill light (position: [-10, -10, -5], intensity: 0.5)

### Orbit Controls

Fine-tune interaction in `ModelViewer.jsx`:
- **dampingFactor**: `0.05` - Smooth deceleration
- **minDistance**: `1` - Minimum zoom level
- **maxDistance**: `20` - Maximum zoom level
- **maxPolarAngle**: `Math.PI / 1.5` - Vertical rotation limit

## Model Integration

### Adding 3D Models

1. **Export your model as GLTF (.gltf) or GLB (.glb)**
   - Ensure all textures are properly embedded or referenced
   - Export with binary data (.bin files) for better performance

2. **Place model files in `public/models/` directory:**
   ```
   public/models/
   ├── your-model.gltf
   ├── your-model.bin
   └── textures/
       ├── texture1.png
       └── texture2.png
   ```

3. **Update the model path in `App.jsx`:**
   ```jsx
   const [modelPath, setModelPath] = useState('/models/your-model.gltf')
   ```

4. **Optimize Model file:**
   - Minimize polygon count for web performance
   - Use compressed image formats for textures
   - Consider using GLB format for single-file distribution

### Supported Formats

- **GLTF 2.0** (.gltf with separate .bin and textures)
- **GLB** (.glb - single file format)

### Model Requirements

- Must be valid GLTF 2.0 compliant
- Recommended maximum size: 50MB for web delivery
- Textures should be <= 4096x4096 resolution
- Polygon count: 50,000 to 500,000 triangles recommended

## Troubleshooting

### Model Fails to Load

**Symptoms**: Red error message displayed, "Error Loading Model"

**Solutions**:
1. Verify file path matches exactly in `App.jsx`
2. Check browser console for specific error messages
3. Ensure all texture files (.bin, .png) are in the correct folders
4. Verify GLTF file is valid using online tools (glTF Viewer)
5. Check file permissions are readable

### Performance Issues

**Symptoms**: Low frame rate, stuttering animation

**Solutions**:
1. Reduce model polygon count
2. Lower texture resolution (max 2048x2048)
3. Disable grid and auto-rotate if not needed
4. Check browser GPU acceleration is enabled
5. Test on different browser (Chrome typically has best WebGL support)

### Controls Not Responding

**Symptoms**: Mouse interactions don't rotate/pan the model

**Solutions**:
1. Verify browser window is in focus
2. Check browser console for errors
3. Try different browser
4. Clear browser cache
5. Ensure JavaScript is enabled

### White Screen or Blank Display

**Symptoms**: Canvas appears blank, no error messages

**Solutions**:
1. Check browser console for JavaScript errors
2. Verify model file exists at specified path
3. Check if model has geometry and materials
4. Try the preview button to test model
5. Test with the default model first

### Build Errors

**Symptoms**: `npm run build` produces errors

**Solutions**:
1. Clear `node_modules` and `dist` folders: `rm -rf node_modules dist`
2. Reinstall dependencies: `npm install`
3. Clear npm cache: `npm cache clean --force`
4. Rebuild: `npm run build`

## Support

For technical support or questions regarding the AEROMINE 3D Model Viewer:

- **Repository**: https://github.com/aeromineRnD/AEROMINE_3D-Viewer-App-Cube
- **Organization**: AEROMINE R&D
- **Issues**: Submit via GitHub Issues

### Documentation References

- [Three.js Documentation](https://threejs.org/docs/)
- [React Three Fiber Docs](https://docs.pmnd.rs/react-three-fiber/)
- [React Three Drei Docs](https://github.com/pmndrs/drei)
- [Vite Documentation](https://vitejs.dev/)

---

**Version**: 1.0.0  
**Last Updated**: February 2026  
**License**: Proprietary - AEROMINE R&D
