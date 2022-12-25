<script setup>
import Hello from './components/content/Hello.vue';
import Knowledge from './components/content/Knowledge.vue';
import Portfolio from './components/content/Portfolio.vue';
import Email from './components/content/Email.vue';
import { ref } from 'vue';

const nav = ref(null);
const hamburger = ref(null);

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

const showNavigation = () => {
nav.value.classList.toggle('active');
hamburger.value.classList.toggle('active')
}

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
		<ul ref="nav">
			<li
				v-for="(item, index) in content"
				:key="index"
				:class="{ active: index == currentId }"
				@click="changeId(index)"
			><button @click="scrollTo(index)">{{item.name}}</button>
			</li>
		</ul>
        <button class="hamburger" ref="hamburger" @click="showNavigation">
            </button>
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
    display:flex;
    justify-content:flex-end;
    height:50px;
    align-items:center;
    ul {
        display:flex;
        justify-content: flex-end;
        transform: translateX(100%);
        transition: transform 1s;
        z-index:1;
        background-color: var(--color-1);
        &.active {
            transform: translateX(-50px);
        }


        button {
        text-transform:uppercase;
        display:flex;
        justify-content: center;
        align-items: center;
        line-height:1;
        height:30px;
        padding:10px 10px;
        color: var(--color-2);
        font-size: 0.7em;
        letter-spacing: 1px;;
    }
    }
   
}

.hamburger {
    position:absolute;
    top:0;right:0;
    display: block;
    margin:10px;
    width:30px;
    height:30px;
    z-index:2;
    background-color:var(--color-1);
    transition: transform 1s;
    &.active {
        transform: rotate(45deg);
    }
}
section {
    width:100%;
    @include breakpoints.device(breakpoints.$medium) {
        min-height: 100vh;
    }
}

</style>
