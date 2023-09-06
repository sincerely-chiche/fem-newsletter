<template>
  <div
    class="w-full h-full sm:h-auto sm:w-4/12 sm:mx-auto px-6 pt-20 sm:p-14 bg-white text-darkGrey sm:rounded-3xl flex flex-col justify-evenly sm:space-y-10 items-start sm:shadow-md animate__animated animate__zoomIn animate__faster"
  >
    <!-- Success message start -->
    <img src="images/icon-success.svg" alt="Success" class="h-18" />

    <div class="space-y-8">
      <h1 class="text-5xl font-bold">Thanks for subscribing!</h1>

      <p class="text-md text-darkGrey font-medium">
        A confirmation email has been sent to <br />
        <b>{{ email }}.</b> Please open it and click the button inside to
        confirm your subscription.
      </p>
    </div>

    <button @click="$emit('close')" class="btn mt-[20vh] sm:mt-0">
      Dismiss message
    </button>
    <!-- Success message end -->
  </div>
</template>

<script setup>
defineProps(["email"]);
defineEmits(["close"]);
</script>

<style lang="scss" scoped></style>
