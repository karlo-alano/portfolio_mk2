<script setup lang="ts">
import { onMounted, ref } from "vue";
import { gsap } from "gsap";
import { SplitText } from "gsap/SplitText";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(SplitText, ScrollTrigger);

const experience = ref<HTMLElement | null>(null);
const experienceCommand = ref<HTMLElement | null>(null);
const experienceHeader = ref<HTMLElement | null>(null);
const experienceDetails = ref<HTMLElement | null>(null);

onMounted(() => {
  if (
    !experience.value ||
    !experienceCommand.value ||
    !experienceHeader.value ||
    !experienceDetails.value
  ) {
    return;
  }

  const ctx = gsap.context(() => {
    const bullets = experienceDetails.value!.querySelectorAll("p");

    const tl = gsap.timeline({
      scrollTrigger: {
        trigger: experience.value,
        start: "top bottom",
        end: "bottom 90%",
        scrub: true,
      },
    });

    tl.from(experienceCommand.value, {
      y: 15,
      opacity: 0,
      duration: 0.4,
      ease: "steps(2)",
    })

      .from(
        experienceHeader.value,
        {
          y: 15,
          opacity: 0,
          duration: 0.5,
          ease: "steps(2)",
        },
        "-=0.15"
      )

      .from(
        bullets,
        {
          y: 15,
          opacity: 0,
          duration: 0.5,
          ease: "steps(2)",
          stagger: {
            each: 0.08,
            from: "start",
          },
        },
        "-=0.1"
      );
  }, experience.value);

  return () => ctx.revert();
});
</script>

<template>
  <section ref="experience" class="experience">
    <div
      class="min-h-[60vh] flex flex-col md:p-10 p-2 justify-center items-center"
    >
      <div class="flex flex-col md:w-[40%] w-[90%]">
        <p
          ref="experienceCommand"
          class="font-fira-code text-green-one md:text-md"
        >
          ~/experience$ cat experience.conf
        </p>

        <div ref="experienceHeader">
          <div class="text-white-one text-md pb-3 font-bold opacity-70">
            <div class="flex gap-3 justify-between">
              <span>S.P. Madrid and Associates</span>
              <span>June 2026 - August 2026</span>
            </div>

            <span>DevOps Engineer Intern</span>
          </div>
        </div>

        <div
          ref="experienceDetails"
          class="text-white-one font-fira-mono text-l flex flex-col gap-3"
        >
          <p>
            &gt; Designed and implemented CI/CD pipelines for several projects
            without former workflows
          </p>

          <p>
            &gt; Designed and implemented CD pipeline for Dev and Production
            Environments
          </p>

          <p>
            &gt; Worked on establishing CI pipelines for multiple projects
          </p>

          <p>
            &gt; Worked with multiple teams and communicated requirements
            through messaging channels
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
