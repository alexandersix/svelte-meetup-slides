<script lang="ts">
	import { Code, FitText, Presentation, Slide, Step } from '@components'
</script>

<Presentation>
	<Slide animate>
		<Code lang="svelte" lines="1|2-3|1,4">
			{`
				<script>
					let count = 0
					$: double = count * 2
				<\/script>
			`}
		</Code>
	</Slide>

	<Slide animate>
		<Code lang="svelte" lines="6-9|">
			{`
				<script>
					let count = 0
					$: double = count * 2
				<\/script>
			`}
		</Code>
		<Code lang="svelte" lines="6-9">
			{`
				<div>
					Hello world!
					{{ count }}
				<\/div>
			`}
		</Code>
	</Slide>
</Presentation>
