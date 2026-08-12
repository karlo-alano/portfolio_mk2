<script setup lang="ts">
import { onMounted, ref } from "vue";
import { gsap } from "gsap";
import { SplitText } from "gsap/SplitText";

import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger, SplitText);

const projects = ref(null);
const projects_command = ref(null);
const projects_accordion = ref(null);

import {
  Accordion,
  AccordionContent,
  AccordionItem,
  AccordionTrigger,
} from '@/components/ui/accordion'

onMounted(async () => {
  await document.fonts.ready;

  const split_project = SplitText.create(projects_command.value, {
    type:"chars, words, lines"
  });

  const tl_3 = gsap.timeline({
    scrollTrigger: {
      trigger: projects.value,
      start: "top bottom",
      end: "bottom 85%",
      scrub: true,
      markers: true,
     }
  });

  tl_3.from(split_project.chars, {
    y: 150,
    opacity: 0,
    ease: "expo.out",
    duration: 1,
    stagger: {
      each: 0.02,
      from: "start"
    }
  }).from(projects_accordion.value, {
    y: 150,
    opacity: 0,
    ease: "steps(6)",
    duration: 1,
  })

});

</script>

<template>

<section ref="projects" class="projects">
  <div class="min-h-[75vh] flex flex-col md:p-10 p-2 justify-center items-center">
    <div class="flex flex-col md:w-[40%] w-[90%]">
    <p ref="projects_command" class="font-fira-code text-green-one">
      ~/projects$ ls
    </p>
    <div ref="projects_accordion">
      <Accordion  type="single" collapsible>
        <AccordionItem value="item-1" class=" border-0 grow">
          <AccordionTrigger clas="">
            <p class="font-fira-code text-xl text-white-one">Itinero.md</p>
          </AccordionTrigger>
          <AccordionContent class="text-white-one">
            <div class="flex flex-col gap-3">
              <div class="w-full h-70 bg-[url('@/assets/images/itinero.png')] bg-cover opacity-70">

              </div>
              <p>
                This is Itinero, a time-Constrained Automatic Itinerary Generator for Effective
                Travel Planning in Intramuros, Manila This project is developed and research by
                three computer science students from Cavite State University Indang Campus. In an
                effort to streamline and automate itinerary planning, Itinero proposes an automated
                generator which plans, searches, and schedules Places Of Interests (POIs) that
                dynamically changes based on the time requirements specified by the user. It uses
                the Google Maps Places API to search and filter through a list of POIs and then
                forwards the list to by scheduled by a Nearest Neighbor Algorithm. The result is
                then presented into a GUI that a user can interact with
              </p>
              <div class="flex gap-3 justify-end">
                <a
                  class="text-s md:text-lg no-underline! hover:bg-green-two hover:text-white-one! p-2 font-fira-code"
                  href="https://github.com/karlo-alano/itinero-web"
                  >./github</a>
                <a
                  class="text-s md:text-lg no-underline! hover:bg-green-two hover:text-white-one! p-2 font-fira-code"
                  href="https://www.itinero.site"
                  >./website</a>
              </div>
            </div>
          </AccordionContent>
        </AccordionItem>
        <AccordionItem value="item-2" class="border-0 grow">
          <AccordionTrigger clas="">
            <p class="font-fira-code text-xl text-white-one">The_Keeper.md</p>
          </AccordionTrigger>
          <AccordionContent class="text-white-one">
            <div class="flex flex-col gap-3">
              <div class="w-full h-70 bg-[url('@/assets/images/thekeeper.png')] bg-cover opacity-70"></div>
              <p>
                The Keeper is a meta-horror game that explores feelings of deception, manipulation, and deceit, especially in times of vulnerability.
                You play as Nanay Angelina, a dorm keeper who balances chores with complex extrapersonal relationships with the rest of the tenants and her daughter.
                When everything else goes wrong, do you have what it takes to remain calm, observant, and skeptical?
              </p>
              <div class="flex gap-3 justify-end">
                <a
                  class="text-s md:text-lg no-underline! hover:bg-green-two hover:text-white-one! p-2 font-fira-code"
                  href="https://github.com/karlo-alano/the-keeper-game"
                  >./github</a>
              </div>
            </div>
          </AccordionContent>
        </AccordionItem>
        <AccordionItem value="item-3" class=" border-0 grow">
          <AccordionTrigger clas="">
            <p class="font-fira-code text-xl text-white-one">DevOps_Experiments.md</p>
          </AccordionTrigger>
          <AccordionContent class="text-white-one">
            Recently, I have been enthralled with the world of DevOps. Docker, deployments, monitoring, and scaling are all concepts that had me awe-struck.
            I always believed that software and systems should be designed with efficiency and that they should benefit the user, but I only clicked in me recently
            that DevOps adopts that same mantra, but for other developers.
          </AccordionContent>
        </AccordionItem>
      </Accordion>
    </div>
    </div>
  </div>
</section>

</template>
