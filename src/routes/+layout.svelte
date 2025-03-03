<script lang="ts">
	import '../app.postcss';

	import { settings } from 'svelte-ux';

	settings({
		themes: {
			light: ['light', 'winter'],
			dark: ['skeleton', 'black', 'dracula']
		}
	});
</script>

<slot />
