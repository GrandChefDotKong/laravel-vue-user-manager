<template>
  <div class="toolbar">
      <h2>Team</h2>
      <div class="button-group">
          <button class="button" @click="$emit('show-form')">Add team member</button>
          <button class="button button-outline">Export team</button>
      </div>
  </div>
</template>

<script>
export default {
    emits: ["show-form"],
}
</script>

<style>
.toolbar {
    padding: 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.toolbar h2 {
    color: var(--dark);
    font-size: 32px;
    font-weight: 400;
}
</style>