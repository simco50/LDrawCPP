# :yellow_square: LDrawCpp

Single cpp/h LDraw loader.

Small hobby project.

## Usage: Loading

```c++
#include "LDraw.h"

LdrConfig config;
config.pDatabasePath = "C:/ldraw/";
config.Quality = LdrQuality::High; // Prefer high quality parts

// Use logo studs
// config.ReplacementMap.push_back({ "stud.dat", "stud-logo4.dat" });

// No studs
//config.ReplacementMap.push_back({ "stud.dat", nullptr });

LdrState context;
if (LdrInit(&config, &context) != LdrResult::Success)
    return;

LdrModel mdl;
if (LdrLoadModel(pFilePath, &context, mdl) != LdrResult::Success)
    return;

for (const LdrModel::Instance& instance : mdl.Instances)
{
    const LdrPart* pPart = mdl.Parts[instance.Index];
    
    ...
}

```

## Features:

- Materials
- Part Instancing
- Smooth Vertex Normals
- Multi-material Parts
- Index Buffer Generation
- Part Replacement
