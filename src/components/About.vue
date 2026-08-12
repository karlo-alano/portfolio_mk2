<script setup lang="ts">
import { onMounted, ref } from "vue";
import { gsap } from "gsap";
import { SplitText } from "gsap/SplitText";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(SplitText, ScrollTrigger);

const about = ref(null);
const about_command = ref(null);
const about_links = ref(null);
const about_paragraph_1 = ref(null);
const about_paragraph_2 = ref(null);
const about_paragraph_3 = ref(null);

onMounted(async () => {
  await document.fonts.ready;

  const tl_2 = gsap.timeline({
    scrollTrigger: {
      trigger: about.value,
      start: "top bottom",
      end: "bottom 95%",
      scrub: true,
      markers: true
    }
  });

  const split_about_command = SplitText.create(about_command.value, {
    type: "chars, words, lines"
  });
  const split_about_1 = SplitText.create(about_paragraph_1.value, {
    type: "chars, words, lines"
  });
  const split_about_2 = SplitText.create(about_paragraph_2.value, {
    type: "chars, words, lines"
  });
  const split_about_3 = SplitText.create(about_paragraph_3.value, {
    type: "chars, words, lines"
  });

  tl_2.from(split_about_command.words, {
    x: 15,
    opacity: 0,
    ease: "steps(2)",
    duration: 1,
    stagger: {
      each: 0.02,
      from: "start"
    },
  }).from(about_links.value, {
    y: 15,
    opacity: 0,
    ease: "easeInOut",
    duration: 1,

  }).from(split_about_1.words, {
    y: 15,
    opacity: 0,
    ease: "steps(2)",
    duration: 0.5,
    stagger: {
      each: 0.02,
      from: "start"
    },
  }).from(split_about_2.words, {
    y: 15,
    opacity: 0,
    ease: "steps(2)",
    duration: 0.5,
    stagger: {
      each: 0.02,
      from: "start"
    },
  }).from(split_about_3.words, {
    y: 15,
    opacity: 0,
    ease: "steps(2)",
    duration: 0.5,
    stagger: {
      each: 0.02,
      from: "start"
    },
  });
});
</script>

<template>
  <section ref="about" class="about" id="about">
    <div class="min-h-screen flex flex-col md:p-10 p-2 justify-center items-center ">
      <div class="flex flex-col gap-4 justify-center md:w-[40%] w-[90%]">
        <p ref="about_command" class="font-fira-code text-green-one">
          ~/about$ nano about.conf
        </p>
        <div ref="about_links" class="links md:w-full flex gap-3 flex-row flex-wrap justify-start">
          <a class="opacity-70 transition-all cursor-pointer" href="https://github.com/karlo-alano">
            <p class="font-fira-code text-white-one hover:text-green-one">Github <i class="pi pi-github"></i></p>
          </a>
          <a class="opacity-70 hover:text-yellow-1 transition-all cursor-pointer" href="https://www.linkedin.com/in/juan-karlo-alano-a74821412/">
            <p class="font-fira-code text-white-one hover:text-green-one">LinkedIn <i class="pi pi-linkedin"></i></p>
          </a>
          <a class="opacity-70 hover:text-yellow-1 transition-all cursor-pointer" href="mailto:alano.juankarlo@gmail.com">
            <p class="font-fira-code text-white-one hover:text-green-one">Email <i class="pi pi-envelope"></i></p>
          </a>
          <a class="opacity-70 hover:text-yellow-1 transition-all cursor-pointer" href="https://www.facebook.com/karl0wo/">
            <p class="font-fira-code text-white-one hover:text-green-one">Facebook <i class="pi pi-facebook"></i></p>
          </a>
          <a class="opacity-70 hover:text-yellow-1 transition-all cursor-pointer" href="https://www.instagram.com/karl0__o/">
            <p class="font-fira-code text-white-one hover:text-green-one">Instagram <i class="pi pi-instagram"></i></p>
          </a>
        </div>
        <p ref="about_paragraph_1" class="font-geist text-white-one text-xl">
          I'm Juan Karlo T. Alano, a fourth year computer science student. I have a growing interest in DevOps and site reliability. I think that systems
          shouldn't just be pretty - they have run well, scale well, and maintain well.
        </p>
        <p ref="about_paragraph_2" class="font-geist text-white-one text-xl">
          My projects focus on production-inspired software, from containerized applications and CI/CD pipelines to monitoring stacks.
          I like understanding what happens behind the scenes after code is written, especially how software is deployed, monitored, and scaled.
          I like the systems part of it - how everything slots together perfectly, not how the next piece will be crammed in.
        </p>
        <p ref="about_paragraph_3" class="font-geist text-white-one text-xl">
          Outside of programming, I play bass, enjoy photography, and have an unhealthy fascination with vechicles and transport, military history, and well-designed systems.
          Those hobbies probably explain why I'm drawn to systems with lots of moving parts.
        </p>
      </div>
    </div>
  </section>
</template>
