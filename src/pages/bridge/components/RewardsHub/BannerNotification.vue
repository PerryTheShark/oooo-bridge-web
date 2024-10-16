<template>
    <div class="flex items-center p-4 rounded-lg bg-gradient-to-r from-pink-500 via-orange-400 to-orange-300 text-white">
      <span class="text-xl mr-2">🔔</span>
      <span class="text-sm">
        Check in today for 
        <strong class="font-bold">{{ gemMultiplier }}x Gems</strong> if there's any bridging!
        Earn <strong class="font-bold">{{ consecutiveBonus }}x Gems</strong> for each consecutive daily check-in.
      </span>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        gemMultiplier: 5, // Dynamic value for gems
        consecutiveBonus: 2 // Dynamic value for consecutive bonus
      };
    }
  };
  </script>
  
  <!-- No custom CSS needed as Tailwind handles all styles -->
  