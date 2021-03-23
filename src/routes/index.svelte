<script context="module">
	/**
	 * @param {import('@sveltejs/kit).LoadOptions} options
	 * @returns {import('@sveltejs/kit').Loaded}
	 */
	export async function load({ fetch }) {
		const res = await fetch("test");

		if (res.ok) {
			return {
				props: {
					test: await res.json(),
				},
			};
		}

		return {
			status: res.status,
			error: new Error(`Could not load test`),
		};
	}
</script>

<script lang="ts">
	export let test;
</script>

<pre>
	{JSON.stringify(test, null, 2)}
</pre>
