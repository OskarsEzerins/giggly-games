<script lang="ts">
	import { goto } from '$app/navigation';
	let isHamburgerMenuOpen = false;
	const navItems = [{ label: 'Triple word flickster', path: '/triple-word-flickster' }];
</script>

<header class="header">
	<div class="nav">
		<div class="nav-logo" on:click={() => goto('/')}>
			<svg viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg" width="30" height="30">
				<rect x="0" y="0" width="40" height="40" fill="#ff6b6b" />
				<rect x="5" y="5" width="30" height="30" fill="#ffffff" />
				<circle cx="20" cy="20" r="8" fill="#ff6b6b" />
				<path d="M 20 23 L 26 29" stroke="#ffffff" stroke-width="2" stroke-linecap="round" />
				<path d="M 20 23 L 14 29" stroke="#ffffff" stroke-width="2" stroke-linecap="round" />
			</svg>
		</div>
		<div class="nav-items">
			{#each navItems as item}
				<div class="nav-item" on:click={() => goto(item.path)}>{item.label}</div>
			{/each}
		</div>
		<button
			class="nav-toggle {isHamburgerMenuOpen ? 'open' : ''}"
			on:click={() => (isHamburgerMenuOpen = !isHamburgerMenuOpen)}
		>
			<span class="nav-toggle-line" />
			<span class="nav-toggle-line" />
			<span class="nav-toggle-line" />
		</button>
	</div>
	{#if isHamburgerMenuOpen}
		<div class="nav-mobile {isHamburgerMenuOpen ? 'open' : ''}">
			{#each navItems as item}
				<div
					class="nav-item"
					on:click={() => {
						isHamburgerMenuOpen = false;
						goto(item.path);
					}}
				>
					{item.label}
				</div>
			{/each}
		</div>
	{/if}
</header>

<style>
	header {
		--primary-color: #3f3f3f;
		--accent-color: #ffffff;
		--nav-bg-color: #85aacf;
		--text-color: #3f3f3f;
		--text-hover-color: #3f3f3f;
		--item-hover-bg-color: #ff8e76;
	}

	.header {
		font-family: 'Roboto', sans-serif;
		position: sticky;
		top: 0;
		z-index: 10;
		width: 100%;
	}

	.nav {
		display: flex;
		align-items: center;
		justify-content: space-between;
		background-color: var(--nav-bg-color);
		padding: 10px 20px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15);
	}

	.nav-logo {
		color: var(--accent-color);
		font-weight: bold;
		font-size: 1.4rem;
		cursor: pointer;
	}

	.nav-items {
		display: flex;
	}

	.nav-item {
		text-decoration: none;
		color: var(--text-color);
		font-weight: bold;
		font-size: 1.1rem;
		margin: 0 10px;
		padding: 6px 12px;
		cursor: pointer;
		border-radius: 4px;
		position: relative;
		overflow: hidden;
		transition: color 0.3s ease;
		background: linear-gradient(45deg, var(--item-hover-bg-color) 50%, transparent 0) right / 250%
				100% no-repeat,
			linear-gradient(45deg, transparent 50%, var(--item-hover-bg-color) 0) left / 250% 100%
				no-repeat;
		transition: 0.5s;
	}

	.nav-item:hover {
		color: var(--text-hover-color);
		background-position: center;
	}

	.nav-toggle {
		display: none;
		flex-direction: column;
		align-items: center;
		justify-content: space-around;
		width: 24px;
		height: 18px;
		background-color: transparent;
		border: none;
		cursor: pointer;
		padding: 0;
		box-sizing: border-box;
		transition: transform 0.3s ease;
	}

	.nav-toggle-line {
		width: 100%;
		height: 2px;
		background-color: var(--accent-color);
		transition: all 0.3s ease;
	}

	.nav-mobile {
		display: none;
	}

	@media (max-width: 768px) {
		.nav {
			padding: 10px;
			transition: background-color 0.3s ease;
		}

		.nav-item {
			display: none;
		}

		.nav-toggle {
			display: flex;
		}

		.nav-toggle-line {
			transition: transform 0.3s ease, background-color 0.3s ease;
		}

		.nav-toggle.open .nav-toggle-line:nth-child(1) {
			transform: translateY(6px) rotate(45deg);
		}
		.nav-toggle.open .nav-toggle-line:nth-child(2) {
			opacity: 0;
		}
		.nav-toggle.open .nav-toggle-line:nth-child(3) {
			transform: translateY(-6px) rotate(-45deg);
		}

		.nav-mobile {
			position: absolute;
			top: 100%;
			left: 0;
			right: 0;
			display: flex;
			flex-direction: column;
			align-items: center;
			background-color: var(--nav-bg-color);
			padding: 10px;
			transform: translateY(-100%);
			transition: transform 0.3s ease;
		}

		.nav-mobile .nav-item {
			display: block;
			margin-top: 10px;
			opacity: 0;
			transform: translateY(-20px);
			transition: opacity 0.3s ease, transform 0.3s ease;
		}

		.nav-mobile.open {
			transform: translateY(0);
		}

		.nav-mobile.open .nav-item {
			opacity: 1;
			transform: translateY(0);
		}

		.nav-mobile.open .nav-item:nth-child(1) {
			transition-delay: 0.1s;
		}
		.nav-mobile.open .nav-item:nth-child(2) {
			transition-delay: 0.2s;
		}
		.nav-mobile.open .nav-item:nth-child(3) {
			transition-delay: 0.3s;
		}
	}
</style>
