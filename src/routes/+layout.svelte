<script lang="ts">
	import '../app.postcss';

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';

	import { page } from '$app/stores';
	import { goto } from '$app/navigation';

	import { storePopup, TabGroup, AppBar, Avatar, TabAnchor } from '@skeletonlabs/skeleton';

	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });

	function goHome() {
		goto('/');
	}
</script>

<AppBar>
	<svelte:fragment slot="lead">
		<button on:click={goHome}>
			<Avatar src="favicon.png" width="w-10" rounded="rounded-3xl" />
		</button>
	</svelte:fragment>
	<button on:click={goHome}>
		<strong>Krishnan Shankar</strong>
	</button>
	<svelte:fragment slot="trail">
		<TabGroup
			rounded="rounded-container-token"
			border=""
			regionList="space-x-2"
			hover="hover:variant-soft-primary"
			active="variant-filled-primary"
		>
			<TabAnchor href="/" selected={$page.url.pathname === '/'}>Home</TabAnchor>
			<TabAnchor href="/portfolio" selected={$page.url.pathname === '/portfolio'}
				>Portfolio</TabAnchor
			>
		</TabGroup>
	</svelte:fragment>
</AppBar>

<slot />
