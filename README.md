<h3><strong>working on a game framework (with AI)</strong></h3>
<h4>
	<strong>genre</strong>: <kbd>sandbox</kbd> <kbd>2d</kbd> <kbd>top-down</kbd> <kbd>survival</kbd> <kbd>multiplayer</kbd><br>
	<strong>inspiration</strong>: <kbd>Mindustry</kbd> <kbd>Terraria</kbd> <kbd>Minecraft</kbd> <kbd>Rust</kbd><br>
	<strong>hook</strong>: <kbd>nested tilemaps</kbd> still idea phase, gdd coming soon hopefully<br>
	<strong>looking for</strong>: people who think this has potential and have spent thousands of hours in games from this genre, but also anyone else who likes this, not just programmers, anyone. helping would be nice, but discussion is fine too!<br><br>
	the initial idea is impossible to achieve right away, i will create different games on the way there, currently looking into replayability in terms of game content interactions in context of ECS. that means different kinds of events like: "onhit", "onkill", "onattack" and so on.<br>
</h4>

<details><summary><strong>rules</strong></summary><blockquote>
	❌stable<br>
	❌memory safe<br>
	❌predictable<br>
	❌writing tests<br>
	❌error handling<br>
	<br>
	✅if its not broken, dont fix it<br>
	✅memory leaks<br>
	✅undefined behavior<br>
	✅works on my machine<br>
	✅printf, the only debugger and profiler<br>
	✅improvisation<br>
	✅stolen laptop<br>
	✅neighbours wifi<br>
	✅never paid for it<br>
	✅"fatal error: too many errors emitted, stopping now"<br>
	<br>
	some of it is sarcasm, some of it is true!<br>
	the only thing that really matters is time, motivation and consistency<br>failures and reality checks are expected
</blockquote></details>

