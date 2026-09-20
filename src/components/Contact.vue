<script setup lang="ts">
import { ref } from "vue";

const name = ref('')
const email = ref('')
const message = ref('')

function submitEmail() {
  pass
}

</script>

<template>
    <section class="contact">
        <div class="min-h-screen flex flex-col p-10 justify-center items-center">
          <div class="flex flex-col w-[40%] gap-4">
            <p class="font-fira-code text-green-one">
              ~/contact$ bash contact.sh
            </p>
            <div ref="contactArea">
              <p class="text-white-one text-l font-fira-code">Reach out to me by filling in this form</p>
            </div>
            <div class="bg-black-two border-black-one border p-2 md:p-10 flex flex-col gap-2 ">
              <form @submit.prevent="submitEmail">
                <div clas="flex flex-row">
                  <span class="font-fira-code text-green-one">Your name: </span>
                  <input v-model=name type="text" placeholder="..." class="text-white-one outline-0 w-[75%]" required>
                </div>
                <div>
                  <span class="font-fira-code text-green-one">Your email: </span>
                  <input v-model=email type="email" placeholder="..." class="text-white-one outline-0 w-[75%]" required>
                </div>
                <div class="mt-5">
                  <span class="font-fira-code text-green-one">Your message: </span>
                  <textarea v-model=message type="text" placeholder="..." class="text-white-one outline-0 w-full" rows="4" requied></textarea>
                </div>
                <div>
                  <button type="submit" class="text-green-one bg-black p-2 cursor-pointer">Send</button>
                </div>
              </form>
            </div>
          </div>
        </div>
      </section>
</template>
