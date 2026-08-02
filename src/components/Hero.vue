<script setup lang="ts">
import { onMounted, ref } from "vue";
import { gsap } from "gsap";
import { SplitText } from "gsap/SplitText";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(SplitText, ScrollTrigger);

const class_greeter_a = ref(null);
const class_greeter_b = ref(null);
const class_button = ref(null);

onMounted(async () => {
  await document.fonts.ready;

  const split_a = SplitText.create(class_greeter_a.value, {
    type:"chars, words"
  });

  const split_b = SplitText.create(class_greeter_b.value, {
    type:"chars, words"
  });

  const tl_1 = gsap.timeline();

  tl_1.from(split_a.chars, {
    yPercent: "random([-50, -25, 25, 50])",
    opacity: 0,
    duration: 0.5,
    ease: "steps(2)",
    stagger: 0.05,
    color: "#12330A",
  }).from(split_b.words, {
    yPercent: "random([-75, -50, 50, 75])",
    opacity: 0,
    duration: 0.5,
    ease: "steps(2)",
    stagger: {
      each: 0.02,
      from: "start"
    },
    color: "#12330A",
  }).from(class_button.value, {
    y: 100,
    opacity: 0,
    duration: 0.5,
    ease: "steps(3)"
  });
})

</script>

<template>
  <section class="hero">
    <div class="min-h-screen flex flex-col justify-center items-center">
      <div ref="class_greeter_box_a" class="font-geist font-extrabold text-8xl text-white-one p-10">
        <p ref="class_greeter_a">Hello there, I'm Karlo!</p>
      </div>
      <div class="class_greeter_box_b font-geist text-2xl text-white-one">
        <p ref="class_greeter_b">I can build, deploy, automate, monitor, and maintain systems. Shall we get along?</p>
      </div>

      <div ref="class_button" class="mt-5">
        <div ref="class_dock" class="flex gap-5">
          <a class="font-fira-code text-xl text-white-one hover:bg-green-two cursor-pointer p-2" href="/about">./about</a>
          <a class="font-fira-code text-xl text-white-one hover:bg-green-two cursor-pointer p-2">./tech-stack</a>
          <a class="font-fira-code text-xl text-white-one hover:bg-green-two cursor-pointer p-2">./projects</a>
          <a class="font-fira-code text-xl text-white-one hover:bg-green-two cursor-pointer p-2">./experience</a>
          <a class="font-fira-code text-xl text-white-one hover:bg-green-two cursor-pointer p-2">./contact</a>
        </div>
      </div>
      <div>

      </div>
    </div>
  </section>
</template>
