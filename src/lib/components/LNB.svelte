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
		<h5>3D Masking Prototype</h5>
	</div>
	<div class="sub-title-lv1">
		<p>ver 0.1.2</p>
	</div>
	<div class="sub-title-lv1">
		<p>by MIN GEUN</p>
	</div>
	<div class="sub-title">
		<h5>제품 GLB 업로드</h5>
	</div>
	<div class="sub-card">
		<input
			type="file"
			id="glb-import"
			accept=".glb,.gltf"
			style="display: none;"
			on:change={handleGLBImport}
		/>
		<button on:click={() => document.getElementById('glb-import').click()}>GLB 불러오기</button>
	</div>
	<div class="sub-title">
		<h5>사용법</h5>
	</div>
	<div class="sub-card">
		<p>
			1. 위 버튼을 클릭해 GLB 파일을 불러옵니다.<br /><br />

			2. 불러온 GLB 파일은 중앙의 뷰포트에 표시됩니다.<br /><br />

			3. 뷰포트에서 마우스 드래그로 회전, 확대, 이동이 가능합니다.<br /><br />

			4. 원하는 각도로 조정한 뒤 뷰포트 아래의 마스크 다운로드 버튼을 클릭하세요.<br /><br />

			5. 다운로드 받은 이미지들을 ComfyUI의 인풋으로 사용하세요.<br /><br />
		</p>
	</div>
	<!-- <div class="sub-title">
		<h5>UPLOAD HDRI</h5>
	</div>
	<div class="sub-card">
		<button id="hdr-import-btn">Import HDR</button>
	</div> -->
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
		align-items: center;
		flex-direction: column;
		color: var(--text-color);
		box-sizing: border-box;
		width: 100%;
		padding: 8px;
		border: 1px solid var(--border-color);
		background-color: var(--background-color);
	}

	.sub-card p {
		font-size: 1em;
		margin: 4px;
		line-height: 1.5em;
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
