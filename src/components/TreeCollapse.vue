<template>
  <div :class="childClass" class="wrapper">
    <div @click="toggleVisible" class="list-item">
      <div class="icon">
        <i
          v-if="item.child"
          :class="{ 'rotate-90': isVisible }"
          class="fa-solid fa-chevron-right arrow"
        ></i>
      </div>
      <p class="title">{{ item.title }}</p>
    </div>
    <transition name="fade" mode="in-out">
      <div v-if="isVisible">
        <template v-if="item?.child?.length">
          <TreeCollapse
            v-for="item in item.child"
            :key="item.id"
            v-bind="{ item }"
            childClass="p-4"
          />
        </template>
      </div>
    </transition>
  </div>
</template>

<script setup lang="ts">
import { defineProps, ref } from "vue";
interface Props {
  item: {
    title: string;
    id: number;
    child?: {
      title: string;
      id: number;
    }[];
  };
  childClass?: string;
  titleClass?: string;
}
defineProps<Props>();

const isVisible = ref(false);
const toggleVisible = () => {
  isVisible.value = !isVisible.value;
};
</script>

<style scoped lang="scss">
.wrapper {
  cursor: pointer;
  .list-item {
    display: flex;
    gap: 8px;
    align-items: center;
  }
  .icon {
    width: 20px;
    height: 20px;
    display: grid;
    place-items: center;
    .arrow {
      transition: all 0.3s ease;
      font-weight: bold;
      color: limegreen;
    }
  }
  .rotate-90 {
    transform: rotate(90deg);
    transition: all 0.3s ease;
  }
}
.fade-enter-active,
.fade-leave-active {
  transform: translateY(0);
  transition: all 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  transform: translateY(-20px);
  opacity: 0;
}

.p-4 {
  padding-left: 10px;
  padding-top: 6px;
}
</style>
