<script setup lang="ts">
import type { HTMLAttributes } from 'vue'
import type { AccordionTriggerProps } from 'reka-ui'

import { reactiveOmit } from '@vueuse/core'
import { ChevronDown, ChevronUp } from 'lucide-vue-next'
import {
  AccordionHeader,
  AccordionTrigger,
} from 'reka-ui'

import { cn } from '@/lib/utils'

const props = defineProps<
  AccordionTriggerProps & {
    class?: HTMLAttributes['class']
  }
>()

const delegatedProps = reactiveOmit(props, 'class')
</script>

<template>
  <AccordionHeader class="flex">
    <AccordionTrigger
      v-bind="delegatedProps"
      data-slot="accordion-trigger"
      :class="
        cn(
          `
          group/accordion-trigger
          relative flex flex-1 items-center justify-center

          rounded-none
          border border-transparent

          py-5
          text-left text-xl font-extrabold
          text-white-one
          hover:bg-green-two
          cursor-pointer

          transition-all
          outline-none

          focus-visible:ring-ring/50
          focus-visible:border-ring
          focus-visible:after:border-ring
          focus-visible:ring-1

          disabled:pointer-events-none
          disabled:opacity-50

          **:data-[slot=accordion-trigger-icon]:ml-auto
          **:data-[slot=accordion-trigger-icon]:size-4
          **:data-[slot=accordion-trigger-icon]:text-muted-foreground
          data-[state=closed]:hover:bg-green-two
          data-[state=open]:bg-black-two
          `,
          props.class,
        )
      "
    >
      <slot />

      <slot name="icon">
        <ChevronDown
          data-slot="accordion-trigger-icon"
          class="absolute right-4 pointer-events-none group-aria-expanded/accordion-trigger:hidden"
        />

        <ChevronUp
          data-slot="accordion-trigger-icon"
          class="absolute right-4 hidden pointer-events-none group-aria-expanded/accordion-trigger:inline"
        />
      </slot>
    </AccordionTrigger>
  </AccordionHeader>
</template>
