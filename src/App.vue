<script setup>
import Hello from './components/content/Hello.vue';
import Knowledge from './components/content/Knowledge.vue';
import Portfolio from './components/content/Portfolio.vue';
import Email from './components/content/Email.vue';
import { ref, computed } from 'vue';

const currentId = ref(0);
const content = ref([
    {
        'name': 'Intro',
        'component': Hello
    }, 
    {
        'name': 'Knowledge',
        'component': Knowledge
    },
    {
        'name': 'Portfolio',
        'component': Portfolio
    },
    {
        'name': 'Contact me',
        'component': Email
    }
]);

const changeId = (id) => {
	currentId.value = id;
};

const scrollTo = (id) => {
    const offsetTop = document.querySelector(".content section:nth-child("+id+")").offsetTop;
    scroll({
        top: offsetTop,
        behavior: "smooth"
    });
}

</script>

<template>
    <header>
	<nav class="navigation">
        <img src="./assets/lpe_icon.png" width="50" height="50" alt="Nadezda Gurska Front end developer" />
		<ul>
			<li
				v-for="(item, index) in content"
				:key="index"
				:class="{ active: index == currentId }"
				@click="changeId(index)"
			><button @click="scrollTo(index)">{{item.name}}</button>
			</li>
		</ul>
	</nav>
    </header>

	<div class="content">
        <section v-for="(section, index) in content" :key="index" class="content__section">
            <component :is="section.component"></component>
        </section>
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

nav {
    position:fixed;
    top:0;
    left:0;
    z-index:3;
    width:100%;
    display: grid;
    grid-template-columns: 1fr auto;
    ul {
        display:flex;
        justify-content: flex-end;
    }
    button {
        text-transform:uppercase;
        display:inline-block;
        line-height:1;
        padding:5px 10px;
    }
}

section {
    width:100%;
    @include breakpoints.device(breakpoints.$medium) {
        min-height: 100vh;
    }
}

</style>
