# CUDA Image Filters

A parallel computing project implementing various image filters using CUDA to leverage GPU acceleration. The project demonstrates significant performance improvements through GPU parallelization and optimization techniques.

## Features

Six image filters have been implemented:

1. Gaussian Blur - Applies smoothing using a Gaussian kernel
2. Emboss - Creates a 3D-like effect with directional shading
3. Erosion - Morphological operation that shrinks bright regions
4. Dilation - Morphological operation that expands bright regions
5. Wave - Creates a wave-like distortion effect
6. Oil Painting - Simulates an oil painting artistic effect

## Implementation Details

### Filter Types

- **Min/Max Operations**
  - Erosion and Dilation filters using neighborhood operations
  - Implementation focuses on finding minimum/maximum values in local windows

- **Weighted Combinations**
  - Gaussian Blur using configurable radius and sigma
  - Emboss effect using directional kernels
  
- **Special Operations**
  - Wave effect using pixel displacement
  - Oil Painting using intensity-based operations

### Optimization Techniques

1. Shared Memory Usage
2. Block-based Processing
3. Memory Coalescing
4. Loop Unrolling
5. Thread Block Optimization

## Performance Results

- Achieved up to 37x speedup compared to sequential CPU implementation
- OpenMP implementation showed linear scaling with number of CPU cores
- CUDA optimizations provided significant improvements:
  - Shared memory implementation reduced global memory access
  - Block size optimization improved thread utilization
  - Memory coalescing enhanced memory access patterns

## Usage

```bash
./filter_cuda input.png output.png <filter_type> [parameters]
```

Filter types and parameters:
- `gaussian <radius> <sigma>`
- `emboss <intensity>`
- `erode <radius>`
- `dilate <radius>`
- `wave <amplitudeX> <amplitudeY> <frequencyX>`
- `oil <radius>`

## Building

### Requirements
- CUDA Toolkit (with compute capability sm_61 or higher)
- libpng library for PNG image processing
- GCC/G++ compiler with C++11 support
- GNU Make

### Compilation
The project uses a Makefile for build automation. Available make targets:

```bash
make        # Build the filter program (default)
make clean  # Remove build artifacts
```

### Project Structure
- `main.cu`: Main program entry point and CLI handling
- `image.cu`: Image loading and saving utilities
- `filters.cu`: Filter implementation and CPU-GPU memory management
- `kernels.cu`: CUDA kernel implementations for each filter
