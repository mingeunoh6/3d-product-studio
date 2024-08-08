<script>
	import { onMount, createEventDispatcher } from 'svelte';
	import { glbFileStore } from '$lib/components/stores/lnb_store';

	const dispatch = createEventDispatcher();
	function handleGLBImport(event) {
		const file = event.target.files[0];
		if (file) {
			dispatch('importGLB', { file });
		}
	}

	onMount(() => {
		console.log('Hello LNB component');
	});
</script>

<section>
	<div class="main-title">
		<h5>DASH 3D Prototype</h5>
	</div>
	<div class="sub-title-lv1">
		<p>ver 0.1.1</p>
	</div>
	<div class="sub-title-lv1">
		<p>by MIN GEUN</p>
	</div>
	<div class="sub-title">
		<h5>UPLOAD PRODUCT</h5>
	</div>
	<div class="sub-card">
		<input
			type="file"
			id="glb-import"
			accept=".glb,.gltf"
			style="display: none;"
			on:change={handleGLBImport}
		/>
		<button on:click={() => document.getElementById('glb-import').click()}>Import GLB</button>
	</div>
	<div class="sub-title">
		<h5>UPLOAD HDRI</h5>
	</div>
	<div class="sub-card">
		<button id="hdr-import-btn">Import HDR</button>
	</div>
</section>

<style>
	section {
		box-sizing: border-box;
		width: 100%; /* 30% of the smaller viewport dimension */
		height: 100%;

		background-color: var(--background-color);
	}

	.main-title {
		display: flex;
		justify-content: center;
		align-items: center;
		box-sizing: border-box;
		width: 100%;
		height: 72px;
		border: 1px solid var(--border-color);
		color: var(--text-color);
		background-color: var(--primary-color);
	}

	.sub-title {
		display: flex;
		justify-content: center;
		align-items: center;
		box-sizing: border-box;
		width: 100%;
		height: 48px;
		border: 1px solid var(--border-color);
		color: var(--text-color);
		background-color: var(--primary-color);
	}

	.sub-title-lv1 {
		display: flex;
		justify-content: center;
		align-items: center;
		box-sizing: border-box;
		width: 100%;
		height: 36px;
		border: 1px solid var(--border-color);
		color: var(--accent-color);
		background-color: var(--background-color);
	}

	.sub-card {
		display: flex;
		justify-content: center;

		box-sizing: border-box;
		width: 100%;
		padding: 8px;
		border: 1px solid var(--border-color);
		background-color: var(--background-color);
	}

	button {
		box-sizing: border-box;
		width: 80%;
		height: 42px;
		border: 1px solid var(--border-color);
		background-color: var(--accent-color);
		color: var(--text-color);
	}

	button:hover {
		background-color: var(--accent-hover-color);
		cursor: pointer;
	}
</style>
