<script lang="ts">
	let { stars }: { stars: number } = $props();
</script>

<div class="flex gap-x-1">
	<span class="sr-only">{stars} star{stars > 1 ? 's' : ''}</span>
	{#each Array(5), i}
		<svg
			xmlns="http://www.w3.org/2000/svg"
			viewBox="0 0 256 256"
			fill="currentColor"
			aria-hidden="true"
			class={['w-4', i < stars ? 'text-white' : 'text-gray-500']}
		>
			<path
				d="m234.29 114.85l-45 38.83L203 211.75a16.4 16.4 0 0 1-24.5 17.82L128 198.49l-50.53 31.08A16.4 16.4 0 0 1 53 211.75l13.76-58.07l-45-38.83A16.46 16.46 0 0 1 31.08 86l59-4.76l22.76-55.08a16.36 16.36 0 0 1 30.27 0l22.75 55.08l59 4.76a16.46 16.46 0 0 1 9.37 28.86Z"
			/>
		</svg>
	{/each}
</div>