<details><summary><strong>tech</strong></summary><blockquote>
	🌕 already went through it<br>
	🌗 working on it<br>
	🌑 planning to look into it<br><br>
	currently focusing on migration to Odin content side with minimal codegen this time<br><br>
	<details><summary><strong>engine/framework/graphics-library</strong></summary><blockquote>
		🌕 Unity, HTML/JS (2d rendering context), Unreal, Godot, Monogame, Raylib, Bevy, SDL, OpenGL (OpenGL-ES, WebGL), Roblox Studio<br>
		🌕 SDL2<br>
		🌗 Sokol<br>
		🌑 Vulkan, DirectX, SFML, Love2D, the Forge, bgfx<br>
	</blockquote></details>
	<details><summary><strong>tooling</strong></summary><blockquote>
		🌕 Git - Github<br>
		🌕 Cmake<br>
		🌕 Emscripten - WASM<br>
		🌕 python codegen<br>
		🌑 Tracy profiler<br>
	</blockquote></details>
	<details><summary><strong>engine architecture</strong></summary><blockquote>
		🌕 two ECS worlds, one for tick thread, one for render thread. this required snapshots, and made things way too complicated<br>
		🌕 server to client ECS world replication via networking<br>
		🌗 single shared ECS world, its so much easier to do stuff on both tick and render side, but might face performance bottlenecks later, theres only one way to find out :)<br>
		🌗 hot reloading via DLL swapping, ECS world is in engine, so it survives the reload. reload takes one second and its unoptimized Odin "everything" compilation, including all game code content files, all shaders and all assets, theres also optimized web build<br>
	</blockquote></details>
	<details><summary><strong>networking</strong></summary><blockquote>
		🌕 UDP, then TCP<br>
		🌕 basic client/server project<br>
		🌕 sent spatially partitioned entity component data<br>
		🌕 better dirty ecs component tracking to send only changes<br>
		🌕 WebTransport - QUIC, imquic<br>
		🌕 message types (reliable, unreliable), payloads, serverless mode<br>
		🌕 grid based server-side fog of war<br>
		🌑 VPS?<br>
		🌑 UDP again?<br>
	</blockquote></details>
	<details><summary><strong>ecs</strong></summary><blockquote>
		🌕 entt<br>
		🌕 serializable ECS components for networking/saving<br>
		🌕 spatially partitioned collision detection with swept box cast<br>
		🌕 linear and angular velocity<br>
		🌗 flecs<br>
		🌗 tile entities<br>
		🌗 events!!! still getting used to them<br>
		🌗 switched to box2D<br>
		🌑 more types of colliders, tilemap collider, SDF colliders?<br>
	</blockquote></details>
	<details><summary><strong>codegen</strong></summary><blockquote>
		🌕 using python, extending C++ with tags and special keywords<br>
		🌕 ECS integration - component structs<br>
		🌕 residency tags and transitioning between them (SERVER -> netcode -> CLIENT -> mirroring/snapshots -> RENDER)<br>
		🌕 shader components (shader logic defined directly in component as a function, component variables have automatically generated GPU layout), this includes vertex shader and fragment shader<br>
		🌕 it is also possible to define compute shader blocks which are primarily used by particle emitters, those are also directly placed in C++<br>
		🌕 internal components which rely on other components<br>
		🌕 component hierarchy (one component automatically creates other component, several components rely on other component, but that component can only have one child component of this kind, forcing a replacement. there are also required variables, components and events. this essentially works as OOP class inheritance)<br>
		🌕 built-in events (add, remove and set, theres also update event, which is converted to systems under the hood), and custom events with queries, all events have optional named ordering and are defined as regular functions with a special "ON(my_event)" keyword.<br>
		🌕 "dense case" feature, currently used for efficient 2D tilemap storing, used primarily with enums. codegen figures out enum element count, automatically appends to switch case, this makes it possible to store many kinds of tiles in tiny value such as 16bit integer, tiles will have their enum defined in themselves, most commonly a rotation, which is an enum of 4 elements. simple wall tile without rotation will take up one space, while a tile we can rotate will take up 4. if a tile also has growth enum with 3 elements and can also rotate, it will take up 12 lines in a switch case. there is also offset enum used in pairs by the offset tile, enabling clean multi-tile structure references (currently a 7x7 space)<br>
		<br>
		🌗 NO CODEGEN ALLOWED! enough codegen for life hopefully :D ..except for atlas coordinate generation, msdf-atlas-gen for fonts, Sokol-shdc and Odin's directory auto-include<br>
	</blockquote></details>
	<details><summary><strong>procgen</strong></summary><blockquote>
		🌕 rectangular structures with pathways<br>
		🌕 noise (perlin, simplex...)<br>
		🌕 cellular rooms<br>
		🌗 layered subdivison / erosion<br>
		🌗 deterministic scaling structure layers<br>
		🌗 realtime simulated generation with branching - "biome brush" entities<br>
		🌑 cave carving<br>
	</blockquote></details>
	<details><summary><strong>editor</strong></summary><blockquote>
		live preview simulated editor for: <kbd>graphics</kbd> <kbd>audio</kbd> <kbd>entity</kbd> <kbd>code</kbd><br>
		🌕 shaders<br>
		🌕 ecs<br>
		🌕 dsp<br>
		🌕 basic export<br>
		🌕 seamless noise texture generation<br>
		🌑 font file to font SDF texture converter<br>
		🌑 whole native editor: view all assets simultaneously, while being separate files, also while being able to change them from the editor. edit shaders, write custom hierarchies to show assets combined into live entity, export with custom values such as points. in general similar direction to Aseprite, but more custom game framework focused<br>
	</blockquote></details>
	<details><summary><strong>gpu</strong></summary><blockquote>
		🌕 OpenGL/GLEW within SDL<br>
		🌕 compute shaders<br>
		🌕 using textures to store everything (very wrong)<br>
		🌕 single shader for everything (also wrong)<br>
		🌕 no separate thread (TPS = FPS, also wrong)<br>
		🌕 custom text rendering, with font SDF texture<br>
		🌕 update/render thread separation + sub-tick interpolation<br>
		🌕 frame buffer, start of graphics editor<br>
		🌕 tiny C-like language into wasm<br>
		🌕 bloom (hate it)<br>
		🌕 VFX editor<br>
		🌕 WebGPU<br>
		🌗 Sokol with sokol-shdc<br>
		🌑 multi-shader pipelines<br>
		🌑 geometry shader, tesselation shader and native 3D GPU programming in general<br>
	</blockquote></details>
	<details><summary><strong>audio</strong></summary><blockquote>
		🌕 audio callback<br>
		🌕 spectrogram<br>
		🌕 spectral synthesis<br>
		🌕 digital signal processing<br>
		🌕 DSP editor<br>
		🌗 spatial audio (stereo)<br>
	</blockquote></details>
	<details><summary><strong>language</strong></summary><blockquote>
		🌕 C, C#, JS, Rust, HLSL, Lua<br>
		🌕 C++, GLSL, WGSL, custom DSL for use with ECS<br>
		🌗 C++, Odin, GLSL: sokol-shdc version<br>
		🌑 Java, Jai, Zig, Rust (again)<br>
	</blockquote></details>
	<details><summary><strong>llm coding</strong></summary><blockquote>
		🌕 gpt (browser), gemini (browser), gemini cli (decent amount of time until nerfed), cursor (barely tried), claude (barely tried)<br>
		🌕 local models: qwen coder, gemma. using: ollama, aider, LM studio, roocode - not enough VRAM and RAM for it to be smart enough<br>
		🌗 Codex plus: currently planning with GPT6 Sol and implementing with GPT6 Luna<br>
		secret AI opinion: i believe its extremely powerful, but using it correctly is difficult, using it incorrectly can cause serious issues, so basically the same as C++ and GPU programming :)<br>AI is what made me realize the importance of technical debt<br>
	</blockquote></details>
</blockquote></details>

<details><summary><strong>personal</strong></summary><blockquote>
	from: <kbd>Czechia</kbd><br>
	age: <kbd>22</kbd><br>
	career: <kbd>CEO @ unemployed</kbd><br>
	job experience: <kbd>0</kbd> in total less than a year<br>
	education: <kbd>graduation</kbd> worthless nowadays<br>
	first touched C: <kbd>3 years ago</kbd> thats when i believe a software developer is born :)<br>
	personal info: <kbd>sold</kbd><br>
	if you got this far, DM me the word "frog" :)<br>
</blockquote></details>
progress updated: <strong>September 30, 2026</strong><br>
discord: <strong>pyroxdd</strong>