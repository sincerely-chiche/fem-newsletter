<template>
  <div
    class="min-w-screen h-screen overflow-auto lg:overflow-hidden bg-lightGrey text-white md:flex md:flex-col md:justify-center md:items-center lg:items-start"
  >
    <AlertModal :email="email" @close="closeModal" v-if="success.state" />
    <div
      v-else
      class="w-full lg:w-10/12 xl:w-8/12 lg:mx-auto h-full lg:h-[70vh] lg:pl-6 lg:pr-4 lg:py-4 bg-white text-darkGrey lg:rounded-3xl flex md:flex-row flex-col-reverse lg:shadow-md animate__animated animate__zoomIn animate__faster"
    >
      <div
        class="w-full lg:w-7/12 md:pt-28 lg:pt-16 lg:pl-10 lg:pr-16 px-6 lg:overflow-auto"
      >
        <!-- Sign-up form start -->
        <h1 class="text-5xl font-bold">Stay updated!</h1>

        <p class="py-4 text-md font-medium">
          Join 60,000+ product managers receiving monthly <br />
          updates on:
        </p>

        <ul class="mt-2">
          <li class="flex items-center space-x-4 mb-2 text-md font-semibold">
            <img src="/images/icon-list.svg" class="h-4" alt="List" />
            <span>Product discovery and building what matters</span>
          </li>
          <li class="flex items-center space-x-4 mb-2 text-md font-semibold">
            <img src="/images/icon-list.svg" class="h-4" alt="List" />
            <span>Measuring to ensure updates are a success</span>
          </li>
          <li class="flex items-center space-x-4 mb-2 text-md font-semibold">
            <img src="/images/icon-list.svg" class="h-4" alt="List" />
            <span>And much more!</span>
          </li>
        </ul>

        <form action="#" method="post" class="my-8">
          <div class="flex flex-col">
            <div class="flex items-center justify-between">
              <label for="email" class="text-xs font-bold">Email address</label>
              <label
                v-show="error.state"
                for="email"
                class="text-xs font-bold text-red-400"
                >Valid email required</label
              >
            </div>
            <input
              type="email"
              name="email"
              id="email"
              v-model="email"
              @focus="() => (error.state ? (error.state = false) : '')"
              placeholder="email@company.com"
              class="transition outline-none border rounded-lg px-6 py-3 text-sm mt-2"
              :class="{
                'border-red-400 bg-red-200 text-red-600 placeholder:text-red-600':
                  error.state,
                'hover:border-darkGrey': !error.state,
              }"
            />
          </div>

          <button
            @click.prevent="submit"
            class="transition outline-none bg-darkGrey text-white w-full py-3 text-sm font-bold rounded-lg mt-6 duration-300 ease-linear bg-gradient-to-r hover:from-pink-500 hover:to-orange-500 hover:from-5% hover:to-95% cursor-pointer btn"
          >
            Subscribe to monthly newsletter
          </button>
        </form>

        <!-- Sign-up form end -->
      </div>
      <div class="w-full lg:w-5/12">
        <img
          src="/images/desktop-img.svg"
          alt="Frontend mentor"
          class="object-cover object-center h-full w-full -mt-[15%] md:mt-0 rounded-[20px] md:rounded-none lg:rounded-2xl"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import AlertModal from "./components/AlertModal.vue";

const error = ref({
  state: false,
  msg: "",
});
const success = ref({
  state: false,
  msg: "",
});
const email = ref("");
let emailReg =
  /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/;

function submit() {
  if (email.value === "" || !email.value.match(emailReg)) {
    error.value.state = true;
  } else {
    success.value.state = true;
  }
}
function closeModal() {
  success.value.state = false;
  email.value = "";
  error.value.state = false;
}
</script>

<style lang="scss">
.attribution {
  font-size: 11px;
  text-align: center;
}
.attribution a {
  color: hsl(228, 45%, 44%);
}
</style>
