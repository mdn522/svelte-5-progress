<script lang="ts" module>
	import { Tween } from 'svelte/motion';
	import { tv } from 'tailwind-variants';
	import { twMerge } from 'tailwind-merge';
	import type { NavigationTarget } from '@sveltejs/kit';

	export type NavigationParams = { from: NavigationTarget | null; to: NavigationTarget | null };

	export const navbarVariants = tv({
		base: "relative z-50 h-0.5 rounded-r-lg",
		variants: {
			size: {
				sm: "h-0.5",
				md: "h-1",
				lg: "h-1.5",
			},
			color: {
				blue: "bg-gradient-to-bl from-sky-700 to-indigo-700 dark:from-indigo-500 dark:to-sky-400",
				rose: "bg-gradient-to-bl from-rose-700 to-rose-500 dark:from-rose-500 dark:to-rose-300",
				amber: "bg-gradient-to-bl from-amber-700 to-amber-500 dark:from-amber-500 dark:to-amber-300",
				green: "bg-gradient-to-bl from-green-700 to-green-500 dark:from-green-500 dark:to-green-300",
				purple: "bg-gradient-to-bl from-purple-700 to-purple-500 dark:from-purple-500 dark:to-purple-300",
				indigo: "bg-gradient-to-bl from-indigo-700 to-indigo-500 dark:from-indigo-500 dark:to-indigo-300",
				red: "bg-gradient-to-bl from-red-700 to-red-500 dark:from-red-500 dark:to-red-300",
				yellow: "bg-gradient-to-bl from-yellow-700 to-yellow-500 dark:from-yellow-500 dark:to-yellow-300",
			},
		},
		defaultVariants: {
			size: "md",
			color: "blue",
		},
	});

	export let nav = $state({
		is_navigating: false,
		progress: new Tween(0, { duration: 500 }),
	});

	type NavType = typeof navbarVariants;
	export interface ProgressProps {
		class?: string;
		size?: keyof NavType['variants']['size'];
		color?: keyof NavType['variants']['color'];
	}
</script>

<script lang="ts">
	import { afterNavigate, beforeNavigate } from '$app/navigation';
	import { cubicOut } from 'svelte/easing';

	let { size, color, class: className }: ProgressProps = $props();

	const progressReset = () => {
		setTimeout(() => {
			nav.progress.set(0, { duration: 0 });
			nav.is_navigating = false;
		}, 500);
	};

	const progressStyle = $derived(`width: ${nav.progress.current}%`);

	function isDiffNavigation(navigation: NavigationParams) {
		return navigation.from?.url.href === navigation.to?.url.href;
	}

	beforeNavigate(async (navigation) => {
		if (!isDiffNavigation(navigation)) {
			nav.is_navigating = true;
			await nav.progress.set(0, { duration: 0 });
			await nav.progress.set(35, { duration: 900, easing: cubicOut });
			await nav.progress.set(75, { duration: 600, easing: cubicOut });
		} else {
			nav.is_navigating = false;
			await nav.progress.set(0, { duration: 0 });
		}
	});

	afterNavigate(async (navigation) => {
		if (!isDiffNavigation(navigation)) {
			await nav.progress.set(100, { duration: 800 });
			progressReset();
		} else {
			await nav.progress.set(0, { duration: 0 });
			nav.is_navigating = false;
		}
	});
</script>

{#if nav.is_navigating}
	<div class="fixed left-0 top-0 z-[110] w-full">
		<div class={twMerge(className, navbarVariants({ size, color }))} style={progressStyle}></div>
	</div>
{/if}
