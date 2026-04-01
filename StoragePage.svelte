<script lang="ts">
	import type { Auth } from "../../../lib/Auth.ts";

	import App from "../../components/App/App.svelte";
	import IconGoogleCloud from "../../components/Icons/IconGoogleCloud.svelte";
	import IconAws from "../../components/Icons/IconAws.svelte";
	import IconLockOutline from "../../components/Icons/IconLockOutline.svelte";
	import IconUsers from "../../components/Icons/IconUsers.svelte";
	import IconReport from "../../components/Icons/IconReport.svelte";
	import IconEarth from "../../components/Icons/IconEarth.svelte";

	export let auth: Auth.UserAuthInfoFront;
	export let godmode = false;

	const storageLink = "/new-bucket";

	const STORAGE_PRICING_TIERS = [
		{ label: "Base", publicPrice: 12, privatePrice: 18, discount: null },
		{ label: "50TB+", publicPrice: 10, privatePrice: 16, discount: "20% off", discountColor: "green" },
		{ label: "200TB+", publicPrice: 9, privatePrice: 14, discount: "25% off", discountColor: "green" },
		{ label: "500TB+", publicPrice: 8, privatePrice: 12, discount: "33% off", discountColor: "blue" },
	] as const;

	const STORAGE_PRICING_COMPARISON = [
		{ name: "AWS S3", price: 23 },
		{ name: "Backblaze Overdrive", price: 15 },
	] as const;
	const STORAGE_COMPARISON_MAX_PRICE = STORAGE_PRICING_COMPARISON[0].price;
</script>

