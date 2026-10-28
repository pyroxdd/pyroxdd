<h3><strong>vibe coding a game framework</strong></h3>
<h4>
	<strong>genre</strong>: <kbd>sandbox</kbd> <kbd>2d</kbd> <kbd>top-down</kbd> <kbd>survival</kbd> <kbd>multiplayer</kbd><br>
	<strong>inspiration</strong>: <kbd>Mindustry</kbd> <kbd>Terraria</kbd> <kbd>Minecraft</kbd> <kbd>Rust</kbd><br>
	<strong>idea</strong>: <kbd>nested tilemaps</kbd> still idea phase, GDD exists.. in my head<br>
	<br>
	making prototypes on the way there, currently looking into replayability using ECS events ("onhit", "onkill", "onattack"...).<br>
</h4>



<details><summary><strong>why???</strong></summary><blockquote>
	because..<br><br>
	unity felt uncomfortable with all the bloat and the strange mix of its OOP objects and DOTS.. i left before the runtime fee happened!<br>
	unreal engine was extreme overkill for my goals, too much stuff i didnt need, extremely slow to open and set up<br>
	i barely tried godot, but i assumed i would face the same issues as i did with unity<br>
	monogame had menus that i hated, and i wanted to try something other than C#<br>
	bevy had borrow checking that i wasnt ready for<br>
	raylib was efficient, but i hated how i still had to create workarounds for special drawing techniques such as tilemaps.<br>
	C++ was supposedly the game engine language, so i ended up with SDL2, where i stayed for good two or three years, i recently switched to Sokol and i might try Bevy with Rust again.<br><br>
	overall, i hate how all of the frameworks make a lot of things easier, but the things that arent easier, are harder to do instead. im picturing it like staircases in all directions, where each step is something that needs to be done, while these frameworks make lots of these steps smaller, they always have steps that are a lot harder to get past than they would have been otherwise<br>depending on the game that you are making, having all steps with the same height is often better for the long run<br>(me using AI is very contradicting, because it makes a lot of things easier, and other things a lot harder too, i am using it because i have the opportunity, and im open to new technologies. i face the change, i dont hide it from myself, but it would probably be better if i ignored it, at least i know what its good for and what i can use it for, when i need it)<br><br>the most successful games made in the engines probably could have easily made their own engine with the amount of effort they put in, they just might not want to admit it, or they didnt think about it<br><br><br>
	i am not a competent developer and i have no idea how to work in a team. i shall not bother contributing to anyones work, i am not the kind of person to enjoy maintenance, i dont think i will ever create a codebase that will be worth anyones time, so i will just share my high level game engine progress and hope someone finds it informative in some way. i dont think im the kind of person to be making a game engine, im just trying to get a good enough setup to make a game in, also figuring out what is AI capable of in the process
</blockquote></details>

<details><summary><strong>rules</strong></summary><blockquote>
	❌stable<br>
	❌memory safe<br>
	❌predictable<br>
	❌writing tests<br>
	❌error handling<br>
	❌maintenance<br>
	<br>
	✅vibe coded<br>
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
	currently starting over with no codegen this time<br><br>
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
		🌗 NO CODEGEN ALLOWED! enough codegen for life hopefully :D ..except for atlas coordinate generation, msdf-atlas-gen for fonts and Sokol-shdc<br>
	</blockquote></details>
	<details><summary><strong>procgen</strong></summary><blockquote>
		🌕 rectangular structures with pathways<br>
		🌕 noise (perlin, simplex...)<br>
		🌕 cellular rooms<br>
		🌕 layered subdivison / erosion<br>
		🌕 deterministic scaling structure layers<br>
		🌕 realtime simulated generation with branching - "biome brush" entities<br>
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
		🌕 spatial audio (stereo)<br>
	</blockquote></details>
	<details><summary><strong>language</strong></summary><blockquote>
		🌕 C#, JavaScript, HLSL, C, Rust, Lua<br>
		🌕 GLSL, WGSL, custom ECS language, Odin, Zig<br>
		🌗 C++, GLSL: sokol-shdc version<br>
		🌑 Java, Jai, Rust (again), DLang -betterC<br>
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
	if you got this far, DM me the word "frog" on discord :)<br>
</blockquote></details>
progress updated: <strong>October 28, 2026</strong><br>
discord: <strong>pyroxdd</strong>