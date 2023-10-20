<script setup lang="ts">
import {ref, onMounted} from 'vue'

const text1Ref = ref()
const text2Ref = ref()

const texts = [
	"Accessibility",
	"A11y",
];

const morphTime = 4;
const cooldownTime = 0.25;

let textIndex = texts.length - 1;
let time = new Date();
let morph = 0;
let cooldown = cooldownTime;

function doMorph() {
	morph -= cooldown;
	cooldown = 0;

	let fraction = morph / morphTime;

	if (fraction > 1) {
		cooldown = cooldownTime;
		fraction = 1;
	}

	setMorph(fraction);
}

function setMorph(fraction) {
	text2Ref.value.style.filter = `blur(${Math.min(8 / fraction - 8, 100)}px)`;
	text2Ref.value.style.opacity = `${Math.pow(fraction, 0.4) * 100}%`;

	fraction = 1 - fraction;
	text1Ref.value.style.filter = `blur(${Math.min(8 / fraction - 8, 100)}px)`;
	text1Ref.value.style.opacity = `${Math.pow(fraction, 0.4) * 100}%`;

	text1Ref.value.textContent = texts[textIndex % texts.length];
	text2Ref.value.textContent = texts[(textIndex + 1) % texts.length];
}

function doCooldown() {
	morph = 0;

	text2Ref.value.style.filter = "";
	text2Ref.value.style.opacity = "100%";

	text1Ref.value.style.filter = "";
	text1Ref.value.style.opacity = "0%";
}

function animate() {
	requestAnimationFrame(animate);

	let newTime = new Date();
	let shouldIncrementIndex = cooldown > 0;
	let dt = (newTime - time) / 1000;
	time = newTime;

	cooldown -= dt;

	if (cooldown <= 0) {
		if (shouldIncrementIndex) {
			textIndex++;
		}

		doMorph();
	} else {
		doCooldown();
	}
}

onMounted(()=>{
	text1Ref.value.textContent = texts[textIndex % texts.length];
	text2Ref.value.textContent = texts[(textIndex + 1) % texts.length];

	animate();
})

</script>

<template>
	<section>
		<div id="container">
			<span id="text1" ref="text1Ref"></span>
			<span id="text2" ref="text2Ref"></span>
		</div>

		<svg id="filters">
			<defs>
				<filter id="threshold">
					<feColorMatrix in="SourceGraphic" type="matrix" values="1 0 0 0 0
                  0 1 0 0 0
                  0 0 1 0 0
                  0 0 0 255 -140" />
				</filter>
			</defs>
		</svg>
	</section>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Raleway:900&display=swap");

.section-1 {
	width: 100%;
	height: 100%;
	position: relative;
}

#container {
	position:relative;
	width: 100%;
	height: 100%;

	filter: url(#threshold) blur(0.6px);
}

#text1,
#text2 {
	position: absolute;
	left: 0;
	display: inline-block;

	font-family: "Raleway", sans-serif;
	font-size: 75px;
	width: 100%;

	text-align: center;

	user-select: none;
}
</style>