<template>
  <div
    class="sm:w-4/12 sm:mx-auto sm:p-14 bg-white text-darkGrey sm:rounded-3xl flex flex-col space-y-10 items-start sm:shadow-md animate__animated animate__zoomIn animate__faster"
  >
    <!-- Success message start -->
    <img src="images/icon-success.svg" alt="Success" class="h-18" />

    <h1 class="text-5xl sm:font-bold">Thanks for subscribing!</h1>

    <p class="text-xs text-darkGrey">
      A confirmation email has been sent to <br />
      <b>{{ email }}.</b> Please open it and click the button inside to confirm
      your subscription.
    </p>

    <button @click="$emit('close')" class="btn">Dismiss message</button>
    <!-- Success message end -->
  </div>
</template>

<script setup>
defineProps(["email"]);
defineEmits(["close"]);
</script>

<style lang="scss" scoped></style>
