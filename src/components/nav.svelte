<script lang="ts">
	import { goto } from '$app/navigation';
</script>

<div class="nav">
	<a class="nav-item" on:click={() => goto('/triple-word-flickster')}>Triple word flickster</a>
	<!-- Add more nav items as needed -->
</div>

<style>
	.nav {
		display: flex;
		justify-content: center;
		background-color: #333;
		padding: 10px 0;
		position: sticky;
		top: 0;
		z-index: 10;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15);
	}

	.nav-item {
		text-decoration: none;
		color: #fff;
		font-weight: bold;
		font-size: 1.1rem;
		margin: 0 10px;
		padding: 6px 12px;
		cursor: pointer;
		border-radius: 4px;
		transition: all 0.3s ease;
	}

	.nav-item:hover {
		color: #333;
		background-color: #fff;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15);
	}
</style>
