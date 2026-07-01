<h3><strong>working on a game framework</strong></h3>
<h4>
	<strong>genre</strong>: <kbd>sandbox</kbd> <kbd>2d</kbd> <kbd>top-down</kbd> <kbd>survival</kbd> <kbd>multiplayer</kbd><br>
	<strong>inspiration</strong>: <kbd>Mindustry</kbd> <kbd>Terraria</kbd> <kbd>Minecraft</kbd> <kbd>Rust</kbd><br>
	<strong>hook</strong>: <kbd>nested tilemaps</kbd> <small>still idea phase, gdd coming soon hopefully</small><br>
	<strong>looking for</strong>: people who think this has potential and have spent thousands of hours in games from this genre, but also anyone else who likes this, not just programmers, anyone. helping would be nice, but discussion is fine too!<br><br>
	the initial idea is impossible to achieve richt away, i will create different games on the way there, currently looking into replayability in terms of game content interactions in context of ECS. that means different kinds of events like: "onhit", "onkill", "onattack" and so on.<br>
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
	✅"fatal error: too many errors emitted, stopping now"<br>
	✅stolen laptop<br>
	✅neighbours wifi<br>
	✅never paid for it<br>
	<br>
	<small>some of it is sarcasm, some of it is true!</small><br>
	<small>the only thing that really matters is time, motivation and consistency<br>failures and reality checks are expected</small>
</blockquote></details>

<details><summary><strong>tech</strong></summary><blockquote>
	<small>
	🌕 already went through it<br>
	🌗 working on it<br>
	🌑 planning to look into it<br><br></small>
	<details><summary><strong>engine/framework/graphics-library</strong></summary><blockquote>
		🌕 Unity, HTML/JS (2d rendering context), Unreal, Godot, Monogame, Raylib, Bevy, SDL, OpenGL (OpenGL-ES, WebGL), Roblox Studio<br>
		🌗 SDL2, WebGPU<br>
		🌑 Vulkan, DirectX, SFML, Love2D, the Forge, bgfx<br>
	</blockquote></details>
	<details><summary><strong>tooling</strong></summary><blockquote>
		🌕 Git - Github<br>
		🌕 Cmake<br>
		🌕 Emscripten - WASM<br>
		🌗 custom codegen (in python)<br>
		🌑 Tracy profiler<br>
	</blockquote></details>
	<details><summary><strong>networking</strong></summary><blockquote>
		🌕 UDP, then TCP<br>
		🌕 basic client/server project<br>
		🌕 sent spatially partitioned entity component data<br>
		🌕 better dirty ecs component tracking to send only changes<br>
		🌗 WebTransport - QUIC, imquic<br>
		🌗 message types (reliable, unreliable), payloads, serverless mode<br>
		🌗 grid based server-side fog of war<br>
		🌑 VPS?<br>
		🌑 UDP again?<br>
	</blockquote></details>
	<details><summary><strong>ecs</strong></summary><blockquote>
		🌕 entt<br>
		🌕 serializable ECS components for networking/saving<br>
		🌕 spatially partitioned collision detection with swept box cast<br>
		🌕 linear and angular velocity<br>
		🌗 flecs (with codegen)<br>
		🌑 more types of colliders, tilemap collider, SDF colliders?<br>
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
		<small>live preview simulated editor for: <kbd>graphics</kbd> <kbd>audio</kbd> <kbd>entity</kbd> <kbd>code</kbd></small><br>
		🌕 shaders<br>
		🌕 ecs<br>
		🌗 dsp<br>
		🌗 basic export<br>
		🌗 seamless noise texture generation<br>
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
		🌗 VFX editor<br>
		🌗 WebGPU<br>
		🌑 multi-shader pipelines<br>
		🌑 geometry shader, tesselation shader and native 3D GPU programming in general<br>
	</blockquote></details>
	<details><summary><strong>audio</strong></summary><blockquote>
		🌕 audio callback<br>
		🌕 spectrogram<br>
		🌕 spectral synthesis<br>
		🌕 digital signal processing<br>
		🌗 spatial audio (stereo)<br>
		🌗 DSP editor<br>
	</blockquote></details>
	<details><summary><strong>language</strong></summary><blockquote>
		🌕 C, C#, JS, Rust, HLSL, Lua<br>
		🌗 C++, GLSL, WGSL, custom DSL for use with ECS<br>
		🌑 Java, Jai, Odin, Rust (again)<br>
	</blockquote></details>
	<details><summary><strong>llm coding</strong></summary><blockquote>
		🌕 gpt (browser), gemini (browser), gemini cli (decent amount of time until nerfed), cursor (barely tried), claude (barely tried)<br>
		🌕 local models: qwen coder, gemma. using: ollama, aider, LM studio, roocode - not enough VRAM and RAM for it to be smart enough<br>
		🌗 codex plus<br>
		<small>secret AI opinion: i believe its extremely powerful, but using it correctly is difficult, using it incorrectly can cause serious issues, so basically the same as C++ and GPU programming :) like taming a dragon<br>ai is what made me realize the importance of technical debt</small><br>
	</blockquote></details>
</blockquote></details>

<details><summary><strong>personal</strong></summary><blockquote>
	from: <kbd>Czechia</kbd><br>
	age: <kbd>22</kbd><small>m</small><br>
	career: <kbd>CEO @ unemployed</kbd><br>
	job experience: <kbd>0</kbd> <small>in total less than a year</small><br>
	education: <kbd>graduation</kbd> <small>worthless nowadays</small><br>
	first touched C: <kbd>3 years ago</kbd> <small>thats when i believe a software developer is born :)</small><br>
	personal info: <kbd>sold</kbd><br>
	friends: <kbd>only you</kbd> <small>DM me the word "frog" :)</small><br>
</blockquote></details>
<small>progress updated: <strong>June 23, 2026</strong><br>
discord: <strong>pyroxdd</strong></small>