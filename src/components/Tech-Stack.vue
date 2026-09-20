<script setup lang="ts">
import { onMounted, ref } from "vue";
import { gsap } from "gsap";
import { SplitText } from "gsap/SplitText";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(SplitText, ScrollTrigger);

const tech_stack_1 = ref<HTMLElement | null>(null);
const tech_stack_2 = ref<HTMLElement | null>(null);
const tech_stack_3 = ref<HTMLElement | null>(null);
const tech_stack_4 = ref<HTMLElement | null>(null);
const tech_stack_5 = ref<HTMLElement | null>(null);
const tech_stack_6 = ref<HTMLElement | null>(null);
const tech_stack_7 = ref<HTMLElement | null>(null);
onMounted(() => {
  const techStacks = [ tech_stack_1, tech_stack_2, tech_stack_3, tech_stack_4, tech_stack_5, tech_stack_6, tech_stack_7, ];
  techStacks.forEach((stack) => {
    if (!stack.value) return;
    gsap.from(stack.value.querySelectorAll("p"), {
      y: 15,
      opacity: 0,
      ease: "steps(2)",
      duration: 0.5,
      stagger: { each: 0.02, from: "start", },
      scrollTrigger: {
        trigger: stack.value,
        start: "top bottom",
        end: "bottom 75%",
        scrub: true,
      },
    });
  });
});
</script>

<template>
<section ref="tech_stack" class="tech_stack">
  <div class="min-h-[60vh] flex flex-col md:p-10 p-2 justify-center items-center">
    <div class="flex flex-col md:w-[40%] w-[90%]">
      <p ref="tech_stack_command" class="font-fira-code text-green-one">
        ~/tech-stack$ cat stack.conf
      </p>
      <div ref="tech_stack_1" class="p-3">
        <p class="text-2xl font-geist text-white-one">Languages</p>
        <div class="flex md:gap-5 gap-2 flex-wrap">
          <p class="text-white-one">Javascript</p>
          <p class="text-white-one">Typescript</p>
          <p class="text-white-one">Python</p>
          <p class="text-white-one">Java</p>
          <p class="text-white-one">GDScript</p>
        </div>
      </div>
      <div ref="tech_stack_2" class="p-3">
        <p class="text-2xl font-geist text-white-one">Frontend</p>
        <div class="flex md:gap-5 gap-2 flex-wrap">
          <p class="text-white-one">Vue</p>
          <p class="text-white-one">GSAP</p>
          <p class="text-white-one">Tailwind</p>
          <p class="text-white-one">React</p>
        </div>
      </div>
      <div ref="tech_stack_3" class="p-3">
        <p class="text-2xl font-geist text-white-one">Backend</p>
        <div class="flex md:gap-5 gap-2 flex-wrap">
          <p class="text-white-one">Flask</p>
          <p class="text-white-one">FastAPI</p>
        </div>
      </div>
      <div ref="tech_stack_4" class="p-3">
        <p class="text-2xl font-geist text-white-one">Databases</p>
        <div class="flex md:gap-5 gap-2 flex-wrap">
          <p class="text-white-one">PostgreSQL</p>
          <p class="text-white-one">Supabase</p>
          <p class="text-white-one">MySQL</p>
        </div>
      </div>
      <div ref="tech_stack_5" class="p-3">
        <p class="text-2xl font-geist text-white-one">DevOps</p>
        <div class="flex md:gap-5 gap-2 flex-wrap">
          <p class="text-white-one">Docker</p>
          <p class="text-white-one">Docker Compose</p>
          <p class="text-white-one">AWS EC2</p>
          <p class="text-white-one">Github Actions</p>
          <p class="text-white-one">Nginx</p>
          <p class="text-white-one">Linux</p>
        </div>
      </div>
      <div ref="tech_stack_6" class="p-3">
        <p class="text-2xl font-geist text-white-one">Observability</p>
        <div class="flex md:gap-5 gap-2 flex-wrap">
          <p class="text-white-one">Grafana</p>
          <p class="text-white-one">Prometheus</p>
          <p class="text-white-one">Loki</p>
          <p class="text-white-one">Tempo</p>
          <p class="text-white-one">Node Exporter</p>
          <p class="text-white-one">cAdvisor</p>
          <p class="text-white-one">Alloy</p>
        </div>
      </div>
      <div ref="tech_stack_7" class="p-2">
        <p class="text-2xl font-geist text-white-one">Tools</p>
        <div class="flex md:gap-5 gap-2 flex-wrap">
          <p class="text-white-one">Git</p>
          <p class="text-white-one">Bash</p>
          <p class="text-white-one">Zed</p>
          <p class="text-white-one">VS code</p>
          <p class="text-white-one">AWS Kiro</p>
          <p class="text-white-one">Blender</p>
        </div>
      </div>
    </div>
  </div>
</section>
</template>
