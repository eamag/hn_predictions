<script lang="ts">
	import '../app.postcss';
	import { autoModeWatcher } from '@skeletonlabs/skeleton';
	import { AppShell, AppBar } from '@skeletonlabs/skeleton';
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
</script>

<svelte:head>{@html '<script>(' + autoModeWatcher.toString() + ')();</script>'}</svelte:head>
<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar shadow="shadow-2xl" slotTrail="!space-x-2">
			<!-- Logo -->
			<svelte:fragment slot="lead">
				<a class="flex items-center gap-4" href="/">
					<span>HN Prediction Leaderboard</span>
				</a>
			</svelte:fragment>
			<svelte:fragment slot="trail">
				<a class="btn space-x-4 variant-soft hover:variant-soft-primary" href="/table">
					Data Table
				</a>
				<a
					class="btn space-x-4 variant-soft hover:variant-soft-primary"
					href="https://eamag.me/2024/HackerNews-Prediction-Evaluator"
					target="_blank"
				>
					About
				</a>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<!-- Page Slot -->
	<main class="container mx-auto p-10">
		<slot />
	</main>
</AppShell>
