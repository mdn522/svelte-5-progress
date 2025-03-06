<script lang="ts">
	import { Progress } from '$lib';
	let { children } = $props();
</script>

<Progress color="amber"/>
{@render children()}
