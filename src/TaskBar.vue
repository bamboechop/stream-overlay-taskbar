<template>
  <main class="task-bar">
    <hr class="task-bar__border" />
    <div class="task-bar__elements">
      <ButtonComponent
        icon-path="/windows-95/windows.png"
        text="Start" />
      <div class="task-bar__programs">
        <template
          v-for="program of programs">
          <ProgramButton
            :active="program.active"
            :icon-path="program.iconPath"
            :text="program.text" />
        </template>
      </div>
      <StatusAndTimePanel />
    </div>
  </main>
</template>

<script setup lang="ts">
import ButtonComponent from "./components/ButtonComponent.vue";
import StatusAndTimePanel from "./components/StatusAndTimePanel.vue";
import ProgramButton from "./components/ProgramButton.vue";
import { ref } from "vue";

const programs = ref([
  { active: false, iconPath: '/programs/player.icon.png', text: 'Player' },
  { active: true, iconPath: '/programs/chat.icon.png', text: 'Chat' },
  { active: false, iconPath: '/programs/pokemon-community-game.icon.png', text: 'Pokémon Community Game' },
]);
</script>

<style lang="scss" scoped>
.task-bar {
  background-color: #c3c3c3;
  height: 29px;
  padding-top: 2px;

  &__border {
    background-color: #fff;
    border: 0;
    height: 1px;
    margin: 0;
  }

  &__elements {
    display: grid;
    grid-template-columns: 54px 1fr minmax(auto, 114px);
    padding: 2px;
  }

  &__programs {
    display: flex;
    gap: 3px;
    justify-content: start;
  }
}
</style>
