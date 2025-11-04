<h3>hi, i'm stupid enough to work on my own game engine!</h3>

<details><summary><strong>rules i follow</strong></summary><blockquote>
	❌stable<br>
	❌memory safe<br>
	❌predictable<br>
	❌portable<br>
	❌safe<br>
	❌tested<br>
	❌planning<br>
	❌bounds checking<br>
	❌error handling<br>
	<br>
	✅memory leaks<br>
	✅undefined behavior<br>
	✅works on my machine<br>
	✅-O3<br>
	✅segmentation faults<br>
	✅printf, the only debugger<br>
	✅improvisation<br>
	✅UDP<br>
	✅runtime errors<br>
	✅out of bounds memory access<br>
	✅race conditions<br>
	✅deadlocks<br>
	✅git push --force<br>
	✅ignoring compiler warnings<br>
	✅fatal error: too many errors emitted, stopping now<br>
	<br>
	<small>some of it is sarcasm, some of it is true!</small>
</blockquote></details>
<br>

<details><summary><strong>tech i use</strong></summary><blockquote>
	<small>
	" > " = where i am in that category,<br>
	" >> " = something im currently focusing on,<br>
	anything above it means i already went through it,<br>
	anything below it means i am planning to look into it<br><br></small>
	<details><summary><strong>engine/framework/language</strong></summary><blockquote>
		&nbsp;&nbsp;Unity, raw HTML/JS, Unreal, Godot, Monogame, Raylib, Bevy, SDL, Roblox Studio<br>
		> staying with SDL2, C++<br>
		&nbsp;&nbsp;might try at some point: Vulkan, DirectX, SFML, GameMaker, GDevelop<br>
	</blockquote></details>
	<details><summary><strong>tooling</strong></summary><blockquote>
		&nbsp;&nbsp;Git - Github<br>
		&nbsp;&nbsp;Cmake<br>
		&nbsp;&nbsp;Emscripten - WASM<br>
		> Lua<br>
		&nbsp;&nbsp;Tracy profiler<br>
	</blockquote></details>
	<details><summary><strong>networking</strong></summary><blockquote>
		&nbsp;&nbsp;basic client/server project<br>
		&nbsp;&nbsp;tried raw UDP<br>
		&nbsp;&nbsp;decided to stay with TCP<br>
		&nbsp;&nbsp;sent spatially partitioned entity component data<br>
		> better dirty ecs component tracking to send only changes<br>
		&nbsp;&nbsp;grid based server-side fog of war<br>
		&nbsp;&nbsp;VPS?<br>
		&nbsp;&nbsp;UDP again?<br>
	</blockquote></details>
	<details><summary><strong>ecs</strong></summary><blockquote>
		&nbsp;&nbsp;entt<br>
		&nbsp;&nbsp;serializable ECS components for networking/saving<br>
		&nbsp;&nbsp;spatially partitioned collision detection with swept box cast<br>
		> linear and angular velocity<br>
		&nbsp;&nbsp;more types of colliders, tilemap collider, SDF colliders?<br>
	</blockquote></details>
	<details><summary><strong>rendering</strong></summary><blockquote>
		&nbsp;&nbsp;OpenGL/GLEW within SDL<br>
		&nbsp;&nbsp;tried compute shaders, but will use webGL<br>
		&nbsp;&nbsp;not using buffers as i should, but rather textures for everything (not ideal)<br>
		&nbsp;&nbsp;single shader for everything (also not ideal)<br>
		&nbsp;&nbsp;no separate thread (TPS = FPS)<br>
		&nbsp;&nbsp;custom text rendering<br>
		&nbsp;&nbsp;update/render thread separation + sub-tick interpolation<br>
		&nbsp;&nbsp;using vertices and indices more, for visibility order<br>
		>>frame buffer understanding, making graphics editor<br>
		&nbsp;&nbsp;VFX attempt<br>
	</blockquote></details>
	<details><summary><strong>audio</strong></summary><blockquote>
		&nbsp;&nbsp;audio callback<br>
		> spectrogram<br>
		&nbsp;&nbsp;OpenAL<br>
		&nbsp;&nbsp;audio synthesis<br>
	</blockquote></details>
	<small><br>progress updated November 4, 2025<br><br>discord: <strong>pyroxdd</strong></small>
</blockquote></details>
<br>
