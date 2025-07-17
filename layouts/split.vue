<script setup lang="ts">
</script>

<template>
  <div class="grid grid-cols-12">
    <!-- Kiri -->
    <div class="col-span-6">
        <div class="slidev-layout default text-sm space-y-4">
            <slot name="left" />
        </div>
    </div>

    <!-- Kanan -->
    <div class="col-span-6">
        <div class="slidev-layout default text-sm space-y-4">
          <slot name="right" />
        </div>
    </div>
  </div>
</template>
