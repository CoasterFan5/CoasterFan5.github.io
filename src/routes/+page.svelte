<script>
	import TitleThing from './TitleThing.svelte';
	import DiscordIcon from '~icons/flowbite/discord-solid';
	import GithubIcon from '~icons/flowbite/github-solid';
	import Emailicon from '~icons/flowbite/envelope-solid';
</script>

<div class="bg">
	<div class="bgCover" />
	<div class="content">
		<TitleThing />
		<div class="sections">
			<div class="section">
				<h3>Projects</h3>
				<a class="projectLink" href="https://github.com/coasterfan5/clubsaurus">Clubsaurus</a>
				<a class="projectLink" href="https://github.com/coasterfan5/currency-translator"
					>Currency Translator</a
				>
				<a class="projectLink" href="#_blank">Coming Soon</a>
			</div>
			<!-- <hr />
			<div class="section">
				<h3>Tools</h3>
				<a class="projectLink" href="https://svelte.dev">Svelte</a>
				<a class="projectLink" href="https://typescriptlang.org">Typescript</a>
				<a class="projectLink" href="https://prisma.io">Prisma</a>
			</div>
			<hr />
			<div class="section">
				<h3>Experience</h3>
				<a class="projectLink" href="#_blank">Fairmyer</a>
				<a class="projectLink" href="https://aermor.com">Aermor</a>
			</div> -->
		</div>
	</div>
	<div class="socials">
		<a
			class="iconLink"
			target="_blank"
			title="Discord"
			href="https://discord.com/users/382781156665327616"
		>
			<DiscordIcon />
		</a>
		<a class="iconLink" target="_blank" title="Github" href="https://github.com/coasterfan5">
			<GithubIcon />
		</a>
		<a class="iconLink" target="_blank" title="Email" href="mailto:dylanjmyers@proton.me">
			<Emailicon />
		</a>
	</div>
</div>

<style lang="scss">
	.bg {
		position: relative;
		background: linear-gradient(
			-45deg,
			#370617 0%,
			#370617 33%,
			#490919 33%,
			#490919 66%,
			#370617,
			66%,
			#370617 100%
		);
		height: 100%;
		width: 100vw;
	}

	.bgCover {
		background: linear-gradient(#03071e, black);
		animation: gradient 15s ease infinite;
		height: 100%;
		width: 100%;
	}

	@keyframes gradient {
		0% {
			opacity: 0.9;
		}
		50% {
			opacity: 0.5;
		}
		100% {
			opacity: 0.9;
		}
	}

	.content {
		position: absolute;
		display: flex;
		align-items: center;
		justify-content: center;
		top: 0px;
		left: 0px;
		height: 100%;
		width: 100vw;
		flex-direction: column;
		gap: 0.1rem;
	}

	.socials {
		position: absolute;
		bottom: 0px;
		left: 0px;
		width: 100vw;
		display: flex;
		justify-content: center;
		padding-bottom: 1rem;
		gap: 1rem;
	}

	.iconLink {
		opacity: 0.75;
		font-size: 1.5rem;
		color: white;

		&:hover {
			transition: all cubic-bezier(0.075, 0.82, 0.165, 1) 0.25s;
			opacity: 1;
		}
	}

	h3 {
		color: white;
		margin: 0.5rem 0;
		margin-top: 1rem;
		opacity: 0.9;
		font-size: 1.5rem;
		font-weight: 500;
	}

	.projectLink {
		text-decoration: none;
		color: white;
		opacity: 0.7;
		text-decoration: underline;
		margin: 0.25rem 0;
		font-weight: 500;

		&:hover {
			transition: all cubic-bezier(0.075, 0.82, 0.165, 1) 0.25s;
			opacity: 0.9;
		}
	}

	.sections {
		display: flex;
		flex-direction: row;
		gap: 0.5rem;
	}

	.section {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: start;
		padding: 0 2rem;
	}

	hr {
		opacity: 0.1;
	}
</style>