<App {auth} {godmode} footerSize="big">
	<div
		class="bg-linear-to-b min-h-screen from-white via-gray-50 to-white px-4 pb-16 pt-8 dark:from-gray-950 dark:via-gray-925 dark:to-gray-950 sm:px-6 sm:pt-12 lg:px-8"
	>
		<div class="mx-auto max-w-7xl space-y-10 sm:space-y-16">
			<section
				class="shadow-xs relative flex flex-col items-center overflow-hidden text-balance rounded-3xl border border-gray-200 bg-[url('https://cdn-uploads.huggingface.co/production/uploads/5f17f0a0925b9863e28ad517/7yYe9E-d38GWl6bnEUhhG.png')] bg-cover bg-center bg-no-repeat p-8 text-center dark:border-gray-800 max-sm:py-12 sm:p-12 lg:p-16"
			>
				<h1
					class="relative mb-4 text-pretty text-5xl font-black tracking-tight text-gray-900 dark:text-white sm:text-6xl md:text-7xl"
				>
					Hugging Face
					<span class="relative inline-block">
						<span
							class="bg-linear-to-br relative from-blue-500 from-15% via-blue-500 to-sky-500 bg-clip-text font-bold text-transparent"
							style="font-weight: 800;"
						>
							Storage Buckets
						</span>
						<span
							class="bg-linear-to-br absolute left-0 from-blue-500 from-15% via-blue-500 to-sky-500 bg-clip-text font-bold text-transparent opacity-25 blur-xl"
							style="font-weight: 800;"
						>
							Storage Buckets
						</span>
					</span>
				</h1>
				<p class="relative mb-6 text-xl text-gray-600 dark:text-gray-400 sm:text-2xl md:text-3xl xl:mb-12">
					AI-native object storage designed for scale, speed, and team workflows.
				</p>
				<div class="mx-auto flex w-full flex-col items-center justify-center gap-1.5 sm:gap-3 md:flex-row">
					<a
						href={storageLink}
						class="ring-offset-3 relative z-1 flex w-fit items-center gap-1.5 whitespace-nowrap rounded-full bg-black px-5 py-2 text-white ring-1 ring-gray-300 transition-all hover:ring-black dark:bg-gray-100 dark:text-black dark:ring-gray-100 dark:ring-offset-gray-950 sm:text-lg"
						><span class="mr-1">→</span>Create a Bucket</a
					>
					<span class="text-gray-500 dark:text-gray-400">or</span>
					<a
						href="/settings/billing?add-storage=true"
						class="ring-offset-3 relative z-1 flex w-fit items-center gap-1.5 whitespace-nowrap rounded-full bg-gray-200 px-5 py-2 text-base text-gray-900 ring-1 ring-gray-300 transition-all hover:ring-gray-500 dark:bg-gray-600 dark:text-gray-300 dark:ring-gray-600 dark:ring-offset-gray-950 sm:text-lg"
						>Get a Storage package</a
					>
				</div>
			</section>
			<!-- ============================================ -->
			<!-- SECTION 2: OBJECT STORAGE TERMINAL            -->
			<!-- ============================================ -->
			<section
				class="grid overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-sm dark:border-gray-800 dark:bg-gray-900 lg:grid-cols-2"
			>
				<div class="p-8 sm:p-12 lg:p-16">
					<span
						class="text-smd mb-4 inline-block rounded-full bg-blue-100 px-4 py-1 font-semibold text-blue-700 dark:bg-blue-900/30 dark:text-blue-300"
					>
						Storage
					</span>
					<h2 class="mb-6 text-balance text-3xl font-bold text-gray-900 dark:text-white md:text-4xl">
						Storage built for AI teams
					</h2>
					<p class="mb-8 text-lg text-gray-600 dark:text-gray-400">
						Store models, datasets, and artifacts with simple per-TB pricing. Xet deduplication. Included CDN. No git
						overhead.
					</p>
					<div class="space-y-4">
						<div class="flex items-center gap-3">
							<div
								class="flex size-5 shrink-0 items-center justify-center rounded-full bg-blue-100 dark:bg-blue-900/50"
							>
								<svg
									class="size-3 text-blue-600 dark:text-blue-400"
									fill="none"
									viewBox="0 0 24 24"
									stroke="currentColor"
									stroke-width="3"
								>
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</div>
							<p class="text-sm text-gray-700 dark:text-gray-300 sm:text-base">
								Per-TB pricing with built-in CDN and deduplication speedups.
							</p>
						</div>
						<div class="flex items-center gap-3">
							<div
								class="flex size-5 shrink-0 items-center justify-center rounded-full bg-blue-100 dark:bg-blue-900/50"
							>
								<svg
									class="size-3 text-blue-600 dark:text-blue-400"
									fill="none"
									viewBox="0 0 24 24"
									stroke="currentColor"
									stroke-width="3"
								>
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</div>
							<p class="text-sm text-gray-700 dark:text-gray-300 sm:text-base">
								No Git constraints: commit-free sync and fast object updates.
							</p>
						</div>
						<div class="flex items-center gap-3">
							<div
								class="flex size-5 shrink-0 items-center justify-center rounded-full bg-blue-100 dark:bg-blue-900/50"
							>
								<svg
									class="size-3 text-blue-600 dark:text-blue-400"
									fill="none"
									viewBox="0 0 24 24"
									stroke="currentColor"
									stroke-width="3"
								>
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</div>
							<p class="text-sm text-gray-700 dark:text-gray-300 sm:text-base">
								Designed for ML workflows: datasets, checkpoints, model artifacts.
							</p>
						</div>
					</div>
				</div>
				<div
					class="bg-linear-to-br relative flex items-center justify-center overflow-hidden from-sky-50 to-blue-50 p-8 dark:from-blue-950/20 dark:to-sky-950/20 max-lg:order-first lg:rounded-l-sm lg:p-12"
				>
					<div class="w-full max-w-xl">
						<div
							class="shadow-xs overflow-hidden rounded-xl border border-gray-200 bg-white dark:border-gray-800 dark:bg-gray-900/50"
						>
							<div
								class="flex items-center gap-2 border-b border-gray-200 bg-white px-4 py-2.5 dark:border-gray-800 dark:bg-gray-900/60"
							>
								<span class="h-3 w-3 rounded-full bg-red-400"></span>
								<span class="h-3 w-3 rounded-full bg-yellow-400"></span>
								<span class="h-3 w-3 rounded-full bg-green-400"></span>
								<span class="flex-1 text-center font-mono text-xs text-gray-500 dark:text-gray-400"
									>terminal - bash</span
								>
							</div>
							<div
								class="overflow-x-auto p-4 font-mono text-[11px] leading-relaxed text-gray-700 dark:text-gray-200 sm:p-6 sm:text-[12px]"
							>
								<div class="mb-1 text-gray-500 dark:text-gray-400"># Create a storage bucket</div>
								<div class="mb-3">
									<span class="text-green-600 dark:text-green-300">$</span>
									<span class="text-gray-900 dark:text-white"> hf buckets create</span>
									<span class="text-cyan-600 dark:text-cyan-300"> acme-corp/training-data</span>
								</div>
								<div class="mb-1 pl-0 text-gray-500 dark:text-gray-400">
									<span class="text-green-600 dark:text-green-300">✓</span> Bucket created:
									<span class="text-cyan-700 dark:text-cyan-200"> hf://buckets/acme-corp/training-data</span>
								</div>
								<div class="mb-4 pl-0 text-gray-500 dark:text-gray-400">
									<span class="text-green-600 dark:text-green-300">✓</span> Visibility:
									<span class="text-gray-900 dark:text-white">private</span> · Region:
									<span class="text-gray-900 dark:text-white">us-east-1</span>
								</div>
								<div class="mb-1 text-gray-500 dark:text-gray-400"># Sync training data to the bucket</div>
								<div class="mb-3">
									<span class="text-green-600 dark:text-green-300">$</span>
									<span class="text-gray-900 dark:text-white"> hf sync</span>
									<span class="text-yellow-600 dark:text-yellow-300"> ./checkpoints/</span>
									<span class="text-cyan-600 dark:text-cyan-300"> hf://buckets/acme-corp/training-data</span>
								</div>
								<div class="mb-0.5 text-gray-500 dark:text-gray-400">
									Scanning local files...
									<span class="text-gray-900 dark:text-white">12,847 files</span> (<span
										class="text-gray-900 dark:text-white">2.4 TB</span
									>)
								</div>
								<div class="mb-0.5 text-gray-500 dark:text-gray-400">
									Xet dedup:
									<span class="text-green-600 dark:text-green-300">62% deduplicated</span> : uploading
									<span class="text-gray-900 dark:text-white">912 GB</span> (saved 1.5 TB)
								</div>
								<div class="mb-1">
									<span class="text-green-600 dark:text-green-300"
										>&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;</span
									><span class="text-gray-300 dark:text-gray-600">&#9608;&#9608;&#9608;&#9608;&#9608;</span>
									<span class="text-gray-900 dark:text-white"> 78%</span>
									<span class="text-gray-500 dark:text-gray-400"> 714/912 GB · 2.1 GB/s · ETA 1m 34s</span>
								</div>
							</div>
						</div>
					</div>
				</div>
			</section>
			<!-- ============================================ -->
			<!-- SECTION 3: Xet Dedup Deep-Dive              -->
			<!-- ============================================ -->
			<section
				class="relative z-10 grid overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-md dark:border-gray-800 dark:bg-gray-900 lg:grid-cols-2"
			>
				<div class="p-8 sm:p-12 lg:p-16">
					<span
						class="text-smd mb-4 inline-block rounded-full bg-pink-100 px-4 py-1 font-semibold text-pink-700 dark:bg-pink-900/30 dark:text-pink-400"
					>
						Xet Technology
					</span>
					<h2 class="mb-6 text-balance text-3xl font-bold text-gray-900 dark:text-white md:text-4xl">
						Next-gen large-scale storage for AI
					</h2>
					<p class="mb-8 text-lg text-gray-600 dark:text-gray-400">
						Xet uses content-defined chunking to break files into byte-level chunks and deduplicates across your entire
						bucket. When you retrain a model and only 5% of weights change, only that 5% is re-uploaded.
					</p>

					<!-- Benefits list -->
					<div class="space-y-4">
						<div class="flex items-center gap-3">
							<div
								class="flex size-5 shrink-0 items-center justify-center rounded-full bg-pink-100 dark:bg-pink-900/50"
							>
								<svg
									class="size-3 text-pink-600 dark:text-pink-400"
									fill="none"
									viewBox="0 0 24 24"
									stroke="currentColor"
									stroke-width="3"><path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" /></svg
								>
							</div>
							<p class="text-sm text-gray-700 dark:text-gray-300 sm:text-base">
								Raw + processed dataset: stored once, billed once*
							</p>
						</div>
						<div class="flex items-center gap-3">
							<div
								class="flex size-5 shrink-0 items-center justify-center rounded-full bg-pink-100 dark:bg-pink-900/50"
							>
								<svg
									class="size-3 text-pink-600 dark:text-pink-400"
									fill="none"
									viewBox="0 0 24 24"
									stroke="currentColor"
									stroke-width="3"><path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" /></svg
								>
							</div>
							<p class="text-sm text-gray-700 dark:text-gray-300 sm:text-base">
								4x less data per upload, verified with real-world workloads
							</p>
						</div>
					</div>
					<p class="mt-4 text-xs text-gray-400 dark:text-gray-500">
						*Requires <a
							href="/enterprise"
							class="underline underline-offset-2 hover:text-gray-600 dark:hover:text-gray-300"
							>Enterprise or Enterprise Plus</a
						> plan
					</p>
				</div>

				<!-- Dedup visual (right column) - mimics Pro page comparison card -->
				<div
					class="dark:to-purple-950/20 bg-linear-to-br relative flex items-center justify-center overflow-hidden from-pink-50 to-purple-50 p-8 dark:from-pink-950/20 max-lg:order-first max-lg:pb-16 lg:rounded-l-sm lg:p-12"
				>
					<div class="w-full max-w-md space-y-4">
						<!-- Traditional upload -->
						<div class="shadow-xs rounded-xl bg-white p-5 dark:border-gray-800 dark:bg-gray-900">
							<p class="mb-3 text-xs font-semibold uppercase tracking-wider text-gray-500 dark:text-gray-400">
								Traditional S3 Upload
							</p>
							<div class="mb-2 flex gap-1">
								<div class="h-6 flex-1 rounded bg-amber-200 dark:bg-amber-900/35"></div>
								<div class="h-6 flex-1 rounded bg-amber-200 dark:bg-amber-900/35"></div>
								<div class="h-6 flex-1 rounded bg-amber-200 dark:bg-amber-900/35"></div>
								<div class="h-6 flex-1 rounded bg-amber-300 dark:bg-amber-800/45"></div>
								<div class="h-6 flex-1 rounded bg-amber-200 dark:bg-amber-900/35"></div>
								<div class="h-6 flex-1 rounded bg-amber-200 dark:bg-amber-900/35"></div>
								<div class="h-6 flex-1 rounded bg-amber-200 dark:bg-amber-900/35"></div>
								<div class="h-6 flex-1 rounded bg-amber-200 dark:bg-amber-900/35"></div>
							</div>
							<p class="text-right font-mono text-sm text-amber-600 dark:text-amber-300">8 / 8 chunks uploaded</p>
						</div>

						<!-- Separator -->
						<div class="flex items-center justify-center text-sm font-medium text-gray-400">VS</div>

						<!-- Xet upload -->
						<div
							class="shadow-xs rounded-xl border-2 border-indigo-200 bg-white p-5 dark:border-indigo-500/20 dark:bg-gray-900"
						>
							<p class="mb-3 text-xs font-semibold uppercase tracking-wider text-gray-500 dark:text-gray-400">
								<span
									class="dark:to-purple-900/50 bg-linear-to-br mr-2 inline-block rounded-md from-indigo-100 to-purple-100 px-2 py-0.5 text-xs font-bold uppercase text-indigo-700 dark:from-indigo-900/50 dark:text-indigo-300"
									>XET</span
								>
								Deduplicated Upload
							</p>
							<div class="mb-2 flex gap-1">
								<div class="h-6 flex-1 rounded bg-gray-100 dark:bg-gray-700"></div>
								<div class="h-6 flex-1 rounded bg-gray-100 dark:bg-gray-700"></div>
								<div class="h-6 flex-1 rounded bg-gray-100 dark:bg-gray-700"></div>
								<div class="dedup-highlight h-6 flex-1 rounded bg-indigo-400 dark:bg-indigo-500"></div>
								<div class="h-6 flex-1 rounded bg-gray-100 dark:bg-gray-700"></div>
								<div class="h-6 flex-1 rounded bg-gray-100 dark:bg-gray-700"></div>
								<div class="h-6 flex-1 rounded bg-gray-100 dark:bg-gray-700"></div>
								<div class="h-6 flex-1 rounded bg-gray-100 dark:bg-gray-700"></div>
							</div>
							<p class="text-right font-mono text-sm font-medium text-indigo-600 dark:text-indigo-400">
								1 / 8 chunks uploaded
							</p>
						</div>

						<!-- Annotation -->
						<p class="text-center text-sm text-gray-500 dark:text-gray-400">
							Gray = already stored &middot; Purple = only the changed chunk
						</p>
					</div>
				</div>
			</section>
			<!-- ===================== PRICING ===================== -->
			<section
				class="grid overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-sm dark:border-gray-800 dark:bg-gray-900 lg:grid-cols-2"
			>
				<div class="p-8 sm:p-12 lg:p-16">
					<span
						class="text-smd mb-4 inline-block rounded-full bg-sky-100 px-4 py-1 font-semibold text-sky-700 dark:bg-sky-900/30 dark:text-sky-400"
					>
						Pricing
					</span>
					<h2 class="mb-6 text-balance text-3xl font-bold text-gray-900 dark:text-white md:text-4xl">
						Transparent, volume-based pricing
					</h2>
					<p class="mb-8 text-lg text-gray-600 dark:text-gray-400">
						Simple per-TB pricing that scales with usage. Egress and CDN are included at no extra cost.
					</p>

					<!-- Comparison bars -->
					<div class="space-y-2">
						{#each STORAGE_PRICING_COMPARISON as competitor}
							<div class="flex items-center gap-4">
								<div class="w-32 shrink-0 text-sm text-gray-600 dark:text-gray-400">{competitor.name}</div>
								<div class="relative h-2.5 flex-1 overflow-hidden rounded-full bg-gray-100 dark:bg-gray-900">
									<div
										class="absolute inset-y-0 left-0 rounded-full bg-gray-300 dark:bg-gray-600"
										style="width: {(competitor.price / STORAGE_COMPARISON_MAX_PRICE) * 100}%"
									></div>
								</div>
								<div class="w-12 shrink-0 text-right text-sm font-semibold text-gray-500">${competitor.price}</div>
							</div>
						{/each}

						<div class="flex items-center gap-4">
							<div class="w-32 shrink-0 text-sm font-medium text-blue-600 dark:text-blue-400">HF Hub</div>
							<div class="relative h-2.5 flex-1 overflow-hidden rounded-full bg-blue-100 dark:bg-blue-900/30">
								<div
									class="absolute inset-y-0 left-0 rounded-full bg-blue-200/50 dark:bg-blue-800/50"
									style="width: {(STORAGE_PRICING_TIERS[0].publicPrice / STORAGE_COMPARISON_MAX_PRICE) * 100}%"
								></div>
								<div
									class="bg-linear-to-r absolute inset-y-0 left-0 rounded-full from-blue-500 to-blue-400"
									style="width: {(STORAGE_PRICING_TIERS[STORAGE_PRICING_TIERS.length - 1].publicPrice
										/ STORAGE_COMPARISON_MAX_PRICE)
										* 100}%"
								></div>
							</div>
							<div class="w-12 shrink-0 text-right text-sm font-bold text-blue-600 dark:text-blue-400">
								${STORAGE_PRICING_TIERS[STORAGE_PRICING_TIERS.length - 1].publicPrice}–{STORAGE_PRICING_TIERS[0]
									.publicPrice}
							</div>
						</div>
					</div>
				</div>

				<!-- Pricing tiers (right column) -->
				<div
					class="bg-linear-to-br flex items-center justify-center from-sky-50 to-cyan-50 p-8 dark:from-sky-950/20 dark:to-cyan-950/20 max-lg:order-first lg:rounded-l-sm lg:p-12"
				>
					<div class="grid w-full max-w-lg grid-cols-2 gap-3">
						{#each STORAGE_PRICING_TIERS as tier}
							<div class="rounded-xl border border-gray-200 bg-white px-4 py-3 dark:border-gray-800 dark:bg-gray-900">
								<div class="mb-2 flex items-center gap-2">
									<span class="text-sm font-medium text-gray-500">{tier.label}</span>
									{#if tier.discount}
										<span
											class="rounded-full px-2 py-0.5 text-xs font-semibold {tier.discountColor === 'blue'
												? 'bg-blue-100 text-blue-700 dark:bg-blue-900/50 dark:text-blue-400'
												: 'dark:bg-green-900/50 bg-green-100 text-green-700 dark:text-green-400'}">{tier.discount}</span
										>
									{/if}
								</div>
								<div class="mb-0.5 flex items-baseline gap-1">
									<span class="text-2xl font-bold text-gray-900 dark:text-white">${tier.publicPrice}</span>
									<span class="text-sm text-gray-500">/TB/mo</span>
								</div>
								<div class="text-xs text-gray-400">Public repositories</div>
								<div class="mt-3 border-t border-gray-100 pt-2 dark:border-gray-800">
									<div class="flex items-baseline gap-1">
										<span class="text-base font-semibold text-gray-700 dark:text-gray-300">${tier.privatePrice}</span>
										<span class="text-sm text-gray-400">/TB/mo</span>
									</div>
									<div class="text-xs text-gray-400">Private repositories</div>
								</div>
							</div>
						{/each}
					</div>
				</div>
			</section>

			<!-- ============================================================ -->
			<!-- USE CASE 1: Training Data (text left, visual right) -->
			<!-- ============================================================ -->
			<section
				class="grid overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-sm dark:border-gray-800 dark:bg-gray-900 lg:grid-cols-2"
			>
				<div class="p-8 sm:p-12 lg:p-16">
					<span
						class="text-smd mb-4 inline-block rounded-full bg-amber-100 px-4 py-1 font-semibold text-amber-700 dark:bg-amber-900/30 dark:text-amber-300"
					>
						Data Storage
					</span>
					<h2 class="mb-6 text-balance text-3xl font-bold text-gray-900 dark:text-white md:text-4xl">
						Assemble training data at any scale
					</h2>
					<p class="text-lg text-gray-600 dark:text-gray-400">
						Pour raw data from every source into a single bucket: crawls, annotations, synthetic outputs, partner
						datasets. No git overhead, no commit queues, no file-count limits. When training begins, your data is
						already there, streamed to GPUs via the included CDN.
					</p>
					<ul class="mt-6 space-y-3 text-gray-600 dark:text-gray-400">
						<li class="flex items-center gap-3">
							<span
								class="flex size-5 flex-none items-center justify-center rounded-full bg-amber-100 text-amber-600 dark:bg-amber-900/40 dark:text-amber-400"
							>
								<svg class="size-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</span>
							<p class="text-sm sm:text-base">Immediate availability on upload, no queued commits</p>
						</li>
						<li class="flex items-center gap-3">
							<span
								class="flex size-5 flex-none items-center justify-center rounded-full bg-amber-100 text-amber-600 dark:bg-amber-900/40 dark:text-amber-400"
							>
								<svg class="size-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</span>
							<p class="text-sm sm:text-base">Batch API processes thousands of files in a single call</p>
						</li>
						<li class="flex items-center gap-3">
							<span
								class="flex size-5 flex-none items-center justify-center rounded-full bg-amber-100 text-amber-600 dark:bg-amber-900/40 dark:text-amber-400"
							>
								<svg class="size-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</span>
							<p class="text-sm sm:text-base">Raw + processed datasets with dedup = no double billing*</p>
						</li>
					</ul>
					<p class="mt-4 text-xs text-gray-400 dark:text-gray-500">
						*Requires <a
							href="/enterprise"
							class="underline underline-offset-2 hover:text-gray-600 dark:hover:text-gray-300"
							>Enterprise or Enterprise Plus</a
						> plan
					</p>
				</div>
				<!-- Visual: Bucket filling diagram -->
				<div
					class="bg-linear-to-br relative flex items-center justify-center from-amber-50 to-orange-50 p-8 dark:from-amber-950/20 dark:to-orange-950/20 max-lg:order-first lg:rounded-l-sm lg:p-12"
				>
					<div class="w-full max-w-lg space-y-3">
						<!-- Simulated files flowing in -->
						<div
							class="rounded-lg border border-amber-200/60 bg-white/80 px-4 py-3 dark:border-amber-800/20 dark:bg-gray-900/80"
						>
							<div class="flex items-center gap-3">
								<div
									class="flex h-8 w-8 items-center justify-center rounded-lg bg-amber-100 text-amber-600 dark:bg-amber-900/40 dark:text-amber-400"
								>
									<svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
										<path
											stroke-linecap="round"
											stroke-linejoin="round"
											d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"
										/>
									</svg>
								</div>
								<div class="min-w-0 flex-1">
									<p class="truncate text-sm font-medium text-gray-900 dark:text-white">crawl-2026-jan/</p>
									<p class="text-xs text-gray-500 dark:text-gray-400">48 TB &middot; 2.1M files</p>
								</div>
								<span
									class="dark:bg-green-900/30 rounded-full bg-green-100 px-2 py-0.5 text-xs font-medium text-green-700 dark:text-green-400"
									>synced</span
								>
							</div>
						</div>
						<div
							class="rounded-lg border border-amber-200/60 bg-white/80 px-4 py-3 dark:border-amber-800/20 dark:bg-gray-900/80"
						>
							<div class="flex items-center gap-3">
								<div
									class="flex h-8 w-8 items-center justify-center rounded-lg bg-amber-100 text-amber-600 dark:bg-amber-900/40 dark:text-amber-400"
								>
									<svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
										<path
											stroke-linecap="round"
											stroke-linejoin="round"
											d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"
										/>
									</svg>
								</div>
								<div class="min-w-0 flex-1">
									<p class="truncate text-sm font-medium text-gray-900 dark:text-white">annotations-v3/</p>
									<p class="text-xs text-gray-500 dark:text-gray-400">12 TB &middot; 890K files</p>
								</div>
								<span
									class="dark:bg-green-900/30 rounded-full bg-green-100 px-2 py-0.5 text-xs font-medium text-green-700 dark:text-green-400"
									>synced</span
								>
							</div>
						</div>
						<div
							class="rounded-lg border border-amber-200/60 bg-white/80 px-4 py-3 dark:border-amber-800/20 dark:bg-gray-900/80"
						>
							<div class="flex items-center gap-3">
								<div
									class="flex h-8 w-8 items-center justify-center rounded-lg bg-blue-100 text-blue-600 dark:bg-blue-900/40 dark:text-blue-400"
								>
									<svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
										<path
											stroke-linecap="round"
											stroke-linejoin="round"
											d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"
										/>
									</svg>
								</div>
								<div class="min-w-0 flex-1">
									<p class="truncate text-sm font-medium text-gray-900 dark:text-white">synthetic-pairs/</p>
									<p class="text-xs text-gray-500 dark:text-gray-400">6 TB &middot; 340K files</p>
								</div>
								<div class="flex items-center gap-2">
									<div class="h-1.5 w-16 rounded-full bg-gray-200 dark:bg-gray-700">
										<div class="h-full w-3/4 rounded-full bg-blue-500"></div>
									</div>
									<span class="text-xs font-medium text-blue-600 dark:text-blue-400">75%</span>
								</div>
							</div>
						</div>
						<!-- Dedup savings callout -->
						<div
							class="bg-green-50/80 dark:bg-green-950/30 mt-4 rounded-xl border border-dashed border-green-300 px-4 py-3 dark:border-green-800"
						>
							<div class="flex items-center gap-2">
								<svg
									class="h-4 w-4 text-green-600 dark:text-green-400"
									fill="none"
									viewBox="0 0 24 24"
									stroke="currentColor"
									stroke-width="2"
								>
									<path stroke-linecap="round" stroke-linejoin="round" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" />
								</svg>
								<p class="text-sm font-medium text-green-700 dark:text-green-300">
									Xet dedup: 66 TB stored → billed for 41 TB*
								</p>
							</div>
						</div>
					</div>
				</div>
			</section>

			<!-- ============================================================ -->
			<!-- USE CASE 4: CDN & Pre-warming -->
			<!-- ============================================================ -->
			<section
				class="grid overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-sm dark:border-gray-800 dark:bg-gray-900 lg:grid-cols-2"
			>
				<div class="p-8 sm:p-12 lg:p-16">
					<span
						class="text-smd mb-4 inline-block rounded-full bg-teal-100 px-4 py-1 font-semibold text-teal-700 dark:bg-teal-900/30 dark:text-teal-300"
					>
						CDN
					</span>
					<h2 class="mb-6 text-balance text-3xl font-bold text-gray-900 dark:text-white md:text-4xl">
						Built-in CDN for blazing fast access
					</h2>
					<p class="text-lg text-gray-600 dark:text-gray-400">
						Every bucket includes a CDN. Warm localized cache close to where you compute for ultra fast streaming and
						downloads. Egress is included up to a generous 8:1 ratio of your total storage.
					</p>
					<ul class="mt-6 space-y-3 text-gray-600 dark:text-gray-400">
						<li class="flex items-center gap-3">
							<span
								class="flex size-5 flex-none items-center justify-center rounded-full bg-teal-100 text-teal-600 dark:bg-teal-900/40 dark:text-teal-400"
							>
								<svg class="size-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</span>
							<p class="text-sm sm:text-base">Pre-warm cache in any cloud region you need</p>
						</li>
						<li class="flex items-center gap-3">
							<span
								class="flex size-5 flex-none items-center justify-center rounded-full bg-teal-100 text-teal-600 dark:bg-teal-900/40 dark:text-teal-400"
							>
								<svg class="size-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</span>
							<p class="text-sm sm:text-base">Our CDN is deployed inside GCP and AWS networks</p>
						</li>
						<li class="flex items-center gap-3">
							<span
								class="flex size-5 flex-none items-center justify-center rounded-full bg-teal-100 text-teal-600 dark:bg-teal-900/40 dark:text-teal-400"
							>
								<svg class="size-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</span>
							<p class="text-sm sm:text-base">Egress included up to 8:1 your storage</p>
						</li>
					</ul>
					<div class="mt-6 flex items-center gap-3 text-sm text-gray-500 dark:text-gray-400">
						<IconGoogleCloud classNames="text-3xl" />
						<IconAws classNames="text-3xl" />
						<span class="text-sm">More providers coming soon</span>
					</div>
				</div>
				<div
					class="bg-linear-to-br relative flex items-center justify-center from-teal-50 to-emerald-50 p-8 dark:from-teal-950/20 dark:to-emerald-950/20 max-lg:order-first lg:rounded-l-sm lg:p-12"
				>
					<div class="flex items-center justify-center">
						<svg
							viewBox="0 0 400 400"
							class="sm:size-92 size-72 drop-shadow-xl"
							fill="none"
							xmlns="http://www.w3.org/2000/svg"
						>
							<defs>
								<!-- Holographic 3D Shading for the sphere -->
								<radialGradient id="globe-shading" cx="30%" cy="30%" r="70%">
									<stop offset="0%" stop-color="#fff" stop-opacity="0.08" />
									<stop offset="35%" stop-color="#fff" stop-opacity="0" />
									<stop offset="70%" stop-color="#000" stop-opacity="0.15" />
									<stop offset="100%" stop-color="#000" stop-opacity="0.4" />
								</radialGradient>

								<filter id="glow-intense" x="-50%" y="-50%" width="200%" height="200%">
									<feGaussianBlur stdDeviation="4" result="blur" />
									<feComposite in="SourceGraphic" in2="blur" operator="over" />
								</filter>
								<filter id="glow-soft" x="-30%" y="-30%" width="160%" height="160%">
									<feGaussianBlur stdDeviation="15" result="blur" />
									<feComposite in="SourceGraphic" in2="blur" operator="over" />
								</filter>
							</defs>

							<!-- Outer Atmospheric Glow -->
							<circle
								cx="200"
								cy="200"
								r="160"
								fill="currentColor"
								class="text-teal-400/20 dark:text-teal-500/10"
								filter="url(#glow-soft)"
							/>

							<!-- Orbit Ring 1 (Back Half) -->
							<g transform="rotate(-15 200 200)">
								<path
									d="M 10 200 A 190 60 0 0 1 390 200"
									stroke="currentColor"
									class="text-teal-400/30 dark:text-teal-600/30"
									stroke-width="1.5"
								/>
							</g>
							<!-- Orbit Ring 2 (Back Half) -->
							<g transform="rotate(45 200 200)" />

							<!-- Solid Base Sphere (Blocks back elements) -->
							<circle cx="200" cy="200" r="150" fill="currentColor" class="text-teal-50 dark:text-[#061926]" />

							<!-- Back Graticules (Visible through the glass sphere effect) -->
							<g stroke="currentColor" class="text-teal-700/10 dark:text-teal-300/10" stroke-width="1">
								<path d="M 50 200 A 150 45 0 0 1 350 200" />
								<path d="M 73 120 A 127 35 0 0 1 327 120" />
								<path d="M 73 280 A 127 35 0 0 1 327 280" />
								<!-- Vertical lines mapped as ellipses -->
								<path d="M 200 50 L 200 350" />
								<path d="M 200 50 A 50 150 0 0 1 200 350" />
								<path d="M 200 50 A 100 150 0 0 1 200 350" />
							</g>

							<!-- 3D Shading Overlay (light mode only) -->
							<circle cx="200" cy="200" r="150" fill="url(#globe-shading)" class="dark:hidden" />

							<!-- Front Graticules (Lat/Lon) -->
							<g stroke="currentColor" class="text-teal-600/40 dark:text-teal-400/30" stroke-width="1.5">
								<path d="M 50 200 A 150 45 0 0 0 350 200" />
								<path d="M 73 120 A 127 35 0 0 0 327 120" />
								<path d="M 73 280 A 127 35 0 0 0 327 280" />
								<path d="M 200 50 A 50 150 0 0 0 200 350" />
								<path d="M 200 50 A 100 150 0 0 0 200 350" />
								<path d="M 200 50 A 148 150 0 0 0 200 350" />
								<!-- Edge curve -->
								<path d="M 200 50 A 148 150 0 0 1 200 350" />
								<!-- Right Edge curve -->
							</g>

							<!-- Orbit Ring 1 (Front Half) -->
							<g transform="rotate(-15 200 200)">
								<path
									d="M 10 200 A 190 60 0 0 0 390 200"
									stroke="currentColor"
									class="text-teal-500/60 dark:text-teal-400/50"
									stroke-width="2"
								/>
								<!-- Comet flying on the front half -->
							</g>
							<!-- Orbit Ring 2 (Front Half) -->
							<g transform="rotate(45 200 200)" />

							<!-- Surface Drop Shadows for Floating Nodes -->
							<g fill="currentColor" class="text-teal-900/20 dark:text-black/60" filter="url(#glow-soft)">
								<ellipse cx="110" cy="140" rx="12" ry="4" />
								<ellipse cx="240" cy="110" rx="12" ry="4" />
								<ellipse cx="310" cy="180" rx="12" ry="4" />
								<ellipse cx="160" cy="260" rx="12" ry="4" />
							</g>

							<!-- High Arcing Data Connections (Floating in 3D Space) -->
							<g fill="none" stroke-width="2.5" stroke-linecap="round">
								<!-- US to EU -->
								<path
									d="M 110 130 C 120 70, 210 60, 240 100"
									stroke="currentColor"
									class="text-teal-400/30 dark:text-teal-600/50"
								/>

								<!-- EU to Asia -->
								<path
									d="M 240 100 C 280 80, 315 120, 310 170"
									stroke="currentColor"
									class="text-teal-400/30 dark:text-teal-600/50"
								/>

								<!-- US to SA -->
								<path
									d="M 110 130 C 70 170, 100 240, 160 250"
									stroke="currentColor"
									class="text-teal-400/30 dark:text-teal-600/50"
								/>
							</g>

							<!-- Moving Data Packets (Glowing Orbs on Arcs) -->

							<!-- Floating Edge Nodes -->
							<!-- US East -->
							<g class="node-float" style="animation-delay: 0s">
								<g transform="translate(110, 130)">
									<circle
										cx="0"
										cy="0"
										r="8"
										fill="currentColor"
										class="text-teal-400 dark:text-teal-500"
										filter="url(#glow-intense)"
									/>
									<circle cx="0" cy="0" r="4" fill="#fff" class="dark:fill-teal-100" />
									<circle cx="0" cy="0" r="2" fill="currentColor" class="text-teal-500 dark:text-teal-400" />
									<rect
										x="-32"
										y="-40"
										width="64"
										height="18"
										rx="4"
										fill="currentColor"
										class="text-white/90 dark:text-gray-900/90"
									/>
									<text
										x="0"
										y="-28"
										text-anchor="middle"
										font-size="9"
										font-weight="800"
										font-family="monospace"
										fill="currentColor"
										class="text-teal-800 dark:text-teal-300">US-EAST</text
									>
								</g>
							</g>

							<!-- EU West -->
							<g class="node-float" style="animation-delay: 0.5s">
								<g transform="translate(240, 100)">
									<circle
										cx="0"
										cy="0"
										r="8"
										fill="currentColor"
										class="text-teal-400 dark:text-teal-500"
										filter="url(#glow-intense)"
									/>
									<circle cx="0" cy="0" r="4" fill="#fff" class="dark:fill-teal-100" />
									<circle cx="0" cy="0" r="2" fill="currentColor" class="text-teal-500 dark:text-teal-400" />
									<rect
										x="-32"
										y="-40"
										width="64"
										height="18"
										rx="4"
										fill="currentColor"
										class="text-white/90 dark:text-gray-900/90"
									/>
									<text
										x="0"
										y="-28"
										text-anchor="middle"
										font-size="9"
										font-weight="800"
										font-family="monospace"
										fill="currentColor"
										class="text-teal-800 dark:text-teal-300">EU-WEST</text
									>
								</g>
							</g>

							<!-- Asia -->
							<g class="node-float" style="animation-delay: 1s">
								<g transform="translate(310, 170)">
									<circle
										cx="0"
										cy="0"
										r="8"
										fill="currentColor"
										class="text-teal-400 dark:text-teal-500"
										filter="url(#glow-intense)"
									/>
									<circle cx="0" cy="0" r="4" fill="#fff" class="dark:fill-teal-100" />
									<circle cx="0" cy="0" r="2" fill="currentColor" class="text-teal-500 dark:text-teal-400" />
									<rect
										x="-24"
										y="22"
										width="48"
										height="18"
										rx="4"
										fill="currentColor"
										class="text-white/90 dark:text-gray-900/90"
									/>
									<text
										x="0"
										y="34"
										text-anchor="middle"
										font-size="9"
										font-weight="800"
										font-family="monospace"
										fill="currentColor"
										class="text-teal-800 dark:text-teal-300">ASIA</text
									>
								</g>
							</g>

							<!-- SA East -->
							<g class="node-float" style="animation-delay: 1.5s">
								<g transform="translate(160, 250)">
									<circle
										cx="0"
										cy="0"
										r="8"
										fill="currentColor"
										class="text-teal-400 dark:text-teal-500"
										filter="url(#glow-intense)"
									/>
									<circle cx="0" cy="0" r="4" fill="#fff" class="dark:fill-teal-100" />
									<circle cx="0" cy="0" r="2" fill="currentColor" class="text-teal-500 dark:text-teal-400" />
									<rect
										x="-32"
										y="22"
										width="64"
										height="18"
										rx="4"
										fill="currentColor"
										class="text-white/90 dark:text-gray-900/90"
									/>
									<text
										x="0"
										y="34"
										text-anchor="middle"
										font-size="9"
										font-weight="800"
										font-family="monospace"
										fill="currentColor"
										class="text-teal-800 dark:text-teal-300">SA-EAST</text
									>
								</g>
							</g>
						</svg>
					</div>
				</div>
			</section>

			<!-- ============================================================ -->
			<!-- USE CASE 2: Coding Agents (text left, terminal right) -->
			<!-- ============================================================ -->
			<section
				class="grid overflow-hidden rounded-3xl border border-gray-200 bg-white shadow-sm dark:border-gray-800 dark:bg-gray-900 lg:grid-cols-2"
			>
				<div class="p-8 sm:p-12 lg:p-16">
					<span
						class="text-smd mb-4 inline-block rounded-full bg-violet-100 px-4 py-1 font-semibold text-violet-700 dark:bg-violet-900/30 dark:text-violet-300"
					>
						Coding Agents
					</span>
					<h2 class="mb-6 text-balance text-3xl font-bold text-gray-900 dark:text-white md:text-4xl">
						Give your coding agents persistent storage
					</h2>
					<p class="text-lg text-gray-600 dark:text-gray-400">
						Coding agents run in ephemeral environments, but their outputs shouldn't vanish. Checkpoints, benchmark
						results, generated datasets: one <code
							class="rounded bg-gray-100 px-1.5 py-0.5 font-mono text-sm dark:bg-gray-900">hf sync</code
						> command in your agent's bash tool is all it takes.
					</p>
					<ul class="mt-6 space-y-3 text-gray-600 dark:text-gray-400">
						<li class="flex items-center gap-3">
							<span
								class="flex size-5 flex-none items-center justify-center rounded-full bg-violet-100 text-violet-600 dark:bg-violet-900/40 dark:text-violet-400"
							>
								<svg class="size-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</span>
							<p class="text-sm sm:text-base">Pre-warmed CDN and no git overhead for fast reads and writes</p>
						</li>
						<li class="flex items-center gap-3">
							<span
								class="flex size-5 flex-none items-center justify-center rounded-full bg-violet-100 text-violet-600 dark:bg-violet-900/40 dark:text-violet-400"
							>
								<svg class="size-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</span>
							<p class="text-sm sm:text-base">Persist artifacts across ephemeral CI runs and terminal sessions</p>
						</li>
						<li class="flex items-center gap-3">
							<span
								class="flex size-5 flex-none items-center justify-center rounded-full bg-violet-100 text-violet-600 dark:bg-violet-900/40 dark:text-violet-400"
							>
								<svg class="size-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
									<path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
								</svg>
							</span>
							<p class="text-sm sm:text-base">
								Install the official <a
									href="https://huggingface.co/docs/hub/en/agents-cli"
									class="underline hover:text-violet-600 dark:hover:text-violet-300">HF CLI skill</a
								> and your agent knows every command
							</p>
						</li>
					</ul>
				</div>
				<div
					class="bg-linear-to-br relative flex items-center justify-center from-violet-50 to-indigo-50 p-8 dark:from-violet-950/20 dark:to-indigo-950/20 max-lg:order-first lg:rounded-l-sm lg:p-12"
				>
					<div class="w-full max-w-xl">
						<div
							class="shadow-xs overflow-hidden rounded-xl border border-gray-200 bg-white dark:border-gray-800 dark:bg-gray-900/50"
						>
							<div
								class="flex items-center gap-2 border-b border-gray-200 bg-white px-4 py-2.5 dark:border-gray-800 dark:bg-gray-900/60"
							>
								<span class="h-3 w-3 rounded-full bg-red-400"></span>
								<span class="h-3 w-3 rounded-full bg-yellow-400"></span>
								<span class="h-3 w-3 rounded-full bg-green-400"></span>
								<span class="flex-1 text-center font-mono text-xs text-gray-500 dark:text-gray-400"
									>terminal - bash</span
								>
							</div>
							<div
								class="overflow-x-auto p-4 font-mono text-[11px] leading-relaxed text-gray-700 dark:text-gray-200 sm:p-6 sm:text-[12px]"
							>
								<div class="mb-3 text-gray-500 dark:text-gray-400">
									# Agent creates a bucket and syncs experiment outputs
								</div>

								<div class="mb-1">
									<span class="text-green-600 dark:text-green-300">&#9679;</span>
									<span class="font-semibold text-gray-900 dark:text-white"> Bash(</span><span
										class="text-gray-900 dark:text-white">hf buckets create training-artifacts-v2</span
									><span class="font-semibold text-gray-900 dark:text-white">)</span>
								</div>
								<div class="mb-4 pl-3 text-gray-500 dark:text-gray-400">
									&#9492; Bucket created: <span class="text-violet-700 dark:text-violet-300"
										>hf://buckets/acme/training-artifacts-v2</span
									>
								</div>

								<div class="mb-1">
									<span class="text-green-600 dark:text-green-300">&#9679;</span>
									<span class="font-semibold text-gray-900 dark:text-white"> Bash(</span><span
										class="text-gray-900 dark:text-white"
										>hf buckets sync ./experiment_outputs/ hf://buckets/acme/training-artifacts-v2</span
									><span class="font-semibold text-gray-900 dark:text-white">)</span>
								</div>
								<div class="mb-0.5 pl-3 text-gray-500 dark:text-gray-400">
									&#9492; Sync plan: ./experiment_outputs/ &#8594; <span class="text-violet-700 dark:text-violet-300"
										>hf://buckets/acme/training-artifacts-v2</span
									>
								</div>
								<div class="mb-0.5 pl-7 text-gray-500 dark:text-gray-400">
									Uploads: <span class="text-gray-900 dark:text-white">16</span>
								</div>
								<div class="mb-4 pl-7 text-gray-500 dark:text-gray-400">
									Downloads: <span class="text-gray-900 dark:text-white">0</span>
								</div>

								<div class="mb-1">
									<span class="text-green-600 dark:text-green-300">&#9679;</span>
									<span class="text-gray-900 dark:text-white"> All done.</span>
									<span class="text-gray-500 dark:text-gray-400">
										Bucket acme/training-artifacts-v2 synced (14.3 GB total):</span
									>
								</div>
								<div class="mb-0.5 pl-3 text-gray-500 dark:text-gray-400">
									- 3 checkpoints (model.safetensors, optimizer.pt, config.json)
								</div>
								<div class="mb-0.5 pl-3 text-gray-500 dark:text-gray-400">
									- 6 parquet shards (data/train/ and data/eval/)
								</div>
								<div class="mb-3 pl-3 text-gray-500 dark:text-gray-400">- 1 training log</div>

								<div class="text-gray-500 dark:text-gray-400">
									Bucket is live at <span class="text-violet-700 dark:text-violet-300"
										>hf://buckets/acme/training-artifacts-v2</span
									>
								</div>
							</div>
						</div>
					</div>
				</div>
			</section>

			<!-- ============================================================ -->
			<!-- Security & Compliance — dark trust bar                       -->
			<!-- ============================================================ -->
			<section
				class="overflow-hidden rounded-3xl border border-gray-200 bg-white px-6 py-8 shadow-sm dark:border-gray-800 dark:bg-gray-950 dark:ring-1 dark:ring-gray-800 sm:px-10 sm:py-10"
			>
				<p class="mb-6 text-center text-sm font-medium uppercase tracking-widest text-gray-500 dark:text-gray-400">
					Security & Compliance
				</p>
				<div class="flex flex-wrap items-center justify-center gap-x-8 gap-y-4 sm:gap-x-10">
					<div class="flex items-center gap-2.5">
						<IconLockOutline classNames="size-5 flex-none text-emerald-600 dark:text-emerald-400" />
						<span class="whitespace-nowrap text-sm font-medium text-gray-700 dark:text-gray-200"
							>AES-256 encryption</span
						>
					</div>
					<span class="hidden h-5 w-px bg-gray-200 dark:bg-gray-700 sm:block"></span>
					<div class="flex items-center gap-2.5">
						<IconUsers classNames="size-5 flex-none text-blue-600 dark:text-blue-400" />
						<span class="whitespace-nowrap text-sm font-medium text-gray-700 dark:text-gray-200">SSO & RBAC</span>
					</div>
					<span class="hidden h-5 w-px bg-gray-200 dark:bg-gray-700 sm:block"></span>
					<div class="flex items-center gap-2.5">
						<IconReport classNames="size-5 flex-none text-violet-600 dark:text-violet-400" />
						<span class="whitespace-nowrap text-sm font-medium text-gray-700 dark:text-gray-200">Audit logs</span>
					</div>
					<span class="hidden h-5 w-px bg-gray-200 dark:bg-gray-700 sm:block"></span>
					<div class="flex items-center gap-2.5">
						<IconEarth classNames="size-5 flex-none text-teal-600 dark:text-teal-400" />
						<span class="whitespace-nowrap text-sm font-medium text-gray-700 dark:text-gray-200">US & EU regions</span>
					</div>
					<span class="hidden h-5 w-px bg-gray-200 dark:bg-gray-700 sm:block"></span>
					<div class="flex items-center gap-3">
						<img
							src="https://cdn-media.huggingface.co/marketing/pmh-page/soc2.png"
							alt="SOC 2 Type II"
							title="SOC 2 Type II certified"
							class="h-8 opacity-80 dark:opacity-70 dark:brightness-125"
						/>
						<img
							src="https://cdn-media.huggingface.co/marketing/pmh-page/gdpr.png"
							alt="GDPR Compliant"
							title="GDPR compliant"
							class="h-8 opacity-80 dark:opacity-70 dark:brightness-125"
						/>
					</div>
				</div>
			</section>

			<section
				class="shadow-xs relative flex flex-col items-center overflow-hidden text-balance rounded-3xl border border-gray-200 bg-white bg-[url('https://cdn-uploads.huggingface.co/production/uploads/5f17f0a0925b9863e28ad517/7yYe9E-d38GWl6bnEUhhG.png')] bg-cover bg-center bg-no-repeat p-8 text-center dark:border-gray-800 max-sm:py-12 sm:p-12 lg:p-16"
			>
				<h2 class="relative mb-3 text-4xl font-black tracking-tight text-gray-900 dark:text-white xl:text-5xl">
					Get started with <span class="relative inline-block">
						<span
							class="bg-linear-to-br relative from-blue-500 from-15% via-blue-500 to-sky-500 bg-clip-text font-bold text-transparent"
							style="font-weight: 800;"
						>
							HF Storage Buckets
						</span>
						<span
							class="bg-linear-to-br absolute left-0 from-blue-500 from-15% via-blue-500 to-sky-500 bg-clip-text font-bold text-transparent opacity-25 blur-xl"
							style="font-weight: 800;"
						>
							HF Storage Buckets
						</span>
					</span>
				</h2>
				<p class="relative mb-6 text-xl text-gray-600 dark:text-gray-400 sm:text-2xl xl:mb-12">
					Start with buckets, sync your AI data, and unlock object storage built for ML workflows.
				</p>
				<div class="mx-auto flex w-full flex-col items-center justify-center gap-1.5 sm:gap-3 md:flex-row">
					<a
						href={storageLink}
						class="ring-offset-3 relative z-1 flex w-fit items-center gap-1.5 whitespace-nowrap rounded-full bg-black px-5 py-2 text-white ring-1 ring-gray-300 transition-all hover:ring-black dark:bg-gray-100 dark:text-black dark:ring-gray-100 dark:ring-offset-gray-950 sm:text-lg"
						><span class="mr-1">→</span>Create a Bucket</a
					>
					<span class="text-gray-500 dark:text-gray-400">or</span>
					<a
						href="/settings/billing?add-storage=true"
						class="ring-offset-3 relative z-1 flex w-fit items-center gap-1.5 whitespace-nowrap rounded-full bg-gray-200 px-5 py-2 text-base text-gray-900 ring-1 ring-gray-300 transition-all hover:ring-gray-500 dark:bg-gray-600 dark:text-gray-300 dark:ring-gray-600 dark:ring-offset-gray-950 sm:text-lg"
						>Get a Storage package</a
					>
				</div>
			</section>
			<div class="mx-4 -mt-24 grid gap-3">
				<article
					class="shadow-xs flex flex-col items-center text-balance rounded-2xl border border-gray-200 bg-white px-6 pb-4 pt-20 text-center dark:border-gray-800 sm:pt-14"
				>
					<h3 class="mb-2 text-xl font-semibold text-gray-600 sm:mb-0.5 sm:text-2xl">
						Need this for your organization?
					</h3>
					<p class="mx-auto mb-4 text-lg text-gray-500 dark:text-gray-400">
						Need dedicated governance and shared quotas? A Hugging Face <a
							href="/enterprise"
							class="underline-offset-6 font-semibold underline decoration-gray-300 transition-all hover:decoration-gray-800 dark:text-gray-300 dark:decoration-gray-600 dark:hover:decoration-gray-300"
							>Enterprise</a
						> plan includes storage access at scale.
					</p>
				</article>
			</div>
		</div>
	</div>
</App>

<style>
	@keyframes dedup-pulse {
		0%,
		100% {
			opacity: 0.4;
		}
		50% {
			opacity: 1;
		}
	}

	.dedup-highlight {
		animation: dedup-pulse 2s ease-in-out infinite;
	}

	@keyframes float-y {
		0%,
		100% {
			transform: translateY(0px);
		}
		50% {
			transform: translateY(-8px);
		}
	}

	.node-float {
		animation: float-y 3s ease-in-out infinite;
	}
</style>
