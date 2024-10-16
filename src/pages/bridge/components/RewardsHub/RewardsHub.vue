<script setup lang="ts">
import { OContainer, OHeaderPlus, OContent } from "@/components/OContainer";
import WalletConnectButton from "@/components/layout/WalletConnectButton.vue";
import PageLoading from "@/components/PageLoading.vue";
import { useConfig } from "@/pages/bridge/hooks/use-config";
import { useBalance } from "@/pages/bridge/hooks/use-balance";
import Task from "./Task.vue";
import TaskCard from "./TaskCard.vue";
import Checkin from "./Checkin.vue";
import data_quest from "./quest.json"
const { initializing, from, config } = useConfig();
const balance = useBalance(from, config)

console.log("data_quest", data_quest.quests);
const quests = data_quest.quests;
</script>

<template>
  <OContainer class="oooo-rewards-hub">
    <OHeaderPlus title="_ REWARDS HUB" isClose>
      <div class="flex flex-row items-center justify-between">
        <div
        class="flex md:flex-row md:items-center justify-between mt-[20px] md:mt-0 md:mr-auto"
      >
          <p class="mr-[8px] text-[14px] md:text-base text-[#a4a4a4] -tracking-tighter">
            YOUR ACCOUNT:
          </p>
          <WalletConnectButton />

      </div>
      <p class="md:text-base ml-auto" v-if="balance != null">
            BALANCE: {{ balance }}
          </p>
      </div>

    </OHeaderPlus>

    <OContent>
      <h2 class="-tracking-tighter">DAILY CHECK-IN</h2>
      <Checkin />
    </OContent>

    <OContent>
      <h2 class="-tracking-tighter">QUESTS</h2>
      <div class="flex flex-col md:items-center md:my-4 md:justify-start">
        <Task v-for="(quest, index) in quests" :key="index" :quest="quest" class="w-full" />
      </div>
    </OContent>
  </OContainer>
</template>

<style scoped>
h1 {
  color: #42b983;
}
</style>
