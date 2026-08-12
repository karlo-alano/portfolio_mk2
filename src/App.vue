<script setup lang="ts">
import { onMounted, ref } from "vue";
import { gsap } from "gsap";
import { SplitText } from "gsap/SplitText";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { ScrollSmoother } from "gsap/ScrollSmoother";

import Hero from "@/components/Hero.vue";
import About from "@/components/About.vue";
import TechStack from "@/components/Tech-Stack.vue";
import Projects from "@/components/Projects.vue";
import Experience from "@/components/Experience.vue";

gsap.registerPlugin(SplitText, ScrollTrigger, ScrollSmoother);

onMounted(async () => {
  await document.fonts.ready;
  ScrollSmoother.create({
  	smooth: 1,
  	effects: true
  });

  gsap.to(".background-dots", {
    yPercent: -15,
    ease: "none",
    scrollTrigger: {
      trigger: "#smooth-content",
      start: "top top",
      end: "bottom bottom",
      scrub: true
    }
  });
});
  requestAnimationFrame(() => ScrollTrigger.refresh());

</script>

<template>
  <main id="smooth-wrapper">
    <section class="flex flex-col min-h-screen" id="smooth-content">
      <div class="background-dots"></div>
      <Hero></Hero>
      <About></About>
      <TechStack></TechStack>
      <Projects></Projects>
      <Experience></Experience>


      <section class="future">
        <div class="min-h-screen flex flex-col p-10 justify-center items-center">
          <div class="flex flex-col w-[40%]">
            <p class="font-fira-code text-green-one">
              ~$ sudo nano future.conf
            </p>
          </div>
        </div>
      <section>

      <section class="contact">
        <div class="min-h-screen flex flex-col p-10 justify-center items-center">
          <div class="flex flex-col w-[40%]">
            <p class="font-fira-code text-green-one">
              ~/contact$ bash contact.sh
            </p>
          </div>
        </div>
      </section>


      </section>
    </section>
    </section>
  </main>
</template>

<style scoped></style>
