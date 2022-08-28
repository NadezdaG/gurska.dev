<script setup>
import iconHello from './components/icons/iconHello.vue';
import iconKnowledge from './components/icons/iconKnowledge.vue';
import iconPortfolio from './components/icons/iconPortfolio.vue';
import iconEmail from './components/icons/iconEmail.vue';
import Hello from './components/content/Hello.vue';
import Knowledge from './components/content/Knowledge.vue';
import Portfolio from './components/content/Portfolio.vue';
import Email from './components/content/Email.vue';
import { ref, computed } from 'vue';

const currentId = ref(0);

const content = ref([
	{
		icon: iconHello,
		content: Hello,
	},
	{
		icon: iconKnowledge,
		content: Knowledge,
	},
	{
		icon: iconPortfolio,
		content: Portfolio,
	},
	{
		icon: iconEmail,
		content: Email,
	},
]);

const changeId = (id) => {
	currentId.value = id;
};
</script>

<template>
	<div class="navigation">
		<ul>
			<li class="rotation"><img src="./assets/lpe_icon.png" /></li>
			<li
				v-for="(item, index) in content"
				:key="index"
				:class="{ active: index == currentId }"
				@click="changeId(index)"
			>
				<component :is="item.icon"></component>
			</li>
		</ul>
	</div>
	<div class="content">
		<component :is="content[currentId].content"></component>
	</div>

	<footer>
		Nadezda Gurska trading as Little Purple Elephant.
		<a
			href="https://github.com/NadezdaG/personal-portfolio.git"
			target="_blank"
			title="Front end developer personal portfolio"
			>GitHub</a
		>
		&copy; 2022
	</footer>
</template>

<style lang="scss">
@use './assets/scss/reset.scss';
@use './assets/scss/variables.scss';
@use './assets/scss/breakpoints.scss';
@use './assets/scss/global.scss';

#app {
	width: 90%;
	max-width: 700px;
	display: grid;
	grid-template-columns: auto 1fr;
	grid-template-rows: 1fr auto;
	gap: 0px 0px;
	min-height: 90vh;
	grid-template-areas:
		'side content'
		'copyright copyright';
	@include breakpoints.device(breakpoints.$medium) {
		grid-template-columns: 200px 1fr;
	}
}

.navigation {
	grid-area: side;
	min-height: 80vh;
	position: relative;
	margin-right: 30px;
	@include breakpoints.device(breakpoints.$medium) {
		margin-right: 0px;
	}
	&:before {
		content: '';
		display: block;
		position: absolute;
		height: 100%;
		width: 2px;
		left: 50%;
		margin-left: -1px;
		background-color: var(--color-1);
		z-index: 1;
	}
	ul {
		min-height: 100%;
		display: block;
		position: relative;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
	}
	li {
		display: flex;
		z-index: 2;
		justify-content: center;
		align-items: center;
		width: 50px;
		height: 50px;
		border-radius: 50%;
		border: 2px solid var(--color-1);
		background-color: var(--color-2);
		transition: all 1s;
		cursor: pointer;

		svg,
		img {
			max-height: 30px;
			max-width: 30px;
			height: auto;
		}
		svg {
			path {
				fill: var(--color-1);
			}
		}
		&:first-child {
			svg,
			img {
				max-height: 50px;
				max-width: 50px;
				height: auto;
			}
		}
		&:hover,
		&.active {
			border: 2px solid var(--color-2);
			background-color: var(--color-1);
			svg {
				path {
					fill: var(--color-2);
				}
			}
		}

		&.active + li {
			animation: flash 5s infinite linear;
			&:hover {
				animation: none;
			}
		}
	}
}

.rotation img {
	animation: rotation 5s infinite linear;
}

@keyframes rotation {
	from {
		transform: rotate(0deg);
	}
	to {
		transform: rotate(359deg);
	}
}

@keyframes flash {
	0%,
	30% {
		border: 2px solid var(--color-1);
		background-color: var(--color-2);
	}
	50% {
		border: 2px solid var(--color-2);
		background-color: var(--color-1);
	}
	70%,
	100% {
		border: 2px solid var(--color-1);
		background-color: var(--color-2);
	}
}

.content {
	grid-area: content;
	display: flex;
	flex-direction: column;
	justify-content: center;
	ul {
		li {
			margin-bottom: 1em;
			padding-left: 1em;
			border-left: 1px solid var(--color-1);
			line-height: 1.3;
		}
	}

	.tag {
		font-size: 0.8em;
		display: inline-block;
		padding: 4px 7px;
		border: 1px solid var(--color-1);
		border-radius: 10px;
		margin-right: 10px;
		margin-bottom: 5px;
		background-color: var(--color-2);
		line-height: 1;
		cursor: pointer;
		transition: transform 0.5s;
		&:hover {
			transform: scale(1.5);
		}
	}
}

footer {
	grid-area: copyright;
	font-size: 0.8rem;
	padding-top: 1rem;
	text-align: right;
}
</style>
