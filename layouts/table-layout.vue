<script setup lang="ts">
</script>

<template>
  <div class="">
    <h1>
      <slot name="title" />
    </h1>
    <table class="w-full border-collapse text-xs">
      <thead>
        <tr class="bg-gradient-to-r from-purple-500 to-indigo-500 text-white text-center">
          <slot name="left" />
        </tr>
      </thead>
      <tbody class="divide-y divide-gray-200 text-center">
        <slot name="body" />
      </tbody>
    </table>
  </div>
</template>
