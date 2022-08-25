<script setup>
import { ref, computed } from 'vue';

const currentId = ref(0);

const content = ref([
	{
		icon: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M12 9c1.654 0 3 1.346 3 3s-1.346 3-3 3-3-1.346-3-3 1.346-3 3-3zm0-2c-2.762 0-5 2.238-5 5s2.238 5 5 5 5-2.238 5-5-2.238-5-5-5zm-4.184-.599l-3.593-3.594-1.415 1.414 3.595 3.595c.401-.537.876-1.013 1.413-1.415zm4.184-1.401c.34 0 .672.033 1 .08v-5.08h-2v5.08c.328-.047.66-.08 1-.08zm5.598 2.815l3.595-3.595-1.414-1.414-3.595 3.595c.537.402 1.012.878 1.414 1.414zm-12.598 4.185c0-.34.033-.672.08-1h-5.08v2h5.08c-.047-.328-.08-.66-.08-1zm11.185 5.598l3.594 3.593 1.415-1.414-3.594-3.593c-.403.536-.879 1.012-1.415 1.414zm-9.784-1.414l-3.593 3.593 1.414 1.414 3.593-3.593c-.536-.402-1.011-.877-1.414-1.414zm12.519-5.184c.047.328.08.66.08 1s-.033.672-.08 1h5.08v-2h-5.08zm-6.92 8c-.34 0-.672-.033-1-.08v5.08h2v-5.08c-.328.047-.66.08-1 .08z"/></svg>',
		content: 'Hi',
	},
	{
		icon: '<svg width="24" height="24" xmlns="http://www.w3.org/2000/svg" fill-rule="evenodd" clip-rule="evenodd"><path d="M12.434 24h-.894c-.235 0-.461-.079-.616-.218l-1.187-.782h4.5l-1.188.782c-.154.139-.38.218-.615.218zm1.845-2h-4.558c-.276 0-.5-.223-.5-.5 0-.276.224-.5.5-.5h4.558c.276 0 .5.224.5.5 0 .277-.224.5-.5.5zm-1.507-2c.152-4.705 3.229-6.902 3.229-9.255 0-2.336-1.829-3.745-3.992-3.745-1.973 0-4.009 1.232-4.009 3.754 0 2.347 3.189 5.003 3.225 9.246h-2.011c-.016-3.993-3.214-5.637-3.214-9.254 0-3.537 2.837-5.773 6.068-5.746 3.287.053 5.934 2.344 5.934 5.747 0 3.626-3.189 5.178-3.215 9.253h-2.015zm6.967-7.229l2.699 1.224-.827 1.822-2.596-1.177c.301-.6.55-1.215.724-1.869zm-15.477 0c.173.664.415 1.261.719 1.87l-2.592 1.176-.827-1.822 2.7-1.224zm18.738-1.771h-3.003c.021-.67-.04-1.345-.185-2h3.188v2zm-18.997 0h-3.003v-2h3.187c-.143.654-.203 1.326-.184 1.995v.005zm14.04-5.428l2.485-1.763 1.158 1.631-2.505 1.777c-.292-.582-.67-1.132-1.138-1.645zm-12.087-.001c-.46.503-.837 1.05-1.138 1.645l-2.503-1.776 1.157-1.631 2.484 1.762zm8.869-2.092l1.327-2.69 1.793.885-1.327 2.69c-.557-.367-1.161-.664-1.793-.885zm-5.651-.002c-.631.22-1.236.516-1.794.884l-1.326-2.687 1.794-.885 1.326 2.688zm3.826-.416c-.668-.078-1.309-.082-2-.003v-3.058h2v3.061z"/></svg>',
		content: 'knowledge',
	},
	{
		icon: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M21 9c.552 0 1 .449 1 1v9c0 .551-.448 1-1 1h-18c-.552 0-1-.449-1-1v-9c0-.551.448-1 1-1h18zm0-2h-18c-1.657 0-3 1.343-3 3v9c0 1.657 1.343 3 3 3h18c1.657 0 3-1.343 3-3v-9c0-1.657-1.343-3-3-3zm-12-5c-1.104 0-2 .896-2 2v2h2v-1.5c0-.276.224-.5.5-.5h5c.276 0 .5.224.5.5v1.5h2v-2c0-1.104-.896-2-2-2h-6zm10.5 9h-15c-.276 0-.5.224-.5.5s.224.5.5.5h15c.276 0 .5-.224.5-.5s-.224-.5-.5-.5zm0 3h-15c-.276 0-.5.224-.5.5s.224.5.5.5h15c.276 0 .5-.224.5-.5s-.224-.5-.5-.5zm0 3h-15c-.276 0-.5.224-.5.5s.224.5.5.5h15c.276 0 .5-.224.5-.5s-.224-.5-.5-.5z"/></svg>',
		content: 'Portfolio',
	},
	{
		icon: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M0 3v18h24v-18h-24zm21.518 2l-9.518 7.713-9.518-7.713h19.036zm-19.518 14v-11.817l10 8.104 10-8.104v11.817h-20z"/></svg>',
		content: 'email',
	},
]);

const changeId = (id) => {
	currentId.value = id;
};
</script>

<template>
	<div class="navigation">
		<ul>
			<li><img src="./assets/lpe_icon.png" /></li>
			<li
				v-for="(item, index) in content"
				:key="index"
				:class="{ active: index == currentId }"
				@click="changeId(index)"
				v-html="item.icon"
			></li>
		</ul>
	</div>
	<div class="content">
		{{ content[currentId].content }}
	</div>

	<footer>@copy; 2022 Nadezda Gurska nadezda@gurska.dev</footer>
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
	grid-template-columns: 200px 1fr;
	grid-template-rows: 1fr auto;
	gap: 0px 0px;
	grid-template-areas:
		'side content'
		'copyright copyright';
}

.navigation {
	grid-area: side;
	min-height: 80vh;
	position: relative;
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
	}
}
.content {
	grid-area: content;
}

footer {
	grid-area: copyright;
}
</style>
