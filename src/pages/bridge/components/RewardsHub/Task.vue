<script setup lang="ts">
import FOLLOW_TO_EARN_IMAGE from "@/assets/images/goooo-points/follow.png";
import { Button } from "oooo-components/ui/button";
import TaskItem from "./TaskItem.vue";
</script>

<template>
  <TaskItem
    title="COMPLETE MACARON EVENT TO WIN Goooo AND o-VOUCHER"
    description="REWARDS: 2X MACARON DEFI POINTS, 8 Goooo, $20 o-VOUCHER PACK"
    :image="FOLLOW_TO_EARN_IMAGE"
    :hints="['+8 Goooo', '+2X MACARON DEFI POINTS']"
    dateText="Ended."
    class="md:my-[16px]"
  >
    <Button
      class="w-full md:w-[174px]"
      size="sm"
      as="a"
      href="https://competition.macaron.xyz/#/points"
      target="_blank"
    >
      GO TO BRIDGE
    </Button>
  </TaskItem>
</template>

<style lang="scss" scoped></style>
