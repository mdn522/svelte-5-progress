<script lang="ts" module>
	import { Tween } from 'svelte/motion';
	export let nav = $state({
		is_navigating: false,
		progress: Tween(0, { duration: 500 }),
	});
</script>

<script lang="ts">
	import { afterNavigate, beforeNavigate } from '$app/navigation';

	import { cubicOut } from 'svelte/easing';

	import type { NavigationParams } from '$lib/models';

	const progressReset = () => {
		setTimeout(() => {
			nav.progress.set(0, { duration: 0 });
			nav.is_navigating = false;
		}, 500);
	};

	const progressStyle: string = $derived.by(`width: ${progress}%`);

	/*
	Make sure the navigation is not the same
	 */
	function isDiffNavigation(navigation: NavigationParams) {
		return navigation.from?.url.href === navigation.to?.url.href;
	}

	beforeNavigate(async (navigation) => {
		if (!isDiffNavigation(navigation)) {
			nav.is_navigating = true;
			await progress.set(0, { duration: 0 });
			await progress.set(75, { duration: 500, easing: cubicOut });
		} else {
			nav.is_navigating = false;
			await progress.set(0, { duration: 0 });
		}
	});

	afterNavigate(async (navigation) => {
		if (!isDiffNavigation(navigation)) {
			await progress.set(100, { duration: 800 });
			progressReset();
		} else {
			await progress.set(0, { duration: 0 });
			nav.is_navigating = false;
		}
	});
</script>

{#if is_navigating}
	<div class="fixed left-0 top-0 z-[110] w-full">
		<div
			class="bar relative z-50 h-0.5 rounded-r-lg bg-gradient-to-bl from-sky-700 to-indigo-700 dark:from-indigo-500 dark:to-sky-400"
			style={progressStyle}
		></div>
	</div>
{/if}

<style lang="postcss">
    .bar:after {
        content: '';
        position: absolute;
        top: -7px;
        right: 0;
        transform: translateY(-50%);
        width: 45px;
        height: 100%;
        border-radius: 30%;
        box-shadow: 0 0 35px 6px rgba(139, 212, 255, 0.5);
    }
</style>
