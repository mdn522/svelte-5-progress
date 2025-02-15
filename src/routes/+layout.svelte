<script lang="ts">
	import '../app.css';
	import { Progress } from '$lib';
	let { children } = $props();
</script>

<Progress color="amber"/>
{@render children()}
