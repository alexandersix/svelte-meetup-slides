<script lang="ts">
	import { Code, FitText, Presentation, Slide, Step } from '@components'
</script>

<Presentation>
	<Slide></Slide>
	<Slide>
		<FitText class="font-bold mb-12">Zero to Svelte</FitText>
		<p class="text-5xl">in 15 minutes or less</p>
	</Slide>
	<Slide animate>
		<div class="block text-left h-full w-full">
			<p class="text-4xl font-semibold mb-8">Disclaimer</p>
			<ul class="list-disc text-2xl space-y-2">
				<Step>
					<li>My only goal is to expose you to Svelte and its benefits</li>
				</Step>
				<Step>
					<li>
						I am not telling you to switch all of your Kirschbaum projects over
						to Svelte
					</li>
				</Step>
				<Step>
					<li>
						I am not trying to make Svelte your new favorite UI framework <span
							class="text-sm">(but, that'd be a nice bonus!)</span
						>
					</li>
				</Step>
				<Step>
					<li class="text-yellow-300">
						Come talk to me about Svelte this week!
					</li>
				</Step>
			</ul>
		</div>
	</Slide>
	<Slide animate>
		<div
			class="flex flex-col justify-center items-center text-left h-full w-full"
		>
			<p class="text-6xl font-semibold" data-id="what_is_svelte">
				What is Svelte?
			</p>
		</div>
	</Slide>
	<Slide animate>
		<div class="flex flex-col text-left h-full w-full">
			<p data-id="what_is_svelte" class="text-4xl font-semibold mb-8">
				What is Svelte?
			</p>
			<ul class="list-disc text-2xl space-y-2">
				<Step>
					<li>
						A word meaning <em class="text-yellow-300">slender</em>,
						<em class="text-yellow-300">sleek</em>, or
						<em class="text-yellow-300">suave</em>
					</li>
				</Step>
				<Step>
					<li>
						JS-based tool for building web apps declaratively out of components
					</li>
				</Step>
				<Step>
					<li>
						Components are <strong class="text-yellow-300">compiled</strong> into
						small, efficient JS modules (without a virtual DOM!)
					</li>
				</Step>
				<Step>
					<li>
						Able to build entire applications with Astro, SvelteKit, etc. or be
						added to projects incrementally
					</li>
				</Step>
			</ul>
		</div>
	</Slide>

	<Slide animate>
		<div
			class="flex flex-col justify-center items-center text-center h-full w-full"
		>
			<p class="text-6xl font-semibold" data-id="how_svelte_compares">
				How do Svelte components compare to other frameworks?
			</p>
		</div>
	</Slide>

	<Slide animate>
		<Code lang="html" lines="1-9|1|3-9|4|6,8">
			{`
					@props(['hasIcon'])

					<button class="button">
						{{ $slot }}

						@if ($hasIcon)
							<x-icon />
						@endif
					</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<Code lang="js" lines="1-16|1-8|10-16|12|14">
			{`
					<script setup>
						defineProps([
							hasIcon: {
								type: Boolean,
								required: true
							}
						])
					<\/script>

					<template>
						<button class="button">
							<slot />

							<Icon v-if="hasIcon" />
						</button>
					<\/template>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<Code lang="svelte" lines="1-11|1-3|5-11|6|8,10">
			{`
					<script>
						export let hasIcon;
					<\/script>

					<button class="button">
						<slot />

						{#if hasIcon}
							<Icon />
						{/if}
					</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<div
			class="flex flex-col justify-center items-center text-center h-full w-full"
		>
			<p class="text-6xl font-semibold" data-id="diving_in">Let's dive in!</p>
		</div>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Reactive Values</p>
		<Code lang="svelte">
			{`
					<script>
					<\/script>

					<p>0</p>
					<button class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Reactive Values</p>
		<Code lang="svelte">
			{`
					<script>
						let count = 0;
					<\/script>

					<p>0</p>
					<button class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Reactive Values</p>
		<Code lang="svelte">
			{`
					<script>
						let count = 0;
					<\/script>

					<p>{ count }</p>
					<button class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Reactive Values</p>
		<Code lang="svelte">
			{`
					<script>
						let count = 0;

						function increment() {
							count = count + 1;
						}
					<\/script>

					<p>{ count }</p>
					<button class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Reactive Values</p>
		<Code lang="svelte">
			{`
					<script>
						let count = 0;

						function increment() {
							count = count + 1;
						}
					<\/script>

					<p>{ count }</p>
					<button on:click={increment} class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Props</p>
		<Code lang="svelte" lines="1-16|2">
			{`
					<script>
						let count = 0;

						function increment() {
							count = count + 1;
						}
					<\/script>

					<p>{ count }</p>
					<button on:click={increment} class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Props</p>
		<Code lang="svelte" lines="2">
			{`
					<script>
						export let count = 0;

						function increment() {
							count = count + 1;
						}
					<\/script>

					<p>{ count }</p>
					<button on:click={increment} class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Computed/Derived State</p>
		<Code lang="svelte">
			{`
					<script>
						let count = 0;

						function increment() {
							count = count + 1;
						}
					<\/script>

					<p>{ count }</p>
					<button on:click={increment} class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Computed/Derived State</p>
		<Code lang="svelte" lines="1-18|2-3,10-11">
			{`
					<script>
						let count = 0;
						$: doubleCount = count * 2;

						function increment() {
							count = count + 1;
						}
					<\/script>

					<p>{ count }</p>
					<p>{ doubleCount }</p>
					<button on:click={increment} class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Logic & Loops</p>
		<Code lang="svelte">
			{`
					<script>
						let count = 0;

						function increment() {
							count = count + 1;
						}
					<\/script>

					<p>{ count }</p>
					<button on:click={increment} class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Logic & Loops</p>
		<Code lang="svelte">
			{`
					...

					<p>{ count }</p>

					<button on:click={increment} class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Logic & Loops</p>
		<Code lang="svelte" lines="1-9|3-7">
			{`
					...

					{#if count > 10}
						<p>{ count }</p>
					{:else}
						<p>Count value is not > 10</p>
					{/if}

					<button on:click={increment} class="button">+</button>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Logic & Loops</p>
		<Code lang="svelte" lines="1-9|2,7-9">
			{`
					<script>
						let names = ['Hilleary', 'Nathan', 'Jillian'];
					<\/script>

					<p>List of attendees:</p>

					{#each names as name, index}
						{ index + 1 }. { name }	
					{/each}
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Binding Inputs</p>
		<Code lang="svelte">
			{`
					<script>
						let name = '';
					<\/script>

					<p>Hello, { name }!</p>
				`}
		</Code>
	</Slide>

	<Slide animate>
		<p class="text-4xl font-semibold mb-8">Binding Inputs</p>
		<Code lang="svelte">
			{`
					<script>
						let name = '';
					<\/script>

					<p>Hello, { name }!</p>

					<input type="text" bind:value={name} />
				`}
		</Code>
	</Slide>

	<Slide animate>
		<div class="flex flex-col text-left h-full w-full">
			<p data-id="more_advanced_resources" class="text-4xl font-semibold mb-8">
				(Some) Advanced Svelte Features
			</p>
			<ul class="list-disc text-2xl space-y-2">
				<li>Stores</li>
				<li>Motion (Tweens & Springs)</li>
				<li>Transitions (CSS & JS)</li>
				<li>Animations</li>
			</ul>
		</div>
	</Slide>

	<Slide animate>
		<div
			class="flex flex-col justify-center items-center text-left h-full w-full"
		>
			<p class="text-6xl font-semibold" data-id="interested_in_learning_more">
				Interested in learning more?
			</p>
		</div>
	</Slide>
	<Slide animate>
		<div class="flex flex-col text-left h-full w-full">
			<p
				data-id="interested_in_learning_more"
				class="text-4xl font-semibold mb-8"
			>
				Interested in learning more?
			</p>
			<ul class="list-disc text-2xl space-y-2">
				<li>
					Svelte Documentation - <a
						class="text-yellow-300"
						href="https://svelte.dev/docs"
					>
						https://svelte.dev/docs
					</a>
				</li>
				<li>
					Svelte Tutorial - <a
						class="text-yellow-300"
						href="https://learn.svelte.dev"
					>
						https://learn.svelte.dev
					</a>
				</li>
				<li>
					Joy of Code - <a class="text-yellow-300" href="https://joyofcode.xyz">
						https://joyofcode.xyz
					</a>
				</li>
			</ul>
		</div>
	</Slide>
	<Slide></Slide>
</Presentation>
