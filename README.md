
🌍 TerraLite-Craft-3DA lightweight, highly optimized voxel engine built with Three.js. This project demonstrates how to implement dynamic chunk loading, infinite terrain generation, and efficient rendering in the browser without the need for a complex build step.!(https://via.placeholder.com/800x400?text=TerraLite+Craft+3D+Screenshot)(You can replace this placeholder with a screenshot of your game!)

✨ Core Features & MechanicsFeatureDescriptionVoxel WorldThe world is built of individual 1x1x1 meter cubes.Infinite TerrainThe world generates and removes chunks based on the player's position, allowing for endless exploration.

Procedural GenerationUses basic Sine and Cosine functions to generate varied hill height and includes procedural tree placement.

First-Person ControlsStandard FPS controls with PointerLock functionality.

Building/BreakingFull block interaction: Right-Click to place, Left-Click to destroy.PhysicsIncludes gravity, friction, jumping, and collision detection to prevent the player from walking through blocks.

🚀 Optimization HighlightsThe performance of this engine is based on several key optimizations within the "One-Mesh-Per-Block" architecture:Shared Resources: The single THREE.BoxGeometry and all unique THREE.MeshLambertMaterial instances are created once and reused across all blocks in the world. This drastically reduces CPU memory and GPU draw calls compared to creating unique materials for every single block.Fast Chunk Unloading: The removeChunk function uses the chunkGroup.userData.voxelKeys Set to rapidly look up and clean up associated blocks from the global voxelMap and the objects array. This is critical to prevent noticeable lag spikes (hitching) when new chunks are loaded and old ones are destroyed.Scoped Cleanup: The code meticulously disposes of geometries (like the bedrock plane) and removes references to meshes upon removal, preventing memory leaks over long sessions.

🎮 ControlsKey Action W, A, S, D Move Player SHIFT Sprint (Increases movement speed) SPACEJump Mouse Look Look Around (requires PointerLock)Left Click Destroy the targeted block Right Click Place the currently selected block 1 - 5 Select Block Type from the inventory hotbar

⚙️ ConfigurationThe primary constants for world configuration are found at the top of the script:ConstantDefault ValueDescriptionCHUNK_SIZE16The width and depth of a single chunk (in blocks).VIEW_DISTANCE3The number of chunks rendered outward from the player (e.g., $3 \times 3$ chunks total).PLAYER_SPEED30.0Base walking speed.SPRINT_SPEED20.0Additional speed boost when sprinting.TREE_DENSITY0.05Probability of a tree spawning in a viable location.

🛠️ How to Run LocallySince this project uses modern JavaScript (ES Modules) to import Three.js, you must run it from a local web server (browsers restrict module loading from local file:// paths for security).Option 1: VS Code (Recommended)Install the Live Server extension.Right-click the index.html file and choose "Open with Live Server".

📄 License
This project is open-source under the MIT License. Feel free to use this as a starter template for your own web-based voxel games!
