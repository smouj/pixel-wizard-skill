title: "Pixel Wizard"
version: "1.0.0"
author: "OpenClaw AI"
description: "Specialized skill for generating retro pixel art sprites and assets for games and interfaces"
tags: ["pixel", "art", "sprites", "retro", "design", "creative", "gaming", "ui"]
created: "2026-03-10"
updated: "2026-03-10"
dependencies: ["stable-diffusion-webui", "pixel-art-lora", "python-3.8+", "torch", "diffusers"]
environment_variables:
  - PIXEL_WIZARD_MODEL_PATH: "/models/pixel-art-v2.ckpt"
  - PIXEL_WIZARD_LORA_PATH: "/loras/retro-pixel-art.safetensors"
  - PIXEL_WIZARD_OUTPUT_DIR: "/outputs/pixel-assets"
  - PIXEL_WIZARD_PROMPT_STRENGTH: "0.75"
requirements:
  - GPU with at least 4GB VRAM
  - 10GB free disk space for models
  - Internet connection for model downloads
  - Basic knowledge of pixel art terminology
---

# Pixel Wizard Skill

## Purpose

Pixel Wizard specializes in generating high-quality retro pixel art sprites and assets specifically designed for indie games, retro-style interfaces, and nostalgic digital art. Unlike generic AI image generators, Pixel Wizard focuses on authentic 8-bit and 16-bit aesthetics, ensuring pixel-perfect outputs that maintain the charm of classic gaming eras.

### Real Use Cases

- **Game Development**: Create character sprites, tilesets, and UI elements for pixel art games like platformers, RPGs, or arcade-style shooters
- **Nostalgic Interfaces**: Generate retro UI components such as buttons, icons, and HUD elements for apps with a vintage feel
- **Asset Libraries**: Build cohesive sprite sheets for game jam projects or indie game prototypes
- **Concept Art**: Produce pixel art concepts for game pitches or promotional materials
- **Educational Tools**: Generate visual aids for teaching pixel art techniques or demonstrating retro game design principles

## Scope

Pixel Wizard operates through specialized CLI commands that leverage Stable Diffusion with pixel art-specific LoRAs and control nets. It supports batch processing, style variations, and output optimization for game-ready assets.

### Specific Commands

- `pixel-wizard generate <prompt> [--style=8bit|16bit|gba|snes] [--size=32x32|64x64|128x128] [--batch=5] [--output=sprites/]`
- `pixel-wizard refine <input_image> [--denoise=0.3] [--pixelate=2] [--palette=nes|gameboy|c64]`
- `pixel-wizard spritesheet <directory> [--grid=4x4] [--padding=1] [--format=png|gif]`
- `pixel-wizard optimize <image> [--colors=16] [--dither=floyd-steinberg] [--scale=2x]`
- `pixel-wizard animate <frames_dir> [--fps=12] [--loop=true] [--format=gif|apng]`

### Command Flags and Options

- `--style`: Specifies pixel art era (8bit, 16bit, gba, snes)
- `--size`: Output resolution in pixels
- `--batch`: Number of variations to generate (1-20)
- `--denoise`: Strength of denoising for refinement (0.0-1.0)
- `--pixelate`: Pixelation factor for retro effect
- `--palette`: Color palette preset (nes, gameboy, c64, custom)
- `--grid`: Spritesheet grid layout
- `--colors`: Maximum colors for optimization
- `--dither`: Dithering algorithm for color reduction
- `--fps`: Animation frame rate
- `--loop`: Enable/disable animation looping

## Detailed Work Process

### Step 1: Environment Setup
1. Ensure Stable Diffusion WebUI is installed and running
2. Verify pixel art LoRA models are downloaded and accessible
3. Set environment variables for model paths and output directories
4. Check GPU memory availability (minimum 4GB free)

### Step 2: Prompt Crafting
1. Analyze the desired asset type (character, tile, UI element)
2. Craft detailed prompts focusing on retro aesthetics
3. Specify style parameters (8-bit, 16-bit, console-specific)
4. Include technical details like resolution and color constraints

### Step 3: Generation Phase
1. Execute generation command with optimized parameters
2. Monitor progress through console output
3. Generate multiple variations using batch mode
4. Apply post-processing for pixel-perfect results

### Step 4: Refinement and Optimization
1. Review generated assets for quality and consistency
2. Use refine command for touch-ups if needed
3. Optimize color palettes and file sizes
4. Create spritesheets or animations as required

### Step 5: Output Validation
1. Verify pixel art authenticity and retro feel
2. Check file formats and resolutions match requirements
3. Test assets in target game engine or interface
4. Generate metadata files for asset organization

## Golden Rules

1. **Authenticity First**: Always prioritize genuine pixel art aesthetics over photorealistic outputs. Use terms like "pixel art style", "8-bit", "retro game sprite" in prompts.

