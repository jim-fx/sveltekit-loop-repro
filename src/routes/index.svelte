<script context="module">
	/**
	 * @param {import('@sveltejs/kit).LoadOptions} options
	 * @returns {import('@sveltejs/kit').Loaded}
	 */
	export async function load({ fetch }) {
		const res = await fetch("api/test");

		if (res.ok) {
			return {
				props: {
					test: await res.json(),
				},
			};
		}

		return {
			status: res.status,
			error: new Error(`Could not load /api/test`),
		};
	}
</script>

<script lang="ts">
	export let test;
</script>

{JSON.stringify(test)}