2. **Resolution Constraints**: Stick to power-of-2 resolutions (32x32, 64x64, 128x128) for optimal scaling and game compatibility.

3. **Color Palette Discipline**: Limit to 16 colors maximum for authentic retro feel. Use console-specific palettes (NES, Game Boy, SNES) when possible.

4. **Batch Generation**: Always generate at least 3-5 variations per prompt to ensure quality selection.

5. **No Upscaling**: Never upscale pixel art beyond 2x-4x native resolution to maintain crisp pixels.

6. **Console-Specific Styling**: Match prompts to target console aesthetics (blocky for NES, smooth for SNES, monochromatic for Game Boy).

7. **File Format Standards**: Output as PNG for static assets, GIF/APNG for animations, maintaining transparency where needed.

## Examples

### Example 1: Character Sprite Generation
**Input Command:**
```
pixel-wizard generate "retro pixel art hero character, fantasy warrior with sword, 8-bit style, facing right, action pose" --style=8bit --size=32x32 --batch=5 --output=characters/hero/
```

**Expected Output:**
- 5 PNG files (hero_001.png through hero_005.png) in 32x32 resolution
- Each sprite shows a pixel art warrior in various action poses
- Color palette limited to 16 colors with NES-inspired hues
- Transparent background for easy integration

**Verification Steps:**
1. Open sprites in pixel art editor (Aseprite recommended)
2. Confirm 32x32 pixel dimensions
3. Check color count ≤ 16
4. Test transparency in game engine

### Example 2: Tileset Creation
**Input Command:**
```
pixel-wizard generate "pixel art grass tiles, top-down view, 16-bit style, seamless, various heights" --style=16bit --size=16x16 --batch=8 --output=tiles/grass/
```

**Output:**
- 8 tile variations in 16x16 pixels each
- Seamless textures for platformer backgrounds
- SNES-era color palette with 24-bit RGB approximation
- Files named grass_tile_001.png through grass_tile_008.png

### Example 3: UI Icon Refinement
**Input Command:**
```
pixel-wizard refine ui_draft.png --denoise=0.4 --pixelate=3 --palette=gameboy --colors=4
```

**Output:**
- Refined Game Boy-style icon with 4-color palette
- Enhanced pixel definition and retro aesthetics
- Optimized for low-resolution displays

### Example 4: Animated Sprite
**Input Command:**
```
pixel-wizard animate frames/walking_cycle/ --fps=8 --loop=true --format=gif
```

**Output:**
- walking_animation.gif with 8 FPS looping animation
- Seamless character walk cycle for game integration

## Rollback Commands

- `pixel-wizard undo <output_directory>`: Removes all generated files in specified directory and restores previous versions if available
- `pixel-wizard reset-models`: Reverts to default model configurations, clearing custom LoRA settings
- `pixel-wizard clean-cache`: Clears temporary generation cache and intermediate files
- `pixel-wizard revert <filename>`: Reverts specific file to last known good version from backup

## Dependencies and Requirements

- **Stable Diffusion WebUI**: Version 1.6.0+ with Automatic1111 interface
- **Pixel Art LoRA**: retro-pixel-art-v2.safetensors (download from Civitai)
- **Python Libraries**: torch, diffusers, transformers, PIL
- **GPU Requirements**: NVIDIA GPU with CUDA support, minimum 4GB VRAM
- **Storage**: 10GB for models, additional space for generated assets

## Verification Steps

1. **Model Loading**: Check console output for successful LoRA loading
2. **Generation Success**: Verify output directory contains expected number of files
3. **Pixel Quality**: Open in pixel art software, confirm crisp pixels without blurring
4. **Color Accuracy**: Use color picker to verify palette constraints
5. **File Integrity**: Test files in target application (game engine, UI framework)

## Troubleshooting Common Issues

- **Blurry Output**: Increase denoising strength or use lower resolution prompts
- **Wrong Colors**: Specify exact palette in prompt or use --palette flag
- **GPU Memory Error**: Reduce batch size or use smaller model variants
- **Slow Generation**: Enable GPU acceleration and close other memory-intensive applications
- **Inconsistent Style**: Use more specific style descriptors in prompts (e.g., "NES-style" instead of "retro")
- **File Not Found**: Verify environment variable paths and model file locations

## Performance Optimization

- Use batch processing for multiple similar assets
- Cache frequently used prompts and styles
- Pre-load models at startup for faster generation
- Optimize GPU memory usage with appropriate batch sizes
- Use lower resolutions for quick iterations, upscale later if needed

## Integration Guidelines

- Export spritesheets in JSON format for game engine compatibility
- Maintain consistent naming conventions across asset sets
- Include metadata files with generation parameters for reproducibility
- Test assets in target resolution and color depth before final use
- Document prompt variations that produce best results for future reference